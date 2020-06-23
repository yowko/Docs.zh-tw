---
title: 資料合約名稱
description: 探索資料合約和成員命名規則，以及 WCF 基礎結構的預設行為，其支援使用對等的資料合約進行通訊。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], naming
ms.assetid: 31f87e6c-247b-48f5-8e94-b9e1e33d8d09
ms.openlocfilehash: 85c533d683558520d46f259db0bdb34dcb1214c9
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247399"
---
# <a name="data-contract-names"></a><span data-ttu-id="b0730-103">資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="b0730-103">Data Contract Names</span></span>

<span data-ttu-id="b0730-104">有時候用戶端和服務不會共用相同的類型。</span><span class="sxs-lookup"><span data-stu-id="b0730-104">Sometimes a client and a service do not share the same types.</span></span> <span data-ttu-id="b0730-105">只要兩邊的資料合約都相同，仍然可以相互傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="b0730-105">They can still pass data to each other as long as the data contracts are equivalent on both sides.</span></span> <span data-ttu-id="b0730-106">[資料合約等價](data-contract-equivalence.md)是以資料合約和資料成員名稱為基礎，因此會提供機制來將類型和成員對應至這些名稱。</span><span class="sxs-lookup"><span data-stu-id="b0730-106">[Data Contract Equivalence](data-contract-equivalence.md) is based on data contract and data member names, and therefore a mechanism is provided to map types and members to those names.</span></span> <span data-ttu-id="b0730-107">本主題說明在建立名稱時，命名資料合約的規則，以及 Windows Communication Foundation （WCF）基礎結構的預設行為。</span><span class="sxs-lookup"><span data-stu-id="b0730-107">This topic explains the rules for naming data contracts as well as the default behavior of the Windows Communication Foundation (WCF) infrastructure when creating names.</span></span>

## <a name="basic-rules"></a><span data-ttu-id="b0730-108">基本規則</span><span class="sxs-lookup"><span data-stu-id="b0730-108">Basic Rules</span></span>
<span data-ttu-id="b0730-109">有關命名資料合約的基本規則包括：</span><span class="sxs-lookup"><span data-stu-id="b0730-109">Basic rules regarding naming data contracts include:</span></span>

- <span data-ttu-id="b0730-110">完整的資料合約名稱是由命名空間與名稱組成。</span><span class="sxs-lookup"><span data-stu-id="b0730-110">A fully-qualified data contract name consists of a namespace and a name.</span></span>

- <span data-ttu-id="b0730-111">資料成員只有名稱但是沒有命名空間。</span><span class="sxs-lookup"><span data-stu-id="b0730-111">Data members have only names, but no namespaces.</span></span>

- <span data-ttu-id="b0730-112">在處理資料合約時，WCF 基礎結構會對命名空間和資料合約和資料成員的名稱區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b0730-112">When processing data contracts, the WCF infrastructure is case-sensitive to both the namespaces and the names of data contracts and data members.</span></span>

## <a name="data-contract-namespaces"></a><span data-ttu-id="b0730-113">資料合約命名空間</span><span class="sxs-lookup"><span data-stu-id="b0730-113">Data Contract Namespaces</span></span>
<span data-ttu-id="b0730-114">資料合約命名空間使用的格式為統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="b0730-114">A data contract namespace takes the form of a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="b0730-115">這個 URI 可為絕對或相對的。</span><span class="sxs-lookup"><span data-stu-id="b0730-115">The URI can be either absolute or relative.</span></span> <span data-ttu-id="b0730-116">根據預設，特定類型的資料合約會指派來自該類型之 Common Language Runtime (CLR) 命名空間的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b0730-116">By default, data contracts for a particular type are assigned a namespace that comes from the common language runtime (CLR) namespace of that type.</span></span>

<span data-ttu-id="b0730-117">根據預設，任何指定的 CLR 命名空間（格式為*clr. namespace*）都會對應至命名空間 `http://schemas.datacontract.org/2004/07/Clr.Namespace` 。</span><span class="sxs-lookup"><span data-stu-id="b0730-117">By default, any given CLR namespace (in the format *Clr.Namespace*) is mapped to the namespace `http://schemas.datacontract.org/2004/07/Clr.Namespace`.</span></span> <span data-ttu-id="b0730-118">若要覆寫這個預設值，請將 <xref:System.Runtime.Serialization.ContractNamespaceAttribute> 屬性套用至整個模組或組件。</span><span class="sxs-lookup"><span data-stu-id="b0730-118">To override this default, apply the <xref:System.Runtime.Serialization.ContractNamespaceAttribute> attribute to the entire module or assembly.</span></span> <span data-ttu-id="b0730-119">或是控制每個類型的資料合約命名空間，設定 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="b0730-119">Alternatively, to control the data contract namespace for each type, set the <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> property of the <xref:System.Runtime.Serialization.DataContractAttribute>.</span></span>

