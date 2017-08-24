# Laravel Union Paginator

## Оригинальное ReadMe
Оригинальное ReadMe [здесь](README.md)

## Описание
Paginator для запросов, выполняемых через Union

## Установка

```$bash
composer require kaizer666/laravel-union-paginator
```

## Использование

```$php
use Union\UnionPaginator;

function test() {
    $data = Model::select(["id", "firstname"])
      ->whereIn("id", [1,2,3]);
    $data2 = OtherModel::select(["id", "firstname"])
      ->whereIn("id", [4,5,6])
      ->union($data);
    $paginator = new UnionPaginator();
    $response = $paginator
      ->setQuery($data2)
      ->setCurrentPage(28)
      ->setPerPage(20)
      ->getPaginate();
    return response()->json(
      $response
    );
}