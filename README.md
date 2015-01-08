Error
=====

CakePHP 2.x Error messages plugin

Include Error by adding 

```php
App::uses('Error', 'Error.Lib');
```

to the AppController and use as follows:

```php
Error::add('Your message', Error::TypeError);
Error::add('Your message', Error::TypeWarning);
Error::add('Your message', Error::TypeInfo);
Error::add('Your message', Error::TypeOk);
```

To display errors you can use something like this:

```php
<?php
$errors = Error::getAll();
if ($errors) {
	foreach ($errors as $type=>$group) {
		switch ($type) {
			case Error::TypeOk 	:
				$style = 'success';
				break;
			case Error::TypeWarning :
				$style = 'warning';
				break;
			case Error::TypeError :
				$style = 'danger';
				break;
			case Error::TypeInfo :
				$style = 'info';
				break;
		}
		?>
<div class="alert alert-<?= $style; ?> fade in">
	<button type="button" class="close" data-dismiss="alert" aria-hidden="true">×</button>
	
		<?php
		foreach ($group as $error) {
			echo '<p><i class="fa fa-check-circle fa-fw fa-lg"></i>'.$error.'</p>';
		}
		?>
</div>
<?php
	}
	Error::clear();
}

```