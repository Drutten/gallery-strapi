# Gallery Strapi Backend

> **⚠️ Work in Progress** - This project is currently under active development. Features and API endpoints may change.

This is the Strapi CMS backend for the Gallery project. It provides content management for InfoBlocks and other dynamic content displayed on the frontend.

**Frontend repository:** [github.com/Drutten/gallery](https://github.com/Drutten/gallery)

## 🏗️ Content Types

### InfoBlock
- **title** (String, required) - The heading for the info block
- **text** (Rich Text, required) - Main content with formatting support
- **image** (Media, required) - Associated image
- **ImageToTheRight** (Boolean, required) - Layout direction (false = image left, true = image right)
- **button** (Component, optional) - Call-to-action button with text and slug

### Button Component
- **text** (String, required) - Button label
- **slug** (String, required) - URL path (format: lowercase, numbers, hyphens, underscores)

## 🚀 Local Development Setup

### Prerequisites
- Node.js (v18.x - v20.x)
- npm (v8.x or higher)

### Installation

1. **Clone and navigate to the project:**
   ```bash
   cd gallery-strapi
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set up environment variables:**
   ```bash
   cp .env.example .env
   ```
   The default values work for local development. Strapi will auto-generate secure secrets on first run if using placeholder values.

4. **Start the development server:**
   ```bash
   npm run develop
   ```
   This starts Strapi with auto-reload enabled at `http://localhost:1337`

### First Time Setup

1. **Create Admin Account:**
   - On first launch, navigate to `http://localhost:1337/admin`
   - Create your admin account (no Strapi Cloud account needed for local development)
   - This creates a local SQLite database

2. **Configure API Permissions:**
   - Go to **Settings** → **Users & Permissions Plugin** → **Roles** → **Public**
   - Under **Info-block**, enable:
     - ✅ `find` (get all info blocks)
     - ✅ `findOne` (get single info block)
   - Click **Save**

3. **Create Content:**
   - Go to **Content Manager** → **InfoBlock**
   - Click **Create new entry**
   - Fill in title, text, upload image, set layout direction
   - Optionally add a button
   - Click **Save** and **Publish**

### Database

By default, Strapi uses **SQLite** for local development. The database file is stored at `.tmp/data.db` (gitignored).

For production, configure PostgreSQL or MySQL in `config/database.js`.

## 📡 API Endpoints

Once running, access your data at:

- **All InfoBlocks:** `http://localhost:1337/api/info-blocks?populate=*`
- **Single InfoBlock:** `http://localhost:1337/api/info-blocks/:id?populate=*`

The `?populate=*` parameter includes related data (images, buttons).

## 🔧 Available Commands

### Development
```bash
npm run develop
```
Start with auto-reload enabled (recommended for development)

### Production
```bash
npm run build    # Build the admin panel
npm run start    # Start without auto-reload
```

### Strapi CLI
```bash
npm run strapi   # Access Strapi CLI commands
```

## 🔄 Cloning This Project

If you want to clone and use this project:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Drutten/gallery-strapi.git
   cd gallery-strapi
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set up environment:**
   ```bash
   cp .env.example .env
   ```

4. **Start Strapi:**
   ```bash
   npm run develop
   ```

5. **Create your admin account** when prompted at `http://localhost:1337/admin`

6. **Configure API permissions** (Settings → Roles → Public → Info-block → enable `find` and `findOne`)

7. **Add your own content** through the Content Manager

**Note:** The database starts empty - you'll need to create your own InfoBlocks and upload your own images.

## ⚙️ Deployment

For production deployment options, see [Strapi deployment documentation](https://docs.strapi.io/dev-docs/deployment).

Popular options:
- Strapi Cloud
- Railway
- Heroku
- DigitalOcean
- AWS/Google Cloud

## 📚 Learn More

- [Strapi Documentation](https://docs.strapi.io) - Official documentation
- [Strapi GitHub Repository](https://github.com/strapi/strapi) - Source code and issues
