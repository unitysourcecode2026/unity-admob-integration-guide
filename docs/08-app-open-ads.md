# App Open Ads

App Open Ads are full-screen advertisements shown when users launch or return to your application. They are designed to monetize app openings while maintaining a smooth user experience.

Unlike Banner or Interstitial Ads, App Open Ads should only appear at appropriate moments, such as when the app starts or resumes after being in the background.

---

# What You'll Learn

In this guide you'll learn how to:

- Load an App Open Ad
- Display an App Open Ad
- Handle App Open events
- Reload App Open Ads
- Follow Google Mobile Ads best practices

---

# Import Required Namespace

```csharp
using GoogleMobileAds.Api;
```

---

# Create an AppOpenAd Variable

```csharp
private AppOpenAd appOpenAd;
```

---

# Load an App Open Ad

```csharp
using GoogleMobileAds.Api;
using UnityEngine;

public class AppOpenAdsManager : MonoBehaviour
{
    private AppOpenAd appOpenAd;

    public void LoadAppOpenAd()
    {
        string adUnitId = "YOUR_APP_OPEN_AD_UNIT_ID";

        AdRequest request = new AdRequest();

        AppOpenAd.Load(
            adUnitId,
            request,
            (AppOpenAd ad, LoadAdError error) =>
            {
                if (error != null || ad == null)
                {
                    Debug.LogError("Failed to load App Open Ad.");
                    return;
                }

                appOpenAd = ad;

                RegisterEvents();
            });
    }
}
```

---

# Show an App Open Ad

Always verify that the ad is available before attempting to show it.

```csharp
if (appOpenAd != null &&
    appOpenAd.CanShowAd())
{
    appOpenAd.Show();
}
```

---

# Register App Open Events

```csharp
private void RegisterEvents()
{
    appOpenAd.OnAdPaid += value =>
    {
        Debug.Log("Revenue Generated");
    };

    appOpenAd.OnAdClicked += () =>
    {
        Debug.Log("App Open Ad Clicked");
    };

    appOpenAd.OnAdImpressionRecorded += () =>
    {
        Debug.Log("Impression Recorded");
    };

    appOpenAd.OnAdFullScreenContentClosed += () =>
    {
        Debug.Log("App Open Ad Closed");

        appOpenAd.Destroy();

        LoadAppOpenAd();
    };

    appOpenAd.OnAdFullScreenContentFailed += error =>
    {
        Debug.LogError(error);

        appOpenAd.Destroy();

        LoadAppOpenAd();
    };
}
```

---

# Recommended Usage

Show App Open Ads:

- When the application launches
- When returning from the background
- Before showing the main menu (if loading takes time)

Avoid showing them:

- Every time a scene changes
- During gameplay
- Immediately after another full-screen ad
- Too frequently

---

# Common Problems

## App Open Ad Doesn't Show

Possible causes:

- SDK not initialized
- Ad not loaded
- Invalid App Open Ad Unit ID
- No internet connection

---

## Ad Expired

App Open Ads have a limited lifetime.

If an ad has been loaded for a long time, discard it and load a new one before showing it.

---

# Best Practices

- Preload App Open Ads.
- Reload immediately after one is closed.
- Never interrupt gameplay.
- Display only during natural app launch moments.
- Use test ads while developing.

---

# Example Flow

```
Application Starts

↓

Initialize SDK

↓

Load App Open Ad

↓

Ad Ready

↓

Show App Open Ad

↓

Main Menu

↓

Load Next App Open Ad
```

---

# Next Step

Continue with:

➡️ [AdMob Best Practices](09-admob-best-practices.md)

---

# Related Guides

- [SDK Initialization](04-initialize-sdk.md)
- [Banner Ads](05-banner-ads.md)
- [Interstitial Ads](06-interstitial-ads.md)
- [Rewarded Ads](07-rewarded-ads.md)

---

Back to the [README](../README.md)
