# Installation Guide

Welcome to the Unity AdMob Integration Guide.

This guide walks you through installing the Google Mobile Ads SDK into your Unity project for both Android and iOS.

---

## Prerequisites

Before starting, make sure you have:

- Unity 2022 LTS or newer
- Internet connection
- Google AdMob account
- Android Build Support
- iOS Build Support (optional if targeting iOS)

---

## Step 1 — Create a Unity Project

1. Open Unity Hub.
2. Click **New Project**.
3. Select the **3D (URP)** or **2D** template.
4. Name your project.
5. Click **Create Project**.

> Continue once Unity finishes loading.

---

## Step 2 — Download the Google Mobile Ads SDK

Download the latest Unity package from the official repository.

Official Repository:

https://github.com/googleads/googleads-mobile-unity

---

## Step 3 — Import the Package

Inside Unity:

Assets → Import Package → Custom Package

Select:

GoogleMobileAds.unitypackage

Click **Import All**.

---

## Step 4 — Resolve Dependencies

After importing:

Assets → External Dependency Manager → Android Resolver → Resolve

Wait until the resolver finishes downloading all required libraries.

---

## Step 5 — Verify Installation

After installation you should see folders similar to:

```
Assets/

GoogleMobileAds/

ExternalDependencyManager/

Plugins/

Resources/
```

If these folders exist, the SDK has been installed correctly.

---

## Step 6 — Import Required Namespace

Example:

```csharp
using GoogleMobileAds.Api;
```

If IntelliSense recognizes the namespace, installation was successful.

---

## Common Installation Problems

### GoogleMobileAds namespace not found

Possible causes:

- Package not imported
- Dependency Resolver not executed
- Compilation errors

---

### Duplicate Classes

Run:

Assets

↓

External Dependency Manager

↓

Android Resolver

↓

Force Resolve

---

### Missing DLL

Re-import the SDK package.

---

## Next Step

Continue with:

➡️ [Project Setup](03-project-setup.md)

---

## Related Guides

- [Introduction](01-introduction.md)
- [Project Setup](03-project-setup.md)
- [SDK Initialization](04-initialize-sdk.md)

---

Back to the [README](../README.md).
