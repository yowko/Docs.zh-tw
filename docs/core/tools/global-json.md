---
title: "global.json 參考"
description: "請參閱 global.json 檔案的結構描述，它允許設定 .NET Core 工具的版本。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ffa97164736fc7f3edc450682d23bdf499b6eb34
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="globaljson-reference"></a><span data-ttu-id="b0803-104">global.json 參考</span><span class="sxs-lookup"><span data-stu-id="b0803-104">global.json reference</span></span>

<span data-ttu-id="b0803-105">*global.json* 檔案允許透過 `sdk` 屬性使用選取的 .NET Core 工具版本。</span><span class="sxs-lookup"><span data-stu-id="b0803-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="b0803-106">.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找此檔案。</span><span class="sxs-lookup"><span data-stu-id="b0803-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="b0803-107">SDK</span><span class="sxs-lookup"><span data-stu-id="b0803-107">sdk</span></span>
<span data-ttu-id="b0803-108">類型：Object</span><span class="sxs-lookup"><span data-stu-id="b0803-108">Type: Object</span></span>

<span data-ttu-id="b0803-109">指定 SDK 相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b0803-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="b0803-110">version</span><span class="sxs-lookup"><span data-stu-id="b0803-110">version</span></span>
<span data-ttu-id="b0803-111">類型：String</span><span class="sxs-lookup"><span data-stu-id="b0803-111">Type: String</span></span>

<span data-ttu-id="b0803-112">要使用的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="b0803-112">The version of the SDK to use.</span></span>

<span data-ttu-id="b0803-113">例如：</span><span class="sxs-lookup"><span data-stu-id="b0803-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

