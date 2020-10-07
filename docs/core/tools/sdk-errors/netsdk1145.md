---
title: NETSDK1145：目標或 apphost 套件遺失
description: 如何解決不支援 NuGet 套件還原時的目標套件遺失問題
author: wli3
ms.topic: error-reference
ms.date: 09/14/2020
f1_keywords:
- NETSDK1145
ms.openlocfilehash: c343952582cafb63eae388fd216769e6c67d4741
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2020
ms.locfileid: "91805319"
---
# <a name="netsdk1145-targeting-or-apphost-pack-missing"></a><span data-ttu-id="a46be-103">NETSDK1145：目標或 apphost 套件遺失</span><span class="sxs-lookup"><span data-stu-id="a46be-103">NETSDK1145: Targeting or apphost pack missing</span></span>

<span data-ttu-id="a46be-104">本文**適用于：** ✔️ .NET 5.0.100 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="a46be-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="a46be-105">當 .NET SDK 發出錯誤 NETSDK1145 時，不會安裝目標或 apphost 套件，也不支援 NuGet 套件還原。</span><span class="sxs-lookup"><span data-stu-id="a46be-105">When the .NET SDK issues error NETSDK1145, the targeting or apphost pack is not installed and NuGet package restore is not supported.</span></span> <span data-ttu-id="a46be-106">這通常是因為有較新的 SDK，而不是 c + +/CLI 專案 Visual Studio 中包含的 SDK。</span><span class="sxs-lookup"><span data-stu-id="a46be-106">This is typically caused by having a newer SDK than the one included in Visual Studio for C++/CLI projects.</span></span> <span data-ttu-id="a46be-107">升級 Visual Studio，如果指定特定的 SDK 版本，請移除 _global.js_ ，然後卸載較新的 sdk。</span><span class="sxs-lookup"><span data-stu-id="a46be-107">Upgrade Visual Studio, remove _global.json_ if it specifies a certain SDK version, and uninstall the newer SDK.</span></span> <span data-ttu-id="a46be-108">或者，您可以覆寫目標或 apphost 版本。</span><span class="sxs-lookup"><span data-stu-id="a46be-108">Alternatively, you could override the targeting or apphost version.</span></span> <span data-ttu-id="a46be-109">從錯誤訊息中尋找存在於套件目錄下的版本，並符合專案的目標 framework。</span><span class="sxs-lookup"><span data-stu-id="a46be-109">Find the version that exists under the pack directory from the error message and matches the target framework of the project.</span></span> <span data-ttu-id="a46be-110">將下列內容新增至專案：</span><span class="sxs-lookup"><span data-stu-id="a46be-110">Add the following to the project:</span></span>

<span data-ttu-id="a46be-111">針對 apphost 套件</span><span class="sxs-lookup"><span data-stu-id="a46be-111">For apphost pack</span></span>

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```

<span data-ttu-id="a46be-112">針對目標套件</span><span class="sxs-lookup"><span data-stu-id="a46be-112">For targeting pack</span></span>

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```
