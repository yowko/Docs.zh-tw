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
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a>NETSDK1013：無法辨識 TargetFramework 值

本文 **適用于：** ✔️ .net CORE 3.1.100 SDK 和更新版本

SDK 會嘗試將專案檔中所提供的值，或剖析為 `<TargetFramework>` `<TargetFrameworks>` 已知的值。  如果無法辨識值， `TargetFrameworkIdentifier` 或 `TargetFrameworkVersion` 值可以設定為空字串或 `Unsupported` 。

若要解決此問題，請從支援的架構清單中檢查您的值是否正確 `TargetFramework` 。 [supported frameworks](../../../standard/frameworks.md)
您也可以 `TargetFrameworkIdentifier` `TargetFrameworkVersion` 直接在專案檔中設定和屬性。

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
