# ios-appiconset-generator

Automagically generates all required iOS app icon sizes `.appiconset` from a single provided image for Xcode Asset Catalog `.xcassets`.

![](https://github.com/user-attachments/assets/62992fba-8abc-4cf4-965f-37c88251ae4b)

## Requirements

- macOS (uses `sips` for image resizing)
- Python 3
- Xcode project with an `.appiconset` directory

## Installation

Use directly with `npx` without installing:

```bash
npx @anydigital/ios-appiconset-generator
```

Or install locally:
```bash
npm install @anydigital/ios-appiconset-generator --save-dev
```

## Usage

1. Navigate to your `.appiconset` directory:
   ```bash
   cd ios/YourApp/Images.xcassets/AppIcon.appiconset
   ```

2. Run the generator:
   ```bash
   npx @anydigital/ios-appiconset-generator # OR ios-appiconset-generator if installed locally
   ```

3. Optionally, place your source icon image as `AppIcon.png` in `.appiconset` directory (1024x1024 recommended) before running the generator.

The script will:
- Generate all required icon sizes based on `Contents.json`
- Automatically update `Contents.json` with filenames if missing
- Create a placeholder icon if `AppIcon.png` doesn't exist

## How it works

The tool reads your `Contents.json` file, extracts the required icon sizes and scales, and uses macOS's `sips` utility to generate properly sized PNG files. It preserves the Xcode formatting of `Contents.json` when updating filenames.

## Feedback?

https://www.reddit.com/r/TricksForGeeks/comments/1pnnpwu/iosappiconsetgenerator/

---

_✨ found this useful? `→` give a [star on GitHub](https://github.com/anydigital/ios-appiconset-generator) `or` simply [join TricksForGeeks on Reddit](https://www.reddit.com/r/TricksForGeeks/) for more ✨_
