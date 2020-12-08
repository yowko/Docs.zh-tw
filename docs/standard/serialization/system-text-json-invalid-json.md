---
title: 如何允許某些種類的無效 JSON 搭配 System.Text.Json
description: 瞭解如何在 .NET 中序列化和還原序列化時，允許批註、尾端逗號和引號數位。
ms.date: 12/03/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 1b6402952c4765290d22b530834ed831a68bd2fe
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851239"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a><span data-ttu-id="c0de4-103">如何允許某些種類的無效 JSON 搭配 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c0de4-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="c0de4-104">在本文中，您將瞭解如何在 JSON 中允許批註、尾端逗號和引號數位，以及如何以字串的形式寫入數位。</span><span class="sxs-lookup"><span data-stu-id="c0de4-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="c0de4-105">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="c0de4-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="c0de4-106">根據預設，JSON 中不允許批註和結尾的逗號。</span><span class="sxs-lookup"><span data-stu-id="c0de4-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="c0de4-107">若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設定為 `JsonCommentHandling.Skip` 。</span><span class="sxs-lookup"><span data-stu-id="c0de4-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="c0de4-108">若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="c0de4-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="c0de4-109">下列範例顯示如何允許兩者：</span><span class="sxs-lookup"><span data-stu-id="c0de4-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

<span data-ttu-id="c0de4-110">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="c0de4-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
  // Comments on
  /* separate lines */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="c0de4-111">以引號允許或寫入數位</span><span class="sxs-lookup"><span data-stu-id="c0de4-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="c0de4-112">某些序列化程式會將數位編碼為 JSON 字串， (以引號括住) 。</span><span class="sxs-lookup"><span data-stu-id="c0de4-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="c0de4-113">例如︰</span><span class="sxs-lookup"><span data-stu-id="c0de4-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="c0de4-114">不要這樣撰寫：</span><span class="sxs-lookup"><span data-stu-id="c0de4-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="c0de4-115">若要序列化引號中的數位，或在整個輸入物件圖形中接受以引號括住的數位，請設定 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c0de4-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

<span data-ttu-id="c0de4-116">當您 `System.Text.Json` 透過 ASP.NET Core 間接使用時，當還原序列化時，會允許括住的數位，因為 ASP.NET Core 指定 [web 預設選項](xref:System.Text.Json.JsonSerializerDefaults.Web)。</span><span class="sxs-lookup"><span data-stu-id="c0de4-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="c0de4-117">若要允許或寫入特定屬性、欄位或類型的引號號碼，請使用 [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="c0de4-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="c0de4-118">`System.Text.Json` 在 .NET Core 3.1 中，不支援序列化或還原序列化以引號括住的數位。</span><span class="sxs-lookup"><span data-stu-id="c0de4-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="c0de4-119">如需詳細資訊，請參閱 [允許或寫入以引號括](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)住的數位。</span><span class="sxs-lookup"><span data-stu-id="c0de4-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="c0de4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0de4-120">See also</span></span>

* [<span data-ttu-id="c0de4-121">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="c0de4-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="c0de4-122">Instantiate JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="c0de4-122">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="c0de4-123">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="c0de4-123">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="c0de4-124">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="c0de4-124">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="c0de4-125">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="c0de4-125">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="c0de4-126">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="c0de4-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="c0de4-127">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="c0de4-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="c0de4-128">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="c0de4-128">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="c0de4-129">多型序列化</span><span class="sxs-lookup"><span data-stu-id="c0de4-129">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="c0de4-130">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="c0de4-130">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
