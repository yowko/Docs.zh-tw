---
title: 使用C# -.net 序列化和還原序列化 JSON
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b43c3f6fd8ca56aaa99fffd40317920ee7600a2c
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802709"
---
# <a name="json-serialization-in-net---overview"></a><span data-ttu-id="03390-102">.NET 中的 JSON 序列化-總覽</span><span class="sxs-lookup"><span data-stu-id="03390-102">JSON serialization in .NET - overview</span></span>

<span data-ttu-id="03390-103">`System.Text.Json` 命名空間提供從 JavaScript 物件標記法（JSON）序列化及還原序列化的功能。</span><span class="sxs-lookup"><span data-stu-id="03390-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="03390-104">程式庫設計強調廣泛功能集的高效能和低記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="03390-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="03390-105">內建的 UTF-8 支援將讀取和寫入 JSON 文字編碼為 UTF-8 的程式優化，這對網路上的資料和磁片上的檔案而言是最普遍的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="03390-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="03390-106">程式庫也會提供類別，以使用記憶體中的檔物件模型（DOM）。</span><span class="sxs-lookup"><span data-stu-id="03390-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="03390-107">這項功能可讓您對 JSON 檔案或字串中的元素進行隨機唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="03390-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="03390-108">如何取得程式庫</span><span class="sxs-lookup"><span data-stu-id="03390-108">How to get the library</span></span>

* <span data-ttu-id="03390-109">此程式庫內建為[.Net Core 3.0](https://aka.ms/netcore3download)共用架構的一部分。</span><span class="sxs-lookup"><span data-stu-id="03390-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="03390-110">若是其他目標 framework，請安裝[System.web](https://www.nuget.org/packages/System.Text.Json) NuGet 封裝。</span><span class="sxs-lookup"><span data-stu-id="03390-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="03390-111">封裝支援：</span><span class="sxs-lookup"><span data-stu-id="03390-111">The package supports:</span></span>
  * <span data-ttu-id="03390-112">.NET Standard 2.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="03390-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="03390-113">.NET Framework 4.6.1 和更新版本</span><span class="sxs-lookup"><span data-stu-id="03390-113">.NET Framework 4.6.1 and later versions</span></span>
  * <span data-ttu-id="03390-114">.NET Core 2.0、2.1 和2.2</span><span class="sxs-lookup"><span data-stu-id="03390-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="03390-115">其他資源</span><span class="sxs-lookup"><span data-stu-id="03390-115">Additional resources</span></span>

* [<span data-ttu-id="03390-116">如何使用程式庫</span><span class="sxs-lookup"><span data-stu-id="03390-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="03390-117">原始程式碼 (英文)</span><span class="sxs-lookup"><span data-stu-id="03390-117">Source code</span></span>](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Text.Json)
* [<span data-ttu-id="03390-118">API 參考</span><span class="sxs-lookup"><span data-stu-id="03390-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="03390-119">藍圖</span><span class="sxs-lookup"><span data-stu-id="03390-119">Roadmap</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="03390-120">Dotnet/corefx 存放庫中的 GitHub 問題</span><span class="sxs-lookup"><span data-stu-id="03390-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="03390-121">有關如何開發 System.web 的討論</span><span class="sxs-lookup"><span data-stu-id="03390-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115) <!-- TODO: Issues are still not moved to the new repo-->
  * [<span data-ttu-id="03390-122">所有的 System.object 問題</span><span class="sxs-lookup"><span data-stu-id="03390-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="03390-123">已標記 json 的 system.object 問題-功能-doc</span><span class="sxs-lookup"><span data-stu-id="03390-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/runtime/labels/json-functionality-doc)
