category:: [[SoftTech]]
tags:: #laravel

- Controller files created in the `app/Http/Controllers` path.
- Type `php artisan make:controller` to create a controller class.
- Every route functionality belonging to the same [[Entity]] usually written as the functions of one Controller class.
- There is only one line of code in the `web.php` file for each controller function.
	- ```php
	  Route.get("/jobs", [App\Http\Controllers\JobController::class, '$FUNCTION_NAME']);
	  Route.post("/jobs", [App\Http\Controllers\JobController::class, '$FUNCTION_NAME']);
	  Route.patch("/jobs", [App\Http\Controllers\JobController::class, '$FUNCTION_NAME']);
	  Route.delete("/jobs", [App\Http\Controllers\JobController::class, '$FUNCTION_NAME']);
	  ```
- It's also possible to group all the routes belonging to the same controller class.
	- ```php
	  Route::controller(App\Http\Controllers\JobController::class)->group(function(){
	    	Route.get("/jobs",'$FUNCTION_NAME');
	  	Route.post("/jobs", '$FUNCTION_NAME');
	  	Route.patch("/jobs", '$FUNCTION_NAME');
	  	Route.delete("/jobs",'$FUNCTION_NAME');
	  });
	  ```
- If a Controller class is passed to `Route::resource('$URI', '$CONTROLLER_CLASS')`, it will register all the [[Laravel Default Restful Actions]] automatically.