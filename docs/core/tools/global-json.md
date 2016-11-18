---
title: "global.json 參考 | .NET Core"
description: "global.json 參考"
keywords: .NET, .NET Core
author: aL3891
ms.author: mairaw
manager: wpickett
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e1ac9659-425f-4486-a376-c12ca942ead8
translationtype: Human Translation
ms.sourcegitcommit: 6f3a46284bd5820520739577919fa202f5b784d7
ms.openlocfilehash: adce52849247f5b12d43b389a7699de04fe278c4

---

# <a name="globaljson-reference"></a>global.json 參考

global.json 檔案用於 .NET Core 專案，以定義解決方案中繼資料。 當叫用 [dotnet-restore](dotnet-restore.md) 命令以還原 .NET Core 專案的相依性時，會使用此檔案。
在本參考主題中，您會看到可在 global.json 檔案中定義的屬性清單。

## <a name="projects"></a>專案
類型：String[]

指定在解析相依性時，建置系統應該搜尋專案的哪些資料夾。 建置系統只會搜尋最上層子資料夾。

例如：

```json
{
    "projects": [ "src", "test" ]
}
```

## <a name="packages"></a>套件
類型：String

要還原套件的位置。

例如：
```json
{
    "packages": "packages-dir"
}
```

## <a name="sdk"></a>SDK
類型：Object

指定 SDK 相關資訊。

### <a name="version"></a>version
類型：String

要使用的 SDK 版本。

例如：

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```



<!--HONumber=Nov16_HO3-->


