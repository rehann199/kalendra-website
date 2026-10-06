# Product Overview

## What the site is

The public front door for Kalendra, an AI assistant for scheduling. Its tagline in the page metadata is "Your AI assistant for everything scheduling." The site explains the idea, shows it through animation and collects early-access sign-ups. The app itself is not part of this repository and is described on the site as not yet in general release.

Live site: [getkalendra.com](https://getkalendra.com/)

## What a visitor sees, top to bottom

| Section | Purpose | Notes |
|---|---|---|
| Header | Logo, "Features" and "Insights" anchors, "Get Early Access Now" button | Anchors scroll to sections on the same page |
| Hero | Headline "Kalendra, my week is a mess can we clean it up?", short pitch, community link | Animated wave logo and scrolling suggestion chips such as "Friday cleared" |
| Trusted | Positioning line for power users and managers, with a list of job titles | Glass lens ticker |
| Talk to Kalendra | Shows the conversational idea | Looping chat between a user and Kalendra |
| Capabilities | Three feature cards: natural language (voice-first), all calendars in one place, free slots and insights | Animated diagram linking Kalendra to Google, Outlook and Zoom |
| Vision | Mission statement | Typewriter text and a voice prompt card |
| User stories | Section for testimonials | Currently shows a "not in general release yet" message; the testimonial cards are commented out in source |
| Early access form | Waitlist | Email, role, OS |
| Footer | Privacy, Terms, social links, "Powered by" credit | Privacy and Terms open as dialogs |

## Calls to action

- **Get Early Access Now** in the header scrolls to the form.
- **Join Community** in the hero links out to a community group.
- **Store badges** for the App Store and Google Play exist in the source, but are hidden by CSS and have placeholder links, which matches the pre-release status.

## The early-access form

Fields: email (required), role (required, eight options from founder to student) and operating system (required, Android or iOS). On success the form shows a thank-you overlay and locks, and the entry is delivered by email through a third-party service. The form itself is not a user account or login.

## Product claims versus implementation

Statements about voice control, multi-calendar conflict checks and insights are marketing copy describing the product. The website does not implement any of them; it demonstrates them with scripted animation. This repository documents the website only.
