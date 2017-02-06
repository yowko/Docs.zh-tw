---
title: "global.json 參考 | Microsoft Docs"
description: "global.json 參考"
keywords: ".NET、.NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 97a9ee85025c15e21d4a7cbdce31d35d3894e7d6

---

# <a name="globaljson-reference-tooling-preview-4"></a>global.json 參考 (工具 Preview 4)

> [!WARNING]
> 此主題適用於 Visual Studio 2017 RC - .NET Core 工具 Preview 4。 .NET Core 工具 Preview 2 版本，請參閱 [global.json 參考](../../tools/global-json.md)主題。

global.json 檔案仍出現在 .NET Core 命令列 Preview 4 中。 不過，其主要目的不是要定義如同舊版中的方案中繼資料，而是要允許透過 `sdk` 屬性選取要使用的 CLI 版本。 

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


<!--HONumber=Jan17_HO3-->


