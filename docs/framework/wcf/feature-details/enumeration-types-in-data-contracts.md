---
title: 資料合約中的列舉型別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 1837a3630424ff2a9ee4a84e9ed63f44a06bbecf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309637"
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="8ca98-102">資料合約中的列舉型別</span><span class="sxs-lookup"><span data-stu-id="8ca98-102">Enumeration Types in Data Contracts</span></span>
<span data-ttu-id="8ca98-103">列舉可以在資料合約模型中表示。</span><span class="sxs-lookup"><span data-stu-id="8ca98-103">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="8ca98-104">本主題將逐步介紹幾個範例，說明程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="8ca98-104">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="8ca98-105">列舉基本知識</span><span class="sxs-lookup"><span data-stu-id="8ca98-105">Enumeration Basics</span></span>  
 <span data-ttu-id="8ca98-106">使用資料合約模型中列舉型別的其中一種方法是，將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至型別。</span><span class="sxs-lookup"><span data-stu-id="8ca98-106">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="8ca98-107">然後您必須將 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性套用至必須包含在資料合約中的各個成員。</span><span class="sxs-lookup"><span data-stu-id="8ca98-107">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="8ca98-108">以下範例顯示兩個類別。</span><span class="sxs-lookup"><span data-stu-id="8ca98-108">The following example shows two classes.</span></span> <span data-ttu-id="8ca98-109">第一個是使用列舉，而第二個是定義列舉。</span><span class="sxs-lookup"><span data-stu-id="8ca98-109">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="8ca98-110">只有 `Car` 欄位設定為值 `condition`、`New` 或 `Used` 的其中之一時，才可以傳送或接收 `Rental` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8ca98-110">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="8ca98-111">如果 `condition` 是 `Broken` 或 `Stolen`，便會擲回 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="8ca98-111">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="8ca98-112">您可以和往常一樣，對列舉資料合約使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性 (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 和 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>)。</span><span class="sxs-lookup"><span data-stu-id="8ca98-112">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="8ca98-113">列舉成員值</span><span class="sxs-lookup"><span data-stu-id="8ca98-113">Enumeration Member Values</span></span>  
 <span data-ttu-id="8ca98-114">資料合約通常包括列舉成員名稱，而不是數值。</span><span class="sxs-lookup"><span data-stu-id="8ca98-114">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="8ca98-115">不過，使用時的資料合約模型中，如果接收端的 WCF 用戶端，匯出的結構描述會保存數值。</span><span class="sxs-lookup"><span data-stu-id="8ca98-115">However, when using the data contract model, if the receiving side is a WCF client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="8ca98-116">請注意，這不是使用時[使用 XmlSerializer 類別](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)。</span><span class="sxs-lookup"><span data-stu-id="8ca98-116">Note that this is not the case when using the [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="8ca98-117">在前例中，如果 `condition` 設定為 `Used` 且資料序列化為 XML，結果 XML 就是 `<condition>Used</condition>` 而不是 `<condition>1</condition>`。</span><span class="sxs-lookup"><span data-stu-id="8ca98-117">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="8ca98-118">因此，下列資料合約相等於 `CarConditionEnum` 的資料合約。</span><span class="sxs-lookup"><span data-stu-id="8ca98-118">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="8ca98-119">例如，您可以在傳送端上使用 `CarConditionEnum`，而在接收端上使用 `CarConditionWithNumbers`。</span><span class="sxs-lookup"><span data-stu-id="8ca98-119">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="8ca98-120">雖然傳送端對 `Used` 使用 "1" 值，而接收端使用 "20" 值，但是 XML 表示法對兩端都是 `<condition>Used</condition>`。</span><span class="sxs-lookup"><span data-stu-id="8ca98-120">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="8ca98-121">如果要包含在資料合約中，您必須套用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8ca98-121">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="8ca98-122">在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中，您永遠可以對列舉套用特殊值 0 (零)，這也是任何列舉的預設值。</span><span class="sxs-lookup"><span data-stu-id="8ca98-122">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="8ca98-123">然而，即使這個特殊的零值也無法序列化，除非它標上 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8ca98-123">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="8ca98-124">這種情形有兩個例外狀況：</span><span class="sxs-lookup"><span data-stu-id="8ca98-124">There are two exceptions to this:</span></span>  
  
-   <span data-ttu-id="8ca98-125">旗標列舉 (本主題稍後說明)。</span><span class="sxs-lookup"><span data-stu-id="8ca98-125">Flag enumerations (discussed later in this topic).</span></span>  
  
-   <span data-ttu-id="8ca98-126"><xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 屬性設定為 `false` 的列舉資料成員 (在這種情況中，只會從序列化的資料中省略值為零的列舉)。</span><span class="sxs-lookup"><span data-stu-id="8ca98-126">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="8ca98-127">自訂列舉成員值</span><span class="sxs-lookup"><span data-stu-id="8ca98-127">Customizing Enumeration Member Values</span></span>  
 <span data-ttu-id="8ca98-128">您可以使用 <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> 屬性 (Attribute) 的 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性 (Property) 來自訂列舉成員值，該值會成為資料合約的一部分。</span><span class="sxs-lookup"><span data-stu-id="8ca98-128">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="8ca98-129">例如，下列資料合約也相等於 `CarConditionEnum` 的資料合約。</span><span class="sxs-lookup"><span data-stu-id="8ca98-129">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="8ca98-130">當序列化時，`PreviouslyOwned` 的值具有 XML 表示法 `<condition>Used</condition>`。</span><span class="sxs-lookup"><span data-stu-id="8ca98-130">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="8ca98-131">簡單列舉</span><span class="sxs-lookup"><span data-stu-id="8ca98-131">Simple Enumerations</span></span>  
 <span data-ttu-id="8ca98-132">您也可以序列化列舉型別至尚未套用的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8ca98-132">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="8ca98-133">此類列舉型別的處理方式完全如先前所述，除了每個成員 (未套用 <xref:System.NonSerializedAttribute> 屬性) 會被視為已套用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性之外。</span><span class="sxs-lookup"><span data-stu-id="8ca98-133">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="8ca98-134">例如，以下列舉隱含具有相等於上一個 `CarConditionEnum` 範例的資料合約。</span><span class="sxs-lookup"><span data-stu-id="8ca98-134">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="8ca98-135">當您不需要自訂列舉的資料合約名稱和命名空間和列舉成員值時，可以使用簡單列舉。</span><span class="sxs-lookup"><span data-stu-id="8ca98-135">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="8ca98-136">簡單列舉的注意事項</span><span class="sxs-lookup"><span data-stu-id="8ca98-136">Notes on Simple Enumerations</span></span>  
 <span data-ttu-id="8ca98-137">將 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性套用至簡單列舉沒有作用。</span><span class="sxs-lookup"><span data-stu-id="8ca98-137">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="8ca98-138"><xref:System.SerializableAttribute> 屬性是否套用至列舉並沒有差別。</span><span class="sxs-lookup"><span data-stu-id="8ca98-138">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="8ca98-139">事實上 <xref:System.Runtime.Serialization.DataContractSerializer> 類別允許套用至列舉成員的 <xref:System.NonSerializedAttribute> 屬性，與 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 的行為是不同的。</span><span class="sxs-lookup"><span data-stu-id="8ca98-139">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="8ca98-140">這兩個序列化程式都會略過 <xref:System.NonSerializedAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8ca98-140">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="8ca98-141">旗標列舉</span><span class="sxs-lookup"><span data-stu-id="8ca98-141">Flag Enumerations</span></span>  
 <span data-ttu-id="8ca98-142">您可以將 <xref:System.FlagsAttribute> 屬性套用至列舉。</span><span class="sxs-lookup"><span data-stu-id="8ca98-142">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="8ca98-143">在這種情況下，可以同時傳送或接收零或更多列舉值的清單。</span><span class="sxs-lookup"><span data-stu-id="8ca98-143">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="8ca98-144">如果要執行這項操作，請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至旗標列舉，然後將所有為二之次方的成員以 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性標示。</span><span class="sxs-lookup"><span data-stu-id="8ca98-144">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="8ca98-145">請注意，如果要使用旗標列舉，級數必須是 2 的次方的不中斷序列 (例如，1、2、4、8、16、32、64)。</span><span class="sxs-lookup"><span data-stu-id="8ca98-145">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="8ca98-146">下列步驟適用於傳送旗標的列舉值：</span><span class="sxs-lookup"><span data-stu-id="8ca98-146">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1. <span data-ttu-id="8ca98-147">請嘗試尋找對應至數值的列舉成員 (已套用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="8ca98-147">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="8ca98-148">如果找到，請傳送只包含該成員的清單。</span><span class="sxs-lookup"><span data-stu-id="8ca98-148">If found, send a list that contains just that member.</span></span>  
  
2. <span data-ttu-id="8ca98-149">請嘗試將數值中斷至某個總和，以具有對應至該總和之各部分的列舉成員 (每個都套用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="8ca98-149">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="8ca98-150">傳送所有這些成員的清單。</span><span class="sxs-lookup"><span data-stu-id="8ca98-150">Send the list of all these members.</span></span> <span data-ttu-id="8ca98-151">請注意，*窮盡演算法*用來尋找此類總和，因此沒有此類總和位於，即使它存在於不保證。</span><span class="sxs-lookup"><span data-stu-id="8ca98-151">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="8ca98-152">如果要避免這個問題，請確保列舉成員的數值是二的次方。</span><span class="sxs-lookup"><span data-stu-id="8ca98-152">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3. <span data-ttu-id="8ca98-153">如果上述兩個步驟失敗，且數值非零，請擲回 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="8ca98-153">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="8ca98-154">如果數值為零，則傳送空白清單。</span><span class="sxs-lookup"><span data-stu-id="8ca98-154">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8ca98-155">範例</span><span class="sxs-lookup"><span data-stu-id="8ca98-155">Example</span></span>  
 <span data-ttu-id="8ca98-156">下面的列舉範例可用於旗標作業中。</span><span class="sxs-lookup"><span data-stu-id="8ca98-156">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="8ca98-157">下列範例值會依指示進行序列化。</span><span class="sxs-lookup"><span data-stu-id="8ca98-157">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8ca98-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ca98-158">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="8ca98-159">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="8ca98-159">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="8ca98-160">指定服務合約中的資料傳輸</span><span class="sxs-lookup"><span data-stu-id="8ca98-160">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
