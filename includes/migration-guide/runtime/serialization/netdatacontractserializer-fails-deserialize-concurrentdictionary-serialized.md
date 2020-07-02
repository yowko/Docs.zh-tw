---
ms.openlocfilehash: eef5633ec8566f6d5216b7dca4387766cacb600d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620061"
---
### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a><span data-ttu-id="2df6d-101">NetDataContractSerializer 無法將使用不同 .NET 版本序列化的 ConcurrentDictionary 還原序列化</span><span class="sxs-lookup"><span data-stu-id="2df6d-101">NetDataContractSerializer fails to deserialize a ConcurrentDictionary serialized with a different .NET version</span></span>

#### <a name="details"></a><span data-ttu-id="2df6d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2df6d-102">Details</span></span>

<span data-ttu-id="2df6d-103">根據設計，只有當序列化和還原序列化兩端共用相同的 CLR 類型時，才能使用 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="2df6d-103">By design, the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="2df6d-104">因此，不保證使用其中一個 .NET Framework 版本序列化的物件可以透過不同版本還原序列化。<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2df6d-104">Therefore, it is not guaranteed that an object serialized with one version of the .NET Framework can be deserialized by a different version.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName></span></span> <span data-ttu-id="2df6d-105">是使用 .NET Framework 4.5 或舊版序列化並使用 .NET Framework 4.5.1 或更新版本還原序列化時，無法正確還原序列化的已知類型。</span><span class="sxs-lookup"><span data-stu-id="2df6d-105">is a type that is known to not to deserialize correctly if serialized with the .NET Framework 4.5 or earlier and deserialized with the .NET Framework 4.5.1 or later.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2df6d-106">建議</span><span class="sxs-lookup"><span data-stu-id="2df6d-106">Suggestion</span></span>

<span data-ttu-id="2df6d-107">此問題有許多可能的因應措施：</span><span class="sxs-lookup"><span data-stu-id="2df6d-107">There are a number of possible work-arounds for this issue:</span></span><ul><li><span data-ttu-id="2df6d-108">另升級序列化電腦以使用 .NET Framework 4.5.1。</span><span class="sxs-lookup"><span data-stu-id="2df6d-108">Upgrade the serializing computer to use the .NET Framework 4.5.1, as well.</span></span></li><li><span data-ttu-id="2df6d-109">使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> 而不是 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>，因為這不會預期在序列化和還原序列化的兩端具有完全相同的 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="2df6d-109">Use <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> instead of <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> as this does not expect the exact same CLR types at both serializing and deserializing ends.</span></span></li><li><span data-ttu-id="2df6d-110">使用 <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> 而不是 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>，因為它不會呈現這種特定的 4.5-&gt;4.5.1 中斷。</span><span class="sxs-lookup"><span data-stu-id="2df6d-110">Use <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> instead of <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> since it does not exhibit this particular 4.5-&gt;4.5.1 break.</span></span></li></ul>

| <span data-ttu-id="2df6d-111">名稱</span><span class="sxs-lookup"><span data-stu-id="2df6d-111">Name</span></span>    | <span data-ttu-id="2df6d-112">值</span><span class="sxs-lookup"><span data-stu-id="2df6d-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2df6d-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="2df6d-113">Scope</span></span>   |<span data-ttu-id="2df6d-114">Minor</span><span class="sxs-lookup"><span data-stu-id="2df6d-114">Minor</span></span>|
|<span data-ttu-id="2df6d-115">版本</span><span class="sxs-lookup"><span data-stu-id="2df6d-115">Version</span></span>|<span data-ttu-id="2df6d-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="2df6d-116">4.5.1</span></span>|
|<span data-ttu-id="2df6d-117">類型</span><span class="sxs-lookup"><span data-stu-id="2df6d-117">Type</span></span>|<span data-ttu-id="2df6d-118">執行階段</span><span class="sxs-lookup"><span data-stu-id="2df6d-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2df6d-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2df6d-119">Affected APIs</span></span>

-<xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|
