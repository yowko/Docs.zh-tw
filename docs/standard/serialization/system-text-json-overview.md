---
title: '使用 c # 序列化和還原序列化 JSON-.NET'
description: 本總覽說明在 System.Text.Json .net 中序列化至 JSON 並從 JSON 還原序列化的命名空間功能。
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: b4432e7a137720216e7c0941b3384ce7ad7049e9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970911"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="ddbee-103">JSON 序列化和還原序列化 (.NET 中的封送處理和 unmarshalling) -總覽</span><span class="sxs-lookup"><span data-stu-id="ddbee-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="ddbee-104">`System.Text.Json`命名空間提供序列化和還原序列化 JavaScript 物件標記法 (JSON) 的功能。</span><span class="sxs-lookup"><span data-stu-id="ddbee-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="ddbee-105">程式庫設計強調大量功能集的高效能和低記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="ddbee-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="ddbee-106">內建的 UTF-8 支援可將讀取和寫入 JSON 文字的程式優化為 UTF-8，這是 web 上的資料和磁片上的檔案最普遍的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="ddbee-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="ddbee-107">此程式庫也會提供類別，以處理記憶體中的檔物件模型 (DOM) 。</span><span class="sxs-lookup"><span data-stu-id="ddbee-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="ddbee-108">這項功能可讓您在 JSON 檔案或字串中啟用元素的隨機唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="ddbee-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="ddbee-109">如何取得程式庫</span><span class="sxs-lookup"><span data-stu-id="ddbee-109">How to get the library</span></span>

* <span data-ttu-id="ddbee-110">此程式庫內建為適用于 .NET Core 3.0 和更新版本之共用架構的一部分。</span><span class="sxs-lookup"><span data-stu-id="ddbee-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="ddbee-111">針對較舊的 framework 版本，請安裝 [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="ddbee-111">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="ddbee-112">封裝支援：</span><span class="sxs-lookup"><span data-stu-id="ddbee-112">The package supports:</span></span>

  * <span data-ttu-id="ddbee-113">.NET Standard 2.0 和更新版本</span><span class="sxs-lookup"><span data-stu-id="ddbee-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="ddbee-114">.NET Framework 4.7.2 和更新版本</span><span class="sxs-lookup"><span data-stu-id="ddbee-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="ddbee-115">.NET Core 2.0、2.1 和2。2</span><span class="sxs-lookup"><span data-stu-id="ddbee-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ddbee-116">其他資源</span><span class="sxs-lookup"><span data-stu-id="ddbee-116">Additional resources</span></span>

* [<span data-ttu-id="ddbee-117">如何使用程式庫</span><span class="sxs-lookup"><span data-stu-id="ddbee-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="ddbee-118">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="ddbee-118">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="ddbee-119">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="ddbee-119">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="ddbee-120">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="ddbee-120">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="ddbee-121">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="ddbee-121">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="ddbee-122">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="ddbee-122">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="ddbee-123">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="ddbee-123">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="ddbee-124">保留參考</span><span class="sxs-lookup"><span data-stu-id="ddbee-124">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="ddbee-125">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="ddbee-125">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="ddbee-126">多型序列化</span><span class="sxs-lookup"><span data-stu-id="ddbee-126">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="ddbee-127">從遷移 Newtonsoft.Json 至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="ddbee-127">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="ddbee-128">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="ddbee-128">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="ddbee-129">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="ddbee-129">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="ddbee-130">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="ddbee-130">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="ddbee-131">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="ddbee-131">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="ddbee-132">中支援的集合類型 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="ddbee-132">Supported collection types in System.Text.Json</span></span>](system-text-json-supported-collection-types.md)
* <span data-ttu-id="ddbee-133">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="ddbee-133">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="ddbee-134">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="ddbee-134">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
