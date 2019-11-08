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
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741889"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="38929-102">如何在 .NET 中撰寫 JSON 序列化的自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="38929-103">本文說明如何為 <xref:System.Text.Json> 命名空間中提供的 JSON 序列化類別建立自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="38929-104">如需 `System.Text.Json`的簡介，請參閱[如何在 .net 中序列化和還原序列化 JSON](system-text-json-how-to.md)。</span><span class="sxs-lookup"><span data-stu-id="38929-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="38929-105">*轉換器*是一個類別，可將物件或值轉換成 JSON。</span><span class="sxs-lookup"><span data-stu-id="38929-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="38929-106">針對對應至 JavaScript 基本類型的大部分基本型別，`System.Text.Json` 命名空間具有內建的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="38929-107">您可以撰寫自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-107">You can write custom converters:</span></span>

* <span data-ttu-id="38929-108">覆寫內建轉換器的預設行為。</span><span class="sxs-lookup"><span data-stu-id="38929-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="38929-109">例如，您可能想要以 mm/dd/yyyy 格式來表示 `DateTime` 值，而不是預設的 ISO 8601-1:2019 格式。</span><span class="sxs-lookup"><span data-stu-id="38929-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="38929-110">支援自訂實值型別。</span><span class="sxs-lookup"><span data-stu-id="38929-110">To support a custom value type.</span></span> <span data-ttu-id="38929-111">例如，`PhoneNumber` 結構。</span><span class="sxs-lookup"><span data-stu-id="38929-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="38929-112">您也可以撰寫自訂轉換器，使用目前版本中未包含的功能來擴充 `System.Text.Json`。</span><span class="sxs-lookup"><span data-stu-id="38929-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="38929-113">本文稍後會涵蓋下列案例：</span><span class="sxs-lookup"><span data-stu-id="38929-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="38929-114">[將推斷的類型還原序列化為物件屬性](#deserialize-inferred-types-to-object-properties)。</span><span class="sxs-lookup"><span data-stu-id="38929-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="38929-115">[支援具有非字串索引鍵的字典](#support-dictionary-with-non-string-key)。</span><span class="sxs-lookup"><span data-stu-id="38929-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="38929-116">[支援](#support-polymorphic-deserialization)多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="38929-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="38929-117">自訂轉換器模式</span><span class="sxs-lookup"><span data-stu-id="38929-117">Custom converter patterns</span></span>

<span data-ttu-id="38929-118">建立自訂轉換器的模式有兩種：基本模式和 factory 模式。</span><span class="sxs-lookup"><span data-stu-id="38929-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="38929-119">Factory 模式適用于處理類型 `Enum` 或開放式泛型的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="38929-120">基本模式適用于非泛型和封閉式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="38929-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="38929-121">例如，下列類型的轉換器需要 factory 模式：</span><span class="sxs-lookup"><span data-stu-id="38929-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="38929-122">基本模式可以處理的一些類型範例包括：</span><span class="sxs-lookup"><span data-stu-id="38929-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="38929-123">基本模式會建立可處理一種類型的類別。</span><span class="sxs-lookup"><span data-stu-id="38929-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="38929-124">Factory 模式會建立一個類別，它會在執行時間決定需要哪一個特定型別，並以動態方式建立適當的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="38929-125">範例基本轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-125">Sample basic converter</span></span>

<span data-ttu-id="38929-126">下列範例是覆寫現有資料類型之預設序列化的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="38929-127">轉換器會針對 `DateTimeOffset` 屬性使用 mm/dd/yyyy 格式。</span><span class="sxs-lookup"><span data-stu-id="38929-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="38929-128">範例 factory 模式切換器</span><span class="sxs-lookup"><span data-stu-id="38929-128">Sample factory pattern converter</span></span>

<span data-ttu-id="38929-129">下列程式碼顯示可搭配 `Dictionary<Enum,TValue>`使用的自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="38929-130">程式碼會遵循 factory 模式，因為第一個泛型型別參數是 `Enum`，而第二個是開啟的。</span><span class="sxs-lookup"><span data-stu-id="38929-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="38929-131">`CanConvert` 方法只會針對具有兩個泛型參數的 `Dictionary` 傳回 `true`，其中第一個是 `Enum` 型別。</span><span class="sxs-lookup"><span data-stu-id="38929-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="38929-132">內部轉換器會取得現有的轉換器，以處理在執行時間針對 `TValue`所提供的任何類型。</span><span class="sxs-lookup"><span data-stu-id="38929-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="38929-133">上述程式碼與本文稍後的「[包含非字串索引鍵的支援字典](#support-dictionary-with-non-string-key)」中所顯示的相同。</span><span class="sxs-lookup"><span data-stu-id="38929-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="38929-134">遵循基本模式的步驟</span><span class="sxs-lookup"><span data-stu-id="38929-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="38929-135">下列步驟說明如何遵循基本模式來建立轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="38929-136">建立衍生自 <xref:System.Text.Json.Serialization.JsonConverter%601> 的類別，其中 `T` 是要序列化和還原序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="38929-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="38929-137">覆寫 `Read` 方法，將內送 JSON 還原序列化，並將它轉換成類型 `T`。</span><span class="sxs-lookup"><span data-stu-id="38929-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="38929-138">使用傳遞至方法的 <xref:System.Text.Json.Utf8JsonReader> 來讀取 JSON。</span><span class="sxs-lookup"><span data-stu-id="38929-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="38929-139">覆寫 `Write` 方法，將 `T`類型的傳入物件序列化。</span><span class="sxs-lookup"><span data-stu-id="38929-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="38929-140">使用傳遞至方法的 <xref:System.Text.Json.Utf8JsonWriter> 來寫入 JSON。</span><span class="sxs-lookup"><span data-stu-id="38929-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="38929-141">只有在必要時，才覆寫 `CanConvert` 方法。</span><span class="sxs-lookup"><span data-stu-id="38929-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="38929-142">當要轉換的型別是 `T`型別時，預設的實值會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="38929-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="38929-143">因此，只支援類型 `T` 的轉換器不需要覆寫此方法。</span><span class="sxs-lookup"><span data-stu-id="38929-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="38929-144">如需需要覆寫此方法之轉換器的範例，請參閱本文稍後[的多](#support-polymorphic-deserialization)型還原序列化一節。</span><span class="sxs-lookup"><span data-stu-id="38929-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="38929-145">您可以參考[內建的轉換器原始程式碼](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)做為參考執行，以撰寫自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="38929-146">遵循 factory 模式的步驟</span><span class="sxs-lookup"><span data-stu-id="38929-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="38929-147">下列步驟說明如何遵循 factory 模式來建立轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="38929-148">建立衍生自 <xref:System.Text.Json.Serialization.JsonConverterFactory> 的類別。</span><span class="sxs-lookup"><span data-stu-id="38929-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="38929-149">當要轉換的型別是轉換器可以處理的類型時，覆寫 `CanConvert` 方法，使其傳回 true。</span><span class="sxs-lookup"><span data-stu-id="38929-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="38929-150">例如，如果轉換器適用于 `List<T>` 它可能只會處理 `List<int>`、`List<string>`和 `List<DateTime>`。</span><span class="sxs-lookup"><span data-stu-id="38929-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="38929-151">覆寫 `CreateConverter` 方法，以傳回將處理在執行時間所提供之類型轉換的轉換器類別實例。</span><span class="sxs-lookup"><span data-stu-id="38929-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="38929-152">建立 `CreateConverter` 方法具現化的轉換器類別。</span><span class="sxs-lookup"><span data-stu-id="38929-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="38929-153">開放式泛型需要 factory 模式，因為所有類型的物件來回轉換的程式碼都不相同。</span><span class="sxs-lookup"><span data-stu-id="38929-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="38929-154">舉例來說，開放式泛型型別的轉換器（例如`List<T>`）必須針對封閉式泛型型別（例如，`List<DateTime>`）建立轉換子，以供幕後使用。</span><span class="sxs-lookup"><span data-stu-id="38929-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="38929-155">必須撰寫程式碼，以處理轉換器可以處理的每個封閉式泛型型別。</span><span class="sxs-lookup"><span data-stu-id="38929-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="38929-156">`Enum` 類型類似于開放式泛型型別： `Enum` 的轉換器必須針對特定 `Enum` （例如，`WeekdaysEnum`）建立轉換器，以供幕後使用。</span><span class="sxs-lookup"><span data-stu-id="38929-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="38929-157">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="38929-157">Error handling</span></span>

<span data-ttu-id="38929-158">如果您需要在錯誤處理常式代碼中擲回例外狀況，請考慮在沒有訊息的情況下擲回 <xref:System.Text.Json.JsonException>。</span><span class="sxs-lookup"><span data-stu-id="38929-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="38929-159">此例外狀況類型會自動建立訊息，其中包含造成錯誤之 JSON 部分的路徑。</span><span class="sxs-lookup"><span data-stu-id="38929-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="38929-160">例如，語句 `throw new JsonException();` 會產生類似下列範例的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="38929-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="38929-161">如果您提供訊息（例如 `throw new JsonException("Error occurred)`，例外狀況仍然會在 <xref:System.Text.Json.JsonException.Path> 屬性中提供路徑。</span><span class="sxs-lookup"><span data-stu-id="38929-161">If you do provide a message (for example, `throw new JsonException("Error occurred)`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="38929-162">註冊自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-162">Register a custom converter</span></span>

<span data-ttu-id="38929-163">*註冊*自訂轉換器，讓 `Serialize` 和 `Deserialize` 方法使用它。</span><span class="sxs-lookup"><span data-stu-id="38929-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="38929-164">選擇下列其中一種方法：</span><span class="sxs-lookup"><span data-stu-id="38929-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="38929-165">將轉換器類別的實例加入至 <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="38929-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="38929-166">將[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)屬性套用至需要自訂轉換器的屬性。</span><span class="sxs-lookup"><span data-stu-id="38929-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="38929-167">將[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)屬性套用至代表自訂實數值型別的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="38929-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="38929-168">註冊範例-轉換器集合</span><span class="sxs-lookup"><span data-stu-id="38929-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="38929-169">以下範例會讓 `ExampleDateTimeOffsetConverter` `DateTimeOffset`類型的屬性的預設值：</span><span class="sxs-lookup"><span data-stu-id="38929-169">Here's an example that makes the `ExampleDateTimeOffsetConverter` the default for properties of type `DateTimeOffset`:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="38929-170">假設您將下列型別序列化：</span><span class="sxs-lookup"><span data-stu-id="38929-170">Suppose you serialize the following type:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="38929-171">以下是顯示使用自訂轉換器的 JSON 輸出範例：</span><span class="sxs-lookup"><span data-stu-id="38929-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="38929-172">下列程式碼會使用相同的方法，以使用自訂 `DateTimeOffset` 轉換器進行還原序列化：</span><span class="sxs-lookup"><span data-stu-id="38929-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="38929-173">註冊範例-屬性上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="38929-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="38929-174">下列程式碼會選取 `Date` 屬性的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-174">The following code selects a custom converter for the `Date` property:</span></span>

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="38929-175">序列化和還原序列化 `WeatherForecastWithConverter` 的程式碼不需要使用 `JsonSerializeOptions.Converters`：</span><span class="sxs-lookup"><span data-stu-id="38929-175">The code to serialize and deserialize `WeatherForecastWithConverter` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="38929-176">註冊範例-類型上的 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="38929-176">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="38929-177">以下程式碼會建立結構，並將 `[JsonConverter]` 屬性套用至它：</span><span class="sxs-lookup"><span data-stu-id="38929-177">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

<span data-ttu-id="38929-178">以下是上述結構的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-178">Here's the custom converter for the preceding struct:</span></span>

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

<span data-ttu-id="38929-179">結構上的 `[JsonConvert]` 屬性會註冊自訂轉換器，做為 `Temperature`類型屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="38929-179">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="38929-180">當您序列化或還原序列化時，轉換器會自動用於下列類型的 `TemperatureC` 屬性：</span><span class="sxs-lookup"><span data-stu-id="38929-180">The converter is automatically used on the `TemperatureC` property of the following type when you serialize or deserialize it:</span></span>

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a><span data-ttu-id="38929-181">轉換器註冊優先順序</span><span class="sxs-lookup"><span data-stu-id="38929-181">Converter registration precedence</span></span>

<span data-ttu-id="38929-182">在序列化或還原序列化期間，會依下列順序為每個 JSON 元素選擇一個轉換器，從最高優先順序列到最低：</span><span class="sxs-lookup"><span data-stu-id="38929-182">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="38929-183">套用至屬性的 `[JsonConverter]`。</span><span class="sxs-lookup"><span data-stu-id="38929-183">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="38929-184">已新增至 `Converters` 集合的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-184">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="38929-185">`[JsonConverter]` 套用至自訂實數值型別或 POCO。</span><span class="sxs-lookup"><span data-stu-id="38929-185">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="38929-186">如果類型的多個自訂轉換器已在 `Converters` 集合中註冊，則會使用針對 `CanConvert` 傳回 true 的第一個轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-186">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="38929-187">只有在未註冊適用的自訂轉換器時，才會選擇內建的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-187">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="38929-188">常見案例的轉換子範例</span><span class="sxs-lookup"><span data-stu-id="38929-188">Converter samples for common scenarios</span></span>

<span data-ttu-id="38929-189">下列各節提供的轉換器範例可解決一些內建功能無法處理的常見案例。</span><span class="sxs-lookup"><span data-stu-id="38929-189">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="38929-190">將推斷的類型還原序列化為物件屬性</span><span class="sxs-lookup"><span data-stu-id="38929-190">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="38929-191">當還原序列化為 `Object`類型的屬性時，會建立 `JsonElement` 物件。</span><span class="sxs-lookup"><span data-stu-id="38929-191">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="38929-192">原因是還原序列化程式不知道要建立什麼 CLR 型別，而且也不會嘗試猜到。</span><span class="sxs-lookup"><span data-stu-id="38929-192">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="38929-193">例如，如果 JSON 屬性具有 "true"，則還原序列化程式並不會推斷值為 `Boolean`，如果元素具有 "01/01/2019"，則還原序列化程式不會推斷它是 `DateTime`。</span><span class="sxs-lookup"><span data-stu-id="38929-193">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="38929-194">型別推斷可能不正確。</span><span class="sxs-lookup"><span data-stu-id="38929-194">Type inference can be inaccurate.</span></span> <span data-ttu-id="38929-195">如果還原序列化程式會剖析沒有小數點的 JSON 數位做為 `long`，如果值原本序列化為 `ulong` 或 `BigInteger`，可能會導致超出範圍的問題。</span><span class="sxs-lookup"><span data-stu-id="38929-195">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="38929-196">如果數位原本序列化為 `decimal`，則剖析具有小數點做為 `double` 的數位可能會失去精確度。</span><span class="sxs-lookup"><span data-stu-id="38929-196">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="38929-197">針對需要型別推斷的案例，下列程式碼會顯示 `Object` 屬性的自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-197">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="38929-198">程式碼會轉換：</span><span class="sxs-lookup"><span data-stu-id="38929-198">The code converts:</span></span>

* <span data-ttu-id="38929-199">`true` 和 `false` 至 `Boolean`</span><span class="sxs-lookup"><span data-stu-id="38929-199">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="38929-200">要 `long` 或 `double` 的數位</span><span class="sxs-lookup"><span data-stu-id="38929-200">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="38929-201">要 `DateTime` 的日期</span><span class="sxs-lookup"><span data-stu-id="38929-201">Dates to `DateTime`</span></span>
* <span data-ttu-id="38929-202">要 `string` 的字串</span><span class="sxs-lookup"><span data-stu-id="38929-202">Strings to `string`</span></span>
* <span data-ttu-id="38929-203">`JsonElement` 的其他專案</span><span class="sxs-lookup"><span data-stu-id="38929-203">Everything else to `JsonElement`</span></span>

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

<span data-ttu-id="38929-204">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-204">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

<span data-ttu-id="38929-205">以下是具有物件屬性的範例型別：</span><span class="sxs-lookup"><span data-stu-id="38929-205">Here's an example type with an Object property:</span></span>

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

<span data-ttu-id="38929-206">下列要還原序列化的 JSON 範例包含將還原序列化為 `DateTime`、`long`和 `string`的值：</span><span class="sxs-lookup"><span data-stu-id="38929-206">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="38929-207">如果沒有自訂轉換器，還原序列化會將 `JsonElement` 放入每個屬性中。</span><span class="sxs-lookup"><span data-stu-id="38929-207">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="38929-208">`System.Text.Json.Serialization` 命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)，有更多範例可處理還原序列化為物件屬性的自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-208">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="38929-209">支援具有非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="38929-209">Support Dictionary with non-string key</span></span>

<span data-ttu-id="38929-210">字典集合的內建支援適用于 `Dictionary<string, TValue>`。</span><span class="sxs-lookup"><span data-stu-id="38929-210">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="38929-211">也就是，索引鍵必須是字串。</span><span class="sxs-lookup"><span data-stu-id="38929-211">That is, the key must be a string.</span></span> <span data-ttu-id="38929-212">若要支援具有整數或其他類型做為索引鍵的字典，則需要自訂轉換子。</span><span class="sxs-lookup"><span data-stu-id="38929-212">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="38929-213">下列程式碼顯示可搭配 `Dictionary<Enum,TValue>`使用的自訂轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-213">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="38929-214">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-214">The following code registers the converter:</span></span>

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

<span data-ttu-id="38929-215">轉換器可以序列化和還原序列化下列類別中使用下列 `Enum`的 `TemperatureRanges` 屬性：</span><span class="sxs-lookup"><span data-stu-id="38929-215">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

<span data-ttu-id="38929-216">序列化的 JSON 輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="38929-216">The JSON output from serialization looks like the following example:</span></span>

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="38929-217">`System.Text.Json.Serialization` 命名空間中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)，有更多可處理非字串索引鍵字典的自訂轉換器範例。</span><span class="sxs-lookup"><span data-stu-id="38929-217">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="38929-218">支援多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="38929-218">Support polymorphic deserialization</span></span>

<span data-ttu-id="38929-219">多型[序列化](system-text-json-how-to.md#serialize-properties-of-derived-classes)不需要自訂轉換器，但是還原序列化的確需要自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-219">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="38929-220">例如，假設您有一個 `Person` 的抽象基類，`Employee` 和 `Customer` 衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="38929-220">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="38929-221">多型還原序列化表示在設計階段，您可以指定 `Person` 做為還原序列化目標，而且 JSON 中的 `Customer` 和 `Employee` 物件會在執行時間正確地還原序列化。</span><span class="sxs-lookup"><span data-stu-id="38929-221">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="38929-222">在還原序列化期間，您必須尋找識別 JSON 中所需類型的線索。</span><span class="sxs-lookup"><span data-stu-id="38929-222">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="38929-223">可用的線索種類會因每個案例而異。</span><span class="sxs-lookup"><span data-stu-id="38929-223">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="38929-224">例如，鑒別子屬性可能可供使用，或者您可能必須依賴特定屬性的存在與否。</span><span class="sxs-lookup"><span data-stu-id="38929-224">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="38929-225">目前的 `System.Text.Json` 版本並未提供屬性來指定如何處理多型還原序列化案例，因此需要自訂轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-225">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="38929-226">下列程式碼顯示基類、兩個衍生類別和自訂的轉換器。</span><span class="sxs-lookup"><span data-stu-id="38929-226">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="38929-227">轉換器會使用鑒別子屬性來執行多型還原序列化。</span><span class="sxs-lookup"><span data-stu-id="38929-227">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="38929-228">類型鑒別子不在類別定義中，而是在序列化期間建立，並且會在還原序列化期間讀取。</span><span class="sxs-lookup"><span data-stu-id="38929-228">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

<span data-ttu-id="38929-229">下列程式碼會註冊轉換器：</span><span class="sxs-lookup"><span data-stu-id="38929-229">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

<span data-ttu-id="38929-230">轉換器可以還原序列化使用相同的轉換子所建立的 JSON，例如：</span><span class="sxs-lookup"><span data-stu-id="38929-230">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

## <a name="other-custom-converter-samples"></a><span data-ttu-id="38929-231">其他自訂轉換器範例</span><span class="sxs-lookup"><span data-stu-id="38929-231">Other custom converter samples</span></span>

<span data-ttu-id="38929-232">`System.Text.Json.Serialization` 原始程式碼中的 [[單元測試] 資料夾](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)包含其他自訂轉換器範例，例如：</span><span class="sxs-lookup"><span data-stu-id="38929-232">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="38929-233">在還原序列化時，將 null 轉換為0的 `Int32` 轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-233">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="38929-234">在還原序列化時允許字串和數值的 `Int32` 轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-234">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="38929-235">`Enum` 轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-235">`Enum` converter</span></span>
* <span data-ttu-id="38929-236">接受外部資料的 `List<T>` 轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-236">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="38929-237">可搭配以逗號分隔的數位清單使用的 `Long[]` 轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-237">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="38929-238">其他資源</span><span class="sxs-lookup"><span data-stu-id="38929-238">Additional resources</span></span>

* [<span data-ttu-id="38929-239">System.web. Text. Json 總覽</span><span class="sxs-lookup"><span data-stu-id="38929-239">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="38929-240">System.web API 參考</span><span class="sxs-lookup"><span data-stu-id="38929-240">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="38929-241">如何使用 System.object</span><span class="sxs-lookup"><span data-stu-id="38929-241">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="38929-242">內建轉換器的原始程式碼</span><span class="sxs-lookup"><span data-stu-id="38929-242">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="38929-243">`System.Text.Json` 自訂轉換器的相關 GitHub 問題</span><span class="sxs-lookup"><span data-stu-id="38929-243">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="38929-244">36639引進自訂轉換器</span><span class="sxs-lookup"><span data-stu-id="38929-244">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="38929-245">38713關於還原序列化為物件</span><span class="sxs-lookup"><span data-stu-id="38929-245">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="38929-246">40120有關非字串索引鍵的字典</span><span class="sxs-lookup"><span data-stu-id="38929-246">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="38929-247">37787關於多型還原序列化</span><span class="sxs-lookup"><span data-stu-id="38929-247">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
