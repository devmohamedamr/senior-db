#  dbwrapper 

dbwrapper is a small php wrapper for mysql databases.

## installation

install once with composer:

```
composer require seniorclass/Db
```

then add this to your project:

```php
require __DIR__ . '/vendor/autoload.php';
use Senior\Db\db;
$db = new db($server,$user,$pass,$db);
```

## usage

```php
/* connect to database */
$db = new db('127.0.0.1', 'username', 'password', 'database', 3306);

/* insert/update/delete */
$id = $db->insert('tablename', ['col1' => 'foo'])->excu();
$db->update('tablename', ['col1' => 'bar'])->where(['id' => $id])->excu();
$db->delete('tablename')->where(['id' => $id])->excu();

/* select */
$db->select('tablename','columns')->getAll();
$db->select('tablename','columns')->getRow();
$db->select('tablename','columns')->where(['id' => $id])->getRow();

$db->select('tablename','columns')->where(['id' => $id])->andWhere(['id' => $id])->getRow();

$db->select('tablename','columns')->where(['id' => $id])->orWhere(['id' => $id])->getRow();

```

