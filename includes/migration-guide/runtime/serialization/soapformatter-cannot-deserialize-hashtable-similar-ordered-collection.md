---
ms.openlocfilehash: 5a3370e71488e4f9d8d933b504d1d771c78e0385
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620060"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a><span data-ttu-id="d65fc-101">SoapFormatter 無法將 Hashtable 和類似的已排序集合物件還原序列化</span><span class="sxs-lookup"><span data-stu-id="d65fc-101">SoapFormatter cannot deserialize Hashtable and similar ordered collection objects</span></span>

#### <a name="details"></a><span data-ttu-id="d65fc-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d65fc-102">Details</span></span>

<span data-ttu-id="d65fc-103"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> 不保證以某個 .NET Framework 版本序列化的物件，可成功以另一個版本還原序列化。</span><span class="sxs-lookup"><span data-stu-id="d65fc-103">The <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> does not guarantee that objects serialized under one .NET Framework version will successfully deserialize under a different version.</span></span> <span data-ttu-id="d65fc-104">具體來說，某些已排序的集合 (例如 <xref:System.Collections.Hashtable?displayProperty=fullName>) 在 4.0 和 4.5 之間新增成員；如果這些類型的物件以 .NET Framework 4.5 序列化，就無法以 .NET Framework 4.0 還原序列化。</span><span class="sxs-lookup"><span data-stu-id="d65fc-104">Specifically, some ordered collections (like <xref:System.Collections.Hashtable?displayProperty=fullName>) added members between 4.0 and 4.5 such that objects of these types cannot deserialize with .NET Framework 4.0 if they were serialized with .NET Framework 4.5.</span></span> <span data-ttu-id="d65fc-105">請注意，如果序列化資料以相同的 .NET Framework 版本序列化和還原序列化，就不會發生任何問題。</span><span class="sxs-lookup"><span data-stu-id="d65fc-105">Note that if the serialized data is both serialized and deserialized with the same .NET Framework version, no issue will occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d65fc-106">建議</span><span class="sxs-lookup"><span data-stu-id="d65fc-106">Suggestion</span></span>

<span data-ttu-id="d65fc-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> 應該取代為 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> 序列化或 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> 應該彈性處理 .NET Framework 變更。</span><span class="sxs-lookup"><span data-stu-id="d65fc-107"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> serialization should be replaced with <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serialization or <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> to be resilient to .NET Framework changes.</span></span>

| <span data-ttu-id="d65fc-108">名稱</span><span class="sxs-lookup"><span data-stu-id="d65fc-108">Name</span></span>    | <span data-ttu-id="d65fc-109">值</span><span class="sxs-lookup"><span data-stu-id="d65fc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d65fc-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d65fc-110">Scope</span></span>   |<span data-ttu-id="d65fc-111">Minor</span><span class="sxs-lookup"><span data-stu-id="d65fc-111">Minor</span></span>|
|<span data-ttu-id="d65fc-112">版本</span><span class="sxs-lookup"><span data-stu-id="d65fc-112">Version</span></span>|<span data-ttu-id="d65fc-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d65fc-113">4.5</span></span>|
|<span data-ttu-id="d65fc-114">類型</span><span class="sxs-lookup"><span data-stu-id="d65fc-114">Type</span></span>|<span data-ttu-id="d65fc-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="d65fc-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d65fc-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d65fc-116">Affected APIs</span></span>

-<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
