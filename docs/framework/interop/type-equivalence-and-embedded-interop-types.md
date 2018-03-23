---
title: 類型等價和內嵌 interop 類型
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03b906c71b1b3e8f4817697edb520f8cfef1e009
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="type-equivalence-and-embedded-interop-types"></a><span data-ttu-id="196fa-102">類型等價和內嵌 interop 類型</span><span class="sxs-lookup"><span data-stu-id="196fa-102">Type equivalence and embedded interop types</span></span>

<span data-ttu-id="196fa-103">從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，通用語言執行平台支援將 COM 類型的類型資訊直接內嵌到 Managed 組件，而不需要 Managed 組件從 Interop 組件取得 COM 類型的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="196fa-103">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the common language runtime supports embedding type information for COM types directly into managed assemblies, instead of requiring the managed assemblies to obtain type information for COM types from interop assemblies.</span></span> <span data-ttu-id="196fa-104">因為內嵌類型資訊僅包含 Managed 組件實際所使用的類型和成員，所以兩個 Managed 組件可能對於相同的 COM 類型會有非常不同的檢視。</span><span class="sxs-lookup"><span data-stu-id="196fa-104">Because the embedded type information includes only the types and members that are actually used by a managed assembly, two managed assemblies might have very different views of the same COM type.</span></span> <span data-ttu-id="196fa-105">每個 Managed 組件有不同的 <xref:System.Type> 物件以代表其 COM 類型檢視。</span><span class="sxs-lookup"><span data-stu-id="196fa-105">Each managed assembly has a different <xref:System.Type> object to represent its view of the COM type.</span></span> <span data-ttu-id="196fa-106">通用語言執行平台支援介面、結構、列舉和委派等這些不同檢視之間的類型等價。</span><span class="sxs-lookup"><span data-stu-id="196fa-106">The common language runtime supports type equivalence between these different views for interfaces, structures, enumerations, and delegates.</span></span>

<span data-ttu-id="196fa-107">類型等價表示從一個 Managed 組件傳到另一個的 COM 物件，可以在接收的組件中轉換成適當的 Managed 類型。</span><span class="sxs-lookup"><span data-stu-id="196fa-107">Type equivalence means that a COM object that is passed from one managed assembly to another can be cast to the appropriate managed type in the receiving assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="196fa-108">類型等價和內嵌 Interop 類型簡化了使用 COM 元件之應用程式和增益集的部署，因為不必與應用程式一起部署 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="196fa-108">Type equivalence and embedded interop types simplify the deployment of applications and add-ins that use COM components, because it is not necessary to deploy interop assemblies with the applications.</span></span> <span data-ttu-id="196fa-109">共用 COM 元件的開發人員仍然必須建立主要 Interop 組件 (PIA)，如果他們想要舊版 .NET Framework 使用其元件的話。</span><span class="sxs-lookup"><span data-stu-id="196fa-109">Developers of shared COM components still have to create primary interop assemblies (PIAs) if they want their components to be used by earlier versions of the .NET Framework.</span></span>

## <a name="type-equivalence"></a><span data-ttu-id="196fa-110">類型等價</span><span class="sxs-lookup"><span data-stu-id="196fa-110">Type equivalence</span></span>

 <span data-ttu-id="196fa-111">針對介面、結構、列舉和委派支援 COM 類型等價。</span><span class="sxs-lookup"><span data-stu-id="196fa-111">Equivalence of COM types is supported for interfaces, structures, enumerations, and delegates.</span></span> <span data-ttu-id="196fa-112">如果下列所有各項都為 true，COM 類型便視相等：</span><span class="sxs-lookup"><span data-stu-id="196fa-112">COM types qualify as equivalent if all of the following are true:</span></span>

- <span data-ttu-id="196fa-113">類型同時為介面，或同時為結構，或同時為列舉，或同時為委派。</span><span class="sxs-lookup"><span data-stu-id="196fa-113">The types are both interfaces, or both structures, or both enumerations, or both delegates.</span></span>

- <span data-ttu-id="196fa-114">類型具有相同的身分識別，如下一節中所述。</span><span class="sxs-lookup"><span data-stu-id="196fa-114">The types have the same identity, as described in the next section.</span></span>

