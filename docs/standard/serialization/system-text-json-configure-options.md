---
title: 如何使用具現化 JsonSerializerOptions System.Text.Json
description: 瞭解如何避免效能問題，以及如何針對 JsonSerializerOptions 實例使用可用的函式。
ms.date: 12/02/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 257c99e117dea9a9b3ab2352c9a442d71a2cdabd
ms.sourcegitcommit: 0014aa4d5cb2da56a70e03fc68f663d64df5247a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96918550"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="9ff58-103">如何使用具現化 JsonSerializerOptions 實例 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="9ff58-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="9ff58-104">本文說明如何在使用時避免發生效能問題 <xref:System.Text.Json.JsonSerializerOptions> 。</span><span class="sxs-lookup"><span data-stu-id="9ff58-104">This article explains how to avoid performance problems when you use <xref:System.Text.Json.JsonSerializerOptions>.</span></span> <span data-ttu-id="9ff58-105">它也會示範如何使用可用的參數化的函式。</span><span class="sxs-lookup"><span data-stu-id="9ff58-105">It also shows how to use the parameterized constructors that are available.</span></span>

## <a name="reuse-jsonserializeroptions-instances"></a><span data-ttu-id="9ff58-106">重複使用 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="9ff58-106">Reuse JsonSerializerOptions instances</span></span>

<span data-ttu-id="9ff58-107">如果您 `JsonSerializerOptions` 重複使用相同的選項，請勿 `JsonSerializerOptions` 在每次使用時建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="9ff58-107">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="9ff58-108">每次呼叫時重複使用相同的實例。</span><span class="sxs-lookup"><span data-stu-id="9ff58-108">Reuse the same instance for every call.</span></span> <span data-ttu-id="9ff58-109">本指南適用于您為自訂轉換器撰寫的程式碼，以及當您呼叫 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 或時 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9ff58-109">This guidance applies to code you write for custom converters and when you call <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="9ff58-110">下列程式碼示範使用新選項實例的效能負面影響。</span><span class="sxs-lookup"><span data-stu-id="9ff58-110">The following code demonstrates the performance penalty for using new options instances.</span></span>

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

<span data-ttu-id="9ff58-111">上述程式碼會使用相同的選項實例，將小型物件100000次序列化。</span><span class="sxs-lookup"><span data-stu-id="9ff58-111">The preceding code serializes a small object 100,000 times using the same options instance.</span></span> <span data-ttu-id="9ff58-112">然後，它會將相同的物件序列化相同次數，並每次建立新的選項實例。</span><span class="sxs-lookup"><span data-stu-id="9ff58-112">Then it serializes the same object the same number of times and creates a new options instance each time.</span></span> <span data-ttu-id="9ff58-113">相較于40140毫秒，一般的執行時間差異為190。</span><span class="sxs-lookup"><span data-stu-id="9ff58-113">A typical run time difference is 190 compared to 40,140 milliseconds.</span></span> <span data-ttu-id="9ff58-114">如果您增加反復專案的數目，則差異會更大。</span><span class="sxs-lookup"><span data-stu-id="9ff58-114">The difference is even greater if you increase the number of iterations.</span></span>

<span data-ttu-id="9ff58-115">當傳遞新的選項實例時，序列化程式會在物件圖形中的每個類型第一次序列化期間進行準備階段。</span><span class="sxs-lookup"><span data-stu-id="9ff58-115">The serializer undergoes a warm-up phase during the first serialization of each type in the object graph when a new options instance is passed to it.</span></span> <span data-ttu-id="9ff58-116">此準備工作包括建立序列化所需的中繼資料快取。</span><span class="sxs-lookup"><span data-stu-id="9ff58-116">This warm-up includes creating a cache of metadata that is needed for serialization.</span></span> <span data-ttu-id="9ff58-117">中繼資料包含屬性 getter、setter、函式引數、指定屬性等的委派。</span><span class="sxs-lookup"><span data-stu-id="9ff58-117">The metadata includes delegates to property getters, setters, constructor arguments, specified attributes, and so forth.</span></span> <span data-ttu-id="9ff58-118">此中繼資料快取會儲存在 options 實例中。</span><span class="sxs-lookup"><span data-stu-id="9ff58-118">This metadata cache is stored in the options instance.</span></span> <span data-ttu-id="9ff58-119">相同的準備程式和快取會套用至還原序列化。</span><span class="sxs-lookup"><span data-stu-id="9ff58-119">The same warm-up process and cache applies to deserialization.</span></span>

<span data-ttu-id="9ff58-120">實例中的中繼資料快取大小 `JsonSerializerOptions` 取決於要序列化的類型數目。</span><span class="sxs-lookup"><span data-stu-id="9ff58-120">The size of the metadata cache in a `JsonSerializerOptions` instance depends on the number of types to be serialized.</span></span> <span data-ttu-id="9ff58-121">如果您將許多型別（例如，動態產生的型別）傳遞給序列化程式，快取大小將會持續成長，最後會導致 `OutOfMemoryException` 。</span><span class="sxs-lookup"><span data-stu-id="9ff58-121">If you pass numerous types—for example, dynamically generated types—to the serializer, the cache size will continue to grow and can end up causing an `OutOfMemoryException`.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="9ff58-122">複製 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="9ff58-122">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="9ff58-123">有 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerOptions) # A3，可讓您使用與現有實例相同的選項來建立新的實例，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9ff58-123">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="9ff58-124">`JsonSerializerOptions`在 .Net Core 3.1 中無法使用採用現有實例的函式。</span><span class="sxs-lookup"><span data-stu-id="9ff58-124">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="9ff58-125">JsonSerializerOptions 的 Web 預設值</span><span class="sxs-lookup"><span data-stu-id="9ff58-125">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="9ff58-126">以下是針對 web 應用程式具有不同預設值的選項：</span><span class="sxs-lookup"><span data-stu-id="9ff58-126">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="9ff58-127">有一個 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerDefaults) ？ view = net-5.0&preserve-view = true) 可讓您建立新的實例，其中包含 ASP.NET Core 用於 web 應用程式的預設選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9ff58-127">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="9ff58-128">以下是針對 web 應用程式具有不同預設值的選項：</span><span class="sxs-lookup"><span data-stu-id="9ff58-128">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="9ff58-129">`JsonSerializerOptions`指定一組預設值的函式在 .Net Core 3.1 中無法使用。</span><span class="sxs-lookup"><span data-stu-id="9ff58-129">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="9ff58-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ff58-130">See also</span></span>

* [<span data-ttu-id="9ff58-131">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="9ff58-131">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="9ff58-132">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="9ff58-132">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="9ff58-133">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="9ff58-133">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="9ff58-134">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="9ff58-134">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="9ff58-135">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="9ff58-135">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="9ff58-136">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="9ff58-136">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="9ff58-137">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="9ff58-137">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="9ff58-138">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="9ff58-138">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="9ff58-139">多型序列化</span><span class="sxs-lookup"><span data-stu-id="9ff58-139">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="9ff58-140">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="9ff58-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
