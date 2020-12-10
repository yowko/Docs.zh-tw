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
ms.openlocfilehash: 3e2fb8cbdd35e772b5e97c731199f69aa834bd0a
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009738"
---
# <a name="how-to-enable-case-insensitive-property-name-matching-with-no-locsystemtextjson"></a><span data-ttu-id="6e427-103">如何啟用不區分大小寫的屬性名稱比對 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="6e427-103">How to enable case-insensitive property name matching with System.Text.Json</span></span>

<span data-ttu-id="6e427-104">在本文中，您將瞭解如何使用命名空間來啟用不區分大小寫的屬性名稱比對 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="6e427-104">In this article, you will learn how to enable case-insensitive property name matching with the `System.Text.Json` namespace.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="6e427-105">不區分大小寫的屬性比對</span><span class="sxs-lookup"><span data-stu-id="6e427-105">Case-insensitive property matching</span></span>

<span data-ttu-id="6e427-106">根據預設，還原序列化會尋找 JSON 與目標物件屬性之間是否有區分大小寫的屬性名稱相符專案。</span><span class="sxs-lookup"><span data-stu-id="6e427-106">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="6e427-107">若要變更此行為，請將設定 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> 為 `true` ：</span><span class="sxs-lookup"><span data-stu-id="6e427-107">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

> [!NOTE]
> <span data-ttu-id="6e427-108">[Web 預設值](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="6e427-108">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is case-insensitive.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs" id="Deserialize":::

<span data-ttu-id="6e427-109">以下是使用 camel 大小寫屬性名稱的範例 JSON。</span><span class="sxs-lookup"><span data-stu-id="6e427-109">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="6e427-110">您可以將它還原序列化為具有 Pascal 案例屬性名稱的下列型別。</span><span class="sxs-lookup"><span data-stu-id="6e427-110">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="see-also"></a><span data-ttu-id="6e427-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e427-111">See also</span></span>

* [<span data-ttu-id="6e427-112">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="6e427-112">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="6e427-113">如何將 JSON 序列化及還原序列化</span><span class="sxs-lookup"><span data-stu-id="6e427-113">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="6e427-114">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="6e427-114">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="6e427-115">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="6e427-115">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="6e427-116">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="6e427-116">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="6e427-117">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="6e427-117">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="6e427-118">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="6e427-118">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="6e427-119">保留參考</span><span class="sxs-lookup"><span data-stu-id="6e427-119">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="6e427-120">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="6e427-120">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="6e427-121">多型序列化</span><span class="sxs-lookup"><span data-stu-id="6e427-121">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="6e427-122">從遷移 Newtonsoft.Json 至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="6e427-122">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="6e427-123">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="6e427-123">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="6e427-124">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="6e427-124">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="6e427-125">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="6e427-125">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="6e427-126">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="6e427-126">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="6e427-127">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="6e427-127">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="6e427-128">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="6e427-128">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
