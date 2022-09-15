# توابع Common

این توابع عمومی هستند، ممکن است هر کجا استفاده شوند و در سراسر برنامه در دسترس هستند.



## arrayOrderBy

```php
arrayOrderBy($args = []) : array;
```

این تابع برای مرتب‌سازی آرایه‌ها براساس کلیدها و مقدارها است، مانند مرتب‌سازی پایگاه‌های داده.

استفاده از این تابع می‌تواند مانند کد زیر باشد:

```php
arrayOrderBy($data, '{key1}', SORT_DESC, '{key2}', SORT_ASC)
```

ورودی اول آرایه‌ای است که می‌خواهیم آن را مرتب کنیم.

ورودی دوم نام کلیدی است که می‌خواهیم مرتب‌سازی براساس آن انجام شود.

ورودی سوم مشخص می‌کند که مرتب‌سازی صعودی باشد یا نزولی.

ورودی‌های بعدی می‌تواند کلیدهای دیگر و نوع مرتب‌سازی آنها باشد.



**مقدار بازگشتی**

مقدار بازگشتی همان آرایه ورودی است که براساس تنظیمات مرتب شده است.



**نمونه**:

```php
$data = [];
$data[] = array('vol' => 67, 'version' => 2);
$data[] = array('vol' => 86, 'version' => 1);
$data[] = array('vol' => 85, 'version' => 6);
$data[] = array('vol' => 98, 'version' => 2);
$data[] = array('vol' => 86, 'version' => 6);
$data[] = array('vol' => 67, 'version' => 7);

$result = LiteFramework\arrayOrderBy($data, 'vol', SORT_DESC, 'version', SORT_ASC);
```

در کد فوق از تابع خواسته شده مرتب‌سازی را ابتدا براساس کلید vol انجام دهد و آن را به صورت نزولی مرتب کند و مرتب‌سازی کلید version را به‌صورت صعودی انجام دهد. در نتیجه مقدارهای vol از بزرگ به کوچک مرتب می‌شود و مقدارهای version از کوچک به بزرگ.

خروجی:

```php
Array
(
    [0] => Array
        (
            [vol] => 98
            [version] => 2
        )

    [1] => Array
        (
            [vol] => 86
            [version] => 1
        )

    [2] => Array
        (
            [vol] => 86
            [version] => 6
        )

    [3] => Array
        (
            [vol] => 85
            [version] => 6
        )

    [4] => Array
        (
            [vol] => 67
            [version] => 2
        )

    [5] => Array
        (
            [vol] => 67
            [version] => 7
        )
)
```



## getMaxFileUploadSize

```php
getMaxFileUploadSize() : int;
```

این تابع حداکثر مقدار مجاز برای آپلود فایل را برمی‌گرداند. تنظیمات مربوط به post_max_size و upload_max_filesize در PHP INI بررسی می‌کند و حداکثر مقدار مجاز را برمی‌گرداند.



**مقدار بازگشتی**

مقدار بازگشتی integer است و حداکثر اندازهٔ مجاز برای آپلود به‌صورت بایت (Byte) است.



**نمونه**:

```php
$result = LiteFramework\getMaxFileUploadSize();
// $result == 67108864
```



## convertPhpSizeToBytes

```php
function convertPhpSizeToBytes(string $sSize) : int;
```

این تابع برای تبدیل سایزهای string که در php.ini مشخص شده به بایت (Byte) است. برای مثال مقدار '2M' را به‌عنوان ورودی دریافت می‌کند و خروجی می‌شود 2097152.



**مقدار بازگشتی**

مقدار بازگشتی integer است.



**نمونه**:

```php
$result = LiteFramework\convertPhpSizeToBytes('5M');
// $result == 5242880
```



## getValue

```php
getValue(array& $array, string $key, $defaultValue = false);
```

این دستور در واقع همان دستور array_key_exists است اما می‌تواند یک مقدار پیش‌فرض را بگیرد تا اگر کلید مورد نظر وجود نداشت مقدار پیش‌فرض را باز گرداند. راهی برای ساده‌تر کردن کدنویسی.



**مقدار بازگشتی**

مقدار بازگشتی می‌تواند هر نوعی باشد.



**نمونه**:

```php
$result = LiteFramework\getValue($_GET, 'key', false);
if ($result === false) {
    // error handling
}

// OR
$myArray['test'] = 1;
$result = LiteFramework\getValue($myArray, 'key', 100);
echo $result; // output 100
```

