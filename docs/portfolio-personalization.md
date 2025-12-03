# Portfolio Personalization

## Overview
This document describes the personalization features of the portfolio website, including how to update personal information such as name, about section, and other profile details.

## Architecture

The portfolio uses a centralized data structure located in `src/data/resume.tsx` that contains all personal information. This data is exported as a constant `DATA` object and is used throughout the application.

### Data Structure

The main data object (`DATA`) contains the following key fields:

- **name**: Full name displayed in the hero section and throughout the site
- **initials**: Abbreviated initials used for avatar fallback
- **summary**: About section content displayed on the homepage
- **description**: Short description shown in the hero section
- **avatarUrl**: Path to profile image
- **location**: Current location
- **url**: Portfolio website URL
- **contact**: Contact information including email, phone, and social media links
- **work**: Array of work experience entries
- **education**: Array of education entries
- **projects**: Array of project entries
- **hackathons**: Array of hackathon participation entries
- **skills**: Array of technical skills

## Current Configuration

### Personal Information
- **Name**: Vaibhavi Shri A V
- **Initials**: VSAV
- **Role**: UI/UX Designer
- **Location**: Villupuram, Tamil Nadu
- **Email**: vaibhavishriav@gmail.com
- **Phone**: +919003528924
- **Portfolio URL**: https://vaibhavi284.github.io/Vaibhavishri-av-portfolio/
- **GitHub**: https://github.com/Vaibhavi284
- **LinkedIn**: https://www.linkedin.com/in/vaibhavishri-av
- **WordPress Blog**: https://vaibhavishri.wordpress.com
- **About Section**: "I create clean, simple, and meaningful digital experiences.
My work focuses on understanding users and designing interfaces that feel natural, effortless, and visually pleasing.
I blend clarity, creativity, and functionality to make every interaction smooth, enjoyable, and truly useful."

### Technical Skills
- **Programming Languages**: Python
- **Frontend Development**: HTML, CSS, JavaScript
- **Frameworks & Tools**: Flutter, MySQL

### Work Experience
1. **Software Tester** at NMS Works, IITM Research Park, Chennai (Jan 2023 - Apr 2024)
   - Tested web applications and identified usability issues, and improving user flows.

2. **Design Intern** at The Hindu Group, Anna Salai, Chennai (Jul 2023)
   - Internship Training in Information Technology department. Created banners and supported digital design tasks, gaining hands-on experience in visual layouts and branding.

### Education
1. **Bachelor of Information Technology** (2020-2024)
   - University College of Engineering, Villupuram

2. **HSC** (2018-2020)
   - Saraswathi Matric Higher Secondary School, Villupuram

3. **SSLC** (2017-2018)
   - E.S. Matric Higher Secondary School, Villupuram

### Projects
1. **Automated Weather Classification Using Transfer Learning** (2024)
   - Machine learning model using transfer learning for weather classification

2. **TN EB Bill Calculator – Flutter Application** (2024)
   - Flutter mobile app for calculating Tamil Nadu Electricity Board bills

3. **Breast Cancer Prediction using Deep Learning** (2024)
   - Deep learning model for breast cancer prediction from medical data

4. **My Book – Flutter Mobile Application** (2024)
   - Book management Flutter app (Winner with cash prize at IDHAYA College, Chinasalem)

## Usage

### Updating Name and About Section

To update the name and about section:

1. Open `src/data/resume.tsx`
2. Locate the `DATA` object (starts at line 4)
3. Update the following fields:
   - `name`: Set to your full name
   - `initials`: Set to your initials (typically first letter of each name part)
   - `summary`: Set to your about section content

Example:
```typescript
export const DATA = {
  name: "Your Full Name",
  initials: "YFN",
  summary: "Your about section content here...",
  // ... other fields
}
```

### Adding Work Experience

To add or update work experience entries:

1. Open `src/data/resume.tsx`
2. Locate the `work` array within the `DATA` object
3. Add a new object with the following structure:
   - `company`: Company name
   - `href`: Company website URL (use "#" if not available)
   - `badges`: Array of badge strings (usually empty `[]`)
   - `location`: Job location
   - `title`: Job title
   - `logoUrl`: Path to company logo image (use `""` if not available)
   - `start`: Start date in "Month YYYY" format (e.g., "Jan 2023")
   - `end`: End date in "Month YYYY" format, or `null` for current position
   - `description`: Job description and responsibilities

Example:
```typescript
work: [
  {
    company: "Company Name",
    href: "https://company.com",
    badges: [],
    location: "City, State",
    title: "Job Title",
    logoUrl: "/company-logo.png",
    start: "Jan 2023",
    end: "Apr 2024",
    description: "Job description and key responsibilities.",
  },
  // ... more entries
]
```

**Note**: Work entries are typically ordered with the most recent position first.

### Where This Data is Used

The personal information is displayed in multiple locations:

1. **Hero Section** (`src/app/page.tsx`):
   - Name appears in the greeting: "Hi, I'm {firstName} 👋"
   - Description appears below the name
   - Avatar uses the name and initials

2. **About Section** (`src/app/page.tsx`):
   - Summary content is rendered using Markdown

3. **Work Experience Section** (`src/app/page.tsx`):
   - Work entries are displayed using the `ResumeCard` component
   - Each entry shows company logo, title, location, dates, and description
   - Entries are sorted by date (most recent first)

4. **Site Metadata** (`src/app/layout.tsx`):
   - Name is used in page titles and Open Graph metadata
   - Description is used in meta descriptions

5. **Blog Posts** (`src/app/blog/[slug]/page.tsx`):
   - Name is used as the author in structured data

## API Endpoints

This is a static Next.js site, so there are no API endpoints. All data is statically defined in the `resume.tsx` file.

## Database Changes

No database is used in this portfolio. All data is stored in TypeScript files.

## File Locations

- **Data Source**: `src/data/resume.tsx`
- **Homepage**: `src/app/page.tsx`
- **Layout**: `src/app/layout.tsx`
- **Blog Pages**: `src/app/blog/[slug]/page.tsx`

## Best Practices

1. **Keep Data Centralized**: Always update personal information in `src/data/resume.tsx` rather than hardcoding it in components
2. **Use Markdown**: The summary field supports Markdown syntax for formatting
3. **Update Initials**: When changing the name, remember to update the initials to match
4. **Test Changes**: After updating, verify the changes appear correctly on the homepage and in metadata

## Future Enhancements

Potential improvements:
- Add a CMS integration for easier content management
- Add environment variables for sensitive information
- Create an admin panel for content updates
- Add validation for data structure

