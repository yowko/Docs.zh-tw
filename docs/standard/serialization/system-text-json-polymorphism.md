---
title: 如何使用來序列化衍生類別的屬性 System.Text.Json
description: 瞭解如何在 .NET 中序列化至 JSON 並將其序列化，以序列化多型物件。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4b99a402ea4f4c664d3bfd75627ffaf94948d493
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439922"
---
# <a name="how-to-serialize-properties-of-derived-classes-with-no-locsystemtextjson"></a><span data-ttu-id="ae713-103">如何使用來序列化衍生類別的屬性 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="ae713-103">How to serialize properties of derived classes with System.Text.Json</span></span>

<span data-ttu-id="ae713-104">在本文中，您將瞭解如何使用命名空間來序列化衍生類別的屬性 `System.Text.Json` 。</span><span class="sxs-lookup"><span data-stu-id="ae713-104">In this article, you will learn how to serialize properties of derived classes with the `System.Text.Json` namespace.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="ae713-105">序列化衍生類別的屬性</span><span class="sxs-lookup"><span data-stu-id="ae713-105">Serialize properties of derived classes</span></span>

<span data-ttu-id="ae713-106">_不_ 支援多型類型階層的序列化。</span><span class="sxs-lookup"><span data-stu-id="ae713-106">Serialization of a polymorphic type hierarchy is _not_ supported.</span></span> <span data-ttu-id="ae713-107">例如，如果屬性定義為介面或抽象類別，則只有在介面或抽象類別上定義的屬性會序列化，即使執行時間型別具有其他屬性也一樣。</span><span class="sxs-lookup"><span data-stu-id="ae713-107">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="ae713-108">本節將說明此行為的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ae713-108">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="ae713-109">例如，假設您有一個 `WeatherForecast` 類別和一個衍生的類別 `WeatherForecastDerived` ：</span><span class="sxs-lookup"><span data-stu-id="ae713-109">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFDerived":::

<span data-ttu-id="ae713-110">並假設在編譯時期，方法的型別引數 `Serialize` 是 `WeatherForecast` ：</span><span class="sxs-lookup"><span data-stu-id="ae713-110">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeDefault":::

<span data-ttu-id="ae713-111">在此案例中， `WindSpeed` 即使物件實際上是物件，也不會序列化屬性 `weatherForecast` `WeatherForecastDerived` 。</span><span class="sxs-lookup"><span data-stu-id="ae713-111">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="ae713-112">只有基類屬性會序列化：</span><span class="sxs-lookup"><span data-stu-id="ae713-112">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="ae713-113">這項行為旨在協助防止在衍生的執行時間建立型別中意外曝光資料。</span><span class="sxs-lookup"><span data-stu-id="ae713-113">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="ae713-114">若要序列化上述範例中衍生類型的屬性，請使用下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="ae713-114">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="ae713-115">呼叫的多載 <xref:System.Text.Json.JsonSerializer.Serialize%2A> ，可讓您在執行時間指定型別：</span><span class="sxs-lookup"><span data-stu-id="ae713-115">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeGetType":::

* <span data-ttu-id="ae713-116">宣告要序列化為的物件 `object` 。</span><span class="sxs-lookup"><span data-stu-id="ae713-116">Declare the object to be serialized as `object`.</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeObject":::

<span data-ttu-id="ae713-117">在上述範例案例中，這兩種方法都會使 `WindSpeed` 屬性包含在 JSON 輸出中：</span><span class="sxs-lookup"><span data-stu-id="ae713-117">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="ae713-118">這些方法只會針對要序列化的根物件提供多型的序列化，而不是針對該根物件的屬性提供。</span><span class="sxs-lookup"><span data-stu-id="ae713-118">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="ae713-119">如果您將物件定義為類型，則可以取得較低層級物件的多型序列化 `object` 。</span><span class="sxs-lookup"><span data-stu-id="ae713-119">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="ae713-120">例如，假設您的 `WeatherForecast` 類別具有名為 `PreviousForecast` 的屬性，該屬性可以定義為類型 `WeatherForecast` 或 `object` ：</span><span class="sxs-lookup"><span data-stu-id="ae713-120">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPrevious":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPreviousAsObject":::

<span data-ttu-id="ae713-121">如果 `PreviousForecast` 屬性包含的實例 `WeatherForecastDerived` ：</span><span class="sxs-lookup"><span data-stu-id="ae713-121">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="ae713-122">序列化的 JSON 輸出 `WeatherForecastWithPrevious` **不包括在內** `WindSpeed` 。</span><span class="sxs-lookup"><span data-stu-id="ae713-122">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="ae713-123">序列化的 JSON 輸出 `WeatherForecastWithPreviousAsObject` **包含** `WindSpeed` 。</span><span class="sxs-lookup"><span data-stu-id="ae713-123">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="ae713-124">若要序列化 `WeatherForecastWithPreviousAsObject` ，不需要呼叫 `Serialize<object>` 或， `GetType` 因為根物件不是可能是衍生類型的物件。</span><span class="sxs-lookup"><span data-stu-id="ae713-124">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="ae713-125">下列程式碼範例不會呼叫 `Serialize<object>` 或 `GetType` ：</span><span class="sxs-lookup"><span data-stu-id="ae713-125">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeSecondLevel":::

<span data-ttu-id="ae713-126">上述程式碼會正確地序列化 `WeatherForecastWithPreviousAsObject` ：</span><span class="sxs-lookup"><span data-stu-id="ae713-126">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="ae713-127">將屬性定義為 `object` 與介面搭配使用的相同方法。</span><span class="sxs-lookup"><span data-stu-id="ae713-127">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="ae713-128">假設您有下列介面和執行，而且您想要使用包含實實例的屬性來序列化類別：</span><span class="sxs-lookup"><span data-stu-id="ae713-128">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/IForecast.cs":::

<span data-ttu-id="ae713-129">當您序列化的實例時 `Forecasts` ，只 `Tuesday` 會顯示 `WindSpeed` 屬性，因為 `Tuesday` 定義為 `object` ：</span><span class="sxs-lookup"><span data-stu-id="ae713-129">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs" id="SerializeInterface":::

<span data-ttu-id="ae713-130">下列範例顯示上述程式碼所產生的 JSON：</span><span class="sxs-lookup"><span data-stu-id="ae713-130">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="ae713-131">如需多型序列化的詳細資訊，以及有關還原 **序列化** 的詳細 **資訊，請** 參閱 [如何從遷移 Newtonsoft.Json System.Text.Json 至](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization)。</span><span class="sxs-lookup"><span data-stu-id="ae713-131">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae713-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae713-132">See also</span></span>

* [<span data-ttu-id="ae713-133">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="ae713-133">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="ae713-134">具現化 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="ae713-134">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="ae713-135">啟用不區分大小寫的比對</span><span class="sxs-lookup"><span data-stu-id="ae713-135">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="ae713-136">自訂屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="ae713-136">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="ae713-137">略過屬性</span><span class="sxs-lookup"><span data-stu-id="ae713-137">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="ae713-138">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="ae713-138">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="ae713-139">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="ae713-139">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="ae713-140">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="ae713-140">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="ae713-141">不可變類型和非公用存取子</span><span class="sxs-lookup"><span data-stu-id="ae713-141">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* <span data-ttu-id="ae713-142">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="ae713-142">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
