# Route 
### Basic Route

```php
use App\Http\Controllers\UserController;
 
Route::get('/user', [UserController::class, 'index']);
```


### View Route

```php
Route::view('/test', 'test');
 
Route::view('/test', 'test', ['name' => 'Sahos']);    // With Parameter

```

### Redirect Route

```php
Route::redirect('/here', '/there');
```

### Named Route

```php
Route::get('/user/profile', [UserProfileController::class, 'show'])->name('profile');
```

### Route Parameters
```php
//Single Parameter
Route::get('/user/{id}', function ($id) {
    return 'User '.$id;
});

//Multiple Parameter
Route::get('/posts/{post}/comments/{comment}', function ($postId, $commentId) {
    //
});


//Optional Parametrer
Route::get('/user/{name?}', function ($name = 'John') {
    return $name;
});

```





If you want to see all route list, then run this code on your terminal.

```sh
php artisan route:list
```




### Basic Controllers

```php

// Route 
Route::get('/user/{id}', [UserController::class, 'show']);

//Controller
namespace App\Http\Controllers;
 
use App\Http\Controllers\Controller;
use App\Models\User;
 
class UserController extends Controller
{
    public function show($id)
    {
        return view('user.profile', [
            'user' => User::findOrFail($id)
        ]);
    }
}



```
