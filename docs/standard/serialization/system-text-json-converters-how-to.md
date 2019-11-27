---
title: 如何撰寫 JSON 序列化的自訂轉換器-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 33d1cd7764e71d9e2fa382c9f3c5feb77e8defb4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283353"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="23c23-102">如何在 .NET 中撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="23c23-103">本文說明如何為 <xref:System.Text.Json> 命名空間中提供的 JSON 序列化類別建立自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="23c23-104">如需 `System.Text.Json`的簡介，請參閱[如何在 .net 中序列化和還原序列化 JSON](system-text-json-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="23c23-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="23c23-105">*轉換器*是一個類別，可將物件或值轉換成 JSON。</span><span class="sxs-lookup"><span data-stu-id="23c23-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="23c23-106">針對對應至 JavaScript 基本類型的大部分基本型別，`System.Text.Json` 命名空間具有內建的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="23c23-107">您可以撰寫自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-107">You can write custom converters:</span></span>

* <span data-ttu-id="23c23-108">覆寫內建轉換器的預設行為。</span><span class="sxs-lookup"><span data-stu-id="23c23-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="23c23-109">例如，您可能想要以 mm/dd/yyyy 格式來表示 `DateTime` 值，而不是預設的 ISO 8601-1:2019 格式。</span><span class="sxs-lookup"><span data-stu-id="23c23-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="23c23-110">支援自訂實值型別。</span><span class="sxs-lookup"><span data-stu-id="23c23-110">To support a custom value type.</span></span> <span data-ttu-id="23c23-111">例如，`PhoneNumber` 結構。</span><span class="sxs-lookup"><span data-stu-id="23c23-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="23c23-112">您也可以撰寫自訂轉換器，使用目前版本中未包含的功能來擴充 `System.Text.Json`。</span><span class="sxs-lookup"><span data-stu-id="23c23-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="23c23-113">本文稍後會涵蓋下列案例：</span><span class="sxs-lookup"><span data-stu-id="23c23-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="23c23-114">[將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="23c23-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="23c23-115">[支援具有非字串索引鍵的字典](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="23c23-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="23c23-116">[支援](#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="23c23-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="23c23-117">自訂轉換器模式</span><span class="sxs-lookup"><span data-stu-id="23c23-117">Custom converter patterns</span></span>

<span data-ttu-id="23c23-118">建立自訂轉換器的模式有兩種：基本模式和 factory 模式。</span><span class="sxs-lookup"><span data-stu-id="23c23-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="23c23-119">Factory 模式適用于處理類型 `Enum` 或開放式泛型的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="23c23-120">基本模式適用于非泛型和封閉式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="23c23-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="23c23-121">例如，下列類型的轉換器需要 factory 模式：</span><span class="sxs-lookup"><span data-stu-id="23c23-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="23c23-122">基本模式可以處理的一些類型範例包括：</span><span class="sxs-lookup"><span data-stu-id="23c23-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="23c23-123">基本模式會建立可處理一種類型的類別。</span><span class="sxs-lookup"><span data-stu-id="23c23-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="23c23-124">Factory 模式會建立一個類別，它會在執行時間決定需要哪一個特定型別，並以動態方式建立適當的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="23c23-125">範例基本轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-125">Sample basic converter</span></span>

<span data-ttu-id="23c23-126">下列範例是覆寫現有資料類型之預設序列化的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="23c23-127">轉換器會針對 `DateTimeOffset` 屬性使用 mm/dd/yyyy 格式。</span><span class="sxs-lookup"><span data-stu-id="23c23-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="23c23-128">範例 factory 模式切換器</span><span class="sxs-lookup"><span data-stu-id="23c23-128">Sample factory pattern converter</span></span>

<span data-ttu-id="23c23-129">下列程式碼顯示可搭配 `Dictionary<Enum,TValue>`使用的自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="23c23-130">程式碼會遵循 factory 模式，因為第一個泛型型別參數是 `Enum`，而第二個是開啟的。</span><span class="sxs-lookup"><span data-stu-id="23c23-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="23c23-131">`CanConvert` 方法只會針對具有兩個泛型參數的 `Dictionary` 傳回 `true`，其中第一個是 `Enum` 型別。</span><span class="sxs-lookup"><span data-stu-id="23c23-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="23c23-132">內部轉換器會取得現有的轉換器，以處理在執行時間針對 `TValue`所提供的任何類型。</span><span class="sxs-lookup"><span data-stu-id="23c23-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="23c23-133">上述程式碼與本文稍後的「[包含非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)」中所顯示的相同。</span><span class="sxs-lookup"><span data-stu-id="23c23-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="23c23-134">遵循基本模式的步驟</span><span class="sxs-lookup"><span data-stu-id="23c23-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="23c23-135">下列步驟說明如何遵循基本模式來建立轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="23c23-136">建立衍生自 <xref:System.Text.Json.Serialization.JsonConverter%601> 的類別，其中 `T` 是要序列化和還原序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="23c23-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="23c23-137">覆寫 `Read` 方法，將內送 JSON 還原序列化，並將它轉換成類型 `T`。</span><span class="sxs-lookup"><span data-stu-id="23c23-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="23c23-138">使用傳遞至方法的 <xref:System.Text.Json.Utf8JsonReader> 來讀取 JSON。</span><span class="sxs-lookup"><span data-stu-id="23c23-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="23c23-139">覆寫 `Write` 方法，將 `T`類型的傳入物件序列化。</span><span class="sxs-lookup"><span data-stu-id="23c23-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="23c23-140">使用傳遞至方法的 <xref:System.Text.Json.Utf8JsonWriter> 來寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="23c23-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="23c23-141">只有在必要時，才覆寫 `CanConvert` 方法。</span><span class="sxs-lookup"><span data-stu-id="23c23-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="23c23-142">當要轉換的型別是 `T`型別時，預設的實值會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="23c23-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="23c23-143">因此，只支援類型 `T` 的轉換器不需要覆寫此方法。</span><span class="sxs-lookup"><span data-stu-id="23c23-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="23c23-144">如需需要覆寫此方法之轉換器的範例，請參閱本文稍後[的多](#support-polymorphic-deserialization)型還原序列化一節。</span><span class="sxs-lookup"><span data-stu-id="23c23-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="23c23-145">您可以參考[內建的轉換器原始程式碼](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)做為參考執行，以撰寫自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="23c23-146">遵循 factory 模式的步驟</span><span class="sxs-lookup"><span data-stu-id="23c23-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="23c23-147">下列步驟說明如何遵循 factory 模式來建立轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="23c23-148">建立衍生自 <xref:System.Text.Json.Serialization.JsonConverterFactory> 的類別。</span><span class="sxs-lookup"><span data-stu-id="23c23-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="23c23-149">當要轉換的型別是轉換器可以處理的類型時，覆寫 `CanConvert` 方法，使其傳回 true。</span><span class="sxs-lookup"><span data-stu-id="23c23-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="23c23-150">例如，如果轉換器適用于 `List<T>` 它可能只會處理 `List<int>`、`List<string>`和 `List<DateTime>`。</span><span class="sxs-lookup"><span data-stu-id="23c23-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="23c23-151">覆寫 `CreateConverter` 方法，以傳回將處理在執行時間所提供之類型轉換的轉換器類別實例。</span><span class="sxs-lookup"><span data-stu-id="23c23-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="23c23-152">建立 `CreateConverter` 方法具現化的轉換器類別。</span><span class="sxs-lookup"><span data-stu-id="23c23-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="23c23-153">開放式泛型需要 factory 模式，因為所有類型的物件來回轉換的程式碼都不相同。</span><span class="sxs-lookup"><span data-stu-id="23c23-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="23c23-154">舉例來說，開放式泛型型別的轉換器（例如`List<T>`）必須針對封閉式泛型型別（例如，`List<DateTime>`）建立轉換子，以供幕後使用。</span><span class="sxs-lookup"><span data-stu-id="23c23-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="23c23-155">必須撰寫程式碼，以處理轉換器可以處理的每個封閉式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="23c23-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="23c23-156">`Enum` 類型類似于開放式泛型型別： `Enum` 的轉換器必須針對特定 `Enum` （例如，`WeekdaysEnum`）建立轉換器，以供幕後使用。</span><span class="sxs-lookup"><span data-stu-id="23c23-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="23c23-157">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="23c23-157">Error handling</span></span>

<span data-ttu-id="23c23-158">如果您需要在錯誤處理常式代碼中擲回例外狀況，請考慮在沒有訊息的情況下擲回 <xref:System.Text.Json.JsonException>。</span><span class="sxs-lookup"><span data-stu-id="23c23-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="23c23-159">此例外狀況類型會自動建立訊息，其中包含造成錯誤之 JSON 部分的路徑。</span><span class="sxs-lookup"><span data-stu-id="23c23-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="23c23-160">例如，語句 `throw new JsonException();` 會產生類似下列範例的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="23c23-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="23c23-161">如果您提供訊息（例如 `throw new JsonException("Error occurred")`，例外狀況仍然會在 <xref:System.Text.Json.JsonException.Path> 屬性中提供路徑。</span><span class="sxs-lookup"><span data-stu-id="23c23-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="23c23-162">註冊自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-162">Register a custom converter</span></span>

<span data-ttu-id="23c23-163">*註冊*自訂轉換器，讓 `Serialize` 和 `Deserialize` 方法使用它。</span><span class="sxs-lookup"><span data-stu-id="23c23-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="23c23-164">選擇下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="23c23-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="23c23-165">將轉換器類別的實例加入至 <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="23c23-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="23c23-166">將[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)屬性套用至需要自訂轉換器的屬性。</span><span class="sxs-lookup"><span data-stu-id="23c23-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="23c23-167">將[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)屬性套用至代表自訂實數值型別的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="23c23-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="23c23-168">註冊範例-轉換器集合</span><span class="sxs-lookup"><span data-stu-id="23c23-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="23c23-169">以下範例會讓 <xref:System.ComponentModel.DateTimeOffsetConverter> <xref:System.DateTimeOffset>類型的屬性的預設值：</span><span class="sxs-lookup"><span data-stu-id="23c23-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="23c23-170">假設您將下列類型的實例序列化：</span><span class="sxs-lookup"><span data-stu-id="23c23-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="23c23-171">以下是顯示使用自訂轉換器的 JSON 輸出範例：</span><span class="sxs-lookup"><span data-stu-id="23c23-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="23c23-172">下列程式碼會使用相同的方法，以使用自訂 `DateTimeOffset` 轉換器進行還原序列化：</span><span class="sxs-lookup"><span data-stu-id="23c23-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="23c23-173">註冊範例-屬性上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="23c23-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="23c23-174">下列程式碼會選取 `Date` 屬性的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="23c23-175">序列化 `WeatherForecastWithConverterAttribute` 的程式碼不需要使用 `JsonSerializeOptions.Converters`：</span><span class="sxs-lookup"><span data-stu-id="23c23-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="23c23-176">要還原序列化的程式碼也不需要使用 `Converters`：</span><span class="sxs-lookup"><span data-stu-id="23c23-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="23c23-177">註冊範例-類型上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="23c23-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="23c23-178">以下程式碼會建立結構，並將 `[JsonConverter]` 屬性套用至它：</span><span class="sxs-lookup"><span data-stu-id="23c23-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="23c23-179">以下是上述結構的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="23c23-180">結構上的 `[JsonConvert]` 屬性會註冊自訂轉換器，做為 `Temperature`類型屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="23c23-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="23c23-181">當您序列化或還原序列化時，轉換器會自動用於下列類型的 `TemperatureCelsius` 屬性：</span><span class="sxs-lookup"><span data-stu-id="23c23-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="23c23-182">轉換器註冊優先順序</span><span class="sxs-lookup"><span data-stu-id="23c23-182">Converter registration precedence</span></span>

<span data-ttu-id="23c23-183">在序列化或還原序列化期間，會依下列順序為每個 JSON 元素選擇一個轉換器，從最高優先順序列到最低：</span><span class="sxs-lookup"><span data-stu-id="23c23-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="23c23-184">套用至屬性的 `[JsonConverter]`。</span><span class="sxs-lookup"><span data-stu-id="23c23-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="23c23-185">已新增至 `Converters` 集合的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="23c23-186">`[JsonConverter]` 套用至自訂實數值型別或 POCO。</span><span class="sxs-lookup"><span data-stu-id="23c23-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="23c23-187">如果類型的多個自訂轉換器已在 `Converters` 集合中註冊，則會使用針對 `CanConvert` 傳回 true 的第一個轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="23c23-188">只有在未註冊適用的自訂轉換器時，才會選擇內建的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="23c23-189">常見案例的轉換子範例</span><span class="sxs-lookup"><span data-stu-id="23c23-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="23c23-190">下列各節提供的轉換器範例可解決一些內建功能無法處理的常見案例。</span><span class="sxs-lookup"><span data-stu-id="23c23-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="23c23-191">將推斷的類型還原序列化為物件屬性</span><span class="sxs-lookup"><span data-stu-id="23c23-191">Deserialize inferred types to Object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="23c23-192">支援具有非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="23c23-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="23c23-193">支援多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="23c23-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="23c23-194">將推斷的類型還原序列化為物件屬性</span><span class="sxs-lookup"><span data-stu-id="23c23-194">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="23c23-195">當還原序列化為 `Object`類型的屬性時，會建立 `JsonElement` 物件。</span><span class="sxs-lookup"><span data-stu-id="23c23-195">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="23c23-196">原因是還原序列化程式不知道要建立什麼 CLR 型別，而且也不會嘗試猜到。</span><span class="sxs-lookup"><span data-stu-id="23c23-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="23c23-197">例如，如果 JSON 屬性具有 "true"，則還原序列化程式並不會推斷值為 `Boolean`，如果元素具有 "01/01/2019"，則還原序列化程式不會推斷它是 `DateTime`。</span><span class="sxs-lookup"><span data-stu-id="23c23-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="23c23-198">型別推斷可能不正確。</span><span class="sxs-lookup"><span data-stu-id="23c23-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="23c23-199">如果還原序列化程式會剖析沒有小數點的 JSON 數位做為 `long`，如果值原本序列化為 `ulong` 或 `BigInteger`，可能會導致超出範圍的問題。</span><span class="sxs-lookup"><span data-stu-id="23c23-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="23c23-200">如果數位原本序列化為 `decimal`，則剖析具有小數點做為 `double` 的數位可能會失去精確度。</span><span class="sxs-lookup"><span data-stu-id="23c23-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="23c23-201">針對需要型別推斷的案例，下列程式碼會顯示 `Object` 屬性的自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-201">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="23c23-202">程式碼會轉換：</span><span class="sxs-lookup"><span data-stu-id="23c23-202">The code converts:</span></span>

* <span data-ttu-id="23c23-203">`true` 和 `false` 至 `Boolean`</span><span class="sxs-lookup"><span data-stu-id="23c23-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="23c23-204">要 `long` 或 `double` 的數位</span><span class="sxs-lookup"><span data-stu-id="23c23-204">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="23c23-205">要 `DateTime` 的日期</span><span class="sxs-lookup"><span data-stu-id="23c23-205">Dates to `DateTime`</span></span>
* <span data-ttu-id="23c23-206">要 `string` 的字串</span><span class="sxs-lookup"><span data-stu-id="23c23-206">Strings to `string`</span></span>
* <span data-ttu-id="23c23-207">`JsonElement` 的其他專案</span><span class="sxs-lookup"><span data-stu-id="23c23-207">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="23c23-208">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-208">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="23c23-209">以下是具有 `Object` 屬性的範例型別：</span><span class="sxs-lookup"><span data-stu-id="23c23-209">Here's an example type with `Object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="23c23-210">下列要還原序列化的 JSON 範例包含將還原序列化為 `DateTime`、`long`和 `string`的值：</span><span class="sxs-lookup"><span data-stu-id="23c23-210">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="23c23-211">如果沒有自訂轉換器，還原序列化會將 `JsonElement` 放入每個屬性中。</span><span class="sxs-lookup"><span data-stu-id="23c23-211">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="23c23-212">`System.Text.Json.Serialization` 命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)，有更多範例可處理還原序列化為物件屬性的自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-212">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="23c23-213">支援具有非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="23c23-213">Support Dictionary with non-string key</span></span>

<span data-ttu-id="23c23-214">字典集合的內建支援適用于 `Dictionary<string, TValue>`。</span><span class="sxs-lookup"><span data-stu-id="23c23-214">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="23c23-215">也就是，索引鍵必須是字串。</span><span class="sxs-lookup"><span data-stu-id="23c23-215">That is, the key must be a string.</span></span> <span data-ttu-id="23c23-216">若要支援具有整數或其他類型做為索引鍵的字典，則需要自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="23c23-216">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="23c23-217">下列程式碼顯示可搭配 `Dictionary<Enum,TValue>`使用的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-217">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="23c23-218">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-218">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="23c23-219">轉換器可以序列化和還原序列化下列類別中使用下列 `Enum`的 `TemperatureRanges` 屬性：</span><span class="sxs-lookup"><span data-stu-id="23c23-219">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="23c23-220">序列化的 JSON 輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="23c23-220">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="23c23-221">`System.Text.Json.Serialization` 命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)，有更多可處理非字串索引鍵字典的自訂轉換器範例。</span><span class="sxs-lookup"><span data-stu-id="23c23-221">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="23c23-222">支援多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="23c23-222">Support polymorphic deserialization</span></span>

