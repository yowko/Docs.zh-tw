---
title: '使用 c # 序列化和還原序列化 JSON-.NET'
description: 本總覽說明在 System.Text.Json .net 中從 JSON 序列化和還原序列化的命名空間功能。
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 909d979d46b30939e304af071de65d230febd92d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "83380130"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="2cc46-103">.NET 中的 JSON 序列化和還原序列化（封送處理和 unmarshalling）-總覽</span><span class="sxs-lookup"><span data-stu-id="2cc46-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="2cc46-104">`System.Text.Json`命名空間提供從 JavaScript 物件標記法（JSON）序列化及還原序列化的功能。</span><span class="sxs-lookup"><span data-stu-id="2cc46-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="2cc46-105">程式庫設計強調廣泛功能集的高效能和低記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="2cc46-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="2cc46-106">內建的 UTF-8 支援將讀取和寫入 JSON 文字編碼為 UTF-8 的程式優化，這對網路上的資料和磁片上的檔案而言是最普遍的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="2cc46-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="2cc46-107">程式庫也會提供類別，以使用記憶體中的檔物件模型（DOM）。</span><span class="sxs-lookup"><span data-stu-id="2cc46-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="2cc46-108">這項功能可讓您對 JSON 檔案或字串中的元素進行隨機唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="2cc46-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="2cc46-109">如何取得程式庫</span><span class="sxs-lookup"><span data-stu-id="2cc46-109">How to get the library</span></span>

* <span data-ttu-id="2cc46-110">此程式庫內建為[.Net Core 3.0](https://aka.ms/netcore3download)共用架構的一部分。</span><span class="sxs-lookup"><span data-stu-id="2cc46-110">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="2cc46-111">若為其他目標 framework，請安裝 [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="2cc46-111">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="2cc46-112">封裝支援：</span><span class="sxs-lookup"><span data-stu-id="2cc46-112">The package supports:</span></span>
  * <span data-ttu-id="2cc46-113">.NET Standard 2.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2cc46-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="2cc46-114">.NET Framework 4.7.2 和更新版本</span><span class="sxs-lookup"><span data-stu-id="2cc46-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="2cc46-115">.NET Core 2.0、2.1 和2。2</span><span class="sxs-lookup"><span data-stu-id="2cc46-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2cc46-116">其他資源</span><span class="sxs-lookup"><span data-stu-id="2cc46-116">Additional resources</span></span>

* [<span data-ttu-id="2cc46-117">如何使用程式庫</span><span class="sxs-lookup"><span data-stu-id="2cc46-117">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="2cc46-118">[如何從進行遷移Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="2cc46-118">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="2cc46-119">如何撰寫轉換器</span><span class="sxs-lookup"><span data-stu-id="2cc46-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="2cc46-120">[System.Text.Json原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="2cc46-120">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="2cc46-121">[System.Text.JsonAPI 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="2cc46-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="2cc46-122">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="2cc46-122">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
