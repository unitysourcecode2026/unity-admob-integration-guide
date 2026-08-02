# Interstitial Ads

Interstitial Ads are full-screen advertisements displayed at natural transition points in your game, such as after completing a level or before loading the next scene.

When implemented correctly, interstitial ads can significantly increase revenue without disrupting the player experience.

---

# What You'll Learn

In this guide you'll learn how to:

- Create an Interstitial Ad
- Load an Interstitial Ad
- Show an Interstitial Ad
- Handle Ad Events
- Reload Ads Automatically
- Follow Google's recommended implementation

---

# Import Required Namespace

```csharp
using GoogleMobileAds.Api;
```

---

# Create an Interstitial Variable

```csharp
private InterstitialAd interstitialAd;
```

---

# Load an Interstitial Ad

```csharp
using GoogleMobileAds.Api;
using UnityEngine;

public class InterstitialAds : MonoBehaviour
{
    private InterstitialAd interstitialAd;

    public void LoadInterstitial()
    {
        string adUnitId = "YOUR_INTERSTITIAL_AD_UNIT_ID";

        AdRequest request = new AdRequest();

        InterstitialAd.Load(
            adUnitId,
            request,
            (InterstitialAd ad, LoadAdError error) =>
            {
                if (error != null || ad == null)
                {
                    Debug.LogError("Interstitial failed to load.");
                    return;
                }

                interstitialAd = ad;
                RegisterEvents();
            });
    }
}
```

---

# Show an Interstitial Ad

Before displaying an ad, always verify that it has finished loading.

```csharp
if (interstitialAd != null &&
    interstitialAd.CanShowAd())
{
    interstitialAd.Show();
}
```

---

# Register Ad Events

Tracking events allows your game to respond to different stages of the ad lifecycle.

```csharp
private void RegisterEvents()
{
    interstitialAd.OnAdPaid += adValue =>
    {
        Debug.Log("Ad generated revenue.");
    };

    interstitialAd.OnAdImpressionRecorded += () =>
    {
        Debug.Log("Impression recorded.");
    };

    interstitialAd.OnAdClicked += () =>
    {
        Debug.Log("Ad clicked.");
    };

    interstitialAd.OnAdFullScreenContentClosed += () =>
    {
        Debug.Log("Interstitial closed.");

        interstitialAd.Destroy();

        LoadInterstitial();
    };

    interstitialAd.OnAdFullScreenContentFailed += error =>
    {
        Debug.LogError(error);

        interstitialAd.Destroy();

        LoadInterstitial();
    };
}
```

---

# Destroy an Interstitial

After showing an Interstitial Ad, destroy it before requesting another one.

```csharp
if (interstitialAd != null)
{
    interstitialAd.Destroy();
    interstitialAd = null;
}
```

---

# Recommended Placement

Good moments to show an Interstitial:

- Level Complete
- Game Over
- Next Level
- Before returning to Main Menu
- Between long gameplay sessions

Avoid showing Interstitial Ads:

- Immediately after opening the game
- During active gameplay
- During loading screens
- Too frequently

---

# Testing

Always test with Google's official test Ad Unit IDs before using production IDs.

Never click your own live advertisements.

---

# Common Problems

### Ad Not Ready

Possible causes:

- Ad still loading
- Network unavailable
- Invalid Ad Unit ID
- SDK not initialized

Always check:

```csharp
interstitialAd.CanShowAd()
```

before calling:

```csharp
interstitialAd.Show();
```

---

### Interstitial Doesn't Reload

Reload the next ad after the current one closes.

```csharp
OnAdFullScreenContentClosed
```

is the ideal place to call:

```csharp
LoadInterstitial();
```

---

# Best Practices

- Preload the next Interstitial.
- Show ads only during natural breaks.
- Limit ad frequency.
- Never interrupt gameplay.
- Destroy used ads.
- Reload after closing.

---

# Next Step

Continue with:

➡️ [Rewarded Ads](07-rewarded-ads.md)

---

# Related Guides

- [Banner Ads](05-banner-ads.md)
- [Rewarded Ads](07-rewarded-ads.md)
- [App Open Ads](08-app-open-ads.md)

---

Back to the [README](../README.md)
