# SDK Initialization

After installing the Google Mobile Ads SDK and configuring your Unity project, the next step is to initialize the SDK.

Initializing the SDK ensures that all ad formats (Banner, Interstitial, Rewarded, and App Open Ads) are ready to load.

---

# Why Initialization Matters

Before requesting any advertisements, the Google Mobile Ads SDK must be initialized.

Initialization:

- Loads internal SDK components
- Prepares ad services
- Improves ad loading performance
- Prevents runtime errors

> Always initialize the SDK only once when your application starts.

---

# Import the Required Namespace

```csharp
using GoogleMobileAds.Api;
```

---

# Basic SDK Initialization

Create a new C# script.

Example:

```csharp
using UnityEngine;
using GoogleMobileAds.Api;

public class AdManager : MonoBehaviour
{
    void Start()
    {
        MobileAds.Initialize(initStatus =>
        {
            Debug.Log("Google Mobile Ads SDK Initialized");
        });
    }
}
```

---

# Understanding the Code

The method:

```csharp
MobileAds.Initialize();
```

starts the Google Mobile Ads SDK.

The callback:

```csharp
initStatus =>
{
}
```

runs after initialization has completed.

This is the best place to begin loading your advertisements.

---

# Recommended Project Structure

```
Assets
└── Scripts
    └── Ads
        ├── AdManager.cs
        ├── BannerAds.cs
        ├── InterstitialAds.cs
        ├── RewardedAds.cs
        └── AppOpenAds.cs
```

---

# Initialize Only Once

Do NOT initialize the SDK every time a scene loads.

Incorrect:

```
Main Menu
↓

Initialize

↓

Gameplay

↓

Initialize Again ❌
```

Correct:

```
Game Starts

↓

Initialize SDK ✅

↓

Load Ads

↓

Show Ads
```

---

# Singleton Example

For production projects, use a single AdManager.

```csharp
public class AdManager : MonoBehaviour
{
    public static AdManager Instance;

    void Awake()
    {
        if (Instance == null)
        {
            Instance = this;
            DontDestroyOnLoad(gameObject);
        }
        else
        {
            Destroy(gameObject);
        }
    }
}
```

This keeps the AdManager alive across all scenes.

---

# Verify Initialization

If initialization succeeds, the Unity Console should display:

```
Google Mobile Ads SDK Initialized
```

If you see this message, the SDK is ready.

---

# Common Mistakes

❌ Initializing more than once

❌ Loading ads before initialization

❌ Missing namespace

❌ Dependency Resolver not executed

❌ Using an outdated SDK version

---

# Best Practices

- Initialize once.
- Keep one AdManager.
- Load ads only after initialization.
- Use test ads during development.
- Separate Android and iOS App IDs.

---

# Next Step

Continue with:

➡️ [Banner Ads](05-banner-ads.md)

---

# Related Guides

- [Introduction](01-introduction.md)
- [Installation Guide](02-installation.md)
- [Project Setup](03-project-setup.md)
- [Banner Ads](05-banner-ads.md)

---

Back to the [README](../README.md)
