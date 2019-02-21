# create-bundle-symfony4

If you want to create a reusable bundle, do the following things.

## Folder for your own bundle(s)

First, create a folder on the root of your project which will contains your bundle.  
For instance, libs/ can be the folder you need.

## Create your bundle

Secondly, you can now create your bundle.  
For example, libs/MyBundle/MyBundle.php.  
Don't forget to create a tests folder inside your bundle.

Your new class have to extends the Bundle class:

```php
<?php 

namespace My\Own\Namespace;

use Symfony\Component\HttpKernel\Bundle\Bundle;

class MyBundle extends Bundle
{
}

```
## Edit your composer.json

Thirdly, you have to tell where is your bundle and what is his namespace.  

```json
"autoload": {
        "psr-4": {
            "App\\": "src/",
            "My\\Own\\Namespace\\": "libs/MyBundle/"
        }
    },
    "autoload-dev": {
        "psr-4": {
            "App\\Tests\\": "tests/",
            "My\\Own\\Namespace\\Tests\\": "libs/MyBundle/tests/"
        }
    },
```

## Update your composer

If you have installed composer globally, run `composer dump-autoload`.  
Else, run `php path/to/composer.phar dump-autoload`.

## Load your bundle

Finally, you have to load your bundle in the config/bundles.php file.  
For instance,  
```php
<?php

return [
    ...
    \My\Own\Namespace\MyBundle::class => ['all' => true]
];
```

Here is the video (in French) that show you what I've explain here.  
https://www.youtube.com/watch?v=sNmpddaseK8&t=2659s
