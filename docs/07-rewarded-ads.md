# Rewarded Ads

Rewarded Ads are one of the highest-performing ad formats in mobile games. They allow players to voluntarily watch a full-screen advertisement in exchange for an in-game reward such as coins, gems, extra lives, hints, or premium content.

Unlike Interstitial Ads, Rewarded Ads provide value to both developers and players, making them one of the most effective monetization strategies for Unity games.

---

# What You'll Learn

In this guide you'll learn how to:

- Load Rewarded Ads
- Display Rewarded Ads
- Grant Player Rewards
- Handle Ad Events
- Reload Ads Automatically
- Follow Google Mobile Ads best practices

---

# Import Required Namespace

```csharp
using GoogleMobileAds.Api;
```

---

# Create a RewardedAd Variable

```csharp
private RewardedAd rewardedAd;
```

---

# Load a Rewarded Ad

```csharp
using GoogleMobileAds.Api;
using UnityEngine;

public class RewardedAds : MonoBehaviour
{
    private RewardedAd rewardedAd;

    public void LoadRewardedAd()
    {
        string adUnitId = "YOUR_REWARDED_AD_UNIT_ID";

        AdRequest request = new AdRequest();

        RewardedAd.Load(
            adUnitId,
            request,
            (RewardedAd ad, LoadAdError error) =>
            {
                if (error != null || ad == null)
                {
                    Debug.LogError("Rewarded Ad failed to load.");
                    return;
                }

                rewardedAd = ad;

                RegisterEvents();
            });
    }
}
```

---

# Show a Rewarded Ad

Before displaying the advertisement, verify that it is ready.

```csharp
if (rewardedAd != null &&
    rewardedAd.CanShowAd())
{
    rewardedAd.Show((Reward reward) =>
    {
        GrantReward(reward);
    });
}
```

---

# Grant the Player Reward

The reward callback is only executed after the player earns the reward.

```csharp
private void GrantReward(Reward reward)
{
    Debug.Log(
        $"Reward Earned: {reward.Amount} {reward.Type}");

    // Example

    coins += (int)reward.Amount;

    UpdateUI();
}
```

Replace this example with your own reward system.

---

# Register Rewarded Ad Events

```csharp
private void RegisterEvents()
{
    rewardedAd.OnAdPaid += value =>
    {
        Debug.Log("Revenue Generated");
    };

    rewardedAd.OnAdClicked += () =>
    {
        Debug.Log("Rewarded Ad Clicked");
    };

    rewardedAd.OnAdImpressionRecorded += () =>
    {
        Debug.Log("Impression Recorded");
    };

    rewardedAd.OnAdFullScreenContentClosed += () =>
    {
        Debug.Log("Rewarded Ad Closed");

        rewardedAd.Destroy();

        LoadRewardedAd();
    };

    rewardedAd.OnAdFullScreenContentFailed += error =>
    {
        Debug.LogError(error);

        rewardedAd.Destroy();

        LoadRewardedAd();
    };
}
```

---

# Recommended Reward Types

Rewarded Ads work well for:

- Coins
- Gems
- Extra Lives
- Energy
- Hints
- Continue After Game Over
- Double Rewards
- Unlock Premium Chest
- Skip Waiting Time

Players should always understand what they will receive before choosing to watch the ad.

---

# Best Placement

Good locations include:

- Game Over
- Daily Reward
- Extra Coins
- Continue Screen
- Lucky Wheel
- Reward Multiplier
- Bonus Chest

Avoid interrupting active gameplay with Rewarded Ads.

---

# Common Problems

## Reward Not Granted

Possible causes:

- Reward callback not implemented
- Ad closed before completion
- Game logic not updating player data

Always grant rewards only inside the reward callback.

---

## Ad Not Showing

Verify:

- SDK initialized
- Ad loaded successfully
- Internet connection available
- Valid Ad Unit ID
- Test Ad Unit ID used during development

---

# Best Practices

- Preload Rewarded Ads.
- Explain the reward before showing the ad.
- Never grant rewards before the callback.
- Reload a new ad after each completed ad.
- Use Rewarded Ads as an optional feature.

---

# Example Reward Flow

```
Player Clicks

↓

Watch Rewarded Ad

↓

Ad Completes

↓

Reward Callback

↓

Grant Reward

↓

Update UI

↓

Load Next Rewarded Ad
```

---

# Next Step

Continue with:

➡️ [App Open Ads](08-app-open-ads.md)

---

# Related Guides

- [Banner Ads](05-banner-ads.md)
- [Interstitial Ads](06-interstitial-ads.md)
- [App Open Ads](08-app-open-ads.md)

---

Back to the [README](../README.md)
