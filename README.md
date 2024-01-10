# CacheBundle
Простой хелпер для подключения/использования кеша, оформленный как Symfony bundle.
```
autowire: CacheHelper $cacheHelper
$this->cacheHelper->getCache() // вернет стандартный Symfony\Component\Cache\Adapter\MemcachedAdapter
```

CacheTrait содержит удобную обертку для кеширования справочных и т.п. данных

```
use CacheTrait;
//$force - флаг обязывающий насильно перестроить кеш
public function getEvents($force = false){

        $callback = function(){
            $rows = ...; // get data form DB
            ... // some process data
            return $rows;
        };
        return $this->cached('cache_variable_name', $callback, $force);
    }
```

## Установка 
`composer require justcommunication/wb-cache-bundle`

## Подключение
Прописать в /config/services.yaml:
```
parameters:
    ...    
    memcache:
        host: 127.0.0.1
        port: 11211
        namespace: 'tb'
        lifetime: 86400
```

// Новая версия 0.2.0