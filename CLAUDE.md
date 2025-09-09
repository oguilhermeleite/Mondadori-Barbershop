# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-file HTML website for **Mondadori Barbershop**, a premium barbershop located in Curitiba, PR. The entire application is contained in `index.html` with inline CSS and JavaScript - no external dependencies or build tools required.

## Architecture & Structure

**Single-File Architecture**: Everything is contained in `index.html`:
- HTML structure with semantic sections
- CSS styles embedded in `<style>` tags (lines 11-667)
- JavaScript functionality in `<script>` tags (lines 1024-1217)
- External dependencies: Font Awesome CDN for icons

**Key Sections**:
- Header with navigation and mobile hamburger menu
- Hero section with CTA button
- About section (Diego's story)
- Services grid (14 individual services)
- Packages section (4 special packages)
- Booking form with WhatsApp integration
- Contact section with map
- Footer with social links

## Core Features

**WhatsApp Integration**: The booking form generates a formatted WhatsApp message and redirects users to WhatsApp with pre-filled text. The message format is defined in the `setupFormSubmission()` function (lines 1113-1163).

**Responsive Design**: Mobile-first approach with breakpoints at 768px and 480px. Mobile menu transforms to hamburger navigation.

**Form Validation**: 
- Phone number masking for Brazilian format
- Date validation excluding Sundays/Mondays
- Required field validation
- Business hours: Tuesday-Friday 10h-20h, Saturday by appointment

**Business Information**:
- Phone: (41) 98432-5356
- Address: Rua Marechal Hermes, 2055, Curitiba-PR
- Instagram: @mondadori.barbershop
- Closed: Sundays and Mondays

## Development Commands

Since this is a static HTML file, no build process is required:

**Development**: Open `index.html` directly in a browser or use a simple HTTP server:
```bash
# Using Python (recommended for local development)
python -m http.server 8000

# Using Node.js http-server (if installed)
npx http-server

# Or simply open index.html in a browser
```

**Testing**: Manual testing in browser, no automated tests configured.

## Customization Points

**Service Prices**: Update in two places:
- Service cards display (lines 727-812)  
- Booking form options (lines 867-888)

**Business Hours**: Modify `generateTimeSlots()` function (lines 1050-1070) and date validation (lines 1073-1092)

**Color Scheme**: CSS custom properties in `:root` (lines 18-27):
- `--primary-gold: #FFD700`
- `--secondary-gold: #B8860B`  
- `--accent-orange: #FFA500`

**WhatsApp Message Template**: Located in form submission handler (lines 1130-1148)

## Technical Details

**CSS Framework**: Vanilla CSS with:
- CSS Grid and Flexbox for layouts
- Custom properties for theming
- Responsive design with media queries
- Smooth animations and transitions

**JavaScript Features**:
- Mobile menu toggle
- Form validation and phone masking
- WhatsApp message generation
- Smooth scrolling navigation
- Intersection Observer for scroll animations

**External Resources**:
- Font Awesome 6.4.0 for icons
- Google Maps embed for location
- Logo image: `./assets/Mondadori.jpg`

## Important Notes

**Logo Image**: The site references `./assets/Mondadori.jpg` - ensure this file exists for proper logo display.

**Phone Number Format**: All phone numbers should follow Brazilian WhatsApp format: +55 41 98432-5356

**Date Restrictions**: Booking system automatically blocks Sundays and Mondays (business closed days).

**Form Submission**: No server-side processing - all bookings go through WhatsApp integration.