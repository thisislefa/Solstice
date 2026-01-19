# Brand Reviews Flip Card Component

An interactive testimonial showcase featuring flip cards that reveal brand reviews. Each card displays a company logo on the front and flips to show a detailed testimonial with client information when clicked. Built with pure HTML, CSS, and minimal JavaScript for a smooth 3D flip animation.

<img width="1920" height="1071" alt="solstice" src="https://github.com/user-attachments/assets/d12e384c-dec8-41cd-bb8b-2f1f7ecdc96c" />

## Live Preview

[View Live Demo](https://lefajmofokeng.github.io/Solstice)

## Features

- **Interactive Flip Cards**: Click-to-flip animation with 3D perspective
- **Responsive Grid Layout**: 4-column desktop, 3-column tablet, 2-column mobile, 1-column small mobile
- **Minimalist Design**: Clean white cards on beige background with black/grey accents
- **FontAwesome Icons**: Custom icons for each brand/logo
- **Smooth Animations**: CSS 3D transforms with custom easing
- **Accessible**: Semantic HTML with proper button roles
- **No Dependencies**: Pure HTML/CSS/JS - no frameworks or libraries
- **Mobile-First**: Fully responsive with touch-friendly interactions

## Design System

### Colors
- **Background**: `#F8F8F5` (Beige)
- **Card Background**: `#FFFFFF` (White)
- **Primary Text**: `#000000` (Black)
- **Secondary Text**: `#6B7280` (Grey)
- **Accent Border**: `#E5E7EB` (Light Grey)

### Typography
- **Font Family**: Inter (400, 500, 600, 700, 800 weights)
- **Text Transform**: Uppercase for headings and labels
- **Font Sizes**: 14px to 32px hierarchy

### Spacing
- **Grid Gap**: 20px
- **Card Padding**: 40px
- **Button Position**: 24px from edges

## Project Structure

```
├── index.html          # Main HTML structure
├── style.css          # All styling and animations
└── README.md          # This documentation file
```

## Quick Start

1. **Clone or download** the repository
2. **Open** `index.html` in any modern web browser
3. **Click** on any card to flip it and read the testimonial
4. **Click** the × button to flip back

## Setup Instructions

### Local Development
```bash
# Clone the repository
git clone https://github.com/thisislefa/Solstice.git

# Navigate to project directory
cd brand-reviews-component

# Open in browser
open index.html  # macOS
start index.html # Windows
xdg-open index.html # Linux
```

### Online Deployment
1. **Netlify**: Drag and drop the folder to Netlify Drop
2. **Vercel**: Import Git repository
3. **GitHub Pages**: Push to GitHub and enable Pages in repository settings

## Customization Guide

### Adding New Cards
Add a new card to the `.bs-grid` container in `index.html`:

```html
<div class="bs-card" id="card-9">
    <div class="bs-card-inner">
        <div class="bs-card-front">
            <button class="bs-toggle-btn" onclick="toggleCard('card-9')">
                <i class="fa-solid fa-plus"></i>
            </button>
            <div class="bs-logo-wrapper">
                <!-- Add your icon and text here -->
                <i class="fa-brands fa-your-icon bs-logo-icon"></i>
                <span>YourBrand</span>
            </div>
        </div>
        <div class="bs-card-back">
            <button class="bs-toggle-btn" onclick="toggleCard('card-9')">
                <i class="fa-solid fa-xmark"></i>
            </button>
            <p class="bs-review-text">
                "Your testimonial text here."
            </p>
            <div class="bs-author-info">
                <span class="bs-author-name">Author Name</span>
                <span class="bs-author-role">Author Role</span>
            </div>
        </div>
    </div>
</div>
```

### Modifying Colors
Edit the CSS variables in `style.css`:

```css
:root {
    --bg-color: #F8F8F5;
    --card-bg: #FFFFFF;
    --primary-text: #000000;
    --secondary-text: #6B7280;
    --border-color: #E5E7EB;
}
```

### Changing Icons
Replace FontAwesome icons with any from the [FontAwesome library](https://fontawesome.com/icons):
- Use `fa-brands` for brand icons
- Use `fa-solid` for solid icons
- Use `fa-regular` for regular icons

### Adjusting Animation Speed
Modify the transition duration in `.bs-card-inner`:
```css
.bs-card-inner {
    transition: transform 0.6s cubic-bezier(0.4, 0.0, 0.2, 1);
    /* Change 0.6s to adjust speed */
}
```

## Responsive Behavior

| Breakpoint | Columns | Card Height | Layout |
|------------|---------|-------------|---------|
| > 1200px   | 4       | Square      | Desktop |
| 901-1200px | 3       | Square      | Tablet  |
| 601-900px  | 2       | Square      | Tablet  |
| ≤ 600px    | 1       | 350px       | Mobile  |

## Browser Support

- **Chrome 36+** (Full support)
- **Firefox 16+** (Full support)
- **Safari 9+** (Full support)
- **Edge 79+** (Full support)
- **Opera 23+** (Full support)

*Note: 3D transforms may have reduced performance on older browsers.*

## Performance Features

- **Hardware Acceleration**: 3D transforms use GPU for smooth animations
- **Minimal JavaScript**: Only 3 lines of JS for the flip functionality
- **Optimized Assets**: FontAwesome loaded from CDN with proper preconnect hints
- **Efficient CSS**: Minimal reflows and repaints during animations
- **Aspect Ratio**: Maintains perfect squares without JavaScript

## Testing

### Manual Testing Checklist
- [ ] All cards flip correctly
- [ ] Cards flip back when clicked again
- [ ] Responsive behavior on all breakpoints
- [ ] Hover effects on buttons
- [ ] Touch interactions on mobile
- [ ] No layout shifts during animation
- [ ] Proper text alignment in both states

### Accessibility Testing
- [ ] Keyboard navigation (Tab/Enter)
- [ ] Screen reader compatibility
- [ ] Sufficient color contrast
- [ ] Focus indicators
- [ ] ARIA labels (if needed)

## Integration Guide

### As a Standalone Component
Simply copy the HTML, CSS, and JS into your project. Ensure you include:
1. FontAwesome CDN link
2. Google Fonts Inter link
3. The flip card JavaScript function

### With a Framework (React Example)
```jsx
import React, { useState } from 'react';
import './style.css';

const FlipCard = ({ id, logo, review, author, role }) => {
  const [flipped, setFlipped] = useState(false);
  
  return (
    <div className={`bs-card ${flipped ? 'flipped' : ''}`}>
      <div className="bs-card-inner">
        {/* Front side */}
        <div className="bs-card-front">
          <button className="bs-toggle-btn" onClick={() => setFlipped(!flipped)}>
            <i className="fa-solid fa-plus"></i>
          </button>
          <div className="bs-logo-wrapper">
            {logo}
          </div>
        </div>
        
        {/* Back side */}
        <div className="bs-card-back">
          <button className="bs-toggle-btn" onClick={() => setFlipped(!flipped)}>
            <i className="fa-solid fa-xmark"></i>
          </button>
          <p className="bs-review-text">{review}</p>
          <div className="bs-author-info">
            <span className="bs-author-name">{author}</span>
            <span className="bs-author-role">{role}</span>
          </div>
        </div>
      </div>
    </div>
  );
};
```

## License

This project is open source and available under the [MIT License](https://github.com/thisislefa/Solstice/blob/main/LICENSE).

## Acknowledgments

- **FontAwesome** for the beautiful icons
- **Google Fonts** for the Inter typeface
- **CSS-Tricks** for flip card inspiration
- **Unsplash** for placeholder imagery ideas

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Cards not flipping | Check JavaScript console for errors |
| Icons not loading | Ensure FontAwesome CDN is accessible |
| Animation choppy | Reduce animation duration or check GPU acceleration |
| Layout broken on mobile | Check viewport meta tag |
| Text overflow | Adjust padding or font sizes |

## Future Enhancements

1. **Auto-flip carousel** for automatic rotation
2. **Hover effects** without click on desktop
3. **Multiple card states** (selected, active, disabled)
4. **Dynamic content loading** from JSON/API
5. **Custom color themes** with toggle
6. **Print styles** for better printing
7. **Accessibility improvements** with ARIA labels
8. **Performance optimizations** for older devices

## Support

For issues, questions, or contributions:
1. Open an issue on GitHub
2. Submit a pull request
3. Contact the maintainer

---

*Built with pure HTML, CSS, and JavaScript. No frameworks, no build steps, just clean code.*