- <span data-ttu-id="196fa-115">中所述，這兩種類型是否適合類型等價，[標示 COM 類型的類型等價](#marking-com-types-for-type-equivalence)> 一節。</span><span class="sxs-lookup"><span data-stu-id="196fa-115">Both types are eligible for type equivalence, as described in the [Marking COM types for type equivalence](#marking-com-types-for-type-equivalence) section.</span></span>

### <a name="type-identity"></a><span data-ttu-id="196fa-116">型別身分識別</span><span class="sxs-lookup"><span data-stu-id="196fa-116">Type identity</span></span>

<span data-ttu-id="196fa-117">當兩個類型的範圍和身分識別相符時，會判斷它們具有相同的身分識別；換句話說，如果它們都有 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性，且兩個屬性都有相符的 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 和 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="196fa-117">Two types are determined to have the same identity when their scopes and identities match, in other words, if they each have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, and the two attributes have matching <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> and <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> properties.</span></span> <span data-ttu-id="196fa-118"><xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 的比較不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="196fa-118">The comparison for <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> is case-insensitive.</span></span>

<span data-ttu-id="196fa-119">如果類型沒有 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性，或它具有未指定範圍和識別項的 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性，該類型仍可以視為等價，如下所示：</span><span class="sxs-lookup"><span data-stu-id="196fa-119">If a type does not have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, or if it has a <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute that does not specify scope and identifier, the type can still be considered for equivalence as follows:</span></span>

- <span data-ttu-id="196fa-120">對於介面，會使用 <xref:System.Runtime.InteropServices.GuidAttribute> 的值而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> 屬性，而且會使用 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 屬性 (也就是類型名稱，包括命名空間) 而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="196fa-120">For interfaces, the value of the <xref:System.Runtime.InteropServices.GuidAttribute> is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> property, and the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property (that is, the type name, including the namespace) is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="196fa-121">對於結構、列舉和委派，會使用包含組件的 <xref:System.Runtime.InteropServices.GuidAttribute>而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 屬性，而且會使用 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 屬性，而非 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="196fa-121">For structures, enumerations, and delegates, the <xref:System.Runtime.InteropServices.GuidAttribute> of the containing assembly is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> property, and the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> property.</span></span>

### <a name="marking-com-types-for-type-equivalence"></a><span data-ttu-id="196fa-122">標記類型等價的 COM 型別</span><span class="sxs-lookup"><span data-stu-id="196fa-122">Marking COM types for type equivalence</span></span>

 <span data-ttu-id="196fa-123">您可以將類型標記為適合類型等價，有兩種方法：</span><span class="sxs-lookup"><span data-stu-id="196fa-123">You can mark a type as eligible for type equivalence in two ways:</span></span>

- <span data-ttu-id="196fa-124">將 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 屬性套用至該類型。</span><span class="sxs-lookup"><span data-stu-id="196fa-124">Apply the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute to the type.</span></span>

- <span data-ttu-id="196fa-125">讓類型成為 COM 匯入類型。</span><span class="sxs-lookup"><span data-stu-id="196fa-125">Make the type a COM import type.</span></span> <span data-ttu-id="196fa-126">如果介面具有 <xref:System.Runtime.InteropServices.ComImportAttribute> 屬性，便是 COM 匯入類型。</span><span class="sxs-lookup"><span data-stu-id="196fa-126">An interface is a COM import type if it has the <xref:System.Runtime.InteropServices.ComImportAttribute> attribute.</span></span> <span data-ttu-id="196fa-127">如果定義介面、結構、列舉或委派所在的組件具有 <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> 屬性，便是 COM 匯入類型。</span><span class="sxs-lookup"><span data-stu-id="196fa-127">An interface, structure, enumeration, or delegate is a COM import type if the assembly in which it is defined has the <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="196fa-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="196fa-128">See also</span></span>

<xref:System.Type.IsEquivalentTo%2A>  
<span data-ttu-id="196fa-129">[在 Managed 程式碼中使用 COM 類型](http://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="196fa-129">[Using COM Types in Managed Code](http://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span></span>  
[<span data-ttu-id="196fa-130">匯入類型程式庫做為組件</span><span class="sxs-lookup"><span data-stu-id="196fa-130">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)  
