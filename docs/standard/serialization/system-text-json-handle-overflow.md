---
title: 如何使用來處理溢位 JSON System.Text.Json
description: 瞭解如何在 .NET 中序列化至 JSON 並進行還原序列化時，處理溢位 JSON。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 265ce4f77d353720419122d17c36e508a377b68f
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008912"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a><span data-ttu-id="5b805-103">如何使用來處理溢位 JSON System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="5b805-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="5b805-104">在本文中，您將瞭解如何使用命名空間來處理溢位 JSON `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="5b805-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="5b805-105">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="5b805-105">Handle overflow JSON</span></span>

<span data-ttu-id="5b805-106">還原序列化時，您可能會收到 JSON 中的資料，而該資料不是由目標型別的屬性所表示。</span><span class="sxs-lookup"><span data-stu-id="5b805-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="5b805-107">例如，假設您的目標型別是：</span><span class="sxs-lookup"><span data-stu-id="5b805-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="5b805-108">而且要還原序列化的 JSON 如下所示：</span><span class="sxs-lookup"><span data-stu-id="5b805-108">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="5b805-109">如果您將顯示的 JSON 還原序列化為顯示的類型， `DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="5b805-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="5b805-110">若要捕獲額外的資料（例如這些屬性），請將 [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 屬性套用至類型或的屬性 `Dictionary<string,object>` `Dictionary<string,JsonElement>` ：</span><span class="sxs-lookup"><span data-stu-id="5b805-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

<span data-ttu-id="5b805-111">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成屬性的索引鍵/值組 `ExtensionData` ：</span><span class="sxs-lookup"><span data-stu-id="5b805-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="5b805-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5b805-112">Property</span></span> | <span data-ttu-id="5b805-113">值</span><span class="sxs-lookup"><span data-stu-id="5b805-113">Value</span></span> | <span data-ttu-id="5b805-114">注意</span><span class="sxs-lookup"><span data-stu-id="5b805-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="5b805-115">JSON)  (區分大小寫不符 `temperatureCelsius` ，因此未設定屬性。</span><span class="sxs-lookup"><span data-stu-id="5b805-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="5b805-116">因為大小寫不相符，所以這個 JSON 屬性是一個額外的，並且會成為字典中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="5b805-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="5b805-117">JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。</span><span class="sxs-lookup"><span data-stu-id="5b805-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="5b805-118">JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。</span><span class="sxs-lookup"><span data-stu-id="5b805-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="5b805-119">序列化目標物件時，擴充功能資料索引鍵值組會變成 JSON 屬性，就像在傳入的 JSON 中一樣：</span><span class="sxs-lookup"><span data-stu-id="5b805-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="5b805-120">請注意， `ExtensionData` 屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="5b805-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="5b805-121">此行為可讓 JSON 進行往返，而不會遺失任何額外的資料，否則不會還原序列化。</span><span class="sxs-lookup"><span data-stu-id="5b805-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b805-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b805-122">See also</span></span>

* [<span data-ttu-id="5b805-123">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="5b805-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="5b805-124">如何將 JSON 序列化及還原序列化</span><span class="sxs-lookup"><span data-stu-id="5b805-124">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="5b805-125">具現化 JsonSerializerOptions 實例</span><span class="sxs-lookup"><span data-stu-id="5b805-125">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="5b805-126">啟用不區分大小寫比對</span><span class="sxs-lookup"><span data-stu-id="5b805-126">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="5b805-127">自訂屬性名稱與值</span><span class="sxs-lookup"><span data-stu-id="5b805-127">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="5b805-128">忽略屬性</span><span class="sxs-lookup"><span data-stu-id="5b805-128">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="5b805-129">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="5b805-129">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="5b805-130">保留參考</span><span class="sxs-lookup"><span data-stu-id="5b805-130">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="5b805-131">不可變型別及非公用存取子</span><span class="sxs-lookup"><span data-stu-id="5b805-131">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="5b805-132">多型序列化</span><span class="sxs-lookup"><span data-stu-id="5b805-132">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="5b805-133">從遷移 Newtonsoft.Json 至 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="5b805-133">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="5b805-134">自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="5b805-134">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="5b805-135">撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="5b805-135">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="5b805-136">撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="5b805-136">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="5b805-137">DateTime 和 DateTimeOffset 支援</span><span class="sxs-lookup"><span data-stu-id="5b805-137">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="5b805-138">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="5b805-138">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="5b805-139">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="5b805-139">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
