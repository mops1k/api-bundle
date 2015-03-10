# mops1k/api-bundle

Symfony fast RESTful API generator installation

## Installation
```
php composer.phar require mops1k/api-bundle dev-master
```

## Settings
#### add to app/AppKernel.php
```
    $bundles = array(
            // ...
            new FOS\RestBundle\FOSRestBundle(),
            new JMS\SerializerBundle\JMSSerializerBundle($this),
            new Sylius\Bundle\ResourceBundle\SyliusResourceBundle(),
            new Sylius\Bundle\TranslationBundle\SyliusTranslationBundle(),
            new WhiteOctober\PagerfantaBundle\WhiteOctoberPagerfantaBundle(),
            new Bazinga\Bundle\HateoasBundle\BazingaHateoasBundle(),
            new mops1k\ApiBundle\mops1kApiBundle(),
            // ...
        );
```

#### Import resource
```
#app/config/config.yml
imports:
    ...
    - { resource: '@mops1kApiBundle/Resources/config/api.yml' }
```

#### Create service
```
#app/config/config.yml
sylius_resource:
    resources:
        service.user: #service name
            driver: doctrine/orm
            classes:
                model: Entity #entity for api
                controller: Sylius\Bundle\ResourceBundle\Controller\ResourceController
                repository: Sylius\Bundle\ResourceBundle\Doctrine\ORM\EntityRepository
```

#### Add routing
```
#@YourBundle/Resource/config/config.yml
amtelcom_users_rest_users:
    prefix: /api #required
    resource: service.user #service name
    type: sylius.api
```

# Enjoy it!
