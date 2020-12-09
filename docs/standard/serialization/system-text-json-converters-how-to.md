---
title: 如何撰寫 JSON 序列化的自訂轉換器-.NET
description: 瞭解如何針對命名空間中提供的 JSON 序列化類別，建立自訂的轉換器 System.Text.Json 。
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
- converters
ms.openlocfilehash: 008455a77f98cd9975b04001121217866cc2ba6e
ms.sourcegitcommit: 0014aa4d5cb2da56a70e03fc68f663d64df5247a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96918602"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="67da0-103">如何在 .NET 中撰寫 JSON 序列化的自訂轉換器 (封送處理) </span><span class="sxs-lookup"><span data-stu-id="67da0-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="67da0-104">本文說明如何為命名空間中提供的 JSON 序列化類別，建立自訂的轉換器 <xref:System.Text.Json> 。</span><span class="sxs-lookup"><span data-stu-id="67da0-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="67da0-105">如需的簡介 `System.Text.Json` ，請參閱 [如何在 .net 中序列化和還原序列化 JSON](system-text-json-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="67da0-105">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="67da0-106">*轉換器* 是一種類別，可將物件或值轉換為 JSON。</span><span class="sxs-lookup"><span data-stu-id="67da0-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="67da0-107">`System.Text.Json`命名空間具有適用于大部分對應至 JavaScript 基本類型之基本類型的內建轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-107">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="67da0-108">您可以撰寫自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="67da0-108">You can write custom converters:</span></span>

