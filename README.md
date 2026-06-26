# Rujal Counselling Center

A premium, modern, and fully accessible website for Rujal Counselling Center — a psychological counselling clinic in Pune, India, led by Ms. Saloni Suryawanshi.

## Features

- **Semantic HTML5** with proper heading hierarchy
- **WCAG 2.1 AA** accessible design (keyboard navigation, focus indicators, ARIA labels, screen reader friendly)
- **SEO optimized** with Open Graph, Twitter Cards, JSON-LD structured data, sitemap, and robots.txt
- **Mobile-first responsive** design with no horizontal scrolling
- **Performance optimized** with lazy loading, deferred scripts, and optimized images
- **Interactive features:** breathing exercise, mood support finder, service tabs, gallery with lightbox, booking form with validation
- **No frameworks** — pure HTML5, CSS3, and vanilla JavaScript (ES6)

## Project Structure

```
rujal-counselling/
├── index.html
├── css/
│   ├── style.css         # Global styles, components, layout
│   ├── animations.css    # Reveal animations, breathing keyframes
│   └── responsive.css    # Breakpoints: 768px, 1024px, 1280px
├── js/
│   ├── app.js            # Navigation, scroll reveal, mood/services tabs, utilities
│   ├── booking.js        # Form validation, Google Sheets integration, WhatsApp
│   ├── gallery.js        # Lightbox, swipe, keyboard navigation
│   └── breathing.js      # Interactive breathing exercise
├── images/
├── favicon/
├── robots.txt
├── sitemap.xml
├── manifest.json
└── README.md
```

## Setup

1. Clone the repository
2. Open `index.html` in a browser, or serve via any static hosting
3. Replace `PASTE_YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE` in `js/booking.js` with your Google Apps Script Web App URL
4. Add your images to the `images/` folder
5. Add favicons to the `favicon/` folder

## Google Sheets Integration

The booking form saves appointments to Google Sheets via Google Apps Script. After a successful save, it automatically opens WhatsApp with the appointment details.

### Google Sheets Columns

| Column | Data |
|--------|------|
| Timestamp | Submission date/time |
| Name | Client name |
| Phone | WhatsApp number |
| Email | Email address |
| Concern | Selected concern |
| Session Type | In-person / Online / Ask first |
| Preferred Date | Selected date |
| Preferred Time | Selected time |
| Message | Optional message |
| Status | "New" |

### Google Apps Script Code

```javascript
function doPost(e) {
  const data = JSON.parse(e.postData.contents);
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  sheet.appendRow([
    data.submittedAt,
    data.name,
    data.phone,
    data.email,
    data.concern,
    data.mode,
    data.preferredDate,
    data.preferredTime,
    data.message,
    data.status
  ]);
  return ContentService.createTextOutput(JSON.stringify({result: 'success'}))
    .setMimeType(ContentService.MimeType.JSON);
}
```

Deploy as a Web App with "Execute as me" and "Anyone" access.

## Design System

- **Colors:** Sage green (`#5f8f8b`), warm clay (`#b68b7a`), soft ink (`#24383d`), mist (`#f7faf9`)
- **Fonts:** Playfair Display (serif headings), Inter (sans-serif body)
- **Spacing:** CSS custom properties for consistent scale
- **Shadows:** Soft, layered shadows for depth
- **Border radius:** 12px to 32px for a calm, friendly aesthetic

## Browser Support

- Chrome / Edge (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)
- Mobile Safari / Chrome

## License

All rights reserved. Rujal Counselling Center.
