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
ms.openlocfilehash: 2c40d42b26bc5bd05f592cc51c6b5b9b4c6bbd9e
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439929"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a><span data-ttu-id="892d0-103">如何使用來處理溢位 JSON System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="892d0-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="892d0-104">在本文中，您將瞭解如何使用命名空間來處理溢位 JSON `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="892d0-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="892d0-105">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="892d0-105">Handle overflow JSON</span></span>

<span data-ttu-id="892d0-106">還原序列化時，您可能會收到 JSON 中的資料，而該資料不是由目標型別的屬性所表示。</span><span class="sxs-lookup"><span data-stu-id="892d0-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="892d0-107">例如，假設您的目標型別是：</span><span class="sxs-lookup"><span data-stu-id="892d0-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="892d0-108">而且要還原序列化的 JSON 如下所示：</span><span class="sxs-lookup"><span data-stu-id="892d0-108">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="892d0-109">如果您將顯示的 JSON 還原序列化為顯示的類型， `DatesAvailable` 和 `SummaryWords` 屬性就不會有任何地方，而且會遺失。</span><span class="sxs-lookup"><span data-stu-id="892d0-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="892d0-110">若要捕獲額外的資料（例如這些屬性），請將 [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 屬性套用至類型或的屬性 `Dictionary<string,object>` `Dictionary<string,JsonElement>` ：</span><span class="sxs-lookup"><span data-stu-id="892d0-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

<span data-ttu-id="892d0-111">當您將稍早所示的 JSON 還原序列化為此範例類型時，額外的資料會變成屬性的索引鍵/值組 `ExtensionData` ：</span><span class="sxs-lookup"><span data-stu-id="892d0-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="892d0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="892d0-112">Property</span></span> | <span data-ttu-id="892d0-113">值</span><span class="sxs-lookup"><span data-stu-id="892d0-113">Value</span></span> | <span data-ttu-id="892d0-114">注意</span><span class="sxs-lookup"><span data-stu-id="892d0-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="892d0-115">JSON)  (區分大小寫不符 `temperatureCelsius` ，因此未設定屬性。</span><span class="sxs-lookup"><span data-stu-id="892d0-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="892d0-116">因為大小寫不相符，所以這個 JSON 屬性是一個額外的，並且會成為字典中的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="892d0-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="892d0-117">JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。</span><span class="sxs-lookup"><span data-stu-id="892d0-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="892d0-118">JSON 中的額外屬性會變成成對的索引鍵/值，並以陣列作為值物件。</span><span class="sxs-lookup"><span data-stu-id="892d0-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="892d0-119">序列化目標物件時，擴充功能資料索引鍵值組會變成 JSON 屬性，就像在傳入的 JSON 中一樣：</span><span class="sxs-lookup"><span data-stu-id="892d0-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="892d0-120">請注意， `ExtensionData` 屬性名稱不會出現在 JSON 中。</span><span class="sxs-lookup"><span data-stu-id="892d0-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="892d0-121">此行為可讓 JSON 進行往返，而不會遺失任何額外的資料，否則不會還原序列化。</span><span class="sxs-lookup"><span data-stu-id="892d0-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="892d0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="892d0-122">See also</span></span>

* [<span data-ttu-id="892d0-123">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="892d0-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="892d0-124">具現化 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="892d0-124">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="892d0-125">啟用不區分大小寫的比對</span><span class="sxs-lookup"><span data-stu-id="892d0-125">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="892d0-126">自訂屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="892d0-126">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="892d0-127">略過屬性</span><span class="sxs-lookup"><span data-stu-id="892d0-127">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="892d0-128">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="892d0-128">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="892d0-129">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="892d0-129">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="892d0-130">不可變類型和非公用存取子</span><span class="sxs-lookup"><span data-stu-id="892d0-130">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="892d0-131">多型序列化</span><span class="sxs-lookup"><span data-stu-id="892d0-131">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="892d0-132">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="892d0-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