<span data-ttu-id="23c23-223">多型[序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)不需要自訂轉換器，但是還原序列化的確需要自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-223">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="23c23-224">例如，假設您有一個 `Person` 的抽象基類，`Employee` 和 `Customer` 衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="23c23-224">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="23c23-225">多型還原序列化表示在設計階段，您可以指定 `Person` 做為還原序列化目標，而且 JSON 中的 `Customer` 和 `Employee` 物件會在執行時間正確地還原序列化。</span><span class="sxs-lookup"><span data-stu-id="23c23-225">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="23c23-226">在還原序列化期間，您必須尋找識別 JSON 中所需類型的線索。</span><span class="sxs-lookup"><span data-stu-id="23c23-226">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="23c23-227">可用的線索種類會因每個案例而異。</span><span class="sxs-lookup"><span data-stu-id="23c23-227">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="23c23-228">例如，鑒別子屬性可能可供使用，或者您可能必須依賴特定屬性的存在與否。</span><span class="sxs-lookup"><span data-stu-id="23c23-228">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="23c23-229">目前的 `System.Text.Json` 版本並未提供屬性來指定如何處理多型還原序列化案例，因此需要自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-229">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="23c23-230">下列程式碼顯示基類、兩個衍生類別和自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="23c23-230">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="23c23-231">轉換器會使用鑒別子屬性來執行多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="23c23-231">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="23c23-232">類型鑒別子不在類別定義中，而是在序列化期間建立，並且會在還原序列化期間讀取。</span><span class="sxs-lookup"><span data-stu-id="23c23-232">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="23c23-233">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="23c23-233">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="23c23-234">轉換器可以還原序列化使用相同的轉換子所建立的 JSON，例如：</span><span class="sxs-lookup"><span data-stu-id="23c23-234">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

