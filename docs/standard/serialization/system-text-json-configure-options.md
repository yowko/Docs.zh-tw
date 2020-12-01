---
title: 如何使用具現化 JsonSerializerOptions System.Text.Json
description: 瞭解如何藉由複製現有的實例或使用 web 預設值，來具現化 JsonSerializerOptions 實例。
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
ms.openlocfilehash: 0febfe15f36856f10699fd327fb17c146277eb9b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439942"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="2919d-103">如何使用具現化 JsonSerializerOptions 實例 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="2919d-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="2919d-104">在本文中，您將瞭解如何藉 <xref:System.Text.Json.JsonSerializerOptions> 由複製現有的實例或使用 web 預設值來具現化實例。</span><span class="sxs-lookup"><span data-stu-id="2919d-104">In this article, you'll learn how to instantiate <xref:System.Text.Json.JsonSerializerOptions> instances by copying existing instances or with web defaults.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="2919d-105">複製 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="2919d-105">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="2919d-106">有 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerOptions) # A3，可讓您使用與現有實例相同的選項來建立新的實例，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2919d-106">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="2919d-107">`JsonSerializerOptions`在 .Net Core 3.1 中無法使用採用現有實例的函式。</span><span class="sxs-lookup"><span data-stu-id="2919d-107">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="2919d-108">JsonSerializerOptions 的 Web 預設值</span><span class="sxs-lookup"><span data-stu-id="2919d-108">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="2919d-109">以下是針對 web 應用程式具有不同預設值的選項：</span><span class="sxs-lookup"><span data-stu-id="2919d-109">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="2919d-110">有一個 [JsonSerializerOptions 的函式] (x： System.Text.Json 。JsonSerializerOptions。% 23ctor (System.Text.Json 。JsonSerializerDefaults) ？ view = net-5.0&preserve-view = true) 可讓您建立新的實例，其中包含 ASP.NET Core 用於 web 應用程式的預設選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2919d-110">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="2919d-111">以下是針對 web 應用程式具有不同預設值的選項：</span><span class="sxs-lookup"><span data-stu-id="2919d-111">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="2919d-112">`JsonSerializerOptions`指定一組預設值的函式在 .Net Core 3.1 中無法使用。</span><span class="sxs-lookup"><span data-stu-id="2919d-112">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="2919d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2919d-113">See also</span></span>

* [<span data-ttu-id="2919d-114">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="2919d-114">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="2919d-115">啟用不區分大小寫的比對</span><span class="sxs-lookup"><span data-stu-id="2919d-115">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="2919d-116">自訂屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="2919d-116">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="2919d-117">略過屬性</span><span class="sxs-lookup"><span data-stu-id="2919d-117">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="2919d-118">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="2919d-118">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="2919d-119">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="2919d-119">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="2919d-120">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="2919d-120">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="2919d-121">不可變類型和非公用存取子</span><span class="sxs-lookup"><span data-stu-id="2919d-121">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="2919d-122">多型序列化</span><span class="sxs-lookup"><span data-stu-id="2919d-122">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="2919d-123">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="2919d-123">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
