---
title: 資料合約中的列舉型別
description: 瞭解資料合約模型如何將列舉表達為 WFC 程式設計模型的一部分。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
ms.openlocfilehash: 88bf2513435a9c00cf11a0681b32871992c8d2b2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276655"
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="12a98-103">資料合約中的列舉型別</span><span class="sxs-lookup"><span data-stu-id="12a98-103">Enumeration Types in Data Contracts</span></span>

<span data-ttu-id="12a98-104">列舉可以在資料合約模型中表示。</span><span class="sxs-lookup"><span data-stu-id="12a98-104">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="12a98-105">本主題將逐步介紹幾個範例，說明程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="12a98-105">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="12a98-106">列舉基本知識</span><span class="sxs-lookup"><span data-stu-id="12a98-106">Enumeration Basics</span></span>  

 <span data-ttu-id="12a98-107">使用資料合約模型中列舉型別的其中一種方法是，將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至型別。</span><span class="sxs-lookup"><span data-stu-id="12a98-107">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="12a98-108">然後您必須將 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性套用至必須包含在資料合約中的各個成員。</span><span class="sxs-lookup"><span data-stu-id="12a98-108">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="12a98-109">以下範例顯示兩個類別。</span><span class="sxs-lookup"><span data-stu-id="12a98-109">The following example shows two classes.</span></span> <span data-ttu-id="12a98-110">第一個是使用列舉，而第二個是定義列舉。</span><span class="sxs-lookup"><span data-stu-id="12a98-110">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="12a98-111">只有 `Car` 欄位設定為值 `condition`、`New` 或 `Used` 的其中之一時，才可以傳送或接收 `Rental` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="12a98-111">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="12a98-112">如果 `condition` 是 `Broken` 或 `Stolen`，便會擲回 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="12a98-112">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="12a98-113">您可以和往常一樣，對列舉資料合約使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性 (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 和 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>)。</span><span class="sxs-lookup"><span data-stu-id="12a98-113">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="12a98-114">列舉成員值</span><span class="sxs-lookup"><span data-stu-id="12a98-114">Enumeration Member Values</span></span>  

 <span data-ttu-id="12a98-115">資料合約通常包括列舉成員名稱，而不是數值。</span><span class="sxs-lookup"><span data-stu-id="12a98-115">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="12a98-116">不過，當使用資料合約模型時，如果接收端是 WCF 用戶端，則匯出的架構會保留數值。</span><span class="sxs-lookup"><span data-stu-id="12a98-116">However, when using the data contract model, if the receiving side is a WCF client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="12a98-117">請注意，使用 [XmlSerializer 類別](using-the-xmlserializer-class.md)時不會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="12a98-117">Note that this is not the case when using the [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="12a98-118">在前例中，如果 `condition` 設定為 `Used` 且資料序列化為 XML，結果 XML 就是 `<condition>Used</condition>` 而不是 `<condition>1</condition>`。</span><span class="sxs-lookup"><span data-stu-id="12a98-118">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="12a98-119">因此，下列資料合約相等於 `CarConditionEnum` 的資料合約。</span><span class="sxs-lookup"><span data-stu-id="12a98-119">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="12a98-120">例如，您可以在傳送端上使用 `CarConditionEnum`，而在接收端上使用 `CarConditionWithNumbers`。</span><span class="sxs-lookup"><span data-stu-id="12a98-120">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="12a98-121">雖然傳送端對 `Used` 使用 "1" 值，而接收端使用 "20" 值，但是 XML 表示法對兩端都是 `<condition>Used</condition>`。</span><span class="sxs-lookup"><span data-stu-id="12a98-121">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="12a98-122">如果要包含在資料合約中，您必須套用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="12a98-122">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="12a98-123">在 .NET Framework 中，您一律可以將特殊值 0 (零) 套用至列舉，這也是任何列舉的預設值。</span><span class="sxs-lookup"><span data-stu-id="12a98-123">In the .NET Framework, you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="12a98-124">然而，即使這個特殊的零值也無法序列化，除非它標上 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="12a98-124">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="12a98-125">這種情形有兩個例外狀況：</span><span class="sxs-lookup"><span data-stu-id="12a98-125">There are two exceptions to this:</span></span>  
  
- <span data-ttu-id="12a98-126">旗標列舉 (本主題稍後說明)。</span><span class="sxs-lookup"><span data-stu-id="12a98-126">Flag enumerations (discussed later in this topic).</span></span>  
  
- <span data-ttu-id="12a98-127"><xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> 屬性設定為 `false` 的列舉資料成員 (在這種情況中，只會從序列化的資料中省略值為零的列舉)。</span><span class="sxs-lookup"><span data-stu-id="12a98-127">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="12a98-128">自訂列舉成員值</span><span class="sxs-lookup"><span data-stu-id="12a98-128">Customizing Enumeration Member Values</span></span>  

 <span data-ttu-id="12a98-129">您可以使用 <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> 屬性 (Attribute) 的 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性 (Property) 來自訂列舉成員值，該值會成為資料合約的一部分。</span><span class="sxs-lookup"><span data-stu-id="12a98-129">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="12a98-130">例如，下列資料合約也相等於 `CarConditionEnum` 的資料合約。</span><span class="sxs-lookup"><span data-stu-id="12a98-130">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="12a98-131">當序列化時，`PreviouslyOwned` 的值具有 XML 表示法 `<condition>Used</condition>`。</span><span class="sxs-lookup"><span data-stu-id="12a98-131">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="12a98-132">簡單列舉</span><span class="sxs-lookup"><span data-stu-id="12a98-132">Simple Enumerations</span></span>  

 <span data-ttu-id="12a98-133">您也可以序列化列舉型別至尚未套用的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="12a98-133">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="12a98-134">此類列舉型別的處理方式完全如先前所述，除了每個成員 (未套用 <xref:System.NonSerializedAttribute> 屬性) 會被視為已套用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性之外。</span><span class="sxs-lookup"><span data-stu-id="12a98-134">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="12a98-135">例如，以下列舉隱含具有相等於上一個 `CarConditionEnum` 範例的資料合約。</span><span class="sxs-lookup"><span data-stu-id="12a98-135">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="12a98-136">當您不需要自訂列舉的資料合約名稱和命名空間和列舉成員值時，可以使用簡單列舉。</span><span class="sxs-lookup"><span data-stu-id="12a98-136">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="12a98-137">簡單列舉的注意事項</span><span class="sxs-lookup"><span data-stu-id="12a98-137">Notes on Simple Enumerations</span></span>  

 <span data-ttu-id="12a98-138">將 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性套用至簡單列舉沒有作用。</span><span class="sxs-lookup"><span data-stu-id="12a98-138">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="12a98-139"><xref:System.SerializableAttribute> 屬性是否套用至列舉並沒有差別。</span><span class="sxs-lookup"><span data-stu-id="12a98-139">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="12a98-140">事實上 <xref:System.Runtime.Serialization.DataContractSerializer> 類別允許套用至列舉成員的 <xref:System.NonSerializedAttribute> 屬性，與 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 的行為是不同的。</span><span class="sxs-lookup"><span data-stu-id="12a98-140">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="12a98-141">這兩個序列化程式都會略過 <xref:System.NonSerializedAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="12a98-141">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="12a98-142">旗標列舉</span><span class="sxs-lookup"><span data-stu-id="12a98-142">Flag Enumerations</span></span>  

 <span data-ttu-id="12a98-143">您可以將 <xref:System.FlagsAttribute> 屬性套用至列舉。</span><span class="sxs-lookup"><span data-stu-id="12a98-143">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="12a98-144">在這種情況下，可以同時傳送或接收零或更多列舉值的清單。</span><span class="sxs-lookup"><span data-stu-id="12a98-144">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="12a98-145">如果要執行這項操作，請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至旗標列舉，然後將所有為二之次方的成員以 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性標示。</span><span class="sxs-lookup"><span data-stu-id="12a98-145">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="12a98-146">請注意，如果要使用旗標列舉，級數必須是 2 的次方的不中斷序列 (例如，1、2、4、8、16、32、64)。</span><span class="sxs-lookup"><span data-stu-id="12a98-146">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="12a98-147">下列步驟適用於傳送旗標的列舉值：</span><span class="sxs-lookup"><span data-stu-id="12a98-147">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1. <span data-ttu-id="12a98-148">請嘗試尋找對應至數值的列舉成員 (已套用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="12a98-148">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="12a98-149">如果找到，請傳送只包含該成員的清單。</span><span class="sxs-lookup"><span data-stu-id="12a98-149">If found, send a list that contains just that member.</span></span>  
  
2. <span data-ttu-id="12a98-150">請嘗試將數值中斷至某個總和，以具有對應至該總和之各部分的列舉成員 (每個都套用 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="12a98-150">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="12a98-151">傳送所有這些成員的清單。</span><span class="sxs-lookup"><span data-stu-id="12a98-151">Send the list of all these members.</span></span> <span data-ttu-id="12a98-152">請注意，使用 *貪婪演算法* 來尋找這類總和，因此不保證即使存在，也不會發現這類的總和。</span><span class="sxs-lookup"><span data-stu-id="12a98-152">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="12a98-153">如果要避免這個問題，請確保列舉成員的數值是二的次方。</span><span class="sxs-lookup"><span data-stu-id="12a98-153">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3. <span data-ttu-id="12a98-154">如果上述兩個步驟失敗，且數值非零，請擲回 <xref:System.Runtime.Serialization.SerializationException>。</span><span class="sxs-lookup"><span data-stu-id="12a98-154">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="12a98-155">如果數值為零，則傳送空白清單。</span><span class="sxs-lookup"><span data-stu-id="12a98-155">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="12a98-156">範例</span><span class="sxs-lookup"><span data-stu-id="12a98-156">Example</span></span>  

 <span data-ttu-id="12a98-157">下面的列舉範例可用於旗標作業中。</span><span class="sxs-lookup"><span data-stu-id="12a98-157">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="12a98-158">下列範例值會依指示進行序列化。</span><span class="sxs-lookup"><span data-stu-id="12a98-158">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="12a98-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12a98-159">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="12a98-160">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="12a98-160">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="12a98-161">指定服務合約中的資料傳輸</span><span class="sxs-lookup"><span data-stu-id="12a98-161">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)
