---
title: 如何保留參考 System.Text.Json
description: 瞭解如何在 .NET 中的 JSON 序列化和還原序列化時保留參考並處理迴圈參考。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 9254ca261c7d748c04c311fa56359014f752ff31
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439921"
---
# <a name="how-to-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="f1e61-103">如何處理迴圈參考 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f1e61-103">How to handle circular references with System.Text.Json</span></span>

<span data-ttu-id="f1e61-104">在本文中，您將學習如何使用命名空間來處理迴圈參考 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="f1e61-104">In this article, you will learn how to handle circular references with the `System.Text.Json` namespace.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="f1e61-105">保留參考並處理迴圈參考</span><span class="sxs-lookup"><span data-stu-id="f1e61-105">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="f1e61-106">若要保留參考並處理迴圈參考，請將設定 <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> 為 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f1e61-106">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="f1e61-107">這項設定會導致下列行為：</span><span class="sxs-lookup"><span data-stu-id="f1e61-107">This setting causes the following behavior:</span></span>

* <span data-ttu-id="f1e61-108">序列化時：</span><span class="sxs-lookup"><span data-stu-id="f1e61-108">On serialize:</span></span>

  <span data-ttu-id="f1e61-109">撰寫複雜型別時，序列化程式也會將中繼資料屬性寫入 (`$id` 、 `$values` 和 `$ref`) 。</span><span class="sxs-lookup"><span data-stu-id="f1e61-109">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="f1e61-110">還原序列化時：</span><span class="sxs-lookup"><span data-stu-id="f1e61-110">On deserialize:</span></span>

  <span data-ttu-id="f1e61-111">雖然不是必要的) ，但還原序列化程式會嘗試瞭解中繼資料，但 (的預期。</span><span class="sxs-lookup"><span data-stu-id="f1e61-111">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="f1e61-112">下列程式碼說明如何使用此 `Preserve` 設定。</span><span class="sxs-lookup"><span data-stu-id="f1e61-112">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="f1e61-113">這項功能不能用來保留實數值型別或不可變的類型。</span><span class="sxs-lookup"><span data-stu-id="f1e61-113">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="f1e61-114">在還原序列化時，會在讀取整個裝載之後，建立不可變型別的實例。</span><span class="sxs-lookup"><span data-stu-id="f1e61-114">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="f1e61-115">因此，如果它的參考出現在 JSON 承載內，就不可能還原序列化相同的實例。</span><span class="sxs-lookup"><span data-stu-id="f1e61-115">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="f1e61-116">如果是實值型別、不可變的型別和陣列，則不會序列化任何參考中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f1e61-116">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="f1e61-117">在還原序列化時，如果找到或，則會擲回例外狀況 `$ref` `$id` 。</span><span class="sxs-lookup"><span data-stu-id="f1e61-117">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="f1e61-118">不過，實值型別 `$id` 會忽略 (，而 `$values` 在集合的情況下) ，讓您可以還原序列化使用序列化的承載 Newtonsoft.Json 。</span><span class="sxs-lookup"><span data-stu-id="f1e61-118">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="f1e61-119">Newtonsoft.Json 會序列化這類類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f1e61-119">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="f1e61-120">若要判斷物件是否相等， System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> 請使用，它會使用參考相等 (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) 而不是 <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> 在比較兩個物件實例時 (值相等。</span><span class="sxs-lookup"><span data-stu-id="f1e61-120">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="f1e61-121">如需如何序列化和還原序列化參考的詳細資訊，請參閱 <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f1e61-121">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f1e61-122"><xref:System.Text.Json.Serialization.ReferenceResolver>類別會定義在序列化和還原序列化時保留參考的行為。</span><span class="sxs-lookup"><span data-stu-id="f1e61-122">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="f1e61-123">建立衍生類別以指定自訂行為。</span><span class="sxs-lookup"><span data-stu-id="f1e61-123">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="f1e61-124">如需範例，請參閱 [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs)。</span><span class="sxs-lookup"><span data-stu-id="f1e61-124">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="f1e61-125">System.Text.Json 在 .NET Core 3.1 中，只支援以傳值方式序列化，並擲回迴圈參考的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f1e61-125">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="f1e61-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1e61-126">See also</span></span>

* [<span data-ttu-id="f1e61-127">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="f1e61-127">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="f1e61-128">具現化 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="f1e61-128">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="f1e61-129">啟用不區分大小寫的比對</span><span class="sxs-lookup"><span data-stu-id="f1e61-129">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="f1e61-130">自訂屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="f1e61-130">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="f1e61-131">略過屬性</span><span class="sxs-lookup"><span data-stu-id="f1e61-131">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="f1e61-132">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="f1e61-132">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="f1e61-133">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="f1e61-133">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="f1e61-134">不可變類型和非公用存取子</span><span class="sxs-lookup"><span data-stu-id="f1e61-134">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="f1e61-135">多型序列化</span><span class="sxs-lookup"><span data-stu-id="f1e61-135">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="f1e61-136">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f1e61-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