> [!NOTE]
> <span data-ttu-id="b0730-120">`http://schemas.microsoft.com/2003/10/Serialization`命名空間是保留的，不能用來做為資料合約命名空間。</span><span class="sxs-lookup"><span data-stu-id="b0730-120">The `http://schemas.microsoft.com/2003/10/Serialization` namespace is reserved and cannot be used as a data contract namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="b0730-121">您無法覆寫其中包含 `delegate` 宣告之資料合約類型中的預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="b0730-121">You cannot override the default namespace in data contract types that contain `delegate` declarations.</span></span>

## <a name="data-contract-names"></a><span data-ttu-id="b0730-122">資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="b0730-122">Data Contract Names</span></span>
<span data-ttu-id="b0730-123">指定類型的資料合約預設名稱是該類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0730-123">The default name of a data contract for a given type is the name of that type.</span></span> <span data-ttu-id="b0730-124">若要覆寫預設值，請將 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性設定為替代名稱。</span><span class="sxs-lookup"><span data-stu-id="b0730-124">To override the default, set the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataContractAttribute> to an alternative name.</span></span> <span data-ttu-id="b0730-125">泛型類型的特殊規則會在本主題稍後的「泛型類型的資料合約名稱」中描述。</span><span class="sxs-lookup"><span data-stu-id="b0730-125">Special rules for generic types are described in "Data Contract Names for Generic Types" later in this topic.</span></span>

## <a name="data-member-names"></a><span data-ttu-id="b0730-126">資料成員名稱</span><span class="sxs-lookup"><span data-stu-id="b0730-126">Data Member Names</span></span>
<span data-ttu-id="b0730-127">指定欄位或屬性的資料成員預設名稱是該欄位或屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0730-127">The default name of a data member for a given field or property is the name of that field or property.</span></span> <span data-ttu-id="b0730-128">若要覆寫預設值，請將 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性設定為替代值。</span><span class="sxs-lookup"><span data-stu-id="b0730-128">To override the default, set the <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to an alternative value.</span></span>

### <a name="examples"></a><span data-ttu-id="b0730-129">範例</span><span class="sxs-lookup"><span data-stu-id="b0730-129">Examples</span></span>
<span data-ttu-id="b0730-130">下列程式碼範例顯示如何覆寫資料合約與資料成員的預設命名行為。</span><span class="sxs-lookup"><span data-stu-id="b0730-130">The following example shows how you can override the default naming behavior of data contracts and data members.</span></span>

