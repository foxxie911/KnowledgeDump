- Laravel has its own default action names for an ideal Restful API functions.
- Those action names are:
	- index()
	  logseq.order-list-type:: number
	- store()
	  logseq.order-list-type:: number
	- create()
	  logseq.order-list-type:: number
	- show()
	  logseq.order-list-type:: number
	- update()
	  logseq.order-list-type:: number
	- destroy()
	  logseq.order-list-type:: number
	- edit()
	  logseq.order-list-type:: number
- These actions are called by `Route::resource()` function
	- ```php
	  Route::resource('$URI', $CONTROLLER_CLASS);
	  ```
- All of them will be rarely used. So, using the 3rd argument I can filter out which ones to take.
	- ```php
	  Route::resource('$URI', $CONTROLLER_CLASS, [
	    /*
	    Instead of the dollar sign there will be 
	    the action names that I don't want
	    */
	    'except' => ['$']
	  ]);
	  ```
	- ```php
	  Route::resource('$URI', $CONTROLLER_CLASS, [
	    /*
	    Instead of the dollar sign there will be
	    the action names that I want
	    */
	    'only' => ['$'] 
	  ]);
	  ```