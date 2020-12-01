---
title: 如何啟用不區分大小寫的屬性名稱比對 System.Text.Json
description: 瞭解如何在 .NET 中序列化至 JSON 並進行序列化時，啟用不區分大小寫的屬性名稱比對。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4bd57d32120f51ffd1ff09c9817edbafa28a3f19
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439896"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="76df6-103">如何啟用不區分大小寫的屬性名稱比對 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="76df6-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="76df6-104">在本文中，您將瞭解如何使用命名空間來啟用不區分大小寫的屬性名稱比對 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="76df6-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="76df6-105">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="76df6-105">Case-insensitive property matching</span></span>

<span data-ttu-id="76df6-106">根據預設，還原序列化會尋找 JSON 與目標物件屬性之間是否有區分大小寫的屬性名稱相符專案。</span><span class="sxs-lookup"><span data-stu-id="76df6-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="76df6-107">若要變更此行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="76df6-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="76df6-108">[Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="76df6-108">The [web defaults](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="76df6-109">以下是使用 camel 大小寫屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="76df6-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="76df6-110">您可以將它還原序列化為具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="76df6-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="76df6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76df6-111">See also</span></span>

* [<span data-ttu-id="76df6-112">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="76df6-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="76df6-113">具現化 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="76df6-113">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="76df6-114">自訂屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="76df6-114">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="76df6-115">略過屬性</span><span class="sxs-lookup"><span data-stu-id="76df6-115">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="76df6-116">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="76df6-116">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="76df6-117">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="76df6-117">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="76df6-118">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="76df6-118">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="76df6-119">不可變類型和非公用存取子</span><span class="sxs-lookup"><span data-stu-id="76df6-119">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="76df6-120">多型序列化</span><span class="sxs-lookup"><span data-stu-id="76df6-120">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="76df6-121">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="76df6-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