[!code-csharp[C_DataContractNames#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#1)]
[!code-vb[C_DataContractNames#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#1)]

## <a name="data-contract-names-for-generic-types"></a><span data-ttu-id="b0730-131">泛型類型的資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="b0730-131">Data Contract Names for Generic Types</span></span>
<span data-ttu-id="b0730-132">判定泛型類型的資料合約名稱有特殊規則。</span><span class="sxs-lookup"><span data-stu-id="b0730-132">Special rules exist for determining data contract names for generic types.</span></span> <span data-ttu-id="b0730-133">這些規則會協助避免相同泛型類型的兩個封閉式泛型之間發生資料合約名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="b0730-133">These rules help avoid data contract name collisions between two closed generics of the same generic type.</span></span>

<span data-ttu-id="b0730-134">根據預設，泛型型別的資料合約名稱是類型的名稱，後面接著字串 "of"，後面接著泛型參數的資料合約名稱，接著是使用泛型參數的資料合約命名空間來計算的*雜湊*。</span><span class="sxs-lookup"><span data-stu-id="b0730-134">By default, the data contract name for a generic type is the name of the type, followed by the string "Of", followed by the data contract names of the generic parameters, followed by a *hash* computed using the data contract namespaces of the generic parameters.</span></span> <span data-ttu-id="b0730-135">雜湊是數學函式計算出來的結果，用來當做唯一識別資料片段的「指紋」。</span><span class="sxs-lookup"><span data-stu-id="b0730-135">A hash is the result of a mathematical function that acts as a "fingerprint" that uniquely identifies a piece of data.</span></span> <span data-ttu-id="b0730-136">當所有的泛型參數都是基本型別時，就會省略雜湊。</span><span class="sxs-lookup"><span data-stu-id="b0730-136">When all of the generic parameters are primitive types, the hash is omitted.</span></span>

<span data-ttu-id="b0730-137">以下列範例中的型別為例：</span><span class="sxs-lookup"><span data-stu-id="b0730-137">For example, see the types in the following example.</span></span>

[!code-csharp[C_DataContractNames#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#2)]
[!code-vb[C_DataContractNames#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#2)]

<span data-ttu-id="b0730-138">在此範例中，型別 `Drawing<Square,RegularRedBrush>` 的資料合約名稱為 "DrawingOfSquareRedBrush5HWGAU6h"，其中 "5HWGAU6h" 是 "urn:shapes" 和 "urn:default" 命名空間的雜湊。</span><span class="sxs-lookup"><span data-stu-id="b0730-138">In this example, the type `Drawing<Square,RegularRedBrush>` has the data contract name "DrawingOfSquareRedBrush5HWGAU6h", where "5HWGAU6h" is a hash of the "urn:shapes" and "urn:default" namespaces.</span></span> <span data-ttu-id="b0730-139">型別 `Drawing<Square,SpecialRedBrush>` 的資料合約名稱為 "DrawingOfSquareRedBrushjpB5LgQ_S"，其中 "jpB5LgQ_S" 是 "urn:shapes" 和 "urn:special" 命名空間的雜湊。</span><span class="sxs-lookup"><span data-stu-id="b0730-139">The type `Drawing<Square,SpecialRedBrush>` has the data contract name "DrawingOfSquareRedBrushjpB5LgQ_S", where "jpB5LgQ_S" is a hash of the "urn:shapes" and the "urn:special" namespaces.</span></span> <span data-ttu-id="b0730-140">請注意，如果沒有使用雜湊，兩個名稱會完全相同，因而會發生名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="b0730-140">Note that if the hash is not used, the two names are identical, and thus a name collision occurs.</span></span>

## <a name="customizing-data-contract-names-for-generic-types"></a><span data-ttu-id="b0730-141">自訂泛型型別的資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="b0730-141">Customizing data contract names for generic types</span></span>

<span data-ttu-id="b0730-142">有時候無法接收針對泛型類型產生的資料合約名稱 (如同之前所描述)。</span><span class="sxs-lookup"><span data-stu-id="b0730-142">Sometimes, the data contract names generated for generic types, as described previously, are unacceptable.</span></span> <span data-ttu-id="b0730-143">例如，您可能事先知道不會產生名稱衝突並且想要移除雜湊。</span><span class="sxs-lookup"><span data-stu-id="b0730-143">For example, you may know in advance that you will not run into name collisions and may want to remove the hash.</span></span> <span data-ttu-id="b0730-144">在此情況下，您可以使用 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> 屬性來指定不同的名稱產生方式。</span><span class="sxs-lookup"><span data-stu-id="b0730-144">In this case, you can use the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A?displayProperty=nameWithType> property to specify a different way to generate names.</span></span> <span data-ttu-id="b0730-145">您可以在 `Name` 屬性內使用以大括號包圍的數字，參考泛型參數的資料合約名稱 </span><span class="sxs-lookup"><span data-stu-id="b0730-145">You can use numbers in curly braces inside of the `Name` property to refer to data contract names of the generic parameters.</span></span> <span data-ttu-id="b0730-146">（0指的是第一個參數，1指的是第二個參數，依此類推）。您可以在大括弧內使用數位（#）符號來參考雜湊。</span><span class="sxs-lookup"><span data-stu-id="b0730-146">(0 refers to the first parameter, 1 refers to the second, and so on.) You can use a number (#) sign inside curly braces to refer to the hash.</span></span> <span data-ttu-id="b0730-147">您可以多次使用這些參考或完全不用。</span><span class="sxs-lookup"><span data-stu-id="b0730-147">You can use each of these references multiple times or not at all.</span></span>

<span data-ttu-id="b0730-148">例如，先前的泛型 `Drawing` 型別應該要如下的宣告方式：</span><span class="sxs-lookup"><span data-stu-id="b0730-148">For example, the preceding generic `Drawing` type could have been declared as shown in the following example.</span></span>

[!code-csharp[c_DataContractNames#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#3)]
[!code-vb[c_DataContractNames#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#3)]

<span data-ttu-id="b0730-149">在此例中，型別 `Drawing<Square,RegularRedBrush>` 的資料合約名稱為 "Drawing_using_RedBrush_brush_and_Square_shape"。</span><span class="sxs-lookup"><span data-stu-id="b0730-149">In this case, the type `Drawing<Square,RegularRedBrush>` has the data contract name "Drawing_using_RedBrush_brush_and_Square_shape".</span></span> <span data-ttu-id="b0730-150">請注意，因為在 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 屬性中有一個 "{#}"，而雜湊不是名稱的一部分，所以型別就容易發生命名衝突；例如型別 `Drawing<Square,SpecialRedBrush>` 可能會擁有完全相同的資料合約名稱。</span><span class="sxs-lookup"><span data-stu-id="b0730-150">Note that because there is a "{#}" in the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> property, the hash is not a part of the name, and thus the type is susceptible to naming collisions; for example, the type `Drawing<Square,SpecialRedBrush>` would have exactly the same data contract name.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0730-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0730-151">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.ContractNamespaceAttribute>
- [<span data-ttu-id="b0730-152">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="b0730-152">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="b0730-153">資料合約等價</span><span class="sxs-lookup"><span data-stu-id="b0730-153">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="b0730-154">資料合約名稱</span><span class="sxs-lookup"><span data-stu-id="b0730-154">Data Contract Names</span></span>](data-contract-names.md)
- [<span data-ttu-id="b0730-155">資料合約版本控制</span><span class="sxs-lookup"><span data-stu-id="b0730-155">Data Contract Versioning</span></span>](data-contract-versioning.md)
