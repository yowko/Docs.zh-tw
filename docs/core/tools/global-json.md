---
title: global.json 參考
description: 請參閱 global.json 檔案的結構描述，它允許設定 .NET Core 工具的版本。
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ac53a899e76c99527f2670d0a6bed3f8cc6ce31f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="globaljson-reference"></a><span data-ttu-id="3eebe-103">global.json 參考</span><span class="sxs-lookup"><span data-stu-id="3eebe-103">global.json reference</span></span>

<span data-ttu-id="3eebe-104">*global.json* 檔案允許透過 `sdk` 屬性使用選取的 .NET Core 工具版本。</span><span class="sxs-lookup"><span data-stu-id="3eebe-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="3eebe-105">.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找此檔案。</span><span class="sxs-lookup"><span data-stu-id="3eebe-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="3eebe-106">SDK</span><span class="sxs-lookup"><span data-stu-id="3eebe-106">sdk</span></span>
<span data-ttu-id="3eebe-107">類型：Object</span><span class="sxs-lookup"><span data-stu-id="3eebe-107">Type: Object</span></span>

<span data-ttu-id="3eebe-108">指定 SDK 相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3eebe-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="3eebe-109">版本</span><span class="sxs-lookup"><span data-stu-id="3eebe-109">version</span></span>
<span data-ttu-id="3eebe-110">類型：String</span><span class="sxs-lookup"><span data-stu-id="3eebe-110">Type: String</span></span>

<span data-ttu-id="3eebe-111">要使用的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="3eebe-111">The version of the SDK to use.</span></span>

<span data-ttu-id="3eebe-112">例如: </span><span class="sxs-lookup"><span data-stu-id="3eebe-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
