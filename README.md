# Laravel Union Paginator

## Russian ReadMe
Russian ReadMe [here](README_ru.md)

## About
Paginator for questions, with Union

## Install

```$bash
composer require kaizer666/laravel-union-paginator
```

## Usage

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