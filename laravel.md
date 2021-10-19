## install composer

> folder

```
composer --create-project --prefer-dist laravel/laravel foldername

```

> http://localhost/laravel-essentials/public/

## The first page
> views > welcome.blade.php

```
@extends ('layouts.app')

@section('content')
<h1>Hello World!</h1>
```

> views > layouts > app.blade.php
```
 @yield('content')
```