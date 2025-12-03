# Figma Embed Feature

## Overview
This feature allows embedding interactive Figma prototypes directly into project cards in the portfolio. Users can view and interact with Figma prototypes without leaving the portfolio page.

## Implementation Details

### Project Data Structure
Projects in `src/data/resume.tsx` can now include a `figma` field that contains the Figma prototype embed URL:

```typescript
{
  title: "Food Delivery App",
  href: "https://www.figma.com/proto/...",
  dates: "2024",
  active: true,
  description: "...",
  technologies: [...],
  links: [],
  image: "",
  video: "",
  figma: "https://www.figma.com/proto/O50P16aA3OsGvELekZULPI/Untitled?node-id=34-91&embed-host=share",
}
```

### Component Updates

#### ProjectCard Component
The `ProjectCard` component (`src/components/project-card.tsx`) has been updated to support Figma embeds:

1. **New Prop**: Added `figma?: string` to the Props interface
2. **Conditional Rendering**: 
   - If `figma` prop is provided, an iframe is rendered with the Figma prototype
   - The iframe is NOT wrapped in a Link component to allow full interactivity
   - If `figma` is not provided, the component falls back to video or image rendering

3. **Iframe Configuration**:
   - Height: 500px for optimal viewing
   - Full width with responsive design
   - `pointer-events-auto` to enable interactions
   - `allowFullScreen` for fullscreen viewing
   - Proper accessibility with title attribute

### Figma URL Format
Figma prototype embed URLs should follow this format:
```
https://www.figma.com/proto/{file-id}/{file-name}?node-id={node-id}&embed-host=share
```

The `&embed-host=share` parameter is required for proper embedding.

## Usage

### Adding a Figma Project
1. Open your Figma prototype
2. Click "Share" and copy the prototype link
3. Add `&embed-host=share` to the end of the URL
4. Add the project to `src/data/resume.tsx` with the `figma` field populated

### Example
```typescript
{
  title: "Food Delivery App",
  href: "https://www.figma.com/proto/O50P16aA3OsGvELekZULPI/Untitled?node-id=34-91",
  figma: "https://www.figma.com/proto/O50P16aA3OsGvELekZULPI/Untitled?node-id=34-91&embed-host=share",
  // ... other fields
}
```

## Features
- **Interactive Prototypes**: Users can click, scroll, and interact with the Figma prototype directly in the portfolio
- **Responsive Design**: The iframe adapts to different screen sizes
- **Accessibility**: Proper title attributes for screen readers
- **Fallback Support**: If no Figma URL is provided, the component falls back to video or image display

## Technical Notes
- The iframe is rendered outside the Link wrapper to prevent interaction blocking
- Height is set to 500px for optimal viewing experience
- Background colors adapt to light/dark theme
- The component maintains backward compatibility with existing projects using images or videos

## Browser Compatibility
Figma embeds work in all modern browsers that support iframes. The prototype interactions depend on Figma's embed functionality.

