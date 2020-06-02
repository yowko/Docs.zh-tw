---
title: 如何撰寫 JSON 序列化的自訂轉換器-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: abda23ea538c2c0da6ada4f359ce745602dca45d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279759"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="81792-102">如何在 .NET 中撰寫 JSON 序列化（封送處理）的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="81792-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="81792-103">本文說明如何為命名空間中提供的 JSON 序列化類別建立自訂轉換器 <xref:System.Text.Json> 。</span><span class="sxs-lookup"><span data-stu-id="81792-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="81792-104">如需的簡介 `System.Text.Json` ，請參閱[如何在 .net 中序列化和還原序列化 JSON](system-text-json-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="81792-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="81792-105">*轉換器*是一個類別，可將物件或值轉換成 JSON。</span><span class="sxs-lookup"><span data-stu-id="81792-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="81792-106">`System.Text.Json`命名空間針對對應至 JavaScript 基本類型的大部分基本型別，具有內建的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="81792-107">您可以撰寫自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="81792-107">You can write custom converters:</span></span>

* <span data-ttu-id="81792-108">覆寫內建轉換器的預設行為。</span><span class="sxs-lookup"><span data-stu-id="81792-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="81792-109">例如，您可能想要 `DateTime` 以 mm/dd/yyyy 格式來表示值，而不是預設的 ISO 8601-1:2019 格式。</span><span class="sxs-lookup"><span data-stu-id="81792-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="81792-110">支援自訂實值型別。</span><span class="sxs-lookup"><span data-stu-id="81792-110">To support a custom value type.</span></span> <span data-ttu-id="81792-111">例如， `PhoneNumber` 結構。</span><span class="sxs-lookup"><span data-stu-id="81792-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="81792-112">您也可以撰寫自訂轉換器，以自訂或擴充 `System.Text.Json` 目前版本中未包含的功能。</span><span class="sxs-lookup"><span data-stu-id="81792-112">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="81792-113">本文稍後會涵蓋下列案例：</span><span class="sxs-lookup"><span data-stu-id="81792-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="81792-114">[將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="81792-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="81792-115">[支援具有非字串索引鍵的字典](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="81792-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="81792-116">[支援](#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="81792-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="81792-117">[支援堆疊 \<T> 的往返](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="81792-117">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="81792-118">自訂轉換器模式</span><span class="sxs-lookup"><span data-stu-id="81792-118">Custom converter patterns</span></span>

<span data-ttu-id="81792-119">建立自訂轉換器的模式有兩種：基本模式和 factory 模式。</span><span class="sxs-lookup"><span data-stu-id="81792-119">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="81792-120">Factory 模式適用于處理類型 `Enum` 或開放式泛型的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-120">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="81792-121">基本模式適用于非泛型和封閉式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="81792-121">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="81792-122">例如，下列類型的轉換器需要 factory 模式：</span><span class="sxs-lookup"><span data-stu-id="81792-122">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="81792-123">基本模式可以處理的一些類型範例包括：</span><span class="sxs-lookup"><span data-stu-id="81792-123">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="81792-124">基本模式會建立可處理一種類型的類別。</span><span class="sxs-lookup"><span data-stu-id="81792-124">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="81792-125">Factory 模式會建立一個類別，它會在執行時間決定所需的特定型別，並以動態方式建立適當的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-125">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="81792-126">範例基本轉換器</span><span class="sxs-lookup"><span data-stu-id="81792-126">Sample basic converter</span></span>

<span data-ttu-id="81792-127">下列範例是覆寫現有資料類型之預設序列化的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-127">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="81792-128">轉換器會針對屬性使用 mm/dd/yyyy 格式 `DateTimeOffset` 。</span><span class="sxs-lookup"><span data-stu-id="81792-128">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="81792-129">範例 factory 模式切換器</span><span class="sxs-lookup"><span data-stu-id="81792-129">Sample factory pattern converter</span></span>

<span data-ttu-id="81792-130">下列程式碼顯示可搭配使用的自訂轉換器 `Dictionary<Enum,TValue>` 。</span><span class="sxs-lookup"><span data-stu-id="81792-130">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="81792-131">程式碼會遵循 factory 模式，因為第一個泛型型別參數是 `Enum` ，而第二個是開啟的。</span><span class="sxs-lookup"><span data-stu-id="81792-131">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="81792-132">`CanConvert`方法 `true` 只 `Dictionary` 會針對具有兩個泛型參數的進行傳回，其中第一個是 `Enum` 型別。</span><span class="sxs-lookup"><span data-stu-id="81792-132">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="81792-133">內部轉換器會取得現有的轉換器，以處理在執行時間提供的任何類型 `TValue` 。</span><span class="sxs-lookup"><span data-stu-id="81792-133">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="81792-134">上述程式碼與本文稍後的「[包含非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)」中所顯示的相同。</span><span class="sxs-lookup"><span data-stu-id="81792-134">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="81792-135">遵循基本模式的步驟</span><span class="sxs-lookup"><span data-stu-id="81792-135">Steps to follow the basic pattern</span></span>

<span data-ttu-id="81792-136">下列步驟說明如何遵循基本模式來建立轉換器：</span><span class="sxs-lookup"><span data-stu-id="81792-136">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="81792-137">建立衍生自的類別， <xref:System.Text.Json.Serialization.JsonConverter%601> 其中 `T` 是要序列化和還原序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="81792-137">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="81792-138">覆寫 `Read` 方法以還原序列化傳入 JSON，並將其轉換成類型 `T` 。</span><span class="sxs-lookup"><span data-stu-id="81792-138">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="81792-139">使用 <xref:System.Text.Json.Utf8JsonReader> 傳遞至方法的來讀取 JSON。</span><span class="sxs-lookup"><span data-stu-id="81792-139">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="81792-140">覆寫 `Write` 方法以序列化類型的傳入物件 `T` 。</span><span class="sxs-lookup"><span data-stu-id="81792-140">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="81792-141">使用 <xref:System.Text.Json.Utf8JsonWriter> 傳遞至方法的來寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="81792-141">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="81792-142">`CanConvert`只有在必要時，才覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="81792-142">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="81792-143">`true`當要轉換的類型為類型時，預設的實值會傳回 `T` 。</span><span class="sxs-lookup"><span data-stu-id="81792-143">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="81792-144">因此，只支援類型的轉換器 `T` 不需要覆寫此方法。</span><span class="sxs-lookup"><span data-stu-id="81792-144">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="81792-145">如需需要覆寫此方法之轉換器的範例，請參閱本文稍後[的多](#support-polymorphic-deserialization)型還原序列化一節。</span><span class="sxs-lookup"><span data-stu-id="81792-145">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="81792-146">您可以參考[內建的轉換器原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/)做為參考執行，以撰寫自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-146">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="81792-147">遵循 factory 模式的步驟</span><span class="sxs-lookup"><span data-stu-id="81792-147">Steps to follow the factory pattern</span></span>

<span data-ttu-id="81792-148">下列步驟說明如何遵循 factory 模式來建立轉換器：</span><span class="sxs-lookup"><span data-stu-id="81792-148">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="81792-149">建立衍生自 <xref:System.Text.Json.Serialization.JsonConverterFactory> 的類別。</span><span class="sxs-lookup"><span data-stu-id="81792-149">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="81792-150">`CanConvert`當要轉換的型別是轉換器可以處理的類型時，覆寫方法以傳回 true。</span><span class="sxs-lookup"><span data-stu-id="81792-150">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="81792-151">例如，如果轉換器適用于 `List<T>` 它，則可能只會處理 `List<int>` 、 `List<string>` 和 `List<DateTime>` 。</span><span class="sxs-lookup"><span data-stu-id="81792-151">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="81792-152">覆寫 `CreateConverter` 方法，以傳回轉換器類別的實例，這個實例將會處理在執行時間所提供的類型轉換。</span><span class="sxs-lookup"><span data-stu-id="81792-152">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="81792-153">建立方法具現化的轉換器類別 `CreateConverter` 。</span><span class="sxs-lookup"><span data-stu-id="81792-153">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="81792-154">開放式泛型需要 factory 模式，因為所有類型的物件來回轉換的程式碼都不相同。</span><span class="sxs-lookup"><span data-stu-id="81792-154">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="81792-155">開放式泛型型別的轉換器（例如 `List<T>` ）必須在幕後建立封閉式泛型型別的轉換器（例如 `List<DateTime>` ）。</span><span class="sxs-lookup"><span data-stu-id="81792-155">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="81792-156">必須撰寫程式碼，以處理轉換器可以處理的每個封閉式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="81792-156">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="81792-157">型別與 `Enum` 開放式泛型型別類似：的轉換器 `Enum` 必須針對幕後的特定（例如）建立轉換器 `Enum` `WeekdaysEnum` 。</span><span class="sxs-lookup"><span data-stu-id="81792-157">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="81792-158">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="81792-158">Error handling</span></span>

<span data-ttu-id="81792-159">如果您需要在錯誤處理常式代碼中擲回例外狀況，請考慮在沒有訊息的情況下擲回 <xref:System.Text.Json.JsonException> 。</span><span class="sxs-lookup"><span data-stu-id="81792-159">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="81792-160">此例外狀況類型會自動建立訊息，其中包含造成錯誤之 JSON 部分的路徑。</span><span class="sxs-lookup"><span data-stu-id="81792-160">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="81792-161">例如，語句會 `throw new JsonException();` 產生類似下列範例的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="81792-161">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="81792-162">如果您提供訊息（例如， `throw new JsonException("Error occurred")` 例外狀況仍會在屬性中提供路徑 <xref:System.Text.Json.JsonException.Path> 。</span><span class="sxs-lookup"><span data-stu-id="81792-162">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="81792-163">註冊自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="81792-163">Register a custom converter</span></span>

<span data-ttu-id="81792-164">*註冊*自訂轉換器，讓 `Serialize` 和 `Deserialize` 方法使用它。</span><span class="sxs-lookup"><span data-stu-id="81792-164">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="81792-165">選擇下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="81792-165">Choose one of the following approaches:</span></span>

* <span data-ttu-id="81792-166">將轉換器類別的實例加入至 <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="81792-166">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="81792-167">將[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)屬性套用至需要自訂轉換器的屬性。</span><span class="sxs-lookup"><span data-stu-id="81792-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="81792-168">將[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)屬性套用至代表自訂實數值型別的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="81792-168">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="81792-169">註冊範例-轉換器集合</span><span class="sxs-lookup"><span data-stu-id="81792-169">Registration sample - Converters collection</span></span>

<span data-ttu-id="81792-170">以下範例會建立 <xref:System.ComponentModel.DateTimeOffsetConverter> 類型屬性的預設值 <xref:System.DateTimeOffset> ：</span><span class="sxs-lookup"><span data-stu-id="81792-170">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="81792-171">假設您將下列類型的實例序列化：</span><span class="sxs-lookup"><span data-stu-id="81792-171">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="81792-172">以下是顯示使用自訂轉換器的 JSON 輸出範例：</span><span class="sxs-lookup"><span data-stu-id="81792-172">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="81792-173">下列程式碼會使用相同的方法，以使用自訂轉換器進行還原序列化 `DateTimeOffset` ：</span><span class="sxs-lookup"><span data-stu-id="81792-173">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="81792-174">註冊範例-屬性上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="81792-174">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="81792-175">下列程式碼會選取屬性的自訂轉換器 `Date` ：</span><span class="sxs-lookup"><span data-stu-id="81792-175">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="81792-176">要序列化的程式碼 `WeatherForecastWithConverterAttribute` 不需要使用 `JsonSerializeOptions.Converters` ：</span><span class="sxs-lookup"><span data-stu-id="81792-176">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="81792-177">要還原序列化的程式碼也不需要使用 `Converters` ：</span><span class="sxs-lookup"><span data-stu-id="81792-177">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="81792-178">註冊範例-類型上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="81792-178">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="81792-179">以下程式碼會建立結構，並將 `[JsonConverter]` 屬性套用至它：</span><span class="sxs-lookup"><span data-stu-id="81792-179">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

<span data-ttu-id="81792-180">以下是上述結構的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="81792-180">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

<span data-ttu-id="81792-181">`[JsonConvert]`結構上的屬性會將自訂轉換器註冊為類型屬性的預設值 `Temperature` 。</span><span class="sxs-lookup"><span data-stu-id="81792-181">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="81792-182">`TemperatureCelsius`當您序列化或還原序列化時，轉換器會自動用於下列類型的屬性：</span><span class="sxs-lookup"><span data-stu-id="81792-182">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="81792-183">轉換器註冊優先順序</span><span class="sxs-lookup"><span data-stu-id="81792-183">Converter registration precedence</span></span>

<span data-ttu-id="81792-184">在序列化或還原序列化期間，會依下列順序為每個 JSON 元素選擇一個轉換器，從最高優先順序列到最低：</span><span class="sxs-lookup"><span data-stu-id="81792-184">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="81792-185">`[JsonConverter]`套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="81792-185">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="81792-186">已新增至集合的轉換器 `Converters` 。</span><span class="sxs-lookup"><span data-stu-id="81792-186">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="81792-187">`[JsonConverter]`適用于自訂實數值型別或 POCO。</span><span class="sxs-lookup"><span data-stu-id="81792-187">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="81792-188">如果在集合中註冊類型的多個自訂轉換器 `Converters` ，則會使用傳回 true 的第一個轉換子 `CanConvert` 。</span><span class="sxs-lookup"><span data-stu-id="81792-188">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="81792-189">只有在未註冊適用的自訂轉換器時，才會選擇內建的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-189">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="81792-190">常見案例的轉換子範例</span><span class="sxs-lookup"><span data-stu-id="81792-190">Converter samples for common scenarios</span></span>

<span data-ttu-id="81792-191">下列各節提供的轉換器範例可解決一些內建功能無法處理的常見案例。</span><span class="sxs-lookup"><span data-stu-id="81792-191">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="81792-192">將推斷的類型還原序列化為物件屬性</span><span class="sxs-lookup"><span data-stu-id="81792-192">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="81792-193">支援具有非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="81792-193">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="81792-194">支援多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="81792-194">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)
* <span data-ttu-id="81792-195">[支援堆疊 \<T> 的往返](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="81792-195">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="81792-196">將推斷的類型還原序列化為物件屬性</span><span class="sxs-lookup"><span data-stu-id="81792-196">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="81792-197">當還原序列化為類型的屬性時 `object` ， `JsonElement` 會建立物件。</span><span class="sxs-lookup"><span data-stu-id="81792-197">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="81792-198">原因是還原序列化程式不知道要建立什麼 CLR 型別，而且也不會嘗試猜到。</span><span class="sxs-lookup"><span data-stu-id="81792-198">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="81792-199">例如，如果 JSON 屬性具有 "true"，則還原序列化程式並不會推斷值為 `Boolean` ，而且如果元素具有 "01/01/2019"，則還原序列化程式不會推斷它是 `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="81792-199">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="81792-200">型別推斷可能不正確。</span><span class="sxs-lookup"><span data-stu-id="81792-200">Type inference can be inaccurate.</span></span> <span data-ttu-id="81792-201">如果還原序列化程式剖析沒有小數點的 JSON 數位做為 `long` ，如果值原本序列化為或，可能會導致超出範圍的問題 `ulong` `BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="81792-201">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="81792-202">如果數位原本序列化為，則將具有小數點的數位剖析 `double` 可能會失去精確度 `decimal` 。</span><span class="sxs-lookup"><span data-stu-id="81792-202">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="81792-203">針對需要型別推斷的案例，下列程式碼會顯示內容的自訂轉換器 `object` 。</span><span class="sxs-lookup"><span data-stu-id="81792-203">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="81792-204">程式碼會轉換：</span><span class="sxs-lookup"><span data-stu-id="81792-204">The code converts:</span></span>

* <span data-ttu-id="81792-205">`true`和 `false``Boolean`</span><span class="sxs-lookup"><span data-stu-id="81792-205">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="81792-206">不含小數的數位`long`</span><span class="sxs-lookup"><span data-stu-id="81792-206">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="81792-207">小數到的數位`double`</span><span class="sxs-lookup"><span data-stu-id="81792-207">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="81792-208">日期到`DateTime`</span><span class="sxs-lookup"><span data-stu-id="81792-208">Dates to `DateTime`</span></span>
* <span data-ttu-id="81792-209">字串至`string`</span><span class="sxs-lookup"><span data-stu-id="81792-209">Strings to `string`</span></span>
* <span data-ttu-id="81792-210">其他專案`JsonElement`</span><span class="sxs-lookup"><span data-stu-id="81792-210">Everything else to `JsonElement`</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="81792-211">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="81792-211">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="81792-212">以下是包含屬性的範例型別 `object` ：</span><span class="sxs-lookup"><span data-stu-id="81792-212">Here's an example type with `object` properties:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="81792-213">下列要還原序列化的 JSON 範例包含將還原序列化為 `DateTime` 、和的值 `long` `string` ：</span><span class="sxs-lookup"><span data-stu-id="81792-213">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="81792-214">如果沒有自訂轉換器，還原序列化會將放入 `JsonElement` 每個屬性中。</span><span class="sxs-lookup"><span data-stu-id="81792-214">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="81792-215">命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)， `System.Text.Json.Serialization` 有更多範例可處理還原序列化為屬性的自訂轉換器 `object` 。</span><span class="sxs-lookup"><span data-stu-id="81792-215">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="81792-216">支援具有非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="81792-216">Support Dictionary with non-string key</span></span>

<span data-ttu-id="81792-217">字典集合的內建支援適用于 `Dictionary<string, TValue>` 。</span><span class="sxs-lookup"><span data-stu-id="81792-217">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="81792-218">也就是，索引鍵必須是字串。</span><span class="sxs-lookup"><span data-stu-id="81792-218">That is, the key must be a string.</span></span> <span data-ttu-id="81792-219">若要支援具有整數或其他類型做為索引鍵的字典，則需要自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="81792-219">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="81792-220">下列程式碼顯示可搭配使用的自訂轉換器 `Dictionary<Enum,TValue>` ：</span><span class="sxs-lookup"><span data-stu-id="81792-220">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="81792-221">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="81792-221">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="81792-222">轉換器可以序列化和還原序列化 `TemperatureRanges` 下列類別的屬性，其使用下列各項 `Enum` ：</span><span class="sxs-lookup"><span data-stu-id="81792-222">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="81792-223">序列化的 JSON 輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="81792-223">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="81792-224">命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)， `System.Text.Json.Serialization` 有更多範例可處理非字串索引鍵字典的自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-224">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="81792-225">支援多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="81792-225">Support polymorphic deserialization</span></span>

<span data-ttu-id="81792-226">內建功能提供有限範圍的多型[序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)，但完全不支援還原序列化。</span><span class="sxs-lookup"><span data-stu-id="81792-226">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="81792-227">還原序列化需要自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-227">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="81792-228">例如，假設您有一個 `Person` 具有 `Employee` 和衍生類別的抽象基類 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="81792-228">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="81792-229">多型還原序列化表示在設計階段，您可以指定 `Person` 做為還原序列化目標，並在 `Customer` `Employee` 執行時間正確地還原序列化 JSON 中的和物件。</span><span class="sxs-lookup"><span data-stu-id="81792-229">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="81792-230">在還原序列化期間，您必須尋找識別 JSON 中所需類型的線索。</span><span class="sxs-lookup"><span data-stu-id="81792-230">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="81792-231">可用的線索種類會因每個案例而異。</span><span class="sxs-lookup"><span data-stu-id="81792-231">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="81792-232">例如，鑒別子屬性可能可供使用，或者您可能必須依賴特定屬性的存在與否。</span><span class="sxs-lookup"><span data-stu-id="81792-232">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="81792-233">目前的版本 `System.Text.Json` 並未提供屬性來指定如何處理多型還原序列化案例，因此需要自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-233">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="81792-234">下列程式碼顯示基類、兩個衍生類別和自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-234">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="81792-235">轉換器會使用鑒別子屬性來執行多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="81792-235">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="81792-236">類型鑒別子不在類別定義中，而是在序列化期間建立，並且會在還原序列化期間讀取。</span><span class="sxs-lookup"><span data-stu-id="81792-236">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="81792-237">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="81792-237">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="81792-238">轉換器可以還原序列化使用相同的轉換子所建立的 JSON，例如：</span><span class="sxs-lookup"><span data-stu-id="81792-238">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="81792-239">前述範例中的轉換器程式碼會以手動方式讀取和寫入每個屬性。</span><span class="sxs-lookup"><span data-stu-id="81792-239">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="81792-240">另一種方法是呼叫 `Deserialize` 或 `Serialize` 來執行一些工作。</span><span class="sxs-lookup"><span data-stu-id="81792-240">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="81792-241">如需範例，請參閱[這 StackOverflow 文章](https://stackoverflow.com/a/59744873/12509023)。</span><span class="sxs-lookup"><span data-stu-id="81792-241">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="81792-242">堆疊的支援來回行程\<T></span><span class="sxs-lookup"><span data-stu-id="81792-242">Support round-trip for Stack\<T></span></span>

<span data-ttu-id="81792-243">如果您將 JSON 字串還原序列化為 <xref:System.Collections.Generic.Stack%601> 物件，然後將該物件序列化，堆疊的內容會以反向順序排列。</span><span class="sxs-lookup"><span data-stu-id="81792-243">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="81792-244">這個行為適用于下列類型和介面，以及從它們衍生的使用者定義型別：</span><span class="sxs-lookup"><span data-stu-id="81792-244">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="81792-245">為了支援在堆疊中保留原始順序的序列化和還原序列化，需要自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="81792-245">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="81792-246">下列程式碼顯示的自訂轉換器可讓您來回往返 `Stack<T>` 物件：</span><span class="sxs-lookup"><span data-stu-id="81792-246">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

<span data-ttu-id="81792-247">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="81792-247">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="other-custom-converter-samples"></a><span data-ttu-id="81792-248">其他自訂轉換器範例</span><span class="sxs-lookup"><span data-stu-id="81792-248">Other custom converter samples</span></span>

<span data-ttu-id="81792-249">[[從遷移 Newtonsoft.Json 至 System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md) ] 文章包含自訂轉換器的其他範例。</span><span class="sxs-lookup"><span data-stu-id="81792-249">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="81792-250">原始程式碼中的 [[單元測試] 資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) `System.Text.Json.Serialization` 包含其他自訂轉換器範例，例如：</span><span class="sxs-lookup"><span data-stu-id="81792-250">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="81792-251">[在還原序列化時，將 null 轉換為0的 Int32 轉換子](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="81792-251">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="81792-252">[Int32 轉換器，可在還原序列化時同時允許字串和數位值](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="81792-252">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="81792-253">[列舉轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="81792-253">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="81792-254">[列出 \<T> 接受外部資料的轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="81792-254">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="81792-255">[Long [] 轉換器，適用于以逗號分隔的數位清單](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="81792-255">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="81792-256">如果您需要建立可修改現有內建轉換器行為的轉換器，您可以取得[現有轉換器的原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)，做為自訂的起點。</span><span class="sxs-lookup"><span data-stu-id="81792-256">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="81792-257">其他資源</span><span class="sxs-lookup"><span data-stu-id="81792-257">Additional resources</span></span>

* <span data-ttu-id="81792-258">[內建轉換器的原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="81792-258">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* <span data-ttu-id="81792-259">[中的 DateTime 和 DateTimeOffset 支援System.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="81792-259">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="81792-260">[System.Text.Json簡要](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="81792-260">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* <span data-ttu-id="81792-261">[如何使用System.Text.Json](system-text-json-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="81792-261">[How to use System.Text.Json](system-text-json-how-to.md)</span></span>
* <span data-ttu-id="81792-262">[如何從進行遷移Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="81792-262">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="81792-263">[System.Text.JsonAPI 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="81792-263">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="81792-264">[System.Text.Json.序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="81792-264">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
