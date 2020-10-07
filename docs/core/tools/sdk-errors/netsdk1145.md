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
# <a name="netsdk1145-targeting-or-apphost-pack-missing"></a>NETSDK1145：目標或 apphost 套件遺失

本文**適用于：** ✔️ .NET 5.0.100 SDK 和更新版本

當 .NET SDK 發出錯誤 NETSDK1145 時，不會安裝目標或 apphost 套件，也不支援 NuGet 套件還原。 這通常是因為有較新的 SDK，而不是 c + +/CLI 專案 Visual Studio 中包含的 SDK。 升級 Visual Studio，如果指定特定的 SDK 版本，請移除 _global.js_ ，然後卸載較新的 sdk。 或者，您可以覆寫目標或 apphost 版本。 從錯誤訊息中尋找存在於套件目錄下的版本，並符合專案的目標 framework。 將下列內容新增至專案：

針對 apphost 套件

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```

針對目標套件

```xml
<ItemGroup>
  <KnownAppHostPack Update="@(KnownAppHostPack)">
    <AppHostPackVersion Condition="'%(TargetFramework)' == 'TARGETFRAMEWORK'">EXISTINGVERSION</AppHostPackVersion>
  </KnownAppHostPack>
</ItemGroup>
```
