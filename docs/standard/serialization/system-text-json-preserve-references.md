---
title: 如何保留參考 System.Text.Json
description: 瞭解如何在 .NET 中的 JSON 序列化和還原序列化時保留參考並處理迴圈參考。
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d358c953c0979ca097c080fcd750d5ef95b07de0
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008730"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="c9e7e-103">如何保留參考並處理迴圈參考 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c9e7e-103">How to preserve references and handle circular references with System.Text.Json</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="c9e7e-104">若要保留參考並處理迴圈參考，請將設定 <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> 為 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-104">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="c9e7e-105">這項設定會導致下列行為：</span><span class="sxs-lookup"><span data-stu-id="c9e7e-105">This setting causes the following behavior:</span></span>

* <span data-ttu-id="c9e7e-106">序列化時：</span><span class="sxs-lookup"><span data-stu-id="c9e7e-106">On serialize:</span></span>

  <span data-ttu-id="c9e7e-107">撰寫複雜型別時，序列化程式也會將中繼資料屬性寫入 (`$id` 、 `$values` 和 `$ref`) 。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-107">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="c9e7e-108">還原序列化時：</span><span class="sxs-lookup"><span data-stu-id="c9e7e-108">On deserialize:</span></span>

  <span data-ttu-id="c9e7e-109">雖然不是必要的) ，但還原序列化程式會嘗試瞭解中繼資料，但 (的預期。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-109">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="c9e7e-110">下列程式碼說明如何使用此 `Preserve` 設定。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-110">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="c9e7e-111">這項功能不能用來保留實數值型別或不可變的類型。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-111">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="c9e7e-112">在還原序列化時，會在讀取整個裝載之後，建立不可變型別的實例。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-112">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="c9e7e-113">因此，如果它的參考出現在 JSON 承載內，就不可能還原序列化相同的實例。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-113">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="c9e7e-114">如果是實值型別、不可變的型別和陣列，則不會序列化任何參考中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-114">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="c9e7e-115">在還原序列化時，如果找到或，則會擲回例外狀況 `$ref` `$id` 。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-115">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="c9e7e-116">不過，實值型別 `$id` 會忽略 (，而 `$values` 在集合的情況下) ，讓您可以還原序列化使用序列化的承載 Newtonsoft.Json 。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-116">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="c9e7e-117">Newtonsoft.Json 會序列化這類類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-117">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="c9e7e-118">若要判斷物件是否相等， System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> 請使用，它會使用參考相等 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) 而不是 <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> 在比較兩個物件實例時 (值相等。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-118">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="c9e7e-119">如需如何序列化和還原序列化參考的詳細資訊，請參閱 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-119">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c9e7e-120"><xref:System.Text.Json.Serialization.ReferenceResolver>類別會定義在序列化和還原序列化時保留參考的行為。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-120">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="c9e7e-121">建立衍生類別以指定自訂行為。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-121">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="c9e7e-122">如需範例，請參閱 [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs)。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-122">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="c9e7e-123">System.Text.Json 在 .NET Core 3.1 中，只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c9e7e-123">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="c9e7e-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9e7e-124">See also</span></span>

* [<span data-ttu-id="c9e7e-125">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="c9e7e-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="c9e7e-126">如何將 JSON 序列化及還原序列化</span><span class="sxs-lookup"><span data-stu-id="c9e7e-126">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="c9e7e-127">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="c9e7e-127">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="c9e7e-128">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="c9e7e-128">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="c9e7e-129">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="c9e7e-129">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="c9e7e-130">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="c9e7e-130">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="c9e7e-131">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="c9e7e-131">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="c9e7e-132">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="c9e7e-132">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="c9e7e-133">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="c9e7e-133">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="c9e7e-134">多型序列化</span><span class="sxs-lookup"><span data-stu-id="c9e7e-134">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="c9e7e-135">從遷移 Newtonsoft.Json 至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c9e7e-135">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="c9e7e-136">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="c9e7e-136">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="c9e7e-137">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="c9e7e-137">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="c9e7e-138">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="c9e7e-138">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="c9e7e-139">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="c9e7e-139">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="c9e7e-140">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="c9e7e-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="c9e7e-141">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="c9e7e-141">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
