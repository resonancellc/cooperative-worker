# Cooperative worker

[![Software License][ico-license]](LICENSE.txt)

Class for executing jobs from one list in several processes.
Class not have mechanism to create processes, consumer must create it by self.
Each separate process can create instance of class wich will work with shared storage without collisions.
Temporary storage of jobs will be created in first instance of class and it be use all of instances.

## Requirements

*   PHP >= 7.1

## Install

Install with [Composer](http://getcomposer.org):
    
```bash
composer require php-strict/cooperative-worker
```

## Usage

cw.php

```php
use PhpStrict\CooperativeWorker\CooperativeWorker

$cw = new CooperativeWorker(
    function() {
        return ['job 1', 'job 2', 'job 3', 'job 4', 'job 5'];
    }, 
    function(string $job) {
        echo 'Strart job: ' $job . PHP_EOL;
        //do some job
    }
);
$cw->run();
```

cw.bat

```bat
start php -f cw.php
start php -f cw.php
```

[ico-license]: https://img.shields.io/badge/license-GPL-brightgreen.svg?style=flat-square