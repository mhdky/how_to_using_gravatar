# Cara Menggunakan Gravatar Pada Laravel

1. Instal package Gravatar melalui Composer dengan menjalankan perintah berikut di terminal

```
composer require creativeorange/gravatar
```

2. Masukan kode dibawah pada controller atau file web.php diinginkan
```php
use Creativeorange\Gravatar\Facades\Gravatar;
use Illuminate\Support\Facades\Auth;

Route::get('/', function () {
    if (Auth::check()) {
        $email = Auth::user()->email;
        $profilePhotoUrl = Gravatar::get($email);
    } else {
        $profilePhotoUrl = null;
    }

    return view('home', [
        'title' => 'Home',
        'profil' => $profilePhotoUrl
    ]);
});
```

3. Tangkap variable ` profil ` dan masukan ke file blade yang diinginkan
```html
<img src="{{ $profil }}" alt="profil" class="w-full h-full object-cover">
```
