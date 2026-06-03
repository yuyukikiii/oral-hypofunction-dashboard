# Contributing to Oral Hypofunction Dashboard

Thank you for your interest in contributing! This guide will help you get started.

## Getting Started

1. **Fork** the repository
2. **Clone** your fork:
   ```bash
   git clone https://github.com/YOUR-USERNAME/oral-hypofunction-dashboard.git
   cd oral-hypofunction-dashboard
   ```
3. **Create** a feature branch:
   ```bash
   git checkout -b feature/amazing-feature
   ```

## Development

### No Build Tools Required
This is a vanilla JavaScript project with zero dependencies. Simply:

```bash
# Option 1: Direct file open
open index.html

# Option 2: Local server
python -m http.server 8000
# Then visit http://localhost:8000
```

### Browser Testing
Test in:
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ✅ Mobile browsers (iPad, Android)

## Code Style

### HTML
- Use semantic HTML5 tags
- Maintain proper indentation (2 spaces)
- Include ARIA labels for accessibility

### CSS
- Use CSS custom properties (variables) for colors
- Maintain responsive design with CSS Grid/Flexbox
- Follow mobile-first approach

### JavaScript
- Use vanilla JavaScript (no jQuery)
- Keep functions small and focused
- Document complex logic with comments
- Use `const` by default, `let` when needed

## Making Changes

### Data Updates
To add or modify province data, edit the `DATA` object in `index.html`:

```javascript
const DATA = {
  'ProvinceNameThai': {
    region: 'north',
    regionLabel: 'North Region',
    gender: [
      {sex: 'Male', normal: 50.0, hypo: 50.0, nN: 12, nH: 12, nT: 24},
      {sex: 'Female', normal: 44.0, hypo: 56.0, nN: 11, nH: 14, nT: 25}
    ],
    ageData: [
      {age: '60–65 ปี', normal: 88.9, hypo: 11.1},
      // ... more age groups
    ],
    note: 'Clinical observations here'
  }
};
```

### UI Customization

**Change Colors:**
Edit CSS variables at the top of `<style>`:
```css
:root {
  --blue: #006eb6;
  --red: #d32f2f;
  --green: #388e3c;
  --c-north: #1a9e6a;
  --c-northeast: #b8860b;
  --c-central: #e05a1e;
  --c-east: #0f9e98;
  --c-south: #c0185a;
}
```

**Modify Diagnostic Criteria:**
Update the 7-item checklist in the "Oral Hypofunction Diagnosis" section.

### Documentation
If adding features, update relevant docs in `docs/` folder.

## Committing

### Commit Message Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation
- `style` - Code style (formatting)
- `refactor` - Code refactoring
- `test` - Adding tests
- `chore` - Maintenance

**Examples:**
```
feat(data): add Chiang Mai province data
fix(ui): correct region tab styling on mobile
docs(readme): update browser compatibility
```

## Pull Request Process

1. Update `README.md` with any new features
2. Test in all supported browsers
3. Ensure no console errors
4. Create a clear PR description:
   - What problem does this solve?
   - How was it tested?
   - Any breaking changes?

## Contribution Ideas

### 🐛 Bug Fixes
- Fix mobile responsiveness issues
- Correct data display errors
- Improve accessibility

### ✨ Features
- Add export to CSV/PDF
- Create print-friendly layout
- Add statistical calculations
- Support additional languages

### 📚 Documentation
- Expand methodology documentation
- Create video tutorials
- Write API documentation
- Improve code comments

### ♿ Accessibility
- Add keyboard navigation
- Improve screen reader support
- Enhance color contrast
- Add alt text for images

## Questions?

- 📖 Check existing documentation in `docs/`
- 💬 Open an issue for discussion
- 📧 Contact the maintainers

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

**Thank you for helping improve this project! 🙏**
