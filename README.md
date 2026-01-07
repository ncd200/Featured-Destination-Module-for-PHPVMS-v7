**CHANGELOG**

Fixed Database problem
Fixed Remove Image
Fixed Image Upload



# FeaturedDestination Module (phpVMS v7)

A standalone **admin-driven Featured Destinations** module for phpVMS v7.
It lets you mark airports as “featured”, attach images and marketing text, optionally set a featured time window, and display them on your front page using a responsive grid with a click-to-open modal (hero image + details).
---

## Requirements

- phpVMS v7
- A working `airports` table
- Public storage disk enabled for image uploads

---

## Installation

### 1. Place the module
Copy the module to:

/modules/FeaturedDestination

### 2. Enable the module
phpVMS automatically loads modules from the `/modules` directory.

### 3. Clear caches (recommended)

php artisan cache:clear
php artisan view:clear
php artisan config:clear

### 4. Database setup
Tables are created automatically on first load via the ServiceProvider.
No migrations are used.

## Admin Usage

### Settings
Admin → Featured Destinations → Settings

Configure:
- Enable/disable module
- Featured count
- Rotation mode (manual or random)

### Airport Directory
Admin → Featured Destinations → Airport Directory

For each airport you can:
- Mark as featured
- Set priority
- Add title, subtitle, description
- Upload image or use image URL
- Define featured from / to dates

Expired airports are automatically hidden.

---

## Widget Installation (Front-end)

### Widget class

\Modules\FeaturedDestination\Widgets\FeaturedDestinationsWidget::render()

### Basic usage

{!! \Modules\FeaturedDestination\Widgets\FeaturedDestinationsWidget::render() !!}

## Layout Behavior

- Up to 4 airports per row on desktop
- Always centered (1–4 items)
- Tablet: 2 per row
- Mobile: 1 per row

---

## Image Priority

1. Image URL
2. Uploaded image
3. Fallback image

---

## Troubleshooting

Widget empty:
- Module enabled?
- Airports marked as featured?
- Featured dates valid?

Images missing:
- Run php artisan storage:link
- Verify image URLs

---

## Updating

Replace module files and clear cache.
Schema updates are applied automatically.

---

## Notes

- No core phpVMS files are modified
- Safe to update
- CSS and JS are self-contained in the widget view