* <span data-ttu-id="67da0-109">覆寫內建轉換器的預設行為。</span><span class="sxs-lookup"><span data-stu-id="67da0-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="67da0-110">例如，您可能想要 `DateTime` 以 mm/dd/yyyy 格式表示值，而不是預設的 ISO 8601-1:2019 格式。</span><span class="sxs-lookup"><span data-stu-id="67da0-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="67da0-111">支援自訂實值型別。</span><span class="sxs-lookup"><span data-stu-id="67da0-111">To support a custom value type.</span></span> <span data-ttu-id="67da0-112">例如， `PhoneNumber` 結構。</span><span class="sxs-lookup"><span data-stu-id="67da0-112">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="67da0-113">您也可以撰寫自訂轉換器，以自訂或擴充 `System.Text.Json` 未包含在目前版本中的功能。</span><span class="sxs-lookup"><span data-stu-id="67da0-113">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="67da0-114">本文稍後將討論下列案例：</span><span class="sxs-lookup"><span data-stu-id="67da0-114">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="67da0-115">[將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="67da0-115">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="67da0-116">[支援](#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="67da0-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="67da0-117">[支援 Stack \<T> 的來回行程](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="67da0-117">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="67da0-118">[將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="67da0-118">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="67da0-119">[具有非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="67da0-119">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="67da0-120">[支援](#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="67da0-120">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="67da0-121">[支援 Stack \<T> 的來回行程](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="67da0-121">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

<span data-ttu-id="67da0-122">在您為自訂轉換器撰寫的程式碼中，請留意使用新實例的顯著效能損失 <xref:System.Text.Json.JsonSerializerOptions> 。</span><span class="sxs-lookup"><span data-stu-id="67da0-122">In the code you write for a custom converter, be aware of the substantial performance penalty for using new <xref:System.Text.Json.JsonSerializerOptions> instances.</span></span> <span data-ttu-id="67da0-123">如需詳細資訊，請參閱 [重複使用 JsonSerializerOptions 實例](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)。</span><span class="sxs-lookup"><span data-stu-id="67da0-123">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="67da0-124">自訂轉換器模式</span><span class="sxs-lookup"><span data-stu-id="67da0-124">Custom converter patterns</span></span>

<span data-ttu-id="67da0-125">有兩種模式可建立自訂轉換器：基本模式和 factory 模式。</span><span class="sxs-lookup"><span data-stu-id="67da0-125">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="67da0-126">Factory 模式是用於處理類型 `Enum` 或開放式泛型的轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-126">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="67da0-127">基本模式適用于非泛型和封閉式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="67da0-127">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="67da0-128">例如，下列類型的轉換器需要 factory 模式：</span><span class="sxs-lookup"><span data-stu-id="67da0-128">For example, converters for the following types require the factory pattern:</span></span>

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

<span data-ttu-id="67da0-129">基本模式可處理的一些類型範例包括：</span><span class="sxs-lookup"><span data-stu-id="67da0-129">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

<span data-ttu-id="67da0-130">基本模式會建立可以處理一種類型的類別。</span><span class="sxs-lookup"><span data-stu-id="67da0-130">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="67da0-131">Factory 模式會建立一個類別，在執行時間決定需要何種特定類型，並以動態方式建立適當的轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-131">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="67da0-132">範例基本轉換器</span><span class="sxs-lookup"><span data-stu-id="67da0-132">Sample basic converter</span></span>

<span data-ttu-id="67da0-133">下列範例是覆寫現有資料類型之預設序列化的轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-133">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="67da0-134">轉換器使用 mm/dd/yyyy 格式的 `DateTimeOffset` 屬性。</span><span class="sxs-lookup"><span data-stu-id="67da0-134">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="67da0-135">範例 factory 模式切換器</span><span class="sxs-lookup"><span data-stu-id="67da0-135">Sample factory pattern converter</span></span>

<span data-ttu-id="67da0-136">下列程式碼顯示可搭配使用的自訂轉換器 `Dictionary<Enum,TValue>` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-136">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="67da0-137">因為第一個泛型型別參數為 `Enum` ，第二個是開啟的，所以程式碼會遵循 factory 模式。</span><span class="sxs-lookup"><span data-stu-id="67da0-137">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="67da0-138">`CanConvert`方法 `true` 只 `Dictionary` 會傳回具有兩個泛型參數的，第一個是 `Enum` 型別。</span><span class="sxs-lookup"><span data-stu-id="67da0-138">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="67da0-139">內部轉換器會取得現有的轉換器，以處理執行時間所提供的任何類型 `TValue` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-139">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="67da0-140">上述程式碼與本文稍後的 [非字串索引鍵的支援字典](#support-dictionary-with-non-string-key) 中所顯示的相同。</span><span class="sxs-lookup"><span data-stu-id="67da0-140">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="67da0-141">遵循基本模式的步驟</span><span class="sxs-lookup"><span data-stu-id="67da0-141">Steps to follow the basic pattern</span></span>

<span data-ttu-id="67da0-142">下列步驟說明如何遵循基本模式來建立轉換器：</span><span class="sxs-lookup"><span data-stu-id="67da0-142">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="67da0-143">建立衍生自的類別， <xref:System.Text.Json.Serialization.JsonConverter%601> 其中 `T` 是要序列化和還原序列化的型別。</span><span class="sxs-lookup"><span data-stu-id="67da0-143">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="67da0-144">覆寫方法以將內送 JSON 還原序列化 `Read` ，並將其轉換為類型 `T` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-144">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="67da0-145">使用 <xref:System.Text.Json.Utf8JsonReader> 傳遞至方法的，以讀取 JSON。</span><span class="sxs-lookup"><span data-stu-id="67da0-145">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="67da0-146">覆寫 `Write` 方法以序列化類型的傳入物件 `T` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-146">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="67da0-147">使用 <xref:System.Text.Json.Utf8JsonWriter> 傳遞至方法的，以寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="67da0-147">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="67da0-148">`CanConvert`只有在必要時才覆寫方法。</span><span class="sxs-lookup"><span data-stu-id="67da0-148">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="67da0-149">`true`當要轉換的類型是型別時，就會傳回預設的實值 `T` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-149">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="67da0-150">因此，只支援類型的轉換器 `T` 不需要覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="67da0-150">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="67da0-151">如需需要覆寫這個方法的轉換器範例，請參閱本文稍後的多型還原 [序列化一節](#support-polymorphic-deserialization) 。</span><span class="sxs-lookup"><span data-stu-id="67da0-151">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="67da0-152">您可以參考 [內建的轉換器原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) ，作為撰寫自訂轉換器的參考程式。</span><span class="sxs-lookup"><span data-stu-id="67da0-152">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="67da0-153">遵循 factory 模式的步驟</span><span class="sxs-lookup"><span data-stu-id="67da0-153">Steps to follow the factory pattern</span></span>

<span data-ttu-id="67da0-154">下列步驟說明如何遵循 factory 模式來建立轉換器：</span><span class="sxs-lookup"><span data-stu-id="67da0-154">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="67da0-155">建立衍生自 <xref:System.Text.Json.Serialization.JsonConverterFactory> 的類別。</span><span class="sxs-lookup"><span data-stu-id="67da0-155">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="67da0-156">`CanConvert`當要轉換的型別是轉換器可以處理的型別時，請覆寫方法以傳回 true。</span><span class="sxs-lookup"><span data-stu-id="67da0-156">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="67da0-157">例如，如果轉換器適用于 `List<T>` ，它可能只會處理 `List<int>` 、 `List<string>` 和 `List<DateTime>` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-157">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="67da0-158">覆寫 `CreateConverter` 方法以傳回轉換器類別的實例，這個實例將會處理在執行時間提供的型別轉換。</span><span class="sxs-lookup"><span data-stu-id="67da0-158">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="67da0-159">建立方法具現化的轉換器類別 `CreateConverter` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-159">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="67da0-160">開啟泛型需要 factory 模式，因為將物件與字串相互轉換的程式碼對所有類型而言都不相同。</span><span class="sxs-lookup"><span data-stu-id="67da0-160">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="67da0-161">開放式泛型型別 (的轉換器 `List<T>` ，例如) 必須為封閉式泛型型別 (建立轉換器 `List<DateTime>` ，例如在幕後進行) 。</span><span class="sxs-lookup"><span data-stu-id="67da0-161">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="67da0-162">您必須撰寫程式碼來處理轉換器可以處理的每個封閉式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="67da0-162">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="67da0-163">`Enum`型別類似于開放式泛型型別：的轉換器 `Enum` 必須建立特定 (的轉換器 `Enum` `WeekdaysEnum` ，例如在幕後) 。</span><span class="sxs-lookup"><span data-stu-id="67da0-163">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="67da0-164">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="67da0-164">Error handling</span></span>

<span data-ttu-id="67da0-165">如果您需要在錯誤處理常式代碼中擲回例外狀況，請考慮擲回， <xref:System.Text.Json.JsonException> 而不使用訊息。</span><span class="sxs-lookup"><span data-stu-id="67da0-165">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="67da0-166">此例外狀況類型會自動建立訊息，其中包含造成錯誤之 JSON 部分的路徑。</span><span class="sxs-lookup"><span data-stu-id="67da0-166">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="67da0-167">例如，語句會 `throw new JsonException();` 產生類似下列範例的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="67da0-167">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="67da0-168">如果您確實提供訊息 (例如，例外狀況 `throw new JsonException("Error occurred")` 仍會提供屬性中的路徑 <xref:System.Text.Json.JsonException.Path> 。</span><span class="sxs-lookup"><span data-stu-id="67da0-168">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="67da0-169">註冊自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="67da0-169">Register a custom converter</span></span>

<span data-ttu-id="67da0-170">*註冊* 自訂轉換器，讓 `Serialize` 和 `Deserialize` 方法使用它。</span><span class="sxs-lookup"><span data-stu-id="67da0-170">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="67da0-171">選擇下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="67da0-171">Choose one of the following approaches:</span></span>

* <span data-ttu-id="67da0-172">將轉換器類別的實例新增至 <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="67da0-172">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="67da0-173">將 [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 屬性套用至需要自訂轉換器的屬性。</span><span class="sxs-lookup"><span data-stu-id="67da0-173">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="67da0-174">將 [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 屬性套用至代表自訂實值型別的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="67da0-174">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="67da0-175">註冊範例-轉換器集合</span><span class="sxs-lookup"><span data-stu-id="67da0-175">Registration sample - Converters collection</span></span>

<span data-ttu-id="67da0-176">以下範例會 <xref:System.ComponentModel.DateTimeOffsetConverter> 為類型的屬性建立預設值 <xref:System.DateTimeOffset> ：</span><span class="sxs-lookup"><span data-stu-id="67da0-176">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

<span data-ttu-id="67da0-177">假設您將下列型別的實例序列化：</span><span class="sxs-lookup"><span data-stu-id="67da0-177">Suppose you serialize an instance of the following type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="67da0-178">以下是顯示已使用自訂轉換器的 JSON 輸出範例：</span><span class="sxs-lookup"><span data-stu-id="67da0-178">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="67da0-179">下列程式碼使用自訂轉換器還原序列化的相同方法 `DateTimeOffset` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-179">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="67da0-180">註冊範例-屬性上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="67da0-180">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="67da0-181">下列程式碼會選取屬性的自訂轉換器 `Date` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-181">The following code selects a custom converter for the `Date` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

<span data-ttu-id="67da0-182">要序列化的程式碼 `WeatherForecastWithConverterAttribute` 不需要使用 `JsonSerializeOptions.Converters` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-182">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

<span data-ttu-id="67da0-183">還原序列化的程式碼也不需要使用 `Converters` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-183">The code to deserialize also doesn't require the use of `Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="67da0-184">註冊範例-類型上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="67da0-184">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="67da0-185">以下程式碼會建立結構，並 `[JsonConverter]` 對其套用屬性：</span><span class="sxs-lookup"><span data-stu-id="67da0-185">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

<span data-ttu-id="67da0-186">以下是上述結構的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="67da0-186">Here's the custom converter for the preceding struct:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

<span data-ttu-id="67da0-187">`[JsonConvert]`結構上的屬性會將自訂轉換器註冊為類型屬性的預設值 `Temperature` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-187">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="67da0-188">當您將轉換器序列化或還原序列化時，會自動在下列類型的屬性上使用轉換器 `TemperatureCelsius` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-188">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a><span data-ttu-id="67da0-189">轉換器註冊優先順序</span><span class="sxs-lookup"><span data-stu-id="67da0-189">Converter registration precedence</span></span>

<span data-ttu-id="67da0-190">在序列化或還原序列化期間，會依下列順序為每個 JSON 元素選擇一個轉換器，從最高優先順序到最低：</span><span class="sxs-lookup"><span data-stu-id="67da0-190">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="67da0-191">`[JsonConverter]` 套用至屬性。</span><span class="sxs-lookup"><span data-stu-id="67da0-191">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="67da0-192">加入至集合的轉換器 `Converters` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-192">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="67da0-193">`[JsonConverter]` 套用至自訂實數值型別或 POCO。</span><span class="sxs-lookup"><span data-stu-id="67da0-193">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="67da0-194">如果在集合中註冊了某個類型的多個自訂轉換器 `Converters` ，則會使用第一個傳回 true 的轉換器 `CanConvert` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-194">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="67da0-195">只有在沒有註冊適用的自訂轉換器時，才會選擇內建的轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-195">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="67da0-196">常見案例的轉換器範例</span><span class="sxs-lookup"><span data-stu-id="67da0-196">Converter samples for common scenarios</span></span>

<span data-ttu-id="67da0-197">下列各節提供的轉換器範例可解決一些內建功能未處理的常見案例。</span><span class="sxs-lookup"><span data-stu-id="67da0-197">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="67da0-198">[將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="67da0-198">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="67da0-199">[支援](#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="67da0-199">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="67da0-200">[支援 Stack \<T> 的來回行程](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="67da0-200">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="67da0-201">[將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="67da0-201">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="67da0-202">[具有非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="67da0-202">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="67da0-203">[支援](#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="67da0-203">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="67da0-204">[支援 Stack \<T> 的來回行程](#support-round-trip-for-stackt)。</span><span class="sxs-lookup"><span data-stu-id="67da0-204">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="67da0-205">將推斷的類型還原序列化為物件屬性</span><span class="sxs-lookup"><span data-stu-id="67da0-205">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="67da0-206">當還原序列化為型別的屬性時 `object` ， `JsonElement` 會建立物件。</span><span class="sxs-lookup"><span data-stu-id="67da0-206">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="67da0-207">原因是還原序列化程式不知道要建立什麼 CLR 型別，而且它不會試著猜測。</span><span class="sxs-lookup"><span data-stu-id="67da0-207">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="67da0-208">例如，如果 JSON 屬性有 "true"，則還原序列化程式並不會推斷值為 `Boolean` ，而且如果專案具有 "01/01/2019"，則還原序列化程式並不會推斷它是 a `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-208">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="67da0-209">型別推斷可能不正確。</span><span class="sxs-lookup"><span data-stu-id="67da0-209">Type inference can be inaccurate.</span></span> <span data-ttu-id="67da0-210">如果還原序列化程式會剖析沒有小數點的 JSON 數位 `long` ，如果值原本是序列化為或，可能會導致超出範圍的問題 `ulong` `BigInteger` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-210">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="67da0-211">如果數位原本是序列化為，則剖析具有小數點的數位 `double` 可能會遺失精確度 `decimal` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-211">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="67da0-212">針對需要型別推斷的案例，下列程式碼會顯示內容的自訂轉換器 `object` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-212">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="67da0-213">程式碼會轉換：</span><span class="sxs-lookup"><span data-stu-id="67da0-213">The code converts:</span></span>

* <span data-ttu-id="67da0-214">`true`以及 `false``Boolean`</span><span class="sxs-lookup"><span data-stu-id="67da0-214">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="67da0-215">不含小數位數的數位 `long`</span><span class="sxs-lookup"><span data-stu-id="67da0-215">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="67da0-216">具有小數點的數位 `double`</span><span class="sxs-lookup"><span data-stu-id="67da0-216">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="67da0-217">日期至 `DateTime`</span><span class="sxs-lookup"><span data-stu-id="67da0-217">Dates to `DateTime`</span></span>
* <span data-ttu-id="67da0-218">字串至 `string`</span><span class="sxs-lookup"><span data-stu-id="67da0-218">Strings to `string`</span></span>
* <span data-ttu-id="67da0-219">其他專案 `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="67da0-219">Everything else to `JsonElement`</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

<span data-ttu-id="67da0-220">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="67da0-220">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

<span data-ttu-id="67da0-221">以下是包含屬性的範例類型 `object` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-221">Here's an example type with `object` properties:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

<span data-ttu-id="67da0-222">下列要還原序列化的 JSON 範例包含將還原序列化為 `DateTime` 、和的值 `long` `string` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-222">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="67da0-223">如果沒有自訂轉換器，還原序列化會 `JsonElement` 在每個屬性中放置。</span><span class="sxs-lookup"><span data-stu-id="67da0-223">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="67da0-224">命名空間中的 [單元測試資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) `System.Text.Json.Serialization` 有更多的自訂轉換器範例，可處理屬性的還原序列化 `object` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-224">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="67da0-225">使用非字串索引鍵的支援字典</span><span class="sxs-lookup"><span data-stu-id="67da0-225">Support Dictionary with non-string key</span></span>

<span data-ttu-id="67da0-226">字典集合的內建支援適用于 `Dictionary<string, TValue>` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-226">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="67da0-227">也就是說，索引鍵必須是字串。</span><span class="sxs-lookup"><span data-stu-id="67da0-227">That is, the key must be a string.</span></span> <span data-ttu-id="67da0-228">若要支援具有整數或其他類型作為索引鍵的字典，則需要自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="67da0-228">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="67da0-229">下列程式碼顯示可搭配使用的自訂轉換器 `Dictionary<Enum,TValue>` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-229">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="67da0-230">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="67da0-230">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

<span data-ttu-id="67da0-231">轉換器可以序列化和還原序列化 `TemperatureRanges` 下列使用下列類別的屬性 `Enum` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-231">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

<span data-ttu-id="67da0-232">序列化的 JSON 輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="67da0-232">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="67da0-233">命名空間中的 [單元測試資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) ， `System.Text.Json.Serialization` 有更多的自訂轉換器的範例，可處理非字串金鑰字典。</span><span class="sxs-lookup"><span data-stu-id="67da0-233">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="67da0-234">支援多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="67da0-234">Support polymorphic deserialization</span></span>

<span data-ttu-id="67da0-235">內建功能提供有限範圍的多型 [序列化](system-text-json-polymorphism.md) ，但完全不支援還原序列化。</span><span class="sxs-lookup"><span data-stu-id="67da0-235">Built-in features provide a limited range of [polymorphic serialization](system-text-json-polymorphism.md) but no support for deserialization at all.</span></span> <span data-ttu-id="67da0-236">還原序列化需要自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-236">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="67da0-237">例如，假設您有一個 `Person` 具有 `Employee` 和衍生類別的抽象基類 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-237">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="67da0-238">多型還原序列化表示在設計階段，您可以將指定為還原序列化 `Person` 目標，並在 `Customer` `Employee` 執行時間將 JSON 中的物件正確還原序列化。</span><span class="sxs-lookup"><span data-stu-id="67da0-238">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="67da0-239">在還原序列化期間，您必須在 JSON 中尋找識別所需類型的線索。</span><span class="sxs-lookup"><span data-stu-id="67da0-239">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="67da0-240">可用的線索種類會因每個案例而異。</span><span class="sxs-lookup"><span data-stu-id="67da0-240">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="67da0-241">例如，可能會有鑒別子屬性，或您可能必須依賴特定屬性的存在或不存在。</span><span class="sxs-lookup"><span data-stu-id="67da0-241">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="67da0-242">目前的版本 `System.Text.Json` 並未提供屬性來指定如何處理多型還原序列化案例，因此需要自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-242">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="67da0-243">下列程式碼顯示基類、兩個衍生類別，以及它們的自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="67da0-243">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="67da0-244">轉換器會使用鑒別子屬性來進行多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="67da0-244">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="67da0-245">類型鑒別子不在類別定義中，而是在序列化期間建立，並且會在還原序列化期間讀取。</span><span class="sxs-lookup"><span data-stu-id="67da0-245">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

<span data-ttu-id="67da0-246">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="67da0-246">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

<span data-ttu-id="67da0-247">轉換器可以將使用相同轉換器所建立的 JSON 還原序列化，例如：</span><span class="sxs-lookup"><span data-stu-id="67da0-247">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="67da0-248">上述範例中的轉換器程式碼會以手動方式讀取和寫入每個屬性。</span><span class="sxs-lookup"><span data-stu-id="67da0-248">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="67da0-249">替代方法是呼叫 `Deserialize` 或 `Serialize` 執行某些工作。</span><span class="sxs-lookup"><span data-stu-id="67da0-249">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="67da0-250">如需範例，請參閱 [這 StackOverflow 文章](https://stackoverflow.com/a/59744873/12509023)。</span><span class="sxs-lookup"><span data-stu-id="67da0-250">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="67da0-251">支援堆疊的來回行程\<T></span><span class="sxs-lookup"><span data-stu-id="67da0-251">Support round trip for Stack\<T></span></span>

<span data-ttu-id="67da0-252">如果您將 JSON 字串還原序列化為物件，然後將 <xref:System.Collections.Generic.Stack%601> 該物件序列化，堆疊的內容會以相反的順序排列。</span><span class="sxs-lookup"><span data-stu-id="67da0-252">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="67da0-253">此行為適用于下列型別和介面，以及衍生自這些型別的使用者定義型別：</span><span class="sxs-lookup"><span data-stu-id="67da0-253">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="67da0-254">若要支援在堆疊中保留原始順序的序列化和還原序列化，則需要自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="67da0-254">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="67da0-255">下列程式碼顯示可啟用物件來回往返的自訂轉換器 `Stack<T>` ：</span><span class="sxs-lookup"><span data-stu-id="67da0-255">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

<span data-ttu-id="67da0-256">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="67da0-256">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a><span data-ttu-id="67da0-257">處理 Null 值</span><span class="sxs-lookup"><span data-stu-id="67da0-257">Handle null values</span></span>

<span data-ttu-id="67da0-258">根據預設，序列化程式會處理 null 值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="67da0-258">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="67da0-259">針對參考型別和 <xref:System.Nullable%601> 類型：</span><span class="sxs-lookup"><span data-stu-id="67da0-259">For reference types and <xref:System.Nullable%601> types:</span></span>

  * <span data-ttu-id="67da0-260">它不會 `null` 在序列化時傳遞至自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-260">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="67da0-261">它不會在還原序列化 `JsonTokenType.Null` 時傳遞至自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-261">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="67da0-262">它會在還原序列化 `null` 時傳回實例。</span><span class="sxs-lookup"><span data-stu-id="67da0-262">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="67da0-263">它會 `null` 直接寫入序列化的寫入器。</span><span class="sxs-lookup"><span data-stu-id="67da0-263">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="67da0-264">針對不可為 null 的實數值型別：</span><span class="sxs-lookup"><span data-stu-id="67da0-264">For non-nullable value types:</span></span>

  * <span data-ttu-id="67da0-265">它會 `JsonTokenType.Null` 在還原序列化時傳遞至自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="67da0-265">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="67da0-266"> (如果沒有可用的自訂轉換器，則 `JsonException` 類型的內部轉換器會擲回例外狀況。 ) </span><span class="sxs-lookup"><span data-stu-id="67da0-266">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="67da0-267">這項 null 處理行為主要是藉由略過額外的轉換器呼叫來優化效能。</span><span class="sxs-lookup"><span data-stu-id="67da0-267">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="67da0-268">此外，它可避免 `null` 在每個和方法覆寫的開頭，強制執行可為 null 類型的轉換器 `Read` `Write` 。</span><span class="sxs-lookup"><span data-stu-id="67da0-268">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="67da0-269">若要啟用自訂轉換器來處理 `null` 參考或實數值型別，請覆寫 <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> 以傳回 `true` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="67da0-269">To enable a custom converter to handle `null` for a reference or value type, override <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="19":::
::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="67da0-270">其他自訂轉換器範例</span><span class="sxs-lookup"><span data-stu-id="67da0-270">Other custom converter samples</span></span>

<span data-ttu-id="67da0-271">[從遷移 Newtonsoft.Json 至 System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md)文章包含其他自訂轉換器範例。</span><span class="sxs-lookup"><span data-stu-id="67da0-271">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="67da0-272">原始程式碼中的 [ [單元測試] 資料夾](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) `System.Text.Json.Serialization` 包含其他自訂轉換器範例，例如：</span><span class="sxs-lookup"><span data-stu-id="67da0-272">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="67da0-273">[在還原序列化時將 null 轉換為0的 Int32 轉換子](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="67da0-273">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="67da0-274">[Int32 轉換器，可在還原序列化時同時允許字串和數位值](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="67da0-274">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="67da0-275">[列舉轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="67da0-275">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="67da0-276">[\<T>接受外部資料的清單轉換器](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="67da0-276">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="67da0-277">[Long [] 轉換器，適用于以逗號分隔的數位清單](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="67da0-277">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="67da0-278">如果您需要建立可修改現有內建轉換器行為的轉換器，您可以取得 [現有轉換器的原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) ，以做為自訂的起點。</span><span class="sxs-lookup"><span data-stu-id="67da0-278">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="67da0-279">其他資源</span><span class="sxs-lookup"><span data-stu-id="67da0-279">Additional resources</span></span>

* <span data-ttu-id="67da0-280">[內建轉換器的原始程式碼](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="67da0-280">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="67da0-281">中的 DateTime 和 DateTimeOffset 支援 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="67da0-281">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="67da0-282">如何自訂字元編碼</span><span class="sxs-lookup"><span data-stu-id="67da0-282">How to customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="67da0-283">如何撰寫自訂序列化程式和還原序列化程式</span><span class="sxs-lookup"><span data-stu-id="67da0-283">How to write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* <span data-ttu-id="67da0-284">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="67da0-284">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="67da0-285">[System.Text.Json。序列化 API 參考](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="67da0-285">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
