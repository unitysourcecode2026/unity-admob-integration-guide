# Frequently Asked Questions (FAQ)

This page answers common questions about integrating Google Mobile Ads (AdMob) into Unity projects.

---

# General Questions

## Which Unity versions are supported?

This guide is designed for Unity 2022 LTS and newer. Most concepts also apply to Unity 2021 LTS and later versions, although some APIs may differ.

---

## Does this guide support Android?

Yes.

The guide covers complete AdMob integration for Android using the Google Mobile Ads Unity SDK.

---

## Does this guide support iOS?

Yes.

The documentation also explains the required project configuration for iOS builds.

---

## Is Firebase required?

No.

Google AdMob works independently.

However, Firebase Analytics can provide additional insights into user behavior and ad performance.

---

## Which ad formats are covered?

This repository includes:

- Banner Ads
- Interstitial Ads
- Rewarded Ads
- App Open Ads

---

# SDK Questions

## When should I initialize the SDK?

Initialize the SDK only once when your application starts.

Avoid initializing it every time a scene changes.

---

## Can I use one AdManager for every scene?

Yes.

A single persistent AdManager using `DontDestroyOnLoad()` is the recommended approach.

---

## Should I preload advertisements?

Yes.

Preloading improves user experience by reducing waiting time before an ad is displayed.

---

# Testing Questions

## Can I use my live Ad Unit IDs while developing?

No.

Always use Google's official test Ad Unit IDs during development.

Using live ads for testing may violate Google AdMob policies.

---

## Why aren't my ads showing?

Possible reasons include:

- SDK not initialized
- No internet connection
- Invalid Ad Unit ID
- Ad still loading
- New AdMob account
- Low fill rate

See the [Common Errors & Troubleshooting](10-common-errors.md) guide for detailed solutions.

---

# Rewarded Ads

## When should I grant the reward?

Only after the reward callback executes.

Never grant rewards before the player successfully finishes the advertisement.

---

## Can players skip Rewarded Ads?

Yes.

Rewarded Ads are optional by design.

Players should choose whether they want to watch an ad in exchange for a reward.

---

# Banner Ads

## Where should Banner Ads be placed?

Recommended locations:

- Main Menu
- Shop
- Settings
- Pause Menu

Avoid placing banners over gameplay elements.

---

# Interstitial Ads

## When should Interstitial Ads be shown?

Show them during natural breaks, for example:

- Level Complete
- Game Over
- Before Next Level

Avoid interrupting gameplay.

---

# App Open Ads

## When should App Open Ads appear?

Recommended moments:

- Application launch
- Returning from the background

Avoid displaying them after every scene change.

---

# Best Practices

## How many ads should I show?

Focus on user experience.

Too many advertisements can reduce player retention and long-term revenue.

A balanced monetization strategy usually performs better.

---

## Should I destroy ads after displaying them?

Yes.

Destroy used ads and preload new ones to keep your application running efficiently.

---

# Repository Questions

## Can I use this code in my own project?

Yes.

Please review the repository license for details.

---

## How can I report an issue?

Open an Issue on GitHub describing:

- Unity version
- Platform
- Google Mobile Ads SDK version
- Error message
- Steps to reproduce

---

## Can I contribute?

Yes.

Contributions are welcome.

Please read the [CONTRIBUTING.md](../CONTRIBUTING.md) guide before submitting a Pull Request.

---

# Additional Resources

- [Introduction](01-introduction.md)
- [Installation Guide](02-installation.md)
- [Project Setup](03-project-setup.md)
- [SDK Initialization](04-initialize-sdk.md)
- [Common Errors](10-common-errors.md)

---

# Next Step

Continue with:

➡️ [Resources](12-resources.md)

---

Back to the [README](../README.md)
