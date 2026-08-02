# AdMob Best Practices

Implementing Google AdMob is more than displaying advertisements. A well-designed monetization strategy balances revenue, user experience, and policy compliance.

This guide covers recommended practices for integrating AdMob into Unity games while maintaining player satisfaction.

---

# Why Best Practices Matter

A poor ad implementation can:

- Reduce player retention
- Increase uninstall rates
- Lower revenue
- Trigger AdMob policy violations

A well-planned strategy improves both player experience and monetization.

---

# Choose the Right Ad Format

Different ad formats serve different purposes.

| Ad Format | Recommended Usage |
|-----------|-------------------|
| Banner Ads | Menus, Shop, Settings |
| Interstitial Ads | Between levels |
| Rewarded Ads | Optional rewards |
| App Open Ads | App launch and resume |

Avoid using every ad format at the same time.

---

# Initialize the SDK Only Once

Initialize Google Mobile Ads only once during application startup.

Avoid initializing the SDK every time a scene loads.

Recommended flow:

```
Application Launch

↓

Initialize SDK

↓

Load Ads

↓

Display Ads

↓

Reload Ads
```

---

# Load Ads Before They Are Needed

Instead of loading an ad when the player presses a button, preload it in advance.

Good:

```
Level Starts

↓

Load Rewarded Ad

↓

Player Clicks Reward Button

↓

Show Ad Immediately
```

Bad:

```
Player Clicks Reward Button

↓

Load Ad

↓

Wait Several Seconds
```

---

# Use Test Ads During Development

Always use Google's official test Ad Unit IDs while developing and testing.

Never click your own live advertisements.

Testing with production ads can violate Google AdMob policies.

---

# Rewarded Ads Should Be Optional

Rewarded Ads should always be initiated by the player.

Examples:

- Double Coins
- Extra Life
- Continue Game
- Bonus Chest
- Daily Reward
- Premium Currency

Avoid forcing Rewarded Ads.

---

# Show Interstitial Ads at Natural Breaks

Good placement:

- Level Complete
- Game Over
- Before Next Level

Poor placement:

- During gameplay
- During combat
- During timed challenges

Interrupting gameplay negatively affects retention.

---

# Avoid Showing Too Many Ads

Too many ads can frustrate players.

Consider:

- Longer intervals between Interstitial Ads
- Optional Rewarded Ads
- Banner Ads only on menu screens

Prioritize player experience over short-term revenue.

---

# Separate Test and Production IDs

Keep test and production Ad Unit IDs separate.

Example:

```
Development

↓

Google Test IDs

Production

↓

Your Live AdMob IDs
```

This reduces the risk of accidental policy violations.

---

# Monitor Ad Performance

Track important metrics such as:

- Fill Rate
- Match Rate
- eCPM
- Impressions
- Click-Through Rate (CTR)
- Revenue

Review these metrics regularly in your AdMob dashboard.

---

# Optimize User Experience

A good monetization strategy should feel natural.

Recommended:

- Clear reward descriptions
- Short loading times
- Smooth transitions
- Minimal interruptions

Players are more likely to engage with ads when they understand the benefit.

---

# Common Mistakes

Avoid:

- Initializing the SDK multiple times
- Showing ads before they finish loading
- Using live ads during testing
- Showing ads too frequently
- Rewarding players before the reward callback
- Ignoring AdMob policy updates

---

# Recommended Ad Flow

```
Application Starts

↓

Initialize SDK

↓

Load Banner

↓

Load Interstitial

↓

Load Rewarded

↓

Gameplay

↓

Natural Break

↓

Show Ad

↓

Reload Next Ad
```

---

# Summary

Following these best practices helps:

- Improve player retention
- Increase revenue
- Reduce crashes
- Simplify maintenance
- Stay compliant with Google AdMob policies

A successful monetization strategy focuses on both user experience and long-term performance.

---

# Next Step

➡️ Continue with:

[Common Errors & Troubleshooting](10-common-errors.md)

---

# Related Guides

- [SDK Initialization](04-initialize-sdk.md)
- [Banner Ads](05-banner-ads.md)
- [Interstitial Ads](06-interstitial-ads.md)
- [Rewarded Ads](07-rewarded-ads.md)
- [App Open Ads](08-app-open-ads.md)

---

Back to the [README](../README.md)
