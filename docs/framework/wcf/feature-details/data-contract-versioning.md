---
title: 資料合約版本控制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 0e91bf597e344dd09e80bee5787e92383065b654
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520194"
---
# <a name="data-contract-versioning"></a><span data-ttu-id="781cd-102">資料合約版本控制</span><span class="sxs-lookup"><span data-stu-id="781cd-102">Data Contract Versioning</span></span>
<span data-ttu-id="781cd-103">隨著應用程式的發展，您也必須變更服務所使用的資料合約。</span><span class="sxs-lookup"><span data-stu-id="781cd-103">As applications evolve, you may also have to change the data contracts the services use.</span></span> <span data-ttu-id="781cd-104">本主題說明如何設定資料合約的版本。</span><span class="sxs-lookup"><span data-stu-id="781cd-104">This topic explains how to version data contracts.</span></span> <span data-ttu-id="781cd-105">本主題描述資料合約版本控制的機制。</span><span class="sxs-lookup"><span data-stu-id="781cd-105">This topic describes the data contract versioning mechanisms.</span></span> <span data-ttu-id="781cd-106">如需完整的概觀和規定性的版本控制指導方針，請參閱[最佳做法： 資料合約版本控制](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="781cd-106">For a complete overview and prescriptive versioning guidance, see [Best Practices: Data Contract Versioning](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).</span></span>  
  
## <a name="breaking-vs-nonbreaking-changes"></a><span data-ttu-id="781cd-107">中斷與不中斷變更的比較</span><span class="sxs-lookup"><span data-stu-id="781cd-107">Breaking vs. Nonbreaking Changes</span></span>  
 <span data-ttu-id="781cd-108">資料合約的變更可以採用中斷或不中斷的方式進行。</span><span class="sxs-lookup"><span data-stu-id="781cd-108">Changes to a data contract can be breaking or nonbreaking.</span></span> <span data-ttu-id="781cd-109">當資料合約以不中斷的方式變更時，使用舊版合約的應用程式可以與使用新版合約的應用程式通訊，而使用新版合約的應用程式可以與使用舊版合約的應用程式通訊。</span><span class="sxs-lookup"><span data-stu-id="781cd-109">When a data contract is changed in a nonbreaking way, an application using the older version of the contract can communicate with an application using the newer version, and an application using the newer version of the contract can communicate with an application using the older version.</span></span> <span data-ttu-id="781cd-110">相反的，中斷變更則會阻止單向或雙向的通訊。</span><span class="sxs-lookup"><span data-stu-id="781cd-110">On the other hand, a breaking change prevents communication in one or both directions.</span></span>  
  
 <span data-ttu-id="781cd-111">任何對類型的變更若不會影響其傳輸和接收的方式，則都是不中斷的變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-111">Any changes to a type that do not affect how it is transmitted and received are nonbreaking.</span></span> <span data-ttu-id="781cd-112">此類的變更並不會改變資料合約，只會改變基礎型別。</span><span class="sxs-lookup"><span data-stu-id="781cd-112">Such changes do not change the data contract, only the underlying type.</span></span> <span data-ttu-id="781cd-113">例如，如果您接著將 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性設定為舊版的名稱，則您就可以使用不中斷方式變更欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="781cd-113">For example, you can change the name of a field in a nonbreaking way if you then set the <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to the older version name.</span></span> <span data-ttu-id="781cd-114">下列程式碼說明資料合約的第 1 版。</span><span class="sxs-lookup"><span data-stu-id="781cd-114">The following code shows version 1 of a data contract.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 <span data-ttu-id="781cd-115">下列程式碼示範不中斷變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-115">The following code shows a nonbreaking change.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 <span data-ttu-id="781cd-116">某些變更會修改傳輸的資料，但可能會、也可能不會中斷。</span><span class="sxs-lookup"><span data-stu-id="781cd-116">Some changes do modify the transmitted data, but may or may not be breaking.</span></span> <span data-ttu-id="781cd-117">下列的變更則一定會中斷：</span><span class="sxs-lookup"><span data-stu-id="781cd-117">The following changes are always breaking:</span></span>  
  
-   <span data-ttu-id="781cd-118">變更資料合約的 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 或 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="781cd-118">Changing the <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> or <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> value of a data contract.</span></span>  
  
-   <span data-ttu-id="781cd-119">使用 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性變更資料成員的順序。</span><span class="sxs-lookup"><span data-stu-id="781cd-119">Changing the order of data members by using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute>.</span></span>  
  
-   <span data-ttu-id="781cd-120">重新命名資料成員。</span><span class="sxs-lookup"><span data-stu-id="781cd-120">Renaming a data member.</span></span>  
  
-   <span data-ttu-id="781cd-121">變更資料成員的資料合約。</span><span class="sxs-lookup"><span data-stu-id="781cd-121">Changing the data contract of a data member.</span></span> <span data-ttu-id="781cd-122">例如，將資料成員的型別從整數變更為字串，或從具有名為 "Customer" 資料合約的型別變更成具有名為 "Person" 資料合約的型別。</span><span class="sxs-lookup"><span data-stu-id="781cd-122">For example, changing the type of data member from an integer to a string, or from a type with a data contract named "Customer" to a type with a data contract named "Person".</span></span>  
  
 <span data-ttu-id="781cd-123">以下變更是允許的。</span><span class="sxs-lookup"><span data-stu-id="781cd-123">The following changes are also possible.</span></span>  
  
## <a name="adding-and-removing-data-members"></a><span data-ttu-id="781cd-124">新增及移除資料成員</span><span class="sxs-lookup"><span data-stu-id="781cd-124">Adding and Removing Data Members</span></span>  
 <span data-ttu-id="781cd-125">大部份的情況下，新增或移除資料成員不是採用中斷變更的方式，除非您要求嚴格的結構描述有效性 (根據舊結構描述驗證新執行個體)。</span><span class="sxs-lookup"><span data-stu-id="781cd-125">In most cases, adding or removing a data member is not a breaking change, unless you require strict schema validity (new instances validating against the old schema).</span></span>  
  
 <span data-ttu-id="781cd-126">在將具有額外欄位的類型還原序列化為具有缺少欄位的類型時，則會忽略額外的資訊</span><span class="sxs-lookup"><span data-stu-id="781cd-126">When a type with an extra field is deserialized into a type with a missing field, the extra information is ignored.</span></span> <span data-ttu-id="781cd-127">(也可能儲存往返之用; 如需詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md))。</span><span class="sxs-lookup"><span data-stu-id="781cd-127">(It may also be stored for round-tripping purposes; for more information, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).</span></span>  
  
 <span data-ttu-id="781cd-128">在將缺少欄位的類型還原序列化為具有額外欄位的類型時，額外欄位會保留其預設值，通常為零或 `null`</span><span class="sxs-lookup"><span data-stu-id="781cd-128">When a type with a missing field is deserialized into a type with an extra field, the extra field is left at its default value, usually zero or `null`.</span></span> <span data-ttu-id="781cd-129">(預設值可能會變更; 如需詳細資訊，請參閱 <<c0> [ 版本相容序列化回呼](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)。)</span><span class="sxs-lookup"><span data-stu-id="781cd-129">(The default value may be changed; for more information, see [Version-Tolerant Serialization Callbacks](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)</span></span>  
  
 <span data-ttu-id="781cd-130">例如，您可以在用戶端上使用 `CarV1` 類別，並在服務上使用 `CarV2` 類別，或者可以在服務上使用 `CarV1` 類別，而在用戶端上使用 `CarV2` 類別。</span><span class="sxs-lookup"><span data-stu-id="781cd-130">For example, you can use the `CarV1` class on a client and the `CarV2` class on a service, or you can use the `CarV1` class on a service and the `CarV2` class on a client.</span></span>  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 <span data-ttu-id="781cd-131">第 2 版的端點可以成功地將資料傳送至第 1 版的端點。</span><span class="sxs-lookup"><span data-stu-id="781cd-131">The version 2 endpoint can successfully send data to the version 1 endpoint.</span></span> <span data-ttu-id="781cd-132">序列化第 2 版的 `Car` 資料合約，會產生與下面類似的 XML。</span><span class="sxs-lookup"><span data-stu-id="781cd-132">Serializing version 2 of the `Car` data contract yields XML similar to the following.</span></span>  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 <span data-ttu-id="781cd-133">第 1 版上的還原序列化引擎找不到與 `HorsePower` 欄位相符的資料成員，然後便捨棄該資料。</span><span class="sxs-lookup"><span data-stu-id="781cd-133">The deserialization engine on V1 does not find a matching data member for the `HorsePower` field, and discards that data.</span></span>  
  
 <span data-ttu-id="781cd-134">同時，第 1 版的端點可以將資料傳送至第 2 版的端點。</span><span class="sxs-lookup"><span data-stu-id="781cd-134">Also, the version 1 endpoint can send data to the version 2 endpoint.</span></span> <span data-ttu-id="781cd-135">序列化第 1 版的 `Car` 資料合約，會產生與下列類似的 XML。</span><span class="sxs-lookup"><span data-stu-id="781cd-135">Serializing version 1 of the `Car` data contract yields XML similar to the following.</span></span>  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 <span data-ttu-id="781cd-136">因為傳入的 XML 未包含符合的資料，因此第 2 版的還原序列化程式不知道要將 `HorsePower` 欄位設定為什麼。</span><span class="sxs-lookup"><span data-stu-id="781cd-136">The version 2 deserializer does not know what to set the `HorsePower` field to, because there is no matching data in the incoming XML.</span></span> <span data-ttu-id="781cd-137">相反的，該欄位會設為預設值 0。</span><span class="sxs-lookup"><span data-stu-id="781cd-137">Instead, the field is set to the default value of 0.</span></span>  
  
## <a name="required-data-members"></a><span data-ttu-id="781cd-138">必要的資料成員</span><span class="sxs-lookup"><span data-stu-id="781cd-138">Required Data Members</span></span>  
 <span data-ttu-id="781cd-139">將 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性設定為 `true`，即可將資料成員標記為必要項。</span><span class="sxs-lookup"><span data-stu-id="781cd-139">A data member may be marked as being required by setting the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> to `true`.</span></span> <span data-ttu-id="781cd-140">如果在還原序列化時遺失了必要的資料，則會擲回例外狀況，而不是將該資料成員設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="781cd-140">If required data is missing while deserializing, an exception is thrown instead of setting the data member to its default value.</span></span>  
  
 <span data-ttu-id="781cd-141">新增必要的資料成員是一種中斷變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-141">Adding a required data member is a breaking change.</span></span> <span data-ttu-id="781cd-142">也就是，較新的類型仍舊可以傳送至使用舊類型的端點，而不是將較舊的類型傳送至使用新類型的端點。</span><span class="sxs-lookup"><span data-stu-id="781cd-142">That is, the newer type can still be sent to endpoints with the older type, but not the other way around.</span></span> <span data-ttu-id="781cd-143">將任何舊版內已標記為必要項之資料成員移除，也是一種中斷變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-143">Removing a data member that was marked as required in any prior version is also a breaking change.</span></span>  
  
 <span data-ttu-id="781cd-144">將 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性從 `true` 變更為 `false` 的動作是不中斷變更，但是將其從 `false` 變更為 `true` 的動作則可能會是中斷變更 (如果任何舊版的類型未含有所討論的資料成員)。</span><span class="sxs-lookup"><span data-stu-id="781cd-144">Changing the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property value from `true` to `false` is not breaking, but changing it from `false` to `true` may be breaking if any prior versions of the type do not have the data member in question.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="781cd-145">雖然將 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性設定為 `true`，但傳入的資料可能會為 null 或零，而您必須準備一個類型來處理這種可能性。</span><span class="sxs-lookup"><span data-stu-id="781cd-145">Although the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property is set to `true`, the incoming data may be null or zero, and a type must be prepared to handle this possibility.</span></span> <span data-ttu-id="781cd-146">請勿使用 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 做為防止傳入資料損壞的安全性機制。</span><span class="sxs-lookup"><span data-stu-id="781cd-146">Do not use <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> as a security mechanism to protect against bad incoming data.</span></span>  
  
## <a name="omitted-default-values"></a><span data-ttu-id="781cd-147">省略的預設值</span><span class="sxs-lookup"><span data-stu-id="781cd-147">Omitted Default Values</span></span>  
 <span data-ttu-id="781cd-148">可以 （但不建議） 若要設定`EmitDefaultValue`DataMemberAttribute 屬性上的屬性`false`所述，在[資料成員預設值](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="781cd-148">It is possible (although not recommended) to set the `EmitDefaultValue` property on the DataMemberAttribute attribute to `false`, as described in [Data Member Default Values](../../../../docs/framework/wcf/feature-details/data-member-default-values.md).</span></span> <span data-ttu-id="781cd-149">如果這個設定為 `false`，則如果資料成員設定為預設值 (通常為 null 或零)，將不會予以省略。</span><span class="sxs-lookup"><span data-stu-id="781cd-149">If this setting is `false`, the data member will not be emitted if it is set to its default value (usually null or zero).</span></span> <span data-ttu-id="781cd-150">在以下兩方面，這會與不同版本中之必要資料成員不相容：</span><span class="sxs-lookup"><span data-stu-id="781cd-150">This is not compatible with required data members in different versions in two ways:</span></span>  
  
-   <span data-ttu-id="781cd-151">在某個版本內要求具有資料成員的資料合約，無法從不同版本 (其 `EmitDefaultValue` 設定為 `false`) 接收預設 (null 或零) 資料。</span><span class="sxs-lookup"><span data-stu-id="781cd-151">A data contract with a data member that is required in one version cannot receive default (null or zero) data from a different version in which the data member has `EmitDefaultValue` set to `false`.</span></span>  
  
-   <span data-ttu-id="781cd-152">具有 `EmitDefaultValue` 設定為 `false` 的必要資料成員，無法用來序列化其預設值 (null 或零)，但是可以在還原序列化時接收此類的值。</span><span class="sxs-lookup"><span data-stu-id="781cd-152">A required data member that has `EmitDefaultValue` set to `false` cannot be used to serialize its default (null or zero) value, but can receive such a value on deserialization.</span></span> <span data-ttu-id="781cd-153">如此會產生反覆存取的問題 (可以讀入資料，但卻無法接著將相同的資料寫出)。</span><span class="sxs-lookup"><span data-stu-id="781cd-153">This creates a round-tripping problem (data can be read in but the same data cannot then be written out).</span></span> <span data-ttu-id="781cd-154">因此，如果在某個版本內，`IsRequired` 為 `true`，且 `EmitDefaultValue` 為 `false`，則相同的組合應套用至所有其他版本，此類沒有資料合約的版本將能夠產生不會導致反覆存取的值。</span><span class="sxs-lookup"><span data-stu-id="781cd-154">Therefore, if `IsRequired` is `true` and `EmitDefaultValue` is `false` in one version, the same combination should apply to all other versions such that no version of the data contract would be able to produce a value that does not result in a round trip.</span></span>  
  
## <a name="schema-considerations"></a><span data-ttu-id="781cd-155">結構描述的考量</span><span class="sxs-lookup"><span data-stu-id="781cd-155">Schema Considerations</span></span>  
 <span data-ttu-id="781cd-156">如需資料合約型別會產生哪些結構描述的說明，請參閱 < [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="781cd-156">For an explanation of what schema is produced for data contract types, see [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).</span></span>  
  
 <span data-ttu-id="781cd-157">WCF 的結構描述產生的資料合約型別可讓不提供版本控制。</span><span class="sxs-lookup"><span data-stu-id="781cd-157">The schema WCF produces for data contract types makes no provisions for versioning.</span></span> <span data-ttu-id="781cd-158">也就是說，從某些類型的版本所匯出的結構描述，只會包含該版本內存在的資料成員。</span><span class="sxs-lookup"><span data-stu-id="781cd-158">That is, the schema exported from a certain version of a type contains only those data members present in that version.</span></span> <span data-ttu-id="781cd-159">實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面不會變更類型的結構描述。</span><span class="sxs-lookup"><span data-stu-id="781cd-159">Implementing the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface does not change the schema for a type.</span></span>  
  
 <span data-ttu-id="781cd-160">匯出至結構描述的資料成員，預設會做為選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="781cd-160">Data members are exported to the schema as optional elements by default.</span></span> <span data-ttu-id="781cd-161">亦即，`minOccurs` (XML 屬性) 值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="781cd-161">That is, the `minOccurs` (XML attribute) value is set to 0.</span></span> <span data-ttu-id="781cd-162">必要的資料成員會以設定為 1 的 `minOccurs` 匯出。</span><span class="sxs-lookup"><span data-stu-id="781cd-162">Required data members are exported with `minOccurs` set to 1.</span></span>  
  
 <span data-ttu-id="781cd-163">如果要求嚴格遵循結構描述，則許多被視為是不中斷的變更實際上是中斷變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-163">Many of the changes considered to be nonbreaking are actually breaking if strict adherence to the schema is required.</span></span> <span data-ttu-id="781cd-164">在上述範例中，只具有 `CarV1` 項目的 `Model` 執行個體會根據 `CarV2` 結構描述 (即具有 `Model` 和 `Horsepower` 兩者，但兩者皆是選用項目) 進行驗證。</span><span class="sxs-lookup"><span data-stu-id="781cd-164">In the preceding example, a `CarV1` instance with just the `Model` element would validate against the `CarV2` schema (which has both `Model` and `Horsepower`, but both are optional).</span></span> <span data-ttu-id="781cd-165">不過，反向並不成立：`CarV2` 執行個體根據 `CarV1` 結構描述所進行的驗證則可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="781cd-165">However, the reverse is not true: a `CarV2` instance would fail validation against the `CarV1` schema.</span></span>  
  
 <span data-ttu-id="781cd-166">往返還需要一些其他考量。</span><span class="sxs-lookup"><span data-stu-id="781cd-166">Round-tripping also entails some additional considerations.</span></span> <span data-ttu-id="781cd-167">如需詳細資訊，請參閱中的 < 結構描述考量 > 一節[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="781cd-167">For more information, see the "Schema Considerations" section in [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
### <a name="other-permitted-changes"></a><span data-ttu-id="781cd-168">其他允許的變更</span><span class="sxs-lookup"><span data-stu-id="781cd-168">Other Permitted Changes</span></span>  
 <span data-ttu-id="781cd-169">實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面為不中斷變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-169">Implementing the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface is a nonbreaking change.</span></span> <span data-ttu-id="781cd-170">不過，實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 的版本之前的類型版本，並不存在反覆存取支援。</span><span class="sxs-lookup"><span data-stu-id="781cd-170">However, round-tripping support does not exist for versions of the type prior to the version in which <xref:System.Runtime.Serialization.IExtensibleDataObject> was implemented.</span></span> <span data-ttu-id="781cd-171">如需詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="781cd-171">For more information, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="781cd-172">列舉</span><span class="sxs-lookup"><span data-stu-id="781cd-172">Enumerations</span></span>  
 <span data-ttu-id="781cd-173">新增或移除列舉型別成員是中斷變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-173">Adding or removing an enumeration member is a breaking change.</span></span> <span data-ttu-id="781cd-174">變更列舉型別成員的名稱是中斷變更，除非其合約名稱保持為與舊版中使用 `EnumMemberAttribute` 屬性的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="781cd-174">Changing the name of an enumeration member is breaking, unless its contract name is kept the same as in the old version by using the `EnumMemberAttribute` attribute.</span></span> <span data-ttu-id="781cd-175">如需詳細資訊，請參閱 <<c0> [ 列舉型別 Types in Data Contracts](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="781cd-175">For more information, see [Enumeration Types in Data Contracts](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="781cd-176">集合</span><span class="sxs-lookup"><span data-stu-id="781cd-176">Collections</span></span>  
 <span data-ttu-id="781cd-177">大多數的集合變更是不中斷的，因為大部份的集合類型可以在資料合約模型內互相交換。</span><span class="sxs-lookup"><span data-stu-id="781cd-177">Most collection changes are nonbreaking because most collection types are interchangeable with each other in the data contract model.</span></span> <span data-ttu-id="781cd-178">不過，將非自訂的集合進行自訂 (反之亦然) 則是中斷變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-178">However, making a noncustomized collection customized or vice versa is a breaking change.</span></span> <span data-ttu-id="781cd-179">同時，變更集合的自訂設定是中斷變更，也就是變更其資料合約名稱和命名空間、重複元素名稱、主要元素名稱，以及值元素名稱。</span><span class="sxs-lookup"><span data-stu-id="781cd-179">Also, changing the collection's customization settings is a breaking change; that is, changing its data contract name and namespace, repeating element name, key element name, and value element name.</span></span> <span data-ttu-id="781cd-180">如需有關集合自訂的詳細資訊，請參閱[集合 Types in Data Contracts](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="781cd-180">For more information about collection customization, see [Collection Types in Data Contracts](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).</span></span>  
<span data-ttu-id="781cd-181">當然，變更集合之內容的資料合約 (例如，從整數的清單變更為字串的清單) 是中斷變更。</span><span class="sxs-lookup"><span data-stu-id="781cd-181">Naturally, changing the data contract of contents of a collection (for example, changing from a list of integers to a list of strings) is a breaking change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="781cd-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="781cd-182">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.SerializationException>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 [<span data-ttu-id="781cd-183">版本相容序列化回呼</span><span class="sxs-lookup"><span data-stu-id="781cd-183">Version-Tolerant Serialization Callbacks</span></span>](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [<span data-ttu-id="781cd-184">最佳做法：資料合約版本設定</span><span class="sxs-lookup"><span data-stu-id="781cd-184">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [<span data-ttu-id="781cd-185">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="781cd-185">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="781cd-186">資料合約等價</span><span class="sxs-lookup"><span data-stu-id="781cd-186">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="781cd-187">向前相容資料合約</span><span class="sxs-lookup"><span data-stu-id="781cd-187">Forward-Compatible Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
