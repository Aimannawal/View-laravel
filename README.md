## Cara View Data Pada Database Di Laravel
Halo kali ini saya akan membantu anda cara view database di laravel

**Step 1**
--
1 . Pastikan anda telah menginstall extension yang kami sarankan untuk mempermudah pengerjaan
```
laravel blade snippets dan laravel snippets
```
2 . Jika sudah maka pastikan sudah ada model dan jangan lupa beri protected $fillable pada file model (sesuaikan dengan tabel)
```
protected $fillable = [         
        'nama',         
        'kelas',         
        'alamat',    
    ];
```
3 . buatlah controller 
```
php artisan make:controller MahasiswaController -r
```
4 . Buka Controller yang baru dibuat
5 . Gunakan kode ini didalam class index pada controller yang baru saja dibuat
```
public function index()
{
$Mahasiswa = Mahasiswa::get();

return view('Mahasiswa.index', compact('Mahasiswa'));
}
```
6 . Setelah itu buka file routes/web.php tambahkan kode berikut 
```
Route::get('/', [MahasiswaController::class, 'index'])->name('Mahasiswa');
```
7 . Lalu masuk ke file resources/views/file yang di return view pada Controller tadi
```
<table>
        <thead>
                <tr>
                <th>Nama</th>
                <th>Kelas</th>
                <th>Alamat</th>
                </tr>
        </thead>
        <tbody>
                @foreach ($Mahasiswa as $item)
                <tr>
                <td>{{ $item->name }}</td>
                <td>{{ $item->kelas }}</td>
                <td>{{ $item->alamat }}</td>
                </tr>
                @endforeach
        </tbody>
</table>
```
NB: Jangan lupa php artisan serve 

## Data Anda Berhasil Di Views
