# Portfolio Website - Freelance IT Professional

A modern, responsive portfolio website built with Vue.js 3 and Vite, designed for freelance IT professionals and developers. This portfolio showcases services, projects, skills, and provides an easy way for potential clients to get in touch.

## 🌟 Features

- **Modern Design**: Clean, professional layout with smooth animations and transitions
- **Responsive**: Mobile-first design that works perfectly on all devices
- **Interactive**: Dynamic portfolio filtering, skill progress bars, and contact forms
- **SEO Optimized**: Proper meta tags, semantic HTML, and fast loading times
- **Accessible**: WCAG compliant with proper ARIA labels and keyboard navigation

## 🛠️ Technologies Used

- **Vue.js 3** - Progressive JavaScript framework with Composition API
- **Vite** - Fast build tool and development server
- **CSS3** - Modern styling with Grid, Flexbox, and custom properties
- **Font Awesome** - Professional icons
- **Google Fonts** - Inter font family for modern typography

## 📦 Installation

1. Clone the repository:
```bash
git clone <your-repo-url>
cd portfolio
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Build for production:
```bash
npm run build
```

## 🔧 Configuration

### Personal Information
Update your personal information in `src/App.vue`:

```javascript
const personalInfo = {
  name: 'Your Name',
  title: 'Your Professional Title',
  description: 'Your professional description',
  profileImage: 'path/to/your/photo.jpg',
  socialLinks: [
    { name: 'GitHub', url: 'https://github.com/yourusername', icon: 'fab fa-github' },
    // Add your social links
  ]
}
```

### Skills & Experience
Customize your skills and experience in `src/components/About.vue`:

```javascript
skills: [
  { name: 'JavaScript/TypeScript', level: 95 },
  { name: 'Vue.js/React', level: 90 },
  // Add your skills
]
```

### Services
Update your services and pricing in `src/components/Services.vue`

### Portfolio Projects
Add your projects in `src/components/Portfolio.vue`:

```javascript
projects: [
  {
    id: 1,
    title: 'Project Name',
    category: 'Web Apps',
    image: 'project-image.jpg',
    // Add project details
  }
]
```

### Contact Information
Update contact details in `src/components/Contact.vue` and `src/components/Footer.vue`

## 📱 Sections

1. **Header** - Fixed navigation with smooth scrolling
2. **Hero** - Introduction with call-to-action buttons
3. **About** - Skills, experience, and personal background
4. **Services** - Offered services with pricing
5. **Portfolio** - Project showcase with filtering
6. **Contact** - Contact form and information
7. **Footer** - Additional links and contact details

## 🎨 Customization

### Colors
The website uses a consistent color scheme. Main colors can be updated in CSS:

- Primary: `#3498db` (Blue)
- Secondary: `#f39c12` (Orange)
- Dark: `#2c3e50`
- Light: `#f8f9fa`

### Fonts
The website uses Inter font from Google Fonts. You can change it in `index.html` and update the CSS font-family.

### Images
Replace placeholder images with your actual photos and project screenshots:

- Profile photo: Update `profileImage` in personalInfo
- Project images: Update image URLs in portfolio projects
- Optimize images for web (WebP format recommended)

## 📧 Contact Form

The contact form includes validation and user feedback. To make it functional:

1. Replace the form submission logic in `src/components/Contact.vue`
2. Integrate with your preferred backend service (Node.js, PHP, etc.)
3. Or use a service like Formspree, Netlify Forms, or EmailJS

## 🚀 Deployment

### Netlify (Recommended)
1. Build the project: `npm run build`
2. Deploy the `dist` folder to Netlify
3. Set up continuous deployment with your Git repository

### Vercel
1. Connect your GitHub repository to Vercel
2. Set build command: `npm run build`
3. Set output directory: `dist`

### GitHub Pages
1. Install gh-pages: `npm install --save-dev gh-pages`
2. Add deploy script to package.json: `"deploy": "gh-pages -d dist"`
3. Run: `npm run build && npm run deploy`

## 🔍 SEO Optimization

- Update meta tags in `index.html`
- Add Open Graph and Twitter Card meta tags
- Create a sitemap.xml
- Add structured data (JSON-LD)
- Optimize images with alt tags

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](../../issues).

## 📞 Support

If you have any questions or need help with customization, feel free to reach out or create an issue.

---

**Made with ❤️ using Vue.js and Vite**
