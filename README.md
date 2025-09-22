# 💎 Page Prism - Project Overview & Technical Documentation

## Project Summary

Page Prism is a **design inspiration management application** built for designers and developers who need to collect, organize, and manage visual inspirations for their projects. The application allows users to capture screenshots from websites, organize them into projects, and maintain detailed notes about what makes each inspiration valuable.

## 🎯 Core Functionality

### Primary Features
1. **Project Management**
   - Create and manage design inspiration projects
   - Each project contains a collection of inspirations
   - Full CRUD operations for projects (Create, Read, Update, Delete)

2. **Inspiration Collection**
   - Capture screenshots of websites and save them as inspirations
   - Store website metadata including title, description, favicon, and Open Graph data
   - Add personal notes to each inspiration
   - Link inspirations to specific projects

3. **Data Persistence**
   - Uses IndexedDB for local storage (simulating a backend database)
   - All data persists across browser sessions
   - Mock API latency to simulate real network requests

4. **Responsive UI**
   - Mobile-responsive design using Tailwind CSS
   - Component-based architecture with CSS modules
   - Navigation system with desktop and mobile variants

## 🏗️ Technical Architecture

### Technology Stack
- **Frontend Framework**: React 18 with TypeScript/JavaScript (mixed)
- **Build Tool**: Vite
- **Routing**: React Router DOM v6
- **Styling**: Tailwind CSS + CSS Modules
- **Database**: IndexedDB (via `idb` library)
- **UI Components**: Headless UI, Heroicons
- **Testing**: Jest with React Testing Library
- **Code Quality**: ESLint, Prettier

### Project Structure
```
src/
├── components/          # Reusable UI components
│   ├── Button.jsx      # Primary button component
│   ├── Header.jsx      # Application header
│   ├── Logo.jsx        # Application logo
│   └── Navigation/     # Desktop & mobile navigation
├── layouts/            # Page layout components
│   └── AppLayout/      # Main application layout
├── pages/              # Route-based page components
│   ├── Dashboard.jsx   # Landing/dashboard page
│   ├── Projects.jsx    # Projects listing page
│   └── ProjectDetail.jsx # Individual project view
├── services/           # Data access layer
│   ├── project.ts      # Project CRUD operations
│   └── inspiration.ts  # Inspiration CRUD operations
├── models/             # TypeScript interfaces
│   └── schema.ts       # Data model definitions
├── utils/              # Utility functions
│   ├── indexedDB.ts    # Database initialization
│   ├── mockLatency.js  # API latency simulation
│   ├── api.js          # External API utilities
│   └── stringUtils.ts  # String manipulation utilities
└── hooks/              # Custom React hooks
```

## 📊 Data Models

### Project Schema
```typescript
interface Project {
  id: string              // UUID
  name: string            // Project name
  description: string     // Project description
  createdAt: string       // ISO timestamp
  updatedAt: string       // ISO timestamp
  inspirations: Inspiration[] // Associated inspirations
}
```

### Inspiration Schema
```typescript
interface Inspiration {
  id: string              // UUID
  projectId: string       // Foreign key to Project
  websiteMetadata: WebsiteMetadata // Scraped website data
  screenshot_uri: string  // Screenshot image URI
  notes: string          // User notes
  createdAt: string      // ISO timestamp
  updatedAt: string      // ISO timestamp
}
```

### Website Metadata Schema
```typescript
interface WebsiteMetadata {
  url: string
  title: string | null
  description: string | null
  favicon: string | null
  author: string | null
  date: string | null
  image: string | null
  logo: string | null
  publisher: string | null
  ogTitle: string | null
  ogDescription: string | null
  ogImage: OgImage[]
  ogLocale: string | null
  ogUrl: string | null
  charset: string | null
  urlRequested: string
  urlResolved: string
}
```

## 🔄 Application Flow

### User Journey
1. **Landing**: Users start at the Dashboard (`/`)
2. **Browse Projects**: Navigate to Projects page (`/projects`) to see all projects
3. **Create Project**: Use "Create New Project" button to add new projects
4. **Project Details**: Click on a project to view details (`/projects/:id`)
5. **Manage Inspirations**: Within project details, add/edit/delete inspirations

### Data Flow
1. **Service Layer**: All data operations go through service functions (`src/services/`)
2. **IndexedDB**: Data is persisted locally using IndexedDB
3. **Mock Latency**: Artificial delays simulate real API calls
4. **State Management**: React state handles UI updates and data synchronization

## 🛠️ Development Features

### Code Quality
- **TypeScript**: Strong typing for data models and services
- **ESLint**: Code linting with React-specific rules
- **Prettier**: Consistent code formatting
- **Jest**: Unit testing framework
- **CSS Modules**: Scoped styling to prevent conflicts

### Development Experience
- **Hot Module Replacement**: Instant updates during development
- **Source Maps**: Debugging support
- **Mock APIs**: Simulated backend responses
- **Component Testing**: React Testing Library integration

## 🚀 Build & Deployment

### Available Scripts
- `npm run dev` - Start development server (Vite)
- `npm run build` - Create production build
- `npm run preview` - Preview production build
- `npm run test` - Run Jest tests
- `npm run lint` - Run ESLint

### Build Output
- Optimized bundle using Vite
- TypeScript compilation
- CSS optimization and purging
- Asset optimization and hashing

## 🔧 Configuration Files

### Key Configuration
- `vite.config.ts` - Vite build configuration
- `tsconfig.json` - TypeScript configuration
- `tailwind.config.js` - Tailwind CSS configuration
- `eslint.config.js` - ESLint rules
- `jest.config.mjs` - Testing configuration
- `.prettierrc` - Code formatting rules

## 💡 Secondary Features

### LLM Integration Setup
The project includes setup instructions for running a local LLM (TinyLlama) using Docker/Ollama, suggesting potential AI-powered features for:
- Automatic inspiration categorization
- Content analysis and tagging
- Design pattern recognition

### Extensibility
The architecture supports easy extension for:
- Cloud storage integration
- Team collaboration features
- Advanced search and filtering
- Export functionality
- Integration with design tools

## 🎨 UI/UX Features

### Responsive Design
- Mobile-first approach using Tailwind CSS
- Collapsible mobile navigation
- Touch-friendly interface elements
- Optimized for various screen sizes

### Component System
- Reusable button components with variants
- Consistent navigation across desktop/mobile
- Modular CSS with scoped styling
- Headless UI for accessible components

This application serves as a solid foundation for a design inspiration management tool, with a clean architecture that supports both current functionality and future enhancements.
