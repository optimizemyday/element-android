# OMD Icon Replacement

This document describes the icon replacement implemented for the OMD build variant of Element Android.

## Overview

All Element branding icons have been replaced with OMD (OptimizeMyDay) branded icons for the OMD build variant. The implementation uses Android's resource override system via source sets, which means:

- Element icons are used in the standard Element build variants
- OMD icons automatically replace Element icons when building the OMD variant
- No changes were made to the main source code

## Icons Replaced

### 1. Launcher Icons (`vector-app/src/omd/res/mipmap-*/`)

Created OMD-branded launcher icons in all density buckets:
- `ic_launcher.png` - Standard launcher icon (mdpi through xxxhdpi)
- `ic_launcher_round.png` - Round launcher icon (mdpi through xxxhdpi)

Created adaptive icon support (Android 8.0+):
- `ic_launcher.xml` and `ic_launcher_round.xml` - Adaptive icon configuration
- `ic_launcher_background.xml` - Blue background (#4A90E2) 
- `ic_launcher_foreground.xml` - White "OMD" text logo

### 2. Splash Screen Logo (`library/ui-styles/src/omd/res/drawable-*/`)

Created OMD splash screen logo:
- `element_splash_white.png` - OMD logo for splash screen (mdpi through xxxhdpi)
- Displays blue circle with white "OMD" text

### 3. In-App Logos (`library/ui-styles/src/omd/res/drawable/` and `vector/src/omd/res/drawable/`)

Created vector drawable OMD logos:
- `element_logo_green.xml` - Main OMD logo (replaces Element green logo)
- `element_logotype.xml` - OMD Messenger logotype with text
- `element_logo_stars.xml` - OMD logo with decorative elements
- `ic_logo_element_matrix_services.xml` - OMD Matrix Services branding

## Icon Design

The OMD icons feature:
- **Primary Color**: Blue (#4A90E2) - Professional and trustworthy
- **Text**: White "OMD" text on blue background
- **Style**: Clean, modern, and minimalist design
- **Format**: Vector XML for scalability, PNG for density-specific icons

## Customization

To replace these placeholder icons with final OMD branding:

1. Replace the PNG files in `vector-app/src/omd/res/mipmap-*/` with your branded launcher icons
2. Replace the splash PNG files in `library/ui-styles/src/omd/res/drawable-*/`
3. Update the vector XML files with your final logo designs

The file structure and naming must remain the same to maintain the resource override system.

## Build Variants

The OMD icons are automatically used when building:
- `./gradlew assembleGplayOmdDebug` - OMD Debug build
- `./gradlew assembleGplayOmd` - OMD Production build
- `./gradlew bundleGplayOmd` - OMD AAB for Play Store

Element icons are still used for:
- `./gradlew assembleDebug` - Element Debug build
- `./gradlew assembleRelease` - Element Release build

## Technical Details

The icon replacement uses Android's resource overlay system:
- OMD variant resources are stored in `src/omd/res/`
- During build, Gradle merges resources with OMD-specific overrides taking precedence
- No code changes required - icons are referenced by resource ID in code
- The same resource IDs (`@drawable/element_logo_green`, etc.) resolve to different assets based on build variant

## File Locations

```
vector-app/src/omd/res/
├── drawable/
│   └── ic_launcher_background.xml
├── drawable-anydpi-v26/
│   └── ic_launcher_foreground.xml
├── mipmap-anydpi-v26/
│   ├── ic_launcher.xml
│   └── ic_launcher_round.xml
├── mipmap-mdpi/
│   ├── ic_launcher.png
│   └── ic_launcher_round.png
├── mipmap-hdpi/
│   ├── ic_launcher.png
│   └── ic_launcher_round.png
├── mipmap-xhdpi/
│   ├── ic_launcher.png
│   └── ic_launcher_round.png
├── mipmap-xxhdpi/
│   ├── ic_launcher.png
│   └── ic_launcher_round.png
└── mipmap-xxxhdpi/
    ├── ic_launcher.png
    └── ic_launcher_round.png

library/ui-styles/src/omd/res/
├── drawable/
│   └── element_logo_green.xml
├── drawable-mdpi/
│   └── element_splash_white.png
├── drawable-hdpi/
│   └── element_splash_white.png
├── drawable-xhdpi/
│   └── element_splash_white.png
├── drawable-xxhdpi/
│   └── element_splash_white.png
└── drawable-xxxhdpi/
    └── element_splash_white.png

vector/src/omd/res/drawable/
├── element_logotype.xml
├── element_logo_stars.xml
└── ic_logo_element_matrix_services.xml
```

## Verification

To verify the icons are properly applied:

1. Build the OMD variant: `./gradlew assembleGplayOmdDebug`
2. Install on a device or emulator
3. Check:
   - Launcher icon shows OMD branding
   - Splash screen shows OMD logo
   - In-app branding shows OMD logos

## Notes

- Icons maintain the same resource IDs as Element icons for compatibility
- All original Element icons remain unchanged in main source set
- Vector drawables provide resolution-independent graphics where possible
- PNG icons are provided in all standard Android density buckets
