# VOLBET UI Components Library

Reusable Astro components for the VOLBET website, following design system specifications.

## Components Overview

### 1. **Button.astro**
Universal button component with multiple variants and sizes.

**Props:**
- `variant`: 'primary' | 'secondary' | 'tertiary' (default: 'primary')
- `href`: Optional URL for anchor tag rendering
- `size`: 'default' | 'large' (default: 'default')
- `class`: Additional CSS classes

**Variants:**
- **Primary**: Orange background, white text (main CTAs)
- **Secondary**: Orange border, orange text (secondary actions)
- **Tertiary**: Text-only, orange color (minimal style)

**Usage:**
```astro
<Button variant="primary">Click me</Button>
<Button variant="secondary" href="/services">Learn More</Button>
<Button variant="tertiary" size="large">Explore</Button>
```

---

### 2. **Card.astro**
Flexible card component with support for default and service variants.

**Props:**
- `title`: Card title
- `description`: Short description
- `image`: Featured image URL (default variant)
- `imageAlt`: Alt text for image
- `link`: Optional href for CTA
- `linkText`: Link text (default: 'Learn more')
- `variant`: 'default' | 'service' (default: 'default')
- `icon`: Emoji or icon for service cards
- `class`: Additional CSS classes

**Variants:**
- **Default**: Standard card with flexible content, image support
- **Service**: Icon, title, description, and CTA link

**Usage:**
```astro
<!-- Default Card -->
<Card title="Service Title" description="Description">
  <p>Card content here</p>
</Card>

<!-- Service Card -->
<Card 
  variant="service"
  title="Spoiwa Mineralne"
  description="Best-in-class mineral binders"
  icon="⚙️"
  link="/oferta/spoiwa"
  linkText="View Details"
/>
```

---

### 3. **Input.astro**
Text input field with label, validation, and error states.

**Props:**
- `label`: Label text
- `name`: Input name attribute (required)
- `type`: 'text' | 'email' | 'tel' | 'number' | 'password' | 'url' | 'date' (default: 'text')
- `placeholder`: Placeholder text
- `required`: Boolean (default: false)
- `error`: Error message to display
- `help`: Helper text below label
- `value`: Default value
- `disabled`: Boolean (default: false)
- `class`: Additional CSS classes

**Features:**
- Orange focus border (design system)
- Error state styling
- Helper text support
- Disabled state

**Usage:**
```astro
<Input 
  label="Email" 
  name="email" 
  type="email" 
  required 
/>
<Input 
  label="Company" 
  name="company" 
  error="This field is required" 
/>
```

---

### 4. **Textarea.astro**
Multi-line text input with validation, error states, and character counter.

**Props:**
- `label`: Label text
- `name`: Textarea name attribute (required)
- `placeholder`: Placeholder text
- `rows`: Number of visible rows (default: 5)
- `required`: Boolean (default: false)
- `error`: Error message
- `help`: Helper text
- `value`: Default value
- `disabled`: Boolean (default: false)
- `maxLength`: Max character length
- `showCounter`: Show character counter (default: false)
- `class`: Additional CSS classes

**Features:**
- Orange focus border
- Error state styling
- Optional character counter
- Warning/exceeded states for counter

**Usage:**
```astro
<Textarea 
  label="Message" 
  name="message" 
  rows={6}
  required 
/>
<Textarea 
  label="Notes" 
  name="notes" 
  maxLength={500}
  showCounter
/>
```

---

### 5. **Navigation.astro**
Sticky header with logo, navigation links, and mobile hamburger menu.

**Props:**
- `logo`: Logo image URL
- `logoAlt`: Logo alt text
- `links`: Navigation links array (NavLink[])
- `companyName`: Company name for branding (default: 'VOLBET')
- `sticky`: Sticky positioning (default: true)
- `class`: Additional CSS classes

**NavLink Structure:**
```typescript
{
  label: string;
  href: string;
  submenu?: NavLink[]; // Optional dropdown submenu
}
```

**Features:**
- Responsive design (desktop nav, mobile hamburger)
- Dropdown support for submenu items
- Auto-close on link click
- Hamburger menu animation
- Sticky positioning option

**Usage:**
```astro
<Navigation 
  logo="/logo.svg"
  logoAlt="VOLBET"
  companyName="VOLBET"
  links={[
    { label: 'Home', href: '/' },
    { 
      label: 'Services', 
      href: '/services',
      submenu: [
        { label: 'Spoiwa', href: '/services/spoiwa' },
        { label: 'Torkretowanie', href: '/services/torkretowanie' }
      ]
    },
    { label: 'Projects', href: '/projects' },
    { label: 'About', href: '/about' },
    { label: 'Contact', href: '/contact' }
  ]}
/>
```

