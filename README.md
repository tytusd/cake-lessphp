## LESS Helper

This little Helper converts your .less files into .css without relying on Node.js or client-side parsing.
Everything is compiled on the server, cached, and served as regular css through PHP.

Forked from flug/CakeLess because of leafo/lessphp doesn't compatible with Twitter Bootstrap 3. Now 
oyejorge/less.php is using instead

## Installation


#### Git Submodule

In your cakephp's root directory type

	git submodule add https://github.com/SongPhi/cake-lessphp.git app/Plugin/CakeLess
	git submodule init
	git submodule update

#### Git clone

In your cakephp's root directory type

    git clone https://github.com/SongPhi/cake-lessphp.git app/Plugin/CakeLess

#### Composer

In your root cakephp, edit your composer.json to fit:

```json
"require": {
	"composer/installers": "*",
	"songphi/cakephp-less": "dev-master",
	"oyejorge/less.php": "~1.7"
},
"extra": {
	"installer-paths": {
		"app/Plugin/{$name}/": ["songphi/cakephp-less"]
	}
}
```

#### Plugin Loading

In your app/Config/bootstrap.php add this line:

```php
CakePlugin::load('CakeLess');
```

It doesn't need if you already have this line:

```php
CakePlugin::loadAll();
```

### Create cache and less folders

- Create a folder `app/webroot/less`
- Create a folder `app/tmp/cache/less`
- Apply `chmod 777` to your `css` folder. (The Less Helper will place all compiled css files in your css-directory)

## Usage
Where you want to use LESS files, add the helper. Usually this will be your `AppController`.

```php
public $helpers = array('CakeLess.Less');
```

Next, simply add the less files to your views:

```php
echo $this->Less->css('yourfile');
```

or if the less file is located in the webroot of a plugin

```php
echo $this->Less->css('yourfile',array('plugin' => 'PluginFolderName'));
```

or

```php	
echo $this->Less->css(array(
		'bootstrap/bootstrap',
		'prettify',
	)
);
```

