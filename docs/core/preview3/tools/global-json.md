---
title: "global.json 參考 | .NET Core"
description: "global.json 參考"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e1ac9659-425f-4486-a376-c12ca942ead8
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 281f1b717a0e220e533078e973711977617a1401

---

# <a name="globaljson-reference"></a>global.json 參考

global.json 檔案仍出現在 .NET Core 命令列 Preview 3 中。 不過，其主要目的不是要定義如同舊版中的方案中繼資料，而是要允許透過 `sdk` 屬性選取要使用的 CLI 版本。 

此參考會反映上述事實。 

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


