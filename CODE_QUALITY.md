# Code Quality Tools

This document outlines the code quality tools used in the Stamgjest project and how to use them.

## PHP Code Quality Tools

### Laravel Pint

[Laravel Pint](https://laravel.com/docs/10.x/pint) is an opinionated PHP code style fixer for Laravel projects. It's built on top of PHP-CS-Fixer and comes with a pre-configured set of rules that follow Laravel's coding style.

**Usage:**
```bash
# Check for code style issues
composer lint

# Fix code style issues
composer fix
```

### PHPStan

[PHPStan](https://phpstan.org/) is a static analysis tool that finds errors in your code without running it. It's configured to run at level 8 (the strictest level) to ensure high code quality.

**Usage:**
```bash
# Analyze code for potential issues
composer analyze
```

## JavaScript/CSS Code Quality Tools

### Prettier

[Prettier](https://prettier.io/) is an opinionated code formatter that supports many languages, including JavaScript, TypeScript, CSS, and HTML. It's configured with the Tailwind CSS plugin to automatically sort Tailwind CSS classes.

**Usage:**
```bash
# Check for formatting issues
npm run lint

# Fix formatting issues
npm run format
```

## Running All Quality Checks

You can run all quality checks at once using the following command:

```bash
composer quality
```

## Recommended Additional Tools

Here are some additional code quality tools that could be beneficial for the project:

### PHP Tools

1. **Larastan** - A PHPStan extension for Laravel that provides additional Laravel-specific rules and checks.
   ```bash
   composer require --dev nunomaduro/larastan
   ```

2. **PHP Mess Detector (PHPMD)** - Scans code for potential problems like unused variables, overcomplicated expressions, and more.
   ```bash
   composer require --dev phpmd/phpmd
   ```

3. **PHP Copy/Paste Detector (PHPCPD)** - Finds duplicated code in your PHP files.
   ```bash
   composer require --dev sebastian/phpcpd
   ```

### JavaScript/Frontend Tools

1. **ESLint** - A linting utility for JavaScript and TypeScript that helps identify and fix problems in your code.
   ```bash
   npm install --save-dev eslint
   ```

2. **Stylelint** - A linter for CSS/SCSS files.
   ```bash
   npm install --save-dev stylelint stylelint-config-standard
   ```

### Git Hooks

1. **Husky** - Allows you to run scripts before committing or pushing code.
   ```bash
   npm install --save-dev husky
   ```

2. **lint-staged** - Run linters on git staged files.
   ```bash
   npm install --save-dev lint-staged
   ```

## Integration with CI/CD

Consider setting up GitHub Actions or another CI/CD system to automatically run these quality checks on every pull request and push to the repository.

Example GitHub Actions workflow:

```yaml
name: Code Quality

on:
  push:
    branches: [ main, develop ]
  pull_request:
    branches: [ main, develop ]

jobs:
  quality:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: '8.2'
          
      - name: Install Composer dependencies
        run: composer install --prefer-dist --no-progress
        
      - name: Install NPM dependencies
        run: npm ci
        
      - name: Run PHP linting
        run: composer lint
        
      - name: Run PHP static analysis
        run: composer analyze
        
      - name: Run JavaScript/CSS linting
        run: npm run lint
```

## Best Practices

1. Always run quality checks before committing code
2. Fix issues as they are found rather than letting them accumulate
3. Gradually increase strictness levels as the project matures
4. Document any exceptions or special cases in the code
