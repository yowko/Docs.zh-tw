---
title: 使用C# -.net 序列化和還原序列化 JSON
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 660a2831aa6a807486fc47eae880bcd11347c547
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159542"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="df391-102">.NET 中的 JSON 序列化和還原序列化（封送處理和 unmarshalling）-總覽</span><span class="sxs-lookup"><span data-stu-id="df391-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="df391-103">`System.Text.Json` 命名空間提供從 JavaScript 物件標記法（JSON）序列化及還原序列化的功能。</span><span class="sxs-lookup"><span data-stu-id="df391-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="df391-104">程式庫設計強調廣泛功能集的高效能和低記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="df391-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="df391-105">內建的 UTF-8 支援將讀取和寫入 JSON 文字編碼為 UTF-8 的程式優化，這對網路上的資料和磁片上的檔案而言是最普遍的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="df391-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="df391-106">程式庫也會提供類別，以使用記憶體中的檔物件模型（DOM）。</span><span class="sxs-lookup"><span data-stu-id="df391-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="df391-107">這項功能可讓您對 JSON 檔案或字串中的元素進行隨機唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="df391-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="df391-108">如何取得程式庫</span><span class="sxs-lookup"><span data-stu-id="df391-108">How to get the library</span></span>

* <span data-ttu-id="df391-109">此程式庫內建為[.Net Core 3.0](https://aka.ms/netcore3download)共用架構的一部分。</span><span class="sxs-lookup"><span data-stu-id="df391-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="df391-110">若為其他目標 framework，請安裝[System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="df391-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="df391-111">封裝支援：</span><span class="sxs-lookup"><span data-stu-id="df391-111">The package supports:</span></span>
  * <span data-ttu-id="df391-112">.NET Standard 2.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="df391-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="df391-113">.NET Framework 4.7.2 和更新版本</span><span class="sxs-lookup"><span data-stu-id="df391-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="df391-114">.NET Core 2.0、2.1 和2.2</span><span class="sxs-lookup"><span data-stu-id="df391-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="df391-115">其他資源</span><span class="sxs-lookup"><span data-stu-id="df391-115">Additional resources</span></span>

* [<span data-ttu-id="df391-116">如何使用程式庫</span><span class="sxs-lookup"><span data-stu-id="df391-116">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="df391-117">[如何從 Newtonsoft.Json 遷移](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="df391-117">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="df391-118">如何撰寫轉換器</span><span class="sxs-lookup"><span data-stu-id="df391-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="df391-119">[System.Text.Json 原始碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="df391-119">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="df391-120">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="df391-120">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="df391-121">[System.Text.Json。序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="df391-121">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
