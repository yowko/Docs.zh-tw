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
ms.openlocfilehash: 2559b081010fb0a2fa208b121cb095efdeb8da2e
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009804"
---
# <a name="how-to-allow-some-kinds-of-invalid-json-with-no-locsystemtextjson"></a><span data-ttu-id="3d339-103">如何允許某些種類的無效 JSON 搭配 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="3d339-103">How to allow some kinds of invalid JSON with System.Text.Json</span></span>

<span data-ttu-id="3d339-104">在本文中，您將瞭解如何在 JSON 中允許批註、尾端逗號和引號數位，以及如何以字串的形式寫入數位。</span><span class="sxs-lookup"><span data-stu-id="3d339-104">In this article, you will learn how to allow comments, trailing commas, and quoted numbers in JSON, and how to write numbers as strings.</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="3d339-105">允許批註和尾端逗號</span><span class="sxs-lookup"><span data-stu-id="3d339-105">Allow comments and trailing commas</span></span>

<span data-ttu-id="3d339-106">根據預設，JSON 中不允許批註和結尾的逗號。</span><span class="sxs-lookup"><span data-stu-id="3d339-106">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="3d339-107">若要允許 JSON 中的批註，請將 <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> 屬性設定為 `JsonCommentHandling.Skip` 。</span><span class="sxs-lookup"><span data-stu-id="3d339-107">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="3d339-108">若要允許尾端逗號，請將 <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="3d339-108">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="3d339-109">下列範例顯示如何允許兩者：</span><span class="sxs-lookup"><span data-stu-id="3d339-109">The following example shows how to allow both:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs" id="Deserialize":::

<span data-ttu-id="3d339-110">以下是包含批註和尾端逗號的範例 JSON：</span><span class="sxs-lookup"><span data-stu-id="3d339-110">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
  // Comments on
  /* separate lines */
}
```

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="3d339-111">以引號允許或寫入數位</span><span class="sxs-lookup"><span data-stu-id="3d339-111">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="3d339-112">某些序列化程式會將數位編碼為 JSON 字串， (以引號括住) 。</span><span class="sxs-lookup"><span data-stu-id="3d339-112">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span>

<span data-ttu-id="3d339-113">例如：</span><span class="sxs-lookup"><span data-stu-id="3d339-113">For example:</span></span>

```json
{
    "DegreesCelsius": "23"
}
```

<span data-ttu-id="3d339-114">不要這樣撰寫：</span><span class="sxs-lookup"><span data-stu-id="3d339-114">Instead of:</span></span>

```json
{
    "DegreesCelsius": 23
}
```

<span data-ttu-id="3d339-115">若要序列化引號中的數位，或在整個輸入物件圖形中接受以引號括住的數位，請設定 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="3d339-115">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-29":::

<span data-ttu-id="3d339-116">當您 `System.Text.Json` 透過 ASP.NET Core 間接使用時，當還原序列化時，會允許括住的數位，因為 ASP.NET Core 指定 [web 預設選項](xref:System.Text.Json.JsonSerializerDefaults.Web)。</span><span class="sxs-lookup"><span data-stu-id="3d339-116">When you use `System.Text.Json` indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="3d339-117">若要允許或寫入特定屬性、欄位或類型的引號號碼，請使用 [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="3d339-117">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="3d339-118">`System.Text.Json` 在 .NET Core 3.1 中，不支援序列化或還原序列化以引號括住的數位。</span><span class="sxs-lookup"><span data-stu-id="3d339-118">`System.Text.Json` in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="3d339-119">如需詳細資訊，請參閱 [允許或寫入以引號括](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes)住的數位。</span><span class="sxs-lookup"><span data-stu-id="3d339-119">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="3d339-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d339-120">See also</span></span>

* [<span data-ttu-id="3d339-121">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="3d339-121">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="3d339-122">如何將 JSON 序列化及還原序列化</span><span class="sxs-lookup"><span data-stu-id="3d339-122">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="3d339-123">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="3d339-123">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="3d339-124">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="3d339-124">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="3d339-125">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="3d339-125">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="3d339-126">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="3d339-126">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="3d339-127">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="3d339-127">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="3d339-128">保留參考</span><span class="sxs-lookup"><span data-stu-id="3d339-128">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="3d339-129">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="3d339-129">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="3d339-130">多型序列化</span><span class="sxs-lookup"><span data-stu-id="3d339-130">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="3d339-131">從遷移 Newtonsoft.Json 至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="3d339-131">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="3d339-132">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="3d339-132">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="3d339-133">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="3d339-133">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="3d339-134">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="3d339-134">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="3d339-135">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="3d339-135">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="3d339-136">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="3d339-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="3d339-137">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="3d339-137">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
