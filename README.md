# DeepMerger Brand Assets

DeepMerger's official visual identity, iconography, and cryptographic assets.

This repository houses the strictly defined, mathematically generated vector assets and production-ready raster files required to deploy the DeepMerger brand across web, mobile, and print architectures. 

## 🗄️ Repository Architecture

The repository is structured to separate source mathematical vectors from compiled production formats.

```text
brand_assets/
├── docs/                 # Structural documentation and brand rules
│   ├── BRAND_GUIDELINES.md                  # Core rules for spacing, color, and usage
│   └── Mathematical_Algorithmic_Blueprint.md # Coordinate data and SVG path proofs
├── favicon_io-dark/      # Compiled raster favicons & manifests (Dark Mode)
├── favicon_io-light/     # Compiled raster favicons & manifests (Light Mode)
├── logos/                # Core SVG vector assets (Immutable)
│   ├── logo-full-* # Complete signature (Icon + Wordmark)
│   ├── logo-icon-* # Standalone geometric icon
│   ├── logo-text-only-* # Standalone typographic wordmark
│   └── favicon-* # Scalable vector favicons
├── patterns/             # Brand geometric patterns, textures, and grids
├── social/               # Pre-rendered OpenGraph (OG) and social preview cards
└── README.md             # Repository documentation
```

## 📐 Asset Deployment Standards

DeepMerger's visual identity relies on absolute precision. Please adhere to the following implementation standards:

### 1. Vector Primary (`logos/`)
**Always default to `.svg` files.** The core logos are mathematically defined geometric objects. Utilizing the raw SVG code ensures infinite scalability, zero artifacting on high-density Retina displays, and minimal DOM footprint.

### 2. Raster Secondary (`favicon_io-*/` & `social/`)
Use `.png` and `.ico` files **only** when explicitly required by external platform constraints. 
* Use the `favicon_io` directories for `site.webmanifest`, Android Chrome app icons, and Apple Touch icons.
* Use the `social/` directory for `<meta property="og:image">` tags.

### 3. Binary Contrast (`-light` vs `-dark`)
* **`-light.svg`:** Contains `#030303` (Deep Black) paths. Must be deployed on pure white or highly light-grey backgrounds.
* **`-dark.svg`:** Contains `#FFFFFF` (Pure White) paths. Must be deployed on pitch black or deeply dark-grey backgrounds.

## 📚 Documentation

Before implementing these assets, developers and designers must review the documentation located in the `/docs` directory:

1. **[Brand Guidelines](./docs/BRAND_GUIDELINES.md):** Rules on clear space, forbidden alterations, and the monochromatic OKLCH color system.
2. **[Mathematical & Algorithmic Blueprint](./docs/Mathematical & Algorithmic Blueprint.md):** The technical specification of the Cartesian coordinate space and cubic Bézier curves that form the logo.

---
*Property of DeepMerger. Unauthorized modification of source vectors is strictly prohibited.*
