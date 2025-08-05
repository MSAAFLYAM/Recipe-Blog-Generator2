# Recipe Blog Generator

An AI-powered, SEO-optimized recipe content creation tool that generates comprehensive blog posts from simple recipe titles or CSV data. Built with React, TailwindCSS, and modern web technologies.

## 🚀 Features

### Core Functionality
- **Single Recipe Generation**: Create complete recipe blog posts from just a title
- **Bulk CSV Processing**: Upload or paste CSV data to generate multiple recipes at once
- **SEO Analysis**: Analyze competitor recipes and extract SEO insights
- **AI Content Generation**: Generate comprehensive recipe content including:
  - Detailed ingredients lists
  - Step-by-step instructions
  - Cooking tips and variations
  - FAQ sections
  - Nutrition information

### Advanced Features
- **Image Generation**: AI-powered food photography generation
- **Multi-language Support**: English, Arabic, and French translations
- **Rich Text Editor**: Inline editing with grammar checking
- **Export Options**: HTML, Markdown, and DOCX formats
- **Analytics Dashboard**: Track generation statistics and manage recipes
- **Smart Search**: AI-powered search through generated recipes

### User Experience
- **Responsive Design**: Works perfectly on desktop and mobile
- **Real-time Progress**: Visual feedback during generation processes
- **Professional UI**: Clean, modern interface with intuitive navigation
- **Free & Open Source**: No API limits or subscription requirements

## 🛠️ Technology Stack

- **Frontend**: React 18 + Vite
- **Styling**: TailwindCSS + shadcn/ui components
- **Icons**: Lucide React
- **State Management**: React Hooks
- **Build Tool**: Vite
- **Package Manager**: npm

## 📦 Installation

### Prerequisites
- Node.js 18+ 
- npm or yarn

### Quick Start

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd recipe-blog-generator
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```

4. **Open in browser**
   ```
   http://localhost:5173
   ```

### Build for Production

```bash
npm run build
```

The built files will be in the `dist/` directory.

## 🎯 Usage Guide

### Single Recipe Generation

1. **Enter Recipe Title**: Type your recipe name (e.g., "Chocolate Chip Cookies")
2. **Start Generation**: Click "Start Recipe Generation"
3. **SEO Analysis**: The tool analyzes competitors and suggests optimizations
4. **Configure Recipe**: Set difficulty, cooking time, servings, and dietary restrictions
5. **Generate Content**: AI creates comprehensive recipe content
6. **Review & Edit**: Use the inline editor to refine the content
7. **Export**: Download in your preferred format (HTML, Markdown, DOCX)

### Bulk CSV Processing

1. **Prepare CSV**: Create a CSV file with recipe titles (one per line)
2. **Upload File**: Use the file picker or paste CSV data directly
3. **Parse Data**: Click "Parse CSV Data" to process the list
4. **Batch Generate**: The tool processes all recipes automatically
5. **Review Results**: Use the dashboard to manage generated recipes

### Export Options

- **HTML**: Web-ready format with styling and SEO metadata
- **Markdown**: Perfect for blogs, GitHub, and documentation platforms  
- **DOCX**: Microsoft Word format for printing and sharing

## 🔧 Configuration

### Environment Variables

Create a `.env` file in the root directory:

```env
# Optional: Configure API endpoints for enhanced features
VITE_OPENAI_API_KEY=your_openai_key_here
VITE_REPLICATE_API_TOKEN=your_replicate_token_here
```

### Customization

The application is designed to work without any API keys using free services. However, you can enhance functionality by:

1. **Adding OpenAI API**: For improved content generation
2. **Configuring Image APIs**: For better image generation quality
3. **Translation Services**: For enhanced multi-language support

## 📁 Project Structure

```
recipe-blog-generator/
├── public/                 # Static assets
├── src/
│   ├── components/        # React components
│   │   ├── ui/           # shadcn/ui components
│   │   ├── CSVUploader.jsx
│   │   ├── SEOAnalyzer.jsx
│   │   ├── ContentGenerator.jsx
│   │   ├── ImageGenerator.jsx
│   │   ├── TranslationPanel.jsx
│   │   ├── EditorPanel.jsx
│   │   ├── ExportPanel.jsx
│   │   ├── Dashboard.jsx
│   │   └── SearchBar.jsx
│   ├── App.jsx           # Main application component
│   ├── main.jsx          # Application entry point
│   └── index.css         # Global styles
├── package.json
├── vite.config.js
├── tailwind.config.js
└── README.md
```

## 🌐 Deployment

### Vercel (Recommended)

1. **Connect Repository**: Link your GitHub repository to Vercel
2. **Configure Build**: Vercel auto-detects Vite configuration
3. **Deploy**: Automatic deployment on every push to main branch

### Netlify

1. **Build Command**: `npm run build`
2. **Publish Directory**: `dist`
3. **Deploy**: Drag and drop the `dist` folder or connect via Git

### Manual Deployment

1. **Build the project**:
   ```bash
   npm run build
   ```

2. **Upload the `dist/` folder** to your web server

### Docker Deployment

A Dockerfile is included for containerized deployment:

```bash
docker build -t recipe-blog-generator .
docker run -p 3000:3000 recipe-blog-generator
```

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Documentation**: Check this README and inline comments
- **Issues**: Report bugs via GitHub Issues
- **Discussions**: Use GitHub Discussions for questions

## 🔮 Roadmap

- [ ] Advanced SEO analysis with real SERP data
- [ ] Integration with popular blogging platforms
- [ ] Recipe video generation
- [ ] Advanced nutrition calculation
- [ ] Social media optimization
- [ ] Recipe rating and review system

## 🙏 Acknowledgments

- **shadcn/ui**: For the beautiful UI components
- **TailwindCSS**: For the utility-first CSS framework
- **Lucide**: For the comprehensive icon library
- **Vite**: For the fast build tool
- **React**: For the powerful frontend framework

---

**Built with ❤️ for food bloggers and content creators**