## <a name="other-custom-converter-samples"></a><span data-ttu-id="23c23-235">其他自訂轉換器範例</span><span class="sxs-lookup"><span data-stu-id="23c23-235">Other custom converter samples</span></span>

<span data-ttu-id="23c23-236">`System.Text.Json.Serialization` 原始程式碼中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)包含其他自訂轉換器範例，例如：</span><span class="sxs-lookup"><span data-stu-id="23c23-236">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="23c23-237">在還原序列化時，將 null 轉換為0的 `Int32` 轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-237">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="23c23-238">在還原序列化時允許字串和數值的 `Int32` 轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-238">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="23c23-239">`Enum` 轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-239">`Enum` converter</span></span>
* <span data-ttu-id="23c23-240">接受外部資料的 `List<T>` 轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-240">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="23c23-241">可搭配以逗號分隔的數位清單使用的 `Long[]` 轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-241">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="23c23-242">其他資源</span><span class="sxs-lookup"><span data-stu-id="23c23-242">Additional resources</span></span>

* [<span data-ttu-id="23c23-243">System.web. Text. Json 總覽</span><span class="sxs-lookup"><span data-stu-id="23c23-243">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="23c23-244">System.web API 參考</span><span class="sxs-lookup"><span data-stu-id="23c23-244">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="23c23-245">如何使用 System.object</span><span class="sxs-lookup"><span data-stu-id="23c23-245">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="23c23-246">內建轉換器的原始程式碼</span><span class="sxs-lookup"><span data-stu-id="23c23-246">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="23c23-247">`System.Text.Json` 自訂轉換器的相關 GitHub 問題</span><span class="sxs-lookup"><span data-stu-id="23c23-247">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="23c23-248">36639引進自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="23c23-248">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="23c23-249">38713關於還原序列化為物件</span><span class="sxs-lookup"><span data-stu-id="23c23-249">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="23c23-250">40120有關非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="23c23-250">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="23c23-251">37787關於多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="23c23-251">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
