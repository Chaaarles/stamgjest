# Stamgjest - Party Planning CRM

Stamgjest is a simple party-planning Customer Relationship Management (CRM) system built with Laravel. It helps event organizers manage events, guests, RSVPs, feedback, and post-event reflections.

## Overview

This project is currently under development. It will provide tools for managing events, guests, RSVPs, feedback collection, and post-event reflections.

## Tech Stack

- Laravel 12.0 with PHP 8.4
- Blade templates with Tailwind CSS
- Livewire components with Alpine.js

## Quick Start

```bash
# Clone the repository
git clone https://github.com/chaaarles/stamgjest.git
cd stamgjest

# Install dependencies
composer install
npm install

# Set up environment
cp .env.example .env
php artisan key:generate

# Run migrations and build assets
php artisan migrate
npm run build

# Start the development server
php artisan serve
```

## Documentation

- [Code Quality](CODE_QUALITY.md) - Information about code quality tools and standards

## License

This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
