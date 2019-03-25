---
title: 資料合約名稱
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 16a42a2808104a77e56e93564a679dfc578e73f6
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408869"
---
# <a name="data-contract-names"></a><span data-ttu-id="31c4e-102">資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="31c4e-102">Data Contract Names</span></span>

<span data-ttu-id="31c4e-103">有時候用戶端和服務不會共用相同的類型。</span><span class="sxs-lookup"><span data-stu-id="31c4e-103">Sometimes a client and a service do not share the same types.</span></span> <span data-ttu-id="31c4e-104">只要兩邊的資料合約都相同，仍然可以相互傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="31c4e-104">They can still pass data to each other as long as the data contracts are equivalent on both sides.</span></span> <span data-ttu-id="31c4e-105">[資料合約等價](data-contract-equivalence.md)根據資料合約與資料成員名稱，因此會提供機制將型別和成員對應至這些名稱。</span><span class="sxs-lookup"><span data-stu-id="31c4e-105">[Data Contract Equivalence](data-contract-equivalence.md) is based on data contract and data member names, and therefore a mechanism is provided to map types and members to those names.</span></span> <span data-ttu-id="31c4e-106">本主題說明建立名稱時，命名的資料合約，以及 Windows Communication Foundation (WCF) 基礎結構的預設行為的規則。</span><span class="sxs-lookup"><span data-stu-id="31c4e-106">This topic explains the rules for naming data contracts as well as the default behavior of the Windows Communication Foundation (WCF) infrastructure when creating names.</span></span>

## <a name="basic-rules"></a><span data-ttu-id="31c4e-107">基本規則</span><span class="sxs-lookup"><span data-stu-id="31c4e-107">Basic Rules</span></span>
<span data-ttu-id="31c4e-108">有關命名資料合約的基本規則包括：</span><span class="sxs-lookup"><span data-stu-id="31c4e-108">Basic rules regarding naming data contracts include:</span></span>

- <span data-ttu-id="31c4e-109">完整的資料合約名稱是由命名空間與名稱組成。</span><span class="sxs-lookup"><span data-stu-id="31c4e-109">A fully-qualified data contract name consists of a namespace and a name.</span></span>

- <span data-ttu-id="31c4e-110">資料成員只有名稱但是沒有命名空間。</span><span class="sxs-lookup"><span data-stu-id="31c4e-110">Data members have only names, but no namespaces.</span></span>

- <span data-ttu-id="31c4e-111">處理資料合約，WCF 基礎結構時，區分大小寫的命名空間和資料合約與資料成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="31c4e-111">When processing data contracts, the WCF infrastructure is case-sensitive to both the namespaces and the names of data contracts and data members.</span></span>

## <a name="data-contract-namespaces"></a><span data-ttu-id="31c4e-112">資料合約命名空間</span><span class="sxs-lookup"><span data-stu-id="31c4e-112">Data Contract Namespaces</span></span>
<span data-ttu-id="31c4e-113">資料合約命名空間使用的格式為統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="31c4e-113">A data contract namespace takes the form of a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="31c4e-114">這個 URI 可為絕對或相對的。</span><span class="sxs-lookup"><span data-stu-id="31c4e-114">The URI can be either absolute or relative.</span></span> <span data-ttu-id="31c4e-115">根據預設，特定類型的資料合約會指派來自該類型之 Common Language Runtime (CLR) 命名空間的命名空間。</span><span class="sxs-lookup"><span data-stu-id="31c4e-115">By default, data contracts for a particular type are assigned a namespace that comes from the common language runtime (CLR) namespace of that type.</span></span>

<span data-ttu-id="31c4e-116">根據預設，任何指定的 CLR 命名空間 (格式*Clr.Namespace*) 對應至命名空間`http://schemas.datacontract.org/2004/07/Clr.Namespace`。</span><span class="sxs-lookup"><span data-stu-id="31c4e-116">By default, any given CLR namespace (in the format *Clr.Namespace*) is mapped to the namespace `http://schemas.datacontract.org/2004/07/Clr.Namespace`.</span></span> <span data-ttu-id="31c4e-117">若要覆寫這個預設值，請將 <xref:System.Runtime.Serialization.ContractNamespaceAttribute> 屬性套用至整個模組或組件。</span><span class="sxs-lookup"><span data-stu-id="31c4e-117">To override this default, apply the <xref:System.Runtime.Serialization.ContractNamespaceAttribute> attribute to the entire module or assembly.</span></span> <span data-ttu-id="31c4e-118">或是控制每個類型的資料合約命名空間，設定 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="31c4e-118">Alternatively, to control the data contract namespace for each type, set the <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> property of the <xref:System.Runtime.Serialization.DataContractAttribute>.</span></span>

