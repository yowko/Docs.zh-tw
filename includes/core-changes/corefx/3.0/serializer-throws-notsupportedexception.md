---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568143"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="0e91b-101">Json 序列化程式例外狀況類型已從 `JsonException` 變更為 `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="0e91b-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="0e91b-102">在 .NET Core 3.0 Preview 6 到8中，當序列化程式遇到不受支援的衍生集合類型時，會擲回 <xref:System.Text.Json.JsonException>。</span><span class="sxs-lookup"><span data-stu-id="0e91b-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="0e91b-103">從 .NET Core 3.0 Preview 9 開始，序列化程式會改為擲回 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="0e91b-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0e91b-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="0e91b-104">Change description</span></span>

<span data-ttu-id="0e91b-105">在 .NET Core 3.0 Preview 6 到 Preview 8 中，當序列化程式遇到不受支援的衍生集合類型時，會擲回 <xref:System.Text.Json.JsonException>。</span><span class="sxs-lookup"><span data-stu-id="0e91b-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="0e91b-106">不*支援的衍生集合類型*是無法指派給下列其中一種類型的任何集合類型：</span><span class="sxs-lookup"><span data-stu-id="0e91b-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="0e91b-107">IDictionary\<字串，T ></span><span class="sxs-lookup"><span data-stu-id="0e91b-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="0e91b-108">從 .NET Core 3.0 Preview 9 開始，當遇到不支援的集合類型時，序列化程式會擲回 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="0e91b-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="0e91b-109">新的例外狀況類型更清楚地反映了還原序列化作業失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="0e91b-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0e91b-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0e91b-110">Version introduced</span></span>

<span data-ttu-id="0e91b-111">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="0e91b-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0e91b-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0e91b-112">Recommended action</span></span>

<span data-ttu-id="0e91b-113">如果您要在還原序列化時攔截 <xref:System.Text.Json.JsonException>，您可能會想要考慮同時捕捉 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="0e91b-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="0e91b-114">Category</span><span class="sxs-lookup"><span data-stu-id="0e91b-114">Category</span></span>

<span data-ttu-id="0e91b-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="0e91b-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0e91b-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0e91b-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
