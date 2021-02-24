# KARTABLE TEST APP (Dev in Progress)
---

IMPORTANT !!!! 

This application is not intended to be deployed in production but is a technical inventory 
of several coding methods (TDD, CQRS etc.) and features. This is not optimized (see Toto at bottom of this readme
to see a list of suggestions / improvements to be made).

## Requirements 

- PHP 7.4+
- MySQL
- Composer
- Symfony

## Install 

```
composer install
bin/console doctrine:database:create
bin/console doctrine:migration:migrate

bin/console doctrine:fixtures:load # to load default fixtures
```

## Launch

```
symfony serve
```

access api with given url (usually http://localhost:8000)

## Features 

- Automatic Testing when code pushed to Github (Github Actions)
- CRUD for Students / Classrooms
- Automatic exam generation (select randomly questions from a pool of questions in database)
- Exam control (only one opened exam by classroom at the same time)
- TODO : Exam statistics
- TODO : Allowing students to answer to exams

## Routes

```
 ------------------ -------- -------- ------ --------------------------
  Name               Method   Scheme   Host   Path                     
 ------------------ -------- -------- ------ --------------------------
  _preview_error     ANY      ANY      ANY    /_error/{code}.{_format}
  add_classroom      POST     ANY      ANY    /api/classrooms
  delete_classroom   DELETE   ANY      ANY    /api/classrooms/{id}
  list_classrooms    GET      ANY      ANY    /api/classrooms
  get_classroom      GET      ANY      ANY    /api/classrooms/{id}
  update_classroom   PUT      ANY      ANY    /api/classrooms/{id}
  create_exam        POST     ANY      ANY    /api/exam
  show_exam          GET      ANY      ANY    /api/exam/{id}
  add_student        POST     ANY      ANY    /api/students
  delete_student     DELETE   ANY      ANY    /api/students/{id}
  list_students      GET      ANY      ANY    /api/students
  get_student        GET      ANY      ANY    /api/students/{id}
  update_student     PUT      ANY      ANY    /api/students/{id}

 ------------------ -------- -------- ------ --------------------------

```


## Todo (improvements)

- Docker implementation
- Use of API Platform (not used here to see some coding methods)
- Use of ParamFetcher on controller to fill DTOs
- Use of AMQP / Redis or equivalent for asynchronous actions (stats calculation etc.)
- Better DDD directories split (Application, InfrastructureBundle, Core, UIBundle)
- Add Swagger and/or Nelmio APIDoc (implemented with API Platform)
- HATEOS hypermedia implementation to cover full RESTFUL levels
- Authentication (Oauth2)

