---
title: 中斷性變更：當類型參數為 null 時，序列化擲回例外狀況
description: 瞭解 .NET 5.0 中的重大變更，其中具有類型參數的 JsonSerialize 序列化方法現在會在傳遞該參數的 null 時擲回例外狀況。
ms.date: 10/18/2020
ms.openlocfilehash: af2885394418072ad7efec5855490b5b80152fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760759"
---
# <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a><span data-ttu-id="167d1-103">JsonSerializer。當型別參數為 null 時，序列化會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="167d1-103">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>

<span data-ttu-id="167d1-104"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType><xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> 具有類型之參數的、和多載， <xref:System.Type> 現在會在 <xref:System.ArgumentNullException> 每次 `null` 傳遞該參數時擲回。</span><span class="sxs-lookup"><span data-stu-id="167d1-104"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> overloads that have a parameter of type <xref:System.Type> now throw an <xref:System.ArgumentNullException> whenever `null` is passed for that parameter.</span></span>

## <a name="change-description"></a><span data-ttu-id="167d1-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="167d1-105">Change description</span></span>

<span data-ttu-id="167d1-106">在 .NET Core 3.1 中， <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> 具有參數的、和多載 <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> 會在 <xref:System.Type> <xref:System.ArgumentNullException> 傳遞給參數時擲回， `null` `Type inputType` 但是如果 `Object value` 參數也不是 `null` ，則不會擲回。</span><span class="sxs-lookup"><span data-stu-id="167d1-106">In .NET Core 3.1, the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter throw an <xref:System.ArgumentNullException> when `null` is passed for the `Type inputType` parameter, but not if the `Object value` parameter is also `null`.</span></span> <span data-ttu-id="167d1-107">從 .NET 5.0 開始， *always* <xref:System.ArgumentNullException> 當 `null` 針對參數傳遞時，這些方法一律會擲回 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="167d1-107">Starting in .NET 5.0, these methods *always* throw an <xref:System.ArgumentNullException> when `null` is passed for the <xref:System.Type> parameter.</span></span>

<span data-ttu-id="167d1-108">.NET Core 3.1 中的行為：</span><span class="sxs-lookup"><span data-stu-id="167d1-108">Behavior in .NET Core 3.1:</span></span>

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

<span data-ttu-id="167d1-109">.NET 5.0 和更新版本中的行為：</span><span class="sxs-lookup"><span data-stu-id="167d1-109">Behavior in .NET 5.0 and later:</span></span>

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

## <a name="version-introduced"></a><span data-ttu-id="167d1-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="167d1-110">Version introduced</span></span>

<span data-ttu-id="167d1-111">5.0</span><span class="sxs-lookup"><span data-stu-id="167d1-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="167d1-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="167d1-112">Reason for change</span></span>

<span data-ttu-id="167d1-113">傳入 `null` `Type inputType` 參數是無法接受的，而且一律會擲回 <xref:System.ArgumentNullException> 。</span><span class="sxs-lookup"><span data-stu-id="167d1-113">Passing in `null` for the `Type inputType` parameter is unacceptable and should always throw an <xref:System.ArgumentNullException>.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="167d1-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="167d1-114">Recommended action</span></span>

<span data-ttu-id="167d1-115">請確定您未傳遞 `null` `Type inputType` 這些方法的參數。</span><span class="sxs-lookup"><span data-stu-id="167d1-115">Make sure that you are not passing `null` for the `Type inputType` parameter of these methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="167d1-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="167d1-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
