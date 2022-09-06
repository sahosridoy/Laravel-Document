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

# Route Group
### Middileware 
```php
Route::middleware(['first', 'second'])->group(function () { 
    Route::get('/user/profile', function () {
        // Uses first & second middleware...
    });
});

```

### Controller 
```php
use App\Http\Controllers\OrderController;
 
Route::controller(OrderController::class)->group(function () {
    Route::get('/orders/{id}', 'show');
    Route::post('/orders', 'store');
});
```

### Prefixes 
```php
Route::prefix('admin')->group(function () {
    Route::get('/users', function () {
        // Matches The "/admin/users" URL
    });
});
```

### Name Prefixes
```php
Route::name('admin.')->group(function () {
    Route::get('/users', function () {
        // Route assigned name "admin.users"...
    })->name('users');
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
