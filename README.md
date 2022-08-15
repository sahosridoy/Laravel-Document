# Route 
### Basic Route

```php
 Route::get('/test', function () {
    return 'Hello World';
});

// Hello World
```


### View Route

```php
Route::view('/test', 'test');
 
Route::view('/test', 'test', ['name' => 'Sahos']);

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
