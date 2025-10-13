# OMD Icons Visual Guide

## Overview

This guide shows the OMD-branded icons that replace Element branding in the OMD build variant.

## Icon Design

All OMD icons feature:
- **Primary Color**: Blue (#4A90E2) - Professional and trustworthy
- **Text Color**: White (#FFFFFF)
- **Typography**: Bold "OMD" text
- **Style**: Clean, modern, minimalist design

## Icon Types

### 1. Launcher Icons

**Location**: `vector-app/src/omd/res/mipmap-*/`

The launcher icons appear on the device home screen and app drawer.

**Specifications**:
- Format: PNG (bitmap) + XML (adaptive icon)
- Shape: Square with rounded corners (standard) and circular (round variant)
- Densities: mdpi (48px), hdpi (72px), xhdpi (96px), xxhdpi (144px), xxxhdpi (192px)
- Adaptive Icon: Yes (Android 8.0+)

**Design**:
- Blue background filling the entire icon space
- White "OMD" text centered
- Supports adaptive icon system (background layer + foreground layer)

**Files**:
```
mipmap-mdpi/ic_launcher.png          (48x48)
mipmap-hdpi/ic_launcher.png          (72x72)
mipmap-xhdpi/ic_launcher.png         (96x96)
mipmap-xxhdpi/ic_launcher.png        (144x144)
mipmap-xxxhdpi/ic_launcher.png       (192x192)
mipmap-*dpi/ic_launcher_round.png    (same sizes)
mipmap-anydpi-v26/ic_launcher.xml    (adaptive icon)
drawable/ic_launcher_background.xml  (blue background)
drawable-anydpi-v26/ic_launcher_foreground.xml (OMD text)
```

### 2. Splash Screen Icon

**Location**: `library/ui-styles/src/omd/res/drawable-*/`

The splash screen icon appears when the app launches.

**Specifications**:
- Format: PNG (bitmap)
- Shape: Circular
- Densities: mdpi (108px), hdpi (162px), xhdpi (216px), xxhdpi (324px), xxxhdpi (432px)
- Background: Transparent

**Design**:
- Blue circle with white "OMD" text
- Centered composition
- Consistent with launcher icon design

**Files**:
```
drawable-mdpi/element_splash_white.png     (108x108)
drawable-hdpi/element_splash_white.png     (162x162)
drawable-xhdpi/element_splash_white.png    (216x216)
drawable-xxhdpi/element_splash_white.png   (324x324)
drawable-xxxhdpi/element_splash_white.png  (432x432)
```

### 3. In-App Vector Logos

**Location**: `vector/src/omd/res/drawable/` and `library/ui-styles/src/omd/res/drawable/`

Vector drawable logos used throughout the app interface.

#### element_logo_green.xml
**Usage**: Main app logo (replaces Element green logo)
**Specifications**:
- Format: Vector XML
- Size: 64x64 dp
- Design: Blue circle with white "OMD" text

#### element_logotype.xml
**Usage**: Full branding with "OMD Messenger" text
**Specifications**:
- Format: Vector XML
- Size: 200x40 dp
- Design: "OMD Messenger" text in white

#### element_logo_stars.xml
**Usage**: Decorative logo variant with visual elements
**Specifications**:
- Format: Vector XML
- Size: 120x94 dp
- Design: Blue circle with "OMD" text and decorative dots

#### ic_logo_element_matrix_services.xml
**Usage**: Matrix services branding
**Specifications**:
- Format: Vector XML
- Size: 180x48 dp
- Design: OMD logo circle with "Matrix Services" text

## Icon Usage in App

### Where Icons Appear

1. **Launcher Icon**: 
   - Device home screen
   - App drawer
   - Recent apps screen
   - Settings app list

2. **Splash Screen**:
   - App launch
   - Cold start
   - Initial loading

3. **In-App Logos**:
   - Login/splash screens
   - About screen
   - Settings
   - Notifications
   - Analytics opt-in screen

## Build Variants

### OMD Variant (Uses OMD Icons)
```bash
./gradlew assembleGplayOmdDebug    # Debug
./gradlew assembleGplayOmd         # Production
./gradlew bundleGplayOmd           # AAB for Play Store
```

### Element Variant (Uses Element Icons)
```bash
./gradlew assembleDebug            # Debug
./gradlew assembleRelease          # Production
```

## Customization

To replace these placeholder OMD icons with your final branding:

### For PNG Icons (Launcher & Splash)
1. Create your branded icons in the correct sizes
2. Replace the PNG files in the appropriate directories
3. Maintain the same file names
4. Ensure transparency is handled correctly

### For Vector Logos
1. Edit the XML files directly
2. Update the path data with your logo shapes
3. Adjust colors if needed
4. Test at different screen sizes

### Design Guidelines

When creating replacement icons:

1. **Launcher Icons**:
   - Follow [Android Adaptive Icon Guidelines](https://developer.android.com/develop/ui/views/launch/icon_design_adaptive)
   - Safe zone: Keep important content within the center 66dp of 108dp icon
   - Test on different launcher shapes (circle, square, rounded square)

2. **Splash Icons**:
   - Keep design simple and recognizable
   - Ensure good contrast with background
   - Test on light and dark themes

3. **Vector Logos**:
   - Use vector format for scalability
   - Keep file size reasonable
   - Test at different display densities

## File Structure

```
vector-app/src/omd/res/
├── drawable/
│   └── ic_launcher_background.xml
├── drawable-anydpi-v26/
│   └── ic_launcher_foreground.xml
├── mipmap-anydpi-v26/
│   ├── ic_launcher.xml
│   └── ic_launcher_round.xml
└── mipmap-{density}/
    ├── ic_launcher.png
    └── ic_launcher_round.png

library/ui-styles/src/omd/res/
├── drawable/
│   └── element_logo_green.xml
└── drawable-{density}/
    └── element_splash_white.png

vector/src/omd/res/drawable/
├── element_logotype.xml
├── element_logo_stars.xml
└── ic_logo_element_matrix_services.xml
```

## Testing

To verify icons are properly applied:

1. Build the OMD variant
2. Install on a device or emulator
3. Check all icon locations:
   - Home screen launcher icon
   - App drawer icon
   - Splash screen during app launch
   - In-app logos in various screens

## Resources

- [Android Icon Design Guidelines](https://developer.android.com/guide/practices/ui_guidelines/icon_design)
- [Adaptive Icons](https://developer.android.com/develop/ui/views/launch/icon_design_adaptive)
- [Material Design Icons](https://material.io/design/iconography)
- Android Asset Studio: https://romannurik.github.io/AndroidAssetStudio/

## Technical Notes

- Icons use Android's resource override system via build variants
- No code changes required - icons are referenced by resource ID
- OMD resources automatically override main resources when building OMD variant
- Element resources remain unchanged in main source set
- Compatible with Android 5.0 (API 21) and above
- Adaptive icons work on Android 8.0 (API 26) and above