> [!NOTE]
> <span data-ttu-id="31c4e-119">`http://schemas.microsoft.com/2003/10/Serialization`命名空間已保留，不能當做資料合約命名空間。</span><span class="sxs-lookup"><span data-stu-id="31c4e-119">The `http://schemas.microsoft.com/2003/10/Serialization` namespace is reserved and cannot be used as a data contract namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="31c4e-120">您無法覆寫其中包含 `delegate` 宣告之資料合約類型中的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="31c4e-120">You cannot override the default namespace in data contract types that contain `delegate` declarations.</span></span>

## <a name="data-contract-names"></a><span data-ttu-id="31c4e-121">資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="31c4e-121">Data Contract Names</span></span>
<span data-ttu-id="31c4e-122">指定類型的資料合約預設名稱是該類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="31c4e-122">The default name of a data contract for a given type is the name of that type.</span></span> <span data-ttu-id="31c4e-123">若要覆寫預設值，請將 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性設定為替代名稱。</span><span class="sxs-lookup"><span data-stu-id="31c4e-123">To override the default, set the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataContractAttribute> to an alternative name.</span></span> <span data-ttu-id="31c4e-124">泛型類型的特殊規則會在本主題稍後的「泛型類型的資料合約名稱」中描述。</span><span class="sxs-lookup"><span data-stu-id="31c4e-124">Special rules for generic types are described in "Data Contract Names for Generic Types" later in this topic.</span></span>

## <a name="data-member-names"></a><span data-ttu-id="31c4e-125">資料成員名稱</span><span class="sxs-lookup"><span data-stu-id="31c4e-125">Data Member Names</span></span>
<span data-ttu-id="31c4e-126">指定欄位或屬性的資料成員預設名稱是該欄位或屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="31c4e-126">The default name of a data member for a given field or property is the name of that field or property.</span></span> <span data-ttu-id="31c4e-127">若要覆寫預設值，請將 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性設定為替代值。</span><span class="sxs-lookup"><span data-stu-id="31c4e-127">To override the default, set the <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to an alternative value.</span></span>

### <a name="examples"></a><span data-ttu-id="31c4e-128">範例</span><span class="sxs-lookup"><span data-stu-id="31c4e-128">Examples</span></span>
<span data-ttu-id="31c4e-129">下列程式碼範例顯示如何覆寫資料合約與資料成員的預設命名行為。</span><span class="sxs-lookup"><span data-stu-id="31c4e-129">The following example shows how you can override the default naming behavior of data contracts and data members.</span></span>

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a><span data-ttu-id="31c4e-130">泛型類型的資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="31c4e-130">Data Contract Names for Generic Types</span></span>
<span data-ttu-id="31c4e-131">判定泛型類型的資料合約名稱有特殊規則。</span><span class="sxs-lookup"><span data-stu-id="31c4e-131">Special rules exist for determining data contract names for generic types.</span></span> <span data-ttu-id="31c4e-132">這些規則會協助避免相同泛型類型的兩個封閉式泛型之間發生資料合約名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="31c4e-132">These rules help avoid data contract name collisions between two closed generics of the same generic type.</span></span>

<span data-ttu-id="31c4e-133">根據預設，資料合約名稱的泛型型別為型別的名稱，後面接著"Of"、 字串後面的泛用參數，後面加上的資料合約名稱*雜湊*計算使用的資料合約命名空間泛型參數。</span><span class="sxs-lookup"><span data-stu-id="31c4e-133">By default, the data contract name for a generic type is the name of the type, followed by the string "Of", followed by the data contract names of the generic parameters, followed by a *hash* computed using the data contract namespaces of the generic parameters.</span></span> <span data-ttu-id="31c4e-134">雜湊是數學函式計算出來的結果，用來當做唯一識別資料片段的「指紋」。</span><span class="sxs-lookup"><span data-stu-id="31c4e-134">A hash is the result of a mathematical function that acts as a "fingerprint" that uniquely identifies a piece of data.</span></span> <span data-ttu-id="31c4e-135">當所有的泛型參數都是基本型別時，就會省略雜湊。</span><span class="sxs-lookup"><span data-stu-id="31c4e-135">When all of the generic parameters are primitive types, the hash is omitted.</span></span>

<span data-ttu-id="31c4e-136">以下列範例中的型別為例：</span><span class="sxs-lookup"><span data-stu-id="31c4e-136">For example, see the types in the following example.</span></span>

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

