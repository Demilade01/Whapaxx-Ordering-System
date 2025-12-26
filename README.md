# Whapaxx Ordering System

A complete restaurant ordering system built with vanilla HTML, CSS, and JavaScript. This system provides a customer-facing ordering interface, kitchen display board, and admin management tools—all synchronized via browser LocalStorage.

## Overview

This is a self-contained web-based ordering system designed for restaurants. It consists of four main interfaces that work together to manage the entire order lifecycle:

1. **Customer Interface** - Browse menu and place orders
2. **Kitchen Board** - Track orders through preparation stages
3. **Approval/Dispatch** - Manage order approval and dispatch workflow
4. **Admin Control** - Configure opening hours and stock levels

## Features

### Customer Interface (`Customer.html`)
- 🍕 **Menu Display** - Browse products with images, prices, and descriptions
- 🛒 **Shopping Cart** - Add items with variations, add-ons, and condiments
- ⏰ **Kitchen Hours** - Automatic closure display when kitchen is closed
- 💳 **Pay-at-Counter** - Submit orders for in-person payment
- 📱 **Responsive Design** - Works on desktop, tablet, and mobile devices

### Kitchen Board (`Kitchen-board.html`)
- 📋 **Three-Lane Display** - Pending, Preparing, and Ready columns
- 🔄 **Status Progression** - Move orders through preparation stages
- 📊 **Order Details** - View customer name, buzzer number, items, and condiments
- 🔔 **Live Updates** - Real-time synchronization with admin interface

### Approval/Dispatch (`Approval-Dispatch.html`)
- ✅ **Order Approval** - Review and approve/reject submitted orders
- 🔢 **Buzzer Management** - Automatic assignment of 24 buzzers
- 📦 **Order Tracking** - Board view with four columns (Approvals, Pending, Preparing, Ready)
- 📁 **Archive System** - Store completed orders
- 📊 **Sales Reports** - Export CSV reports (supports iOS Share API)
- 🔍 **Search & Filter** - Find orders by customer, order number, buzzer, or item

### Admin Control (`Hours-Stock.html`)
- ⏰ **Opening Hours** - Configure weekly schedule with enable/disable per day
- 📦 **Stock Management** - Mark items and variations as in stock/sold out
- 🔢 **Quantity Tracking** - Track quantities for items and variations
- 📱 **Touch-Friendly** - Optimized for tablet use in restaurant settings

## Technical Details

### Architecture
- **No Backend Required** - All data stored in browser LocalStorage
- **Cross-Tab Sync** - Uses `storage` events for real-time updates across tabs
- **No Dependencies** - Pure vanilla JavaScript, HTML, and CSS
- **Offline-First** - Works entirely client-side

### Data Storage

The system uses LocalStorage with the following keys:
- `whapaxx_orders_v2` - Active orders
- `whapaxx_orders_archive_v1` - Archived/completed orders
- `whapaxx_hours_v1` - Opening hours configuration
- `whapaxx_stock_v2` - Stock levels for items and variations

### Order Workflow

1. **Customer** places order → Status: `Submitted`
2. **Admin** approves order → Status: `Pending` (assigns order # and buzzer)
3. **Kitchen** starts preparing → Status: `Preparing`
4. **Kitchen** marks ready → Status: `Ready`
5. **Dispatch** marks collected → Moved to Archive

## File Structure

```
.
├── Customer.html           # Customer ordering interface
├── Kitchen-board.html      # Kitchen display board
├── Approval-Dispatch.html  # Admin order management
└── Hours-Stock.html        # Admin configuration panel
```

## Usage

### Setup

1. Open any of the HTML files in a modern web browser
2. No installation or build process required
3. All files can be served from any static file server

### Typical Workflow

1. **Admin Setup** (`Hours-Stock.html`):
   - Configure opening hours for each day
   - Set up stock levels for menu items

2. **Customer Ordering** (`Customer.html`):
   - Customers browse menu and add items to cart
   - Select variations, add-ons, and condiments as needed
   - Submit order with their name

3. **Order Management** (`Approval-Dispatch.html`):
   - Review submitted orders in "Approvals" column
   - Approve orders (assigns order number and buzzer)
   - Track orders through Pending → Preparing → Ready
   - Archive completed orders

4. **Kitchen Operations** (`Kitchen-board.html`):
   - View orders in Pending lane
   - Click "Start Preparing" to move to Preparing lane
   - Click "Mark Ready" when order is complete

### Multi-Device Setup

For a restaurant setup:
- Open `Customer.html` on customer-facing tablets/kiosks
- Open `Kitchen-board.html` on kitchen display screens
- Open `Approval-Dispatch.html` on admin/dispatch station
- Open `Hours-Stock.html` on admin management device

All instances automatically sync via LocalStorage events when running in the same browser (Chrome/Edge profiles or different browsers on the same device).

**Note:** For true multi-device synchronization, you would need to implement a backend server. Currently, synchronization works best when all tabs are in the same browser instance.

## Menu Configuration

The menu is hardcoded in `Customer.html`. To modify the menu, edit the `MENU` array in the JavaScript section. Each item can have:
- `id` - Unique identifier
- `title` - Display name
- `price` - Base price
- `image` - Image URL
- `variations` - Array of variation options (e.g., ["Bacon", "Chicken", "Fish"])
- `condiments` - Boolean flag for condiment selection
- `condimentOptions` - Array of available condiments
- `addons` - Array of add-on items with their own prices

## Browser Compatibility

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)
- Requires LocalStorage support
- Requires ES6+ JavaScript support

## Design

- **Dark Theme** - Blue/purple color scheme optimized for display screens
- **Responsive Layout** - Adapts to different screen sizes
- **Touch-Friendly** - Large buttons and touch targets
- **Accessibility** - Semantic HTML and ARIA labels

## License

This appears to be a proprietary system for "Whapaxx" restaurant/gaming establishment.

## Notes

- All data is stored locally in the browser—clearing browser data will delete all orders
- For production use with multiple devices, consider implementing a backend API
- The system currently supports 24 buzzers (configurable in code)
- Sales reports are exported as CSV files

