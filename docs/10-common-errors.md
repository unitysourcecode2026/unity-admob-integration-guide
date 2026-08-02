# Common Errors & Troubleshooting

Integrating Google Mobile Ads into Unity is generally straightforward, but configuration issues, SDK mismatches, or platform settings can cause unexpected problems.

This guide covers the most common AdMob errors and practical solutions.

---

# GoogleMobileAds Namespace Not Found

## Problem

```text
The type or namespace name 'GoogleMobileAds' could not be found.
```

## Possible Causes

- SDK not imported
- Missing dependency resolution
- Compilation errors
- Incorrect project setup

## Solution

- Verify the Google Mobile Ads SDK is imported.
- Run:

```
Assets
→ External Dependency Manager
→ Android Resolver
→ Force Resolve
```

- Restart Unity if necessary.

---

# Ads Not Loading

## Possible Causes

- No internet connection
- Invalid Ad Unit ID
- SDK not initialized
- Test device not configured

## Solution

✔ Check internet connectivity.

✔ Verify your Ad Unit ID.

✔ Initialize the SDK before loading ads.

✔ Test with Google's official test IDs.

---

# Interstitial Ad Doesn't Show

## Problem

The ad loads successfully but never appears.

## Solution

Always verify the ad is ready.

```csharp
if (interstitialAd != null &&
    interstitialAd.CanShowAd())
{
    interstitialAd.Show();
}
```

---

# Rewarded Ad Doesn't Grant Reward

## Problem

The advertisement finishes but the player receives nothing.

## Solution

Grant rewards only inside the reward callback.

Correct example:

```csharp
rewardedAd.Show((Reward reward) =>
{
    GrantReward(reward);
});
```

Do not reward the player before the callback executes.

---

# Banner Not Visible

## Possible Causes

- Hidden behind UI
- Invalid position
- Invalid Ad Unit ID
- Internet unavailable

## Solution

Try:

```csharp
AdPosition.Bottom
```

or

```csharp
AdPosition.Top
```

Verify your Canvas does not overlap the banner.

---

# Duplicate SDK Initialization

## Problem

Ads become unstable or multiple callbacks occur.

## Cause

Calling:

```csharp
MobileAds.Initialize();
```

every time a scene loads.

## Solution

Initialize the SDK only once when the application starts.

Use a persistent AdManager.

---

# Android Build Errors

## Possible Causes

- Missing Android Build Support
- Outdated Gradle files
- Dependency conflict

## Solution

- Update Unity.
- Force Resolve dependencies.
- Rebuild the project.

---

# iOS Build Errors

## Possible Causes

- CocoaPods not installed
- Xcode configuration issues
- Missing capabilities

## Solution

- Install CocoaPods.
- Rebuild the Xcode project.
- Verify Bundle Identifier.
- Confirm signing settings.

---

# Test Ads Not Showing

## Possible Causes

- Test device not registered
- Invalid App ID
- Invalid Ad Unit ID

## Solution

Use Google's official test IDs and verify initialization completes successfully.

---

# Live Ads Not Showing

Possible reasons:

- New AdMob account
- New Ad Unit
- Low fill rate
- App not yet approved

Allow time for new ad units to begin serving ads.

---

# Common Console Messages

## Initialization Successful

```text
Google Mobile Ads SDK Initialized
```

This indicates the SDK is ready.

---

## Failed to Load Ad

```text
Failed to load ad.
```

Check:

- Network connection
- Ad Unit ID
- SDK version
- Initialization

---

# Troubleshooting Checklist

Before reporting an issue, verify:

- Unity version supported
- Latest Google Mobile Ads SDK installed
- External Dependency Manager resolved
- Test Ad Unit IDs used
- Internet connection available
- SDK initialized once
- Platform configured correctly

---

# Useful Resources

Official Google Mobile Ads documentation

Unity documentation

Google AdMob Help Center

---

# Next Step

➡️ Continue with:

[Frequently Asked Questions](11-faq.md)

---

# Related Guides

- [Installation Guide](02-installation.md)
- [Project Setup](03-project-setup.md)
- [SDK Initialization](04-initialize-sdk.md)
- [AdMob Best Practices](09-admob-best-practices.md)

---

Back to the [README](../README.md)
