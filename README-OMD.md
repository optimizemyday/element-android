# OMD Messenger Android - Build Variant

This is the OMD (OptimizeMyDay) branded build variant of Element Android. 

## Quick Start - Production Build

For a production-ready build for Play Store deployment:

```bash
# Run the production build script
./build-omd-production.sh
```

This will create both APK and AAB files ready for distribution.

## Development Builds

For development and testing:

```bash
# Build OMD Debug variant  
./gradlew assembleGplayOmdDebug

# Install OMD Debug variant directly to device
./gradlew installGplayOmdDebug

# Build OMD Production variant
./gradlew assembleGplayOmd

# Build AAB for Play Store
./gradlew bundleGplayOmd
```

## OMD-Specific Configuration

The OMD build variant includes:

- **App Name**: "OMD Messenger" (release) / "OMD Messenger - dbg" (debug)
- **Application ID**: `com.optimizemyday.messenger`
- **Default Server**: `https://matrix.optimizemyday.ai`
- **URI Scheme**: `omdmessenger://`
- **Domains**: All Element.io domains replaced with optimizemyday.ai
- **Bug Reports**: Sent to `https://support.optimizemyday.ai/bugreports/submit`
- **Jitsi Domain**: `meet.optimizemyday.ai`

## File Structure

OMD-specific configuration is stored in:

```
vector-app/src/omd/              # OMD app-specific overrides
├── AndroidManifest.xml          # OMD manifest overrides
└── res/values/                  # OMD resource overrides

vector-config/src/omd/           # OMD configuration overrides  
└── res/values/
    ├── config.xml               # OMD server and service config
    └── urls.xml                 # OMD URL configuration

vector/src/omd/                  # OMD vector module overrides
└── AndroidManifest.xml          # OMD vector manifest overrides
```

## Production Signing

For Play Store deployment, you need to configure production signing:

1. **Create keystore**: See `signature/README.md` for instructions
2. **Set environment variables** (recommended for CI/CD):
   ```bash
   export OMD_ANDROID_KEYSTORE="/path/to/your/omd.keystore"
   export OMD_ANDROID_KEYID="your-key-alias"
   export OMD_ANDROID_KEYPASSWORD="your-key-password"
   export OMD_ANDROID_STOREPASSWORD="your-store-password"
   ```
3. **Or use gradle.properties**:
   ```properties
   signing.omd.storePath=./signature/omd.keystore
   signing.omd.keyId=omdrelease
   signing.omd.keyPassword=YOUR_KEY_PASSWORD
   signing.omd.storePassword=YOUR_STORE_PASSWORD
   ```

## Play Store Deployment

1. Build production AAB: `./gradlew bundleGplayOmd`
2. Upload to Google Play Console
3. Use metadata from `playstore/listing.md`
4. Submit for review

## Customization

### Icons

OMD-branded icons have been created and are automatically used when building the OMD variant:

- **Launcher Icons**: Blue (#4A90E2) with white "OMD" text in all densities
- **Splash Screen**: OMD logo replaces Element splash screen
- **In-App Logos**: Vector drawable OMD logos for all branding touchpoints

To replace with your final branded icons:
1. Replace PNG files in `vector-app/src/omd/res/mipmap-*/` with your launcher icons
2. Replace PNG files in `library/ui-styles/src/omd/res/drawable-*/` with your splash screens
3. Update vector XML files in `vector/src/omd/res/drawable/` with your logo designs

See `ICON-REPLACEMENT.md` for complete documentation.

### Other Customizations

1. **Colors**: Override colors in `vector-app/src/omd/res/values/colors.xml`
2. **Strings**: Add string overrides in `vector-app/src/omd/res/values/strings.xml`
3. **Signing**: Configure OMD-specific signing in `build.gradle`

## Original Element Build

The original Element Android build variants are still available:

```bash
# Original Element variants
./gradlew assembleDebug          # Element - dbg
./gradlew assembleRelease        # Element  
./gradlew assembleNightly        # Element (nightly)
```

Both Element and OMD variants can coexist and be built from the same codebase.