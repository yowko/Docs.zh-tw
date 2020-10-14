---
ms.openlocfilehash: 07980cf94d5de0173808da2ce44adb409fdd5419
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050455"
---
### <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a><span data-ttu-id="d0a5a-101">序列化和還原序列化機碼值組時，會接受 PropertyNamingPolicy、PropertyNameCaseInsensitive 和編碼器選項</span><span class="sxs-lookup"><span data-stu-id="d0a5a-101">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>

<span data-ttu-id="d0a5a-102"><xref:System.Text.Json.JsonSerializer> 現在會在 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 序列化 <xref:System.Text.Json.JsonSerializerOptions.Encoder> <xref:System.Collections.Generic.KeyValuePair%602.Key> 實例的和屬性名稱時，接受和選項 <xref:System.Collections.Generic.KeyValuePair%602.Value> <xref:System.Collections.Generic.KeyValuePair%602> 。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-102"><xref:System.Text.Json.JsonSerializer> now honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options when serializing the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names of a <xref:System.Collections.Generic.KeyValuePair%602> instance.</span></span> <span data-ttu-id="d0a5a-103">此外， <xref:System.Text.Json.JsonSerializer> 將實例還原序列化時，會接受 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 和 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> 選項 <xref:System.Collections.Generic.KeyValuePair%602> 。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-103">Additionally, <xref:System.Text.Json.JsonSerializer> honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options when deserializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d0a5a-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="d0a5a-104">Change description</span></span>

##### <a name="serialization"></a><span data-ttu-id="d0a5a-105">序列化</span><span class="sxs-lookup"><span data-stu-id="d0a5a-105">Serialization</span></span>

<span data-ttu-id="d0a5a-106">在 .NET Core 3.x 版和 [ NuGet 套件上System.Text.Js](https://www.nuget.org/packages/System.Text.Json)的 4.6.0-4.7.2 版本中，實例的屬性 <xref:System.Collections.Generic.KeyValuePair%602> 一律會正確序列化為 "Key" 和 "Value"，不論任何 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> 和 <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> 選項為何。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-106">In .NET Core 3.x versions and in the 4.6.0-4.7.2 versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), the properties of <xref:System.Collections.Generic.KeyValuePair%602> instances are always serialized as "Key" and "Value" exactly, regardless of any <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> and <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="d0a5a-107">下列程式碼範例會示範在 <xref:System.Collections.Generic.KeyValuePair%602.Key> 序列化之後，和屬性如何以 <xref:System.Collections.Generic.KeyValuePair%602.Value> camel 大小寫為大寫，即使指定的屬性命名原則表示如此。 *not*</span><span class="sxs-lookup"><span data-stu-id="d0a5a-107">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are *not* camel-cased after serialization, even though the specified property-naming policy dictates so.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

<span data-ttu-id="d0a5a-108">從 .NET 5.0 開始， <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 當序列化 <xref:System.Text.Json.JsonSerializerOptions.Encoder> 實例時，會接受和選項 <xref:System.Collections.Generic.KeyValuePair%602> 。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-108">Starting in .NET 5.0, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are honored when serializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span> <span data-ttu-id="d0a5a-109">下列程式碼範例示範如何 <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> 根據指定的屬性命名原則，在序列化之後，和屬性是以 camel 法為大寫。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-109">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are camel-cased after serialization, in accordance with the specified property-naming policy.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

##### <a name="deserialization"></a><span data-ttu-id="d0a5a-110">還原序列化</span><span class="sxs-lookup"><span data-stu-id="d0a5a-110">Deserialization</span></span>

<span data-ttu-id="d0a5a-111">在 .NET Core 3.x 版中，以及在 [ NuGet 套件](https://www.nuget.org/packages/System.Text.Json)的 4.7. x 版System.Text.Js中， <xref:System.Text.Json.JsonException> 如果 JSON 屬性名稱不是精確的，則會擲回 `Key` ， `Value` 例如，如果不是以大寫字母開頭，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-111">In .NET Core 3.x versions and in the 4.7.x versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), a <xref:System.Text.Json.JsonException> is thrown when the JSON property names are not precisely `Key` and `Value`, for example, if they don't start with an uppercase letter.</span></span> <span data-ttu-id="d0a5a-112">即使指定的屬性命名原則明確允許，也會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-112">The exception is thrown even if a specified property-naming policy expressly permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

<span data-ttu-id="d0a5a-113">從 .NET 5.0 開始， <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 使用還原 <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> 序列化時，會接受和選項 <xref:System.Text.Json.JsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-113">Starting in .NET 5.0, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options are honored when deserializing using <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="d0a5a-114">例如，下列程式碼片段會顯示成功的小寫 <xref:System.Collections.Generic.KeyValuePair%602.Key> 和屬性名稱還原序列化， <xref:System.Collections.Generic.KeyValuePair%602.Value> 因為指定的屬性命名原則允許它。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-114">For example, the following code snippet shows successful deserialization of lowercased <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names because the specified property-naming policy permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

<span data-ttu-id="d0a5a-115">為了容納使用先前版本序列化的承載，在還原序列化時，"Key" 和 "Value" 會符合特殊大小寫。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-115">To accommodate payloads that were serialized with previous versions, "Key" and "Value" are special-cased to match when deserializing.</span></span> <span data-ttu-id="d0a5a-116">即使 <xref:System.Collections.Generic.KeyValuePair%602.Key> 和 <xref:System.Collections.Generic.KeyValuePair%602.Value> 屬性名稱不會根據下列程式碼範例中的 in <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 選項，也會成功還原序列化。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-116">Even though the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names aren't camel-cased according to the in <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> option in the following code example, they deserialize successfully.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

#### <a name="version-introduced"></a><span data-ttu-id="d0a5a-117">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d0a5a-117">Version introduced</span></span>

<span data-ttu-id="d0a5a-118">5.0</span><span class="sxs-lookup"><span data-stu-id="d0a5a-118">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d0a5a-119">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d0a5a-119">Reason for change</span></span>

<span data-ttu-id="d0a5a-120">大量的客戶意見反應指出 <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> 應接受。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-120">Substantial customer feedback indicated that the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> should be honored.</span></span> <span data-ttu-id="d0a5a-121">為求完整性， <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> <xref:System.Text.Json.JsonSerializerOptions.Encoder> 也會採用和選項，如此一來，就 <xref:System.Collections.Generic.KeyValuePair%602> 會將實例視為與任何其他單純的 CLR 物件相同， (POCO) 。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-121">For completeness, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are also honored, so that <xref:System.Collections.Generic.KeyValuePair%602> instances are treated the same as any other plain old CLR object (POCO).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d0a5a-122">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d0a5a-122">Recommended action</span></span>

<span data-ttu-id="d0a5a-123">如果這項變更干擾您，您可以使用 [自訂轉換器](../../../../docs/standard/serialization/system-text-json-converters-how-to.md) 來執行所需的語法。</span><span class="sxs-lookup"><span data-stu-id="d0a5a-123">If this change is disruptive to you, you can use a [custom converter](../../../../docs/standard/serialization/system-text-json-converters-how-to.md) that implements the desired semantics.</span></span>

#### <a name="category"></a><span data-ttu-id="d0a5a-124">類別</span><span class="sxs-lookup"><span data-stu-id="d0a5a-124">Category</span></span>

<span data-ttu-id="d0a5a-125">序列化</span><span class="sxs-lookup"><span data-stu-id="d0a5a-125">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d0a5a-126">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d0a5a-126">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Serialize`
- `Overload:System.Text.Json.JsonSerializer.SerializeAsync`
- `Overload:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes`
- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
