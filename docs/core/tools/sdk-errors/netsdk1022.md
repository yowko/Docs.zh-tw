---
title: NETSDK1022：包含重複的專案。
description: 如何根據預設包含來解析重複專案訊息。
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: bc803f5316bf09c12c563f1a63b8385d1be4e9ce
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506632"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022：包含重複的專案。

本文 **適用于：** ✔️ .NET 2.1.100 SDK 和更新版本

從 Visual Studio 2017/MSBuild 15.3 版開始，.NET SDK 預設會自動包含專案目錄中的專案。  這包括 `Compile` 和 `Content` 目標。  這應該會大幅清除您的專案檔，並降低您在該處的複雜度。

您可以藉由將正確的屬性設定為 false，來還原為先前的行為。

專案範例 `Compile` ：

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
