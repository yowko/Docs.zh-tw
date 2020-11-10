---
title: '使用 c # 序列化和還原序列化 JSON-.NET'
description: '本總覽說明在 System.Text.Json .net 中序列化至 JSON 並從 JSON 還原序列化的命名空間功能。'
ms.date: 01/10/2020
no-loc:
- 'System.Text.Json'
- 'Newtonsoft.Json'
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d8bd5bcf78db534bd722972db01253cbd13a7a06
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282409"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="f18d9-103">JSON 序列化和還原序列化 (.NET 中的封送處理和 unmarshalling) -總覽</span><span class="sxs-lookup"><span data-stu-id="f18d9-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="f18d9-104">`System.Text.Json`命名空間提供序列化和還原序列化 JavaScript 物件標記法 (JSON) 的功能。</span><span class="sxs-lookup"><span data-stu-id="f18d9-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="f18d9-105">程式庫設計強調大量功能集的高效能和低記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="f18d9-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="f18d9-106">內建的 UTF-8 支援可將讀取和寫入 JSON 文字的程式優化為 UTF-8，這是 web 上的資料和磁片上的檔案最普遍的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="f18d9-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="f18d9-107">此程式庫也會提供類別，以處理記憶體中的檔物件模型 (DOM) 。</span><span class="sxs-lookup"><span data-stu-id="f18d9-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="f18d9-108">這項功能可讓您在 JSON 檔案或字串中啟用元素的隨機唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="f18d9-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="f18d9-109">如何取得程式庫</span><span class="sxs-lookup"><span data-stu-id="f18d9-109">How to get the library</span></span>

* <span data-ttu-id="f18d9-110">此程式庫內建為適用于 .NET Core 3.0 和更新版本之共用架構的一部分。</span><span class="sxs-lookup"><span data-stu-id="f18d9-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="f18d9-111">針對較舊的 framework 版本，請安裝 [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="f18d9-111">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="f18d9-112">封裝支援：</span><span class="sxs-lookup"><span data-stu-id="f18d9-112">The package supports:</span></span>

  * <span data-ttu-id="f18d9-113">.NET Standard 2.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f18d9-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="f18d9-114">.NET Framework 4.7.2 和更新版本</span><span class="sxs-lookup"><span data-stu-id="f18d9-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="f18d9-115">.NET Core 2.0、2.1 和2。2</span><span class="sxs-lookup"><span data-stu-id="f18d9-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f18d9-116">其他資源</span><span class="sxs-lookup"><span data-stu-id="f18d9-116">Additional resources</span></span>

* [<span data-ttu-id="f18d9-117">如何使用程式庫</span><span class="sxs-lookup"><span data-stu-id="f18d9-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="f18d9-118">如何遷移 Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="f18d9-118">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="f18d9-119">如何寫入轉換器</span><span class="sxs-lookup"><span data-stu-id="f18d9-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="f18d9-120">[System.Text.Json 原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f18d9-120">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="f18d9-121">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f18d9-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f18d9-122">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f18d9-122">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
