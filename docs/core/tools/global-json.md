---
title: global.json 參考
description: 請參閱 global.json 檔案的結構描述，它允許設定 .NET Core 工具的版本。
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33209966"
---
# <a name="globaljson-reference"></a><span data-ttu-id="6c465-103">global.json 參考</span><span class="sxs-lookup"><span data-stu-id="6c465-103">global.json reference</span></span>

<span data-ttu-id="6c465-104">*global.json* 檔案允許透過 `sdk` 屬性使用選取的 .NET Core 工具版本。</span><span class="sxs-lookup"><span data-stu-id="6c465-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="6c465-105">.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找此檔案。</span><span class="sxs-lookup"><span data-stu-id="6c465-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="6c465-106">SDK</span><span class="sxs-lookup"><span data-stu-id="6c465-106">sdk</span></span>
<span data-ttu-id="6c465-107">類型：Object</span><span class="sxs-lookup"><span data-stu-id="6c465-107">Type: Object</span></span>

<span data-ttu-id="6c465-108">指定 SDK 相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6c465-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="6c465-109">版本</span><span class="sxs-lookup"><span data-stu-id="6c465-109">version</span></span>
<span data-ttu-id="6c465-110">類型：String</span><span class="sxs-lookup"><span data-stu-id="6c465-110">Type: String</span></span>

<span data-ttu-id="6c465-111">要使用的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="6c465-111">The version of the SDK to use.</span></span>

<span data-ttu-id="6c465-112">例如: </span><span class="sxs-lookup"><span data-stu-id="6c465-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