<span data-ttu-id="31c4e-137">在此範例中，型別 `Drawing<Square,RegularRedBrush>` 的資料合約名稱為 "DrawingOfSquareRedBrush5HWGAU6h"，其中 "5HWGAU6h" 是 "urn:shapes" 和 "urn:default" 命名空間的雜湊。</span><span class="sxs-lookup"><span data-stu-id="31c4e-137">In this example, the type `Drawing<Square,RegularRedBrush>` has the data contract name "DrawingOfSquareRedBrush5HWGAU6h", where "5HWGAU6h" is a hash of the "urn:shapes" and "urn:default" namespaces.</span></span> <span data-ttu-id="31c4e-138">型別 `Drawing<Square,SpecialRedBrush>` 的資料合約名稱為 "DrawingOfSquareRedBrushjpB5LgQ_S"，其中 "jpB5LgQ_S" 是 "urn:shapes" 和 "urn:special" 命名空間的雜湊。</span><span class="sxs-lookup"><span data-stu-id="31c4e-138">The type `Drawing<Square,SpecialRedBrush>` has the data contract name "DrawingOfSquareRedBrushjpB5LgQ_S", where "jpB5LgQ_S" is a hash of the "urn:shapes" and the "urn:special" namespaces.</span></span> <span data-ttu-id="31c4e-139">請注意，如果沒有使用雜湊，兩個名稱會完全相同，因而會發生名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="31c4e-139">Note that if the hash is not used, the two names are identical, and thus a name collision occurs.</span></span>

## <a name="customizing-data-contract-names-for-generic-types"></a><span data-ttu-id="31c4e-140">泛型類型的自訂資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="31c4e-140">Customizing data contract names for generic types</span></span>

<span data-ttu-id="31c4e-141">有時候無法接收針對泛型類型產生的資料合約名稱 (如同之前所描述)。</span><span class="sxs-lookup"><span data-stu-id="31c4e-141">Sometimes, the data contract names generated for generic types, as described previously, are unacceptable.</span></span> <span data-ttu-id="31c4e-142">例如，您可能事先知道不會產生名稱衝突並且想要移除雜湊。</span><span class="sxs-lookup"><span data-stu-id="31c4e-142">For example, you may know in advance that you will not run into name collisions and may want to remove the hash.</span></span> <span data-ttu-id="31c4e-143">在此情況下，您可以使用<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType>屬性來指定不同的方式，來產生名稱。</span><span class="sxs-lookup"><span data-stu-id="31c4e-143">In this case, you can use the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> property to specify a different way to generate names.</span></span> <span data-ttu-id="31c4e-144">您可以在 `Name` 屬性內使用以大括號包圍的數字，參考泛型參數的資料合約名稱 </span><span class="sxs-lookup"><span data-stu-id="31c4e-144">You can use numbers in curly braces inside of the `Name` property to refer to data contract names of the generic parameters.</span></span> <span data-ttu-id="31c4e-145">(0 參考第一個參數，1 參考第二個參數，以此類推)。您可以在大括號中使用數字 (#) 符號以參考雜湊。</span><span class="sxs-lookup"><span data-stu-id="31c4e-145">(0 refers to the first parameter, 1 refers to the second, and so on.) You can use a number (#) sign inside curly braces to refer to the hash.</span></span> <span data-ttu-id="31c4e-146">您可以多次使用這些參考或完全不用。</span><span class="sxs-lookup"><span data-stu-id="31c4e-146">You can use each of these references multiple times or not at all.</span></span>

<span data-ttu-id="31c4e-147">例如，先前的泛型 `Drawing` 型別應該要如下的宣告方式：</span><span class="sxs-lookup"><span data-stu-id="31c4e-147">For example, the preceding generic `Drawing` type could have been declared as shown in the following example.</span></span>

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

<span data-ttu-id="31c4e-148">在此例中，型別 `Drawing<Square,RegularRedBrush>` 的資料合約名稱為 "Drawing_using_RedBrush_brush_and_Square_shape"。</span><span class="sxs-lookup"><span data-stu-id="31c4e-148">In this case, the type `Drawing<Square,RegularRedBrush>` has the data contract name "Drawing_using_RedBrush_brush_and_Square_shape".</span></span> <span data-ttu-id="31c4e-149">請注意，因為在 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 屬性中有一個 "{#}"，而雜湊不是名稱的一部分，所以型別就容易發生命名衝突；例如型別 `Drawing<Square,SpecialRedBrush>` 可能會擁有完全相同的資料合約名稱。</span><span class="sxs-lookup"><span data-stu-id="31c4e-149">Note that because there is a "{#}" in the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> property, the hash is not a part of the name, and thus the type is susceptible to naming collisions; for example, the type `Drawing<Square,SpecialRedBrush>` would have exactly the same data contract name.</span></span>

## <a name="see-also"></a><span data-ttu-id="31c4e-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31c4e-150">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [<span data-ttu-id="31c4e-151">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="31c4e-151">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="31c4e-152">資料合約等價</span><span class="sxs-lookup"><span data-stu-id="31c4e-152">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="31c4e-153">資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="31c4e-153">Data Contract Names</span></span>](data-contract-names.md)
- [<span data-ttu-id="31c4e-154">資料合約版本控制</span><span class="sxs-lookup"><span data-stu-id="31c4e-154">Data Contract Versioning</span></span>](data-contract-versioning.md)
