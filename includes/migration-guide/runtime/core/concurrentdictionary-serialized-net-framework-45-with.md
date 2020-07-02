---
ms.openlocfilehash: ae0f68a19d6eae53998d61e924cfef3aaaec1784
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619970"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a><span data-ttu-id="b0b99-101">在 .NET Framework 4.5 中利用 NetDataContractSerializer 序列化過的 ConcurrentDictionary，無法由 .NET Framework 4.5.1 或 4.5.2 還原序列化</span><span class="sxs-lookup"><span data-stu-id="b0b99-101">A ConcurrentDictionary serialized in .NET Framework 4.5 with NetDataContractSerializer cannot be deserialized by .NET Framework 4.5.1 or 4.5.2</span></span>

#### <a name="details"></a><span data-ttu-id="b0b99-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b0b99-102">Details</span></span>

<span data-ttu-id="b0b99-103">由於此類型的內部變更，使用 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> 以 .NET Framework 4.5 序列化的 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 物件，無法在 .NET Framework 4.5.1 或 .NET Framework 4.5.2 中還原序列化。請注意，反向移動 (以 .NET Framework 4.5.x 序列化並以 .NET Framework 4.5 還原序列化) 則運作正常。</span><span class="sxs-lookup"><span data-stu-id="b0b99-103">Due to internal changes to the type, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objects that are serialized with the .NET Framework 4.5 using the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> cannot be deserialized in the .NET Framework 4.5.1 or in the .NET Framework 4.5.2.Note that moving in the other direction (serializing with the .NET Framework 4.5.x and deserializing with the .NET Framework 4.5) works.</span></span> <span data-ttu-id="b0b99-104">同樣地，所有 4.x 跨版本序列化在 .NET Framework 4.6 中都會正常運作。以單一 .NET Framework 版本進行序列化和還原序列化則不受影響。</span><span class="sxs-lookup"><span data-stu-id="b0b99-104">Similarly, all 4.x cross-version serialization works with the .NET Framework 4.6.Serializing and deserializing with a single version of the .NET Framework is not affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b0b99-105">建議</span><span class="sxs-lookup"><span data-stu-id="b0b99-105">Suggestion</span></span>

<span data-ttu-id="b0b99-106">如果必須在 .NET Framework 4.5 和 .NET Framework 4.5.1/4.5.2 之間序列化和還原序列化 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>，則應該使用替代的序列化程式 (例如 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> 序列化程式) 來取代 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>。此外，由於此問題已在 .NET Framework 4.6 中解決，因此可藉由升級至該版 .NET Framework 來解決。</span><span class="sxs-lookup"><span data-stu-id="b0b99-106">If it is necessary to serialize and deserialize a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName> between the .NET Framework 4.5 and .NET Framework 4.5.1/4.5.2, an alternate serializer like the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> serializer should be used instead of the <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName>.Alternatively, because this issue is addressed in the .NET Framework 4.6, it may be solved by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="b0b99-107">名稱</span><span class="sxs-lookup"><span data-stu-id="b0b99-107">Name</span></span>    | <span data-ttu-id="b0b99-108">值</span><span class="sxs-lookup"><span data-stu-id="b0b99-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b0b99-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="b0b99-109">Scope</span></span>   |<span data-ttu-id="b0b99-110">Minor</span><span class="sxs-lookup"><span data-stu-id="b0b99-110">Minor</span></span>|
|<span data-ttu-id="b0b99-111">版本</span><span class="sxs-lookup"><span data-stu-id="b0b99-111">Version</span></span>|<span data-ttu-id="b0b99-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="b0b99-112">4.5.1</span></span>|
|<span data-ttu-id="b0b99-113">類型</span><span class="sxs-lookup"><span data-stu-id="b0b99-113">Type</span></span>|<span data-ttu-id="b0b99-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="b0b99-114">Runtime</span></span>|
