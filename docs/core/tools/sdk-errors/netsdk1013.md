---
title: NETSDK1013：無法辨識 TargetFramework 值。
description: 如何判斷及設定有效的 TargetFramework 值
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: 915ac22ad822d17c082498b469acbfb3f1a93efc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717863"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a><span data-ttu-id="00ff3-103">NETSDK1013：無法辨識 TargetFramework 值</span><span class="sxs-lookup"><span data-stu-id="00ff3-103">NETSDK1013: The TargetFramework value was not recognized</span></span>

<span data-ttu-id="00ff3-104">本文 **適用于：** ✔️ .net CORE 3.1.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="00ff3-104">**This article applies to:** ✔️ .NET Core 3.1.100 SDK and later versions</span></span>

<span data-ttu-id="00ff3-105">SDK 會嘗試將專案檔中所提供的值，或剖析為 `<TargetFramework>` `<TargetFrameworks>` 已知的值。</span><span class="sxs-lookup"><span data-stu-id="00ff3-105">The SDK tries to parse the values provided in the project file for `<TargetFramework>` or `<TargetFrameworks>` into a well known value.</span></span>  <span data-ttu-id="00ff3-106">如果無法辨識值， `TargetFrameworkIdentifier` 或 `TargetFrameworkVersion` 值可以設定為空字串或 `Unsupported` 。</span><span class="sxs-lookup"><span data-stu-id="00ff3-106">If the value is not recognized, the `TargetFrameworkIdentifier` or `TargetFrameworkVersion` value may be set to an empty string or `Unsupported`.</span></span>

<span data-ttu-id="00ff3-107">若要解決此問題，請從支援的架構清單中檢查您的值是否正確 `TargetFramework` 。 [supported frameworks](../../../standard/frameworks.md)</span><span class="sxs-lookup"><span data-stu-id="00ff3-107">To resolve this, check the spelling of your `TargetFramework` value from the list of [supported frameworks](../../../standard/frameworks.md).</span></span>
<span data-ttu-id="00ff3-108">您也可以 `TargetFrameworkIdentifier` `TargetFrameworkVersion` 直接在專案檔中設定和屬性。</span><span class="sxs-lookup"><span data-stu-id="00ff3-108">You can also set the `TargetFrameworkIdentifier` and `TargetFrameworkVersion` properties directly in your project file.</span></span>

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
