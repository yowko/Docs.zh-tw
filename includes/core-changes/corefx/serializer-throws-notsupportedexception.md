---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119279"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="65289-101">Json 序列化程式例外狀況類型`JsonException`已從變更為`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="65289-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="65289-102">在 .net Core 3.0 Preview 6 到8中， <xref:System.Text.Json.JsonException>當序列化程式遇到不受支援的衍生集合類型時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="65289-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="65289-103">從 .net Core 3.0 Preview 9 開始，序列化程式會擲<xref:System.NotSupportedException>回，改為擲回。</span><span class="sxs-lookup"><span data-stu-id="65289-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="65289-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="65289-104">Change description</span></span>

<span data-ttu-id="65289-105">在 .net Core 3.0 preview 6 到 preview 8 中， <xref:System.Text.Json.JsonException>當序列化程式遇到不受支援的衍生集合類型時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="65289-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="65289-106">不*支援的衍生集合類型*是無法指派給下列其中一種類型的任何集合類型：</span><span class="sxs-lookup"><span data-stu-id="65289-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

 - <xref:System.Collections.IList>
 - <xref:System.Collections.Generic.ICollection%601>
 - <xref:System.Collections.Generic.Stack%601>
 - <xref:System.Collections.Generic.Queue%601>`
 - <xref:System.Collections.IDictionary>
 - [<span data-ttu-id="65289-107">IDictionary\<字串，T ></span><span class="sxs-lookup"><span data-stu-id="65289-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="65289-108">從 .net Core 3.0 Preview 9 開始， <xref:System.NotSupportedException>當遇到不支援的集合類型時，序列化程式會擲回。</span><span class="sxs-lookup"><span data-stu-id="65289-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="65289-109">新的例外狀況類型更清楚地反映了還原序列化作業失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="65289-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="65289-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="65289-110">Version introduced</span></span>

<span data-ttu-id="65289-111">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="65289-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="65289-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="65289-112">Recommended action</span></span>

<span data-ttu-id="65289-113">如果您<xref:System.Text.Json.JsonException>在還原序列化時攔截到，您可能會想要<xref:System.NotSupportedException>考慮也要攔截。</span><span class="sxs-lookup"><span data-stu-id="65289-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="65289-114">分類</span><span class="sxs-lookup"><span data-stu-id="65289-114">Category</span></span>

<span data-ttu-id="65289-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="65289-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="65289-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="65289-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
