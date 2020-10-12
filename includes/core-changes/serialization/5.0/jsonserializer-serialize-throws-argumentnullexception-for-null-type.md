---
ms.openlocfilehash: 5b49dcae45e44bfd9ec3e150ad25c3f21d62c18e
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955329"
---
### <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a><span data-ttu-id="44462-101">JsonSerializer。當型別參數為 null 時，序列化會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="44462-101">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>

<span data-ttu-id="44462-102"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>具有參數的、和多載， <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> <xref:System.Type> 現在會在 <xref:System.ArgumentNullException> 每次 `null` 傳遞參數時擲回 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="44462-102"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter now throw an <xref:System.ArgumentNullException> whenever `null` is passed for the <xref:System.Type> parameter.</span></span>

#### <a name="change-description"></a><span data-ttu-id="44462-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="44462-103">Change description</span></span>

<span data-ttu-id="44462-104">在 .NET Core 3.1 中， <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 具有參數的、和多載 <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> 會在 <xref:System.Type> <xref:System.ArgumentNullException> 傳遞給參數時擲回， `null` `Type inputType` 但是如果 `Object value` 參數也不是 `null` ，則不會擲回。</span><span class="sxs-lookup"><span data-stu-id="44462-104">In .NET Core 3.1, the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter throw an <xref:System.ArgumentNullException> when `null` is passed for the `Type inputType` parameter, but not if the `Object value` parameter is also `null`.</span></span> <span data-ttu-id="44462-105">從 .NET 5.0 開始， *always* <xref:System.ArgumentNullException> 當 `null` 針對參數傳遞時，這些方法一律會擲回 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="44462-105">Starting in .NET 5.0, these methods *always* throw an <xref:System.ArgumentNullException> when `null` is passed for the <xref:System.Type> parameter.</span></span>

<span data-ttu-id="44462-106">.NET Core 3.1 中的行為：</span><span class="sxs-lookup"><span data-stu-id="44462-106">Behavior in .NET Core 3.1:</span></span>

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

<span data-ttu-id="44462-107">.NET 5.0 和更新版本中的行為：</span><span class="sxs-lookup"><span data-stu-id="44462-107">Behavior in .NET 5.0 and later:</span></span>

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

#### <a name="version-introduced"></a><span data-ttu-id="44462-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="44462-108">Version introduced</span></span>

<span data-ttu-id="44462-109">5.0</span><span class="sxs-lookup"><span data-stu-id="44462-109">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="44462-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="44462-110">Reason for change</span></span>

<span data-ttu-id="44462-111">傳入 `null` `Type inputType` 參數是無法接受的，而且一律會擲回 <xref:System.ArgumentNullException> 。</span><span class="sxs-lookup"><span data-stu-id="44462-111">Passing in `null` for the `Type inputType` parameter is unacceptable and should always throw an <xref:System.ArgumentNullException>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="44462-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="44462-112">Recommended action</span></span>

<span data-ttu-id="44462-113">請確定您未傳遞 `null` `Type inputType` 這些方法的參數。</span><span class="sxs-lookup"><span data-stu-id="44462-113">Make sure that you are not passing `null` for the `Type inputType` parameter of these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="44462-114">類別</span><span class="sxs-lookup"><span data-stu-id="44462-114">Category</span></span>

<span data-ttu-id="44462-115">序列化</span><span class="sxs-lookup"><span data-stu-id="44462-115">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="44462-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="44462-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

-->
