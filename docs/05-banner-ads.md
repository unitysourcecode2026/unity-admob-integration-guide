# Banner Ads

Banner Ads are small rectangular advertisements displayed at the top or bottom of the screen. They remain visible while the user interacts with your game and are suitable for menus, pause screens, and non-gameplay interfaces.

---

# What You'll Learn

In this guide you'll learn how to:

- Create Banner Ads
- Load Banner Ads
- Display Banner Ads
- Hide Banner Ads
- Destroy Banner Ads
- Follow Google's recommended implementation

---

# Import Required Namespace

```csharp
using GoogleMobileAds.Api;
```

---

# Banner Ad Sizes

Google provides several banner sizes.

| Size | Description |
|------|-------------|
| Banner | Standard mobile banner |
| LargeBanner | Larger banner |
| MediumRectangle | Medium rectangle |
| IABBanner | Tablet banner |
| SmartBanner | Deprecated |
| Adaptive Banner | Recommended |

For new projects, use **Adaptive Banner** whenever possible.

---

# Create a BannerAd Variable

```csharp
private BannerView bannerView;
```

---

# Load a Banner Ad

```csharp
using GoogleMobileAds.Api;
using UnityEngine;

public class BannerAds : MonoBehaviour
{
    private BannerView bannerView;

    void Start()
    {
        LoadBanner();
    }

    public void LoadBanner()
    {
        string adUnitId = "YOUR_BANNER_AD_UNIT_ID";

        bannerView = new BannerView(
            adUnitId,
            AdSize.Banner,
            AdPosition.Bottom);

        AdRequest request = new AdRequest();

        bannerView.LoadAd(request);
    }
}
```

---

# Show the Banner

```csharp
bannerView.Show();
```

---

# Hide the Banner

```csharp
bannerView.Hide();
```

Useful during gameplay.

---

# Destroy the Banner

Always destroy banners when they are no longer needed.

```csharp
if (bannerView != null)
{
    bannerView.Destroy();
}
```

---

# Banner Events

Google Mobile Ads provides useful callbacks.

Example:

```csharp
bannerView.OnBannerAdLoaded += () =>
{
    Debug.Log("Banner Loaded");
};

bannerView.OnBannerAdLoadFailed += (LoadAdError error) =>
{
    Debug.Log(error);
};
```

---

# Recommended Placement

Good locations:

- Main Menu
- Pause Menu
- Settings
- Level Complete
- Shop Screen

Avoid showing banners:

- During gameplay
- During fast action
- On loading screens

---

# Testing Banner Ads

Before publishing, always use Google's official test Ad Unit IDs.

Never click your own live advertisements.

---

# Common Problems

### Banner not showing

Possible reasons:

- Invalid Ad Unit ID
- No internet connection
- SDK not initialized
- Test device not configured

---

### Banner overlaps UI

Move the banner to:

```csharp
AdPosition.Bottom
```

or

```csharp
AdPosition.Top
```

depending on your UI layout.

---

# Best Practices

- Load banners once.
- Reuse banners when possible.
- Destroy unused banners.
- Avoid excessive refreshing.
- Test with official test ads.

---

# Next Step

Continue with:

➡️ [Interstitial Ads](06-interstitial-ads.md)

---

# Related Guides

- [SDK Initialization](04-initialize-sdk.md)
- [Interstitial Ads](06-interstitial-ads.md)
- [Rewarded Ads](07-rewarded-ads.md)

---

Back to the [README](../README.md)
