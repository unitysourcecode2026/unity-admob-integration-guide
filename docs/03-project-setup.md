# Project Setup

Now that the Google Mobile Ads SDK is installed, it's time to configure your Unity project for Android and iOS.

---

## Project Configuration Checklist

Before writing any code, verify the following:

- Unity project created
- Google Mobile Ads SDK imported
- External Dependency Manager resolved
- Android Build Support installed
- iOS Build Support installed (if targeting iOS)

---

## Android Player Settings

Open:

Edit → Project Settings → Player

Under **Android**:

- Company Name
- Product Name
- Package Name (Example: com.company.gamename)
- Minimum API Level (Recommended: API 24+)
- Target API Level (Latest Installed)

---

## iOS Player Settings

Select the **iOS** tab.

Configure:

- Bundle Identifier
- Version
- Build Number
- Target minimum iOS version

---

## Internet Permission

Google Mobile Ads requires an internet connection.

Unity automatically adds the required permission in most cases, but verify your Android Manifest if you've customized it.

Required permission:

```xml
<uses-permission android:name="android.permission.INTERNET"/>
```

---

## Enable Android Build Support

Open:

File → Build Settings

Select:

- Android

Click:

**Switch Platform**

Wait until Unity finishes converting the project.

---

## Enable iOS Build Support

If publishing for iPhone:

File → Build Settings

Select:

- iOS

Click:

**Switch Platform**

---

## Recommended Build Settings

### Android

- IL2CPP
- ARM64
- .NET Standard 2.1

### iOS

- IL2CPP
- ARM64

---

## Verify Project Structure

A correctly configured project should contain folders similar to:

```text
Assets/
├── GoogleMobileAds/
├── Plugins/
├── Resources/
├── Scenes/
├── Scripts/
└── ExternalDependencyManager/
```

---

## Create a Scripts Folder

Create a folder named:

```text
Assets/Scripts/Ads/
```

Later we'll add:

```text
AdManager.cs
BannerAds.cs
InterstitialAds.cs
RewardedAds.cs
AppOpenAds.cs
```

---

## Recommended Scene Structure

```text
Assets/
└── Scenes/
    ├── MainMenu
    ├── Gameplay
    ├── Loading
    └── GameOver
```

---

## Best Practices

- Keep all ad scripts in one folder.
- Use a single AdManager.
- Avoid duplicate initialization.
- Test with Google's test IDs before using production IDs.
- Keep Android and iOS App IDs separate.

---

## Next Step

➡️ Continue with:

[SDK Initialization](04-initialize-sdk.md)

---

## Related Guides

- [Introduction](01-introduction.md)
- [Installation Guide](02-installation.md)
- [SDK Initialization](04-initialize-sdk.md)

---

Back to the [README](../README.md)
