- Laravel has its own default action names for an ideal Restful API functions.
- Those action names are:
	1. index()
	2. store()
	3. create()
	4. show()
	5. update()
	6. destroy()
	7. edit()
- These actions are called by `Route::resource()` function

```php
	  Route::resource('$URI', $CONTROLLER_CLASS);
```

- All of them will be rarely used. So, using the 3rd argument I can filter out which ones to take
```php
	  Route::resource('$URI', $CONTROLLER_CLASS, [
	    /*
	    Instead of the dollar sign there will be 
	    the action names that I don't want
	    */
	    'except' => ['$']
	  ]);
```

```php
	  Route::resource('$URI', $CONTROLLER_CLASS, [
	    /*
	    Instead of the dollar sign there will be
	    the action names that I want
	    */
	    'only' => ['$'] 
	  ]);
```