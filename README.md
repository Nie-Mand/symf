# Symfony Sheet

## Creating a Project : Composer

```sh
> composer create-project symfony/framework-standard-edition project_name
```

## Running Server

```sh
> php bin/console server:run
```

## Controller Example

```php
<?php
    namespace AppBundle\Controller;

    use Symfony\Component\HttpFoundation\Response;
    use Symfony\Component\Routing\Annotation\Route;
    use Symfony\Bundle\FrameworkBundle\Controller\Controller;

    class SomeController extends Controller {
        /**
         * @Route("/path")
        */
        public function index() {
            return $this->render('template_file.html.twig', [
                // Data
            ]);
        }
    }
?>
```

## Routing

```php
<?php
    namespace AppBundle\Controller;

    use Symfony\Component\HttpFoundation\Response;
    use Symfony\Component\Routing\Annotation\Route;
    use Symfony\Bundle\FrameworkBundle\Controller\Controller;

    class SomeController extends Controller {
    /**
         * @Route("/path")
         * WildCards :
         * @Route("/path/{somth}")
         * WildCards with Requirements (RegEx) :
         * @Route("/path/{user_id}/{movie_name}", requirements = {"user_id"="\d+"})
        */
        $url = $this->generateUrl(
            'blog_show',
            ['slug' => 'my-blog-post']
        );

        public function index($somth = DEFAULT_VALUE) {
            return $this->render('template_file.html.twig', [
                // Data
            ]);
        }
    }
?>
```

### Generating URLs : IDK

```php
<?php
?>
```

## Templates

```
{{ data }}
{{ data | filters }} // upper, lower, sort...

{% if condition %}
{% elseif %}
{% else %}
{% endif %}

{% for item in items %}
{% endfor %}

{% block BLOCK %}{% endblock %}
{% extends 'where_to_use' %}

{ include('some_file.html.twig', { 'data': data }) }}
```

## Databases

### Create Database (Server Should be Working)

```sh
> php bin/console doctrine:database:create
```

### Create a Table (Entity)

```php

namespace AppBundle\Entity;

use Doctrine\ORM\Mapping as ORM;

/**
 * @ORM\Entity
 * @ORM\Table(name="table_name")
 */
class TableName {

    /**
     * @ORM\Column(type="integer")
     * @ORM\Id
     * @ORM\GeneratedValue(strategy="AUTO")
     */

    private $id;

    /**
     * @ORM\Column(type="string", length=200)
     */

    private $something;
}

```

### Add Getters and Setters

```sh
> php bin/console doctrine:generate:entities AppBundle
```

### Check Tables

```sh
> php bin/console doctrine:schema:validate
```

### Update Changes

```sh
> php bin/console doctrine:schema:update --force
```
