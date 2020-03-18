---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568143"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="f2d1c-101">Json 序列化器異常類型`JsonException`從 更改為`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="f2d1c-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="f2d1c-102">在 .NET Core 3.0 預覽 6 到 8<xref:System.Text.Json.JsonException>中，當序列化器遇到不支援的派生集合類型時，將引發 。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="f2d1c-103">從 .NET 核心 3.0 預覽 9 開始<xref:System.NotSupportedException>，序列化器將拋出一個。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f2d1c-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="f2d1c-104">Change description</span></span>

<span data-ttu-id="f2d1c-105">在 .NET Core 3.0 預覽 6 到預覽 8<xref:System.Text.Json.JsonException>中，當序列化器遇到不支援的派生集合類型時，將引發 。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="f2d1c-106">*不支援的派生集合類型*是不能分配給以下類型之一的任何集合類型：</span><span class="sxs-lookup"><span data-stu-id="f2d1c-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="f2d1c-107">I字典\<字串，T></span><span class="sxs-lookup"><span data-stu-id="f2d1c-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="f2d1c-108">從 .NET Core 3.0 預覽 9 開始<xref:System.NotSupportedException>，序列化程式將引發遇到不受支援的集合類型時。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="f2d1c-109">新的異常類型更好地反映了反序列化操作失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f2d1c-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="f2d1c-110">Version introduced</span></span>

<span data-ttu-id="f2d1c-111">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="f2d1c-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f2d1c-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f2d1c-112">Recommended action</span></span>

<span data-ttu-id="f2d1c-113">如果在反序列化時<xref:System.Text.Json.JsonException>正在捕獲，則可能需要考慮捕獲<xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="f2d1c-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="f2d1c-114">類別</span><span class="sxs-lookup"><span data-stu-id="f2d1c-114">Category</span></span>

<span data-ttu-id="f2d1c-115">CoreFx</span><span class="sxs-lookup"><span data-stu-id="f2d1c-115">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f2d1c-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f2d1c-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
