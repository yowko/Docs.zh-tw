---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021572"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a><span data-ttu-id="e5e07-101">Json 序列化器異常`JsonException`類型 從變更為`NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="e5e07-101">Json serializer exception type changed from `JsonException` to `NotSupportedException`</span></span>

<span data-ttu-id="e5e07-102">在 .NET Core 3.0 預<xref:System.Text.Json.JsonException>覽 6 到 8 中,當序列化器遇到不支援的衍生集合類型時,將引發 。</span><span class="sxs-lookup"><span data-stu-id="e5e07-102">In .NET Core 3.0 Preview 6 through 8, the serializer would throw a <xref:System.Text.Json.JsonException> when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="e5e07-103">從 .NET 核心 3.0<xref:System.NotSupportedException>預覽 9 開始 ,序列化器將拋出一個。</span><span class="sxs-lookup"><span data-stu-id="e5e07-103">Starting in .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> instead.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e5e07-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="e5e07-104">Change description</span></span>

<span data-ttu-id="e5e07-105">在 .NET Core 3.0 預覽<xref:System.Text.Json.JsonException>6 到預覽 8 中,當序列化器遇到不支援的派生集合類型時,將引發 。</span><span class="sxs-lookup"><span data-stu-id="e5e07-105">In .NET Core 3.0 Preview 6 through Preview 8, the serializer would throw a <xref:System.Text.Json.JsonException>  when it encountered an unsupported derived collection type.</span></span> <span data-ttu-id="e5e07-106">*不支援的衍生型態*是不能配置給以下類型之一的任何集合類型:</span><span class="sxs-lookup"><span data-stu-id="e5e07-106">An *unsupported derived collection type* is any collection type that isn't assignable to one of the following types:</span></span>

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [<span data-ttu-id="e5e07-107">I字典\<字串,T></span><span class="sxs-lookup"><span data-stu-id="e5e07-107">IDictionary\<String,T></span></span>](xref:System.Collections.Generic.IDictionary%602)

<span data-ttu-id="e5e07-108">從 .NET Core 3.0<xref:System.NotSupportedException>預覽 9 開始 ,序列化程式將引發遇到不受支援的集合類型時。</span><span class="sxs-lookup"><span data-stu-id="e5e07-108">Starting with .NET Core 3.0 Preview 9, the serializer throws a <xref:System.NotSupportedException> When encountering an unsupported collection type.</span></span> <span data-ttu-id="e5e07-109">新的異常類型更好地反映了反序列化操作失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="e5e07-109">The new exception type better reflects why the deserialization operation is failing.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e5e07-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="e5e07-110">Version introduced</span></span>

<span data-ttu-id="e5e07-111">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="e5e07-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e5e07-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e5e07-112">Recommended action</span></span>

<span data-ttu-id="e5e07-113">如果在反序列化時<xref:System.Text.Json.JsonException>正在捕捉,則可能需要考慮捕捉<xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="e5e07-113">If you're catching <xref:System.Text.Json.JsonException> when deserializing, you might want to consider also catching <xref:System.NotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="e5e07-114">類別</span><span class="sxs-lookup"><span data-stu-id="e5e07-114">Category</span></span>

<span data-ttu-id="e5e07-115">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="e5e07-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5e07-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e5e07-116">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
