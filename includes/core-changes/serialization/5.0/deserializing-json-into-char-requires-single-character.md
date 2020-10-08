---
ms.openlocfilehash: 8209c5336983bde13a698fbc68e6a099091071f7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844498"
---
### <a name="jsonserializerdeserialize-requires-single-character-string"></a><span data-ttu-id="236b5-101">JsonSerializer。還原序列化需要單一字元字串</span><span class="sxs-lookup"><span data-stu-id="236b5-101">JsonSerializer.Deserialize requires single-character string</span></span>

<span data-ttu-id="236b5-102">當型別參數是時 <xref:System.Char> ，的字串引數 <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> 必須包含單一字元才能成功還原序列化。</span><span class="sxs-lookup"><span data-stu-id="236b5-102">When the type parameter is <xref:System.Char>, the string argument to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> must contain a single character for deserialization to succeed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="236b5-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="236b5-103">Change description</span></span>

<span data-ttu-id="236b5-104">在先前的 .NET 版本中，如果您將多個字元的字串傳遞至 <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> ，且類型參數是，則還原序列化會 <xref:System.Char> 成功，而且只會還原序列化第一個字元。</span><span class="sxs-lookup"><span data-stu-id="236b5-104">In previous .NET versions, if you pass a multi-character string to <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> and the type parameter is <xref:System.Char>, the deserialization succeeds and only the first character is deserialized.</span></span>

<span data-ttu-id="236b5-105">在 .NET 5.0 和更新版本中，當型別參數是時 <xref:System.Char> ，傳遞單一字元字串以外的任何字元都會導致擲回 <xref:System.Text.Json.JsonException> 。</span><span class="sxs-lookup"><span data-stu-id="236b5-105">In .NET 5.0 and later, when the type parameter is <xref:System.Char>, passing anything other than a single-character string causes a <xref:System.Text.Json.JsonException> to be thrown.</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first character 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one character.
JsonSerializer.Deserialize<char>("\"abc\"");

// Correct usage.
JsonSerializer.Deserialize<char>("\"a\"");
```

#### <a name="version-introduced"></a><span data-ttu-id="236b5-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="236b5-106">Version introduced</span></span>

<span data-ttu-id="236b5-107">5.0</span><span class="sxs-lookup"><span data-stu-id="236b5-107">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="236b5-108">變更的原因</span><span class="sxs-lookup"><span data-stu-id="236b5-108">Reason for change</span></span>

<span data-ttu-id="236b5-109"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> 將表示單一 JSON 值的文字，剖析成泛型型別參數所指定之類型的實例。</span><span class="sxs-lookup"><span data-stu-id="236b5-109"><xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> parses text that represents a single JSON value into an instance of the type specified by the generic type parameter.</span></span> <span data-ttu-id="236b5-110">只有當提供的裝載對指定的泛型型別參數有效時，才會成功剖析。</span><span class="sxs-lookup"><span data-stu-id="236b5-110">Parsing should only succeed when the provided payload is valid for the specified generic type parameter.</span></span> <span data-ttu-id="236b5-111">對於實 <xref:System.Char> 值型別而言，有效承載是單一字元字串。</span><span class="sxs-lookup"><span data-stu-id="236b5-111">For a <xref:System.Char> value type, a valid payload is a single character string.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="236b5-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="236b5-112">Recommended action</span></span>

<span data-ttu-id="236b5-113">使用將字串剖析為 <xref:System.Char> 型別時 <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> ，請確定字串是由單一字元所組成。</span><span class="sxs-lookup"><span data-stu-id="236b5-113">When parsing a string into a <xref:System.Char> type using <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType>, make sure the string consists of a single character.</span></span>

#### <a name="category"></a><span data-ttu-id="236b5-114">類別</span><span class="sxs-lookup"><span data-stu-id="236b5-114">Category</span></span>

<span data-ttu-id="236b5-115">序列化</span><span class="sxs-lookup"><span data-stu-id="236b5-115">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="236b5-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="236b5-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%60%601(System.String,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Text.Json.JsonSerializer.Deserialize``1(System.String,System.Text.Json.JsonSerializerOptions)`

-->
