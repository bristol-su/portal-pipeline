# Portal Code Style
> Bring your coding style in line with the Bristol SU Portal Guidelines

## Installation

Pull in this project
```shell
composer require bristol-su/portal-code-style
```

Add the following files to the root of your project:

Create a .php_cs.dist file in your project. You can find an example in [`./vendor/bristol-su/portal-code-style/examples/.php_cs.dist.example`](examples/.php_cs.dist.example)
Create a rector.php file in your project. You can find an example in [`./vendor/bristol-su/portal-code-style/examples/rector.php`](examples/rector.php)
Create a phpstan.neon configuration file in your project. You can find an example in [`./vendor/bristol-su/portal-code-style/examples/phpstan.neon`](examples/phpstan.neon)


Add the following to your composer scripts

```
    "scripts": {
        "test": "vendor/bin/phpunit --colors=always --process-isolation --verbose --configuration phpunit.xml",
        "code-style": [
            "vendor/bin/php-cs-fixer fix --config .php_cs --dry-run --verbose --using-cache=no",
            "vendor/bin/rector process --dry-run --output-format=console"
        ],
        "fix-code-style": "vendor/bin/php-cs-fixer fix --config .php_cs --verbose --using-cache=no",
        "phpstan": "vendor/bin/phpstan analyse --configuration ./phpstan.neon"
        "coverage": "vendor/bin/phpunit --colors=always --process-isolation --verbose --configuration phpunit.xml --coverage-html coverage"
    }
```

## Github Actions

You can now set up a github workflow using the actions we provide. See examples of all these at [`./vendor/bristol-su/portal-code-style/examples/workflow.php`](examples/workflow.yml)

## Commands

You can also run the following commands locally

`composer run test`: Run the entire testsuite
`composer run code-style`: Dry run all our coding checks to make sure your code will pass the pipeline
`composer run fix-code-style`: Fix any minor formatting issues automatically
`composer run phpstan`: Run the static analysis engine on the current code
`composer run coverage`: Generate code coverage for the package