---

### 6. **Footer.astro**
Responsive footer with company info, links, contact details, and newsletter signup.

**Props:**
- `companyName`: Company name
- `companyDescription`: Short description
- `address`: Company address
- `email`: Contact email
- `phone`: Contact phone
- `socialLinks`: Social media links (FooterLink[])
- `quickLinks`: Quick navigation links (FooterLink[])
- `serviceLinks`: Service links (FooterLink[])
- `copyrightText`: Copyright text
- `showNewsletter`: Show newsletter form (default: true)
- `class`: Additional CSS classes

**FooterLink Structure:**
```typescript
{
  label: string;
  href: string;
}
```

**Features:**
- 3-column layout (desktop), stacked (mobile)
- Integrated contact information
- Social media links
- Newsletter subscription form
- Responsive design
- Dark theme

**Usage:**
```astro
<Footer 
  companyName="VOLBET"
  companyDescription="Professional mining materials supplier"
  address="Ul. Górnicza 123, 40-001 Katowice"
  email="info@volbet.pl"
  phone="+48 32 123 4567"
  socialLinks={[
    { label: 'LinkedIn', href: '#' },
    { label: 'Facebook', href: '#' }
  ]}
  quickLinks={[
    { label: 'Home', href: '/' },
    { label: 'About', href: '/about' },
    { label: 'Contact', href: '/contact' }
  ]}
  serviceLinks={[
    { label: 'Spoiwa Mineralne', href: '/services/spoiwa' },
    { label: 'Torkretowanie', href: '/services/torkretowanie' }
  ]}
  showNewsletter={true}
/>
```

---

### 7. **Form.astro**
Form wrapper with consistent styling, validation, and submission handling.

**Props:**
- `action`: Form action URL
- `method`: 'GET' | 'POST' (default: 'POST')
- `title`: Form title
- `description`: Form description
- `showSuccess`: Show success message (default: true)
- `successMessage`: Custom success message
- `validateOnBlur`: Enable blur validation (default: true)
- `class`: Additional CSS classes

**Features:**
- Form validation feedback
- Success message animation
- Blur-based validation
- Email validation support
- Flexible field layout

**Usage:**
```astro
<Form 
  title="Contact Us"
  description="Get in touch with our team"
  action="/api/contact"
  method="POST"
>
  <Input label="Name" name="name" required />
  <Input label="Email" name="email" type="email" required />
  <Textarea label="Message" name="message" required rows={6} />
  <Button variant="primary" type="submit">Send Message</Button>
</Form>
```

---

## Design System Integration

All components use the VOLBET design system colors and typography:

### Colors
- **Navy Blue (Primary):** `#1A2332` — Headings, primary text
- **Orange (Accent):** `#D97706` — CTAs, highlights
- **White:** `#FFFFFF` — Backgrounds
- **Light Gray (BG):** `#F8FAFC` — Section backgrounds
- **Medium Gray (Text):** `#475569` — Body text

### Typography
- **Font:** Inter (sans-serif)
- **Heading Scale:** 48px → 12px
- **Line Heights:** 1.2–1.8
- **Font Weights:** 400 (regular), 600 (semibold), 700 (bold)

### Spacing
- **Base Unit:** 8px
- **Scale:** 4px, 8px, 16px, 24px, 32px, 48px, 64px

---

## Installation & Setup

1. Components are located in `/src/components/`
2. Import components in your Astro pages:

```astro
---
import Button from '../components/Button.astro';
import Card from '../components/Card.astro';
import Navigation from '../components/Navigation.astro';
---

<Navigation {...navProps} />
<Button variant="primary">Get Started</Button>
<Card variant="service" {...cardProps} />
```

3. All components use Tailwind CSS classes for styling
4. Design system colors are injected as CSS variables

---

## Best Practices

1. **Accessibility:** All components support proper ARIA attributes and semantic HTML
2. **Responsive:** Mobile-first design with breakpoints at 640px, 768px, 1024px
3. **Performance:** Minimal JavaScript, favoring CSS for interactivity
4. **Reusability:** Props-based API for maximum flexibility
5. **Type Safety:** JSDoc comments for IDE autocomplete (TypeScript optional)

---

## Component Checklist

- ✅ Button.astro — Variants (primary, secondary, tertiary), sizes
- ✅ Card.astro — Default and service variants, image support
- ✅ Input.astro — Text input with validation and error states
- ✅ Textarea.astro — Multi-line input with character counter
- ✅ Navigation.astro — Sticky header with mobile menu and dropdowns
- ✅ Footer.astro — Responsive footer with newsletter form
- ✅ Form.astro — Form wrapper with validation handling

**Total Components:** 7
**Status:** COMPLETE ✅
