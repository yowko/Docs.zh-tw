---
title: "資料合約版本控制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
caps.latest.revision: "35"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 58e88e319da6d78071293ce92bb7e9ebb33224bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="data-contract-versioning"></a>資料合約版本控制
隨著應用程式的發展，您也必須變更服務所使用的資料合約。 本主題說明如何設定資料合約的版本。 本主題描述資料合約版本控制的機制。 如需完整的概觀和規定的版本控制指導方針，請參閱[最佳做法： 資料合約版本控制](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)。  
  
## <a name="breaking-vs-nonbreaking-changes"></a>中斷與不中斷變更的比較  
 資料合約的變更可以採用中斷或不中斷的方式進行。 當資料合約以不中斷的方式變更時，使用舊版合約的應用程式可以與使用新版合約的應用程式通訊，而使用新版合約的應用程式可以與使用舊版合約的應用程式通訊。 相反的，中斷變更則會阻止單向或雙向的通訊。  
  
 任何對類型的變更若不會影響其傳輸和接收的方式，則都是不中斷的變更。 此類的變更並不會改變資料合約，只會改變基礎型別。 例如，如果您接著將 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性設定為舊版的名稱，則您就可以使用不中斷方式變更欄位的名稱。 下列程式碼說明資料合約的第 1 版。  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 下列程式碼示範不中斷變更。  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 某些變更會修改傳輸的資料，但可能會、也可能不會中斷。 下列的變更則一定會中斷：  
  
-   變更資料合約的 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 或 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> 值。  
  
-   使用 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性變更資料成員的順序。  
  
-   重新命名資料成員。  
  
-   變更資料成員的資料合約。 例如，將資料成員的型別從整數變更為字串，或從具有名為 "Customer" 資料合約的型別變更成具有名為 "Person" 資料合約的型別。  
  
 以下變更是允許的。  
  
## <a name="adding-and-removing-data-members"></a>新增及移除資料成員  
 大部份的情況下，新增或移除資料成員不是採用中斷變更的方式，除非您要求嚴格的結構描述有效性 (根據舊結構描述驗證新執行個體)。  
  
 在將具有額外欄位的類型還原序列化為具有缺少欄位的類型時，則會忽略額外的資訊 (也可能儲存往返進行; 如需詳細資訊，請參閱[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md))。  
  
 在將缺少欄位的類型還原序列化為具有額外欄位的類型時，額外欄位會保留其預設值，通常為零或 `null` (預設值可能會變更; 如需詳細資訊，請參閱[版本相容序列化回呼](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)。)  
  
 例如，您可以在用戶端上使用 `CarV1` 類別，並在服務上使用 `CarV2` 類別，或者可以在服務上使用 `CarV1` 類別，而在用戶端上使用 `CarV2` 類別。  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 第 2 版的端點可以成功地將資料傳送至第 1 版的端點。 序列化第 2 版的 `Car` 資料合約，會產生與下面類似的 XML。  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 第 1 版上的還原序列化引擎找不到與 `HorsePower` 欄位相符的資料成員，然後便捨棄該資料。  
  
 同時，第 1 版的端點可以將資料傳送至第 2 版的端點。 序列化第 1 版的 `Car` 資料合約，會產生與下列類似的 XML。  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 因為傳入的 XML 未包含符合的資料，因此第 2 版的還原序列化程式不知道要將 `HorsePower` 欄位設定為什麼。 相反的，該欄位會設為預設值 0。  
  
## <a name="required-data-members"></a>必要的資料成員  
 將 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性設定為 `true`，即可將資料成員標記為必要項。 如果在還原序列化時遺失了必要的資料，則會擲回例外狀況，而不是將該資料成員設定為預設值。  
  
 新增必要的資料成員是一種中斷變更。 也就是，較新的類型仍舊可以傳送至使用舊類型的端點，而不是將較舊的類型傳送至使用新類型的端點。 將任何舊版內已標記為必要項之資料成員移除，也是一種中斷變更。  
  
 將 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性從 `true` 變更為 `false` 的動作是不中斷變更，但是將其從 `false` 變更為 `true` 的動作則可能會是中斷變更 (如果任何舊版的類型未含有所討論的資料成員)。  
  
> [!NOTE]
>  雖然將 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性設定為 `true`，但傳入的資料可能會為 null 或零，而您必須準備一個類型來處理這種可能性。 請勿使用 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 做為防止傳入資料損壞的安全性機制。  
  
## <a name="omitted-default-values"></a>省略的預設值  
 很可能 （雖然不建議） 若要設定`EmitDefaultValue`DataMemberAttribute 屬性上的屬性`false`中所述，[資料成員預設值](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)。 如果這個設定為 `false`，則如果資料成員設定為預設值 (通常為 null 或零)，將不會予以省略。 在以下兩方面，這會與不同版本中之必要資料成員不相容：  
  
-   在某個版本內要求具有資料成員的資料合約，無法從不同版本 (其 `EmitDefaultValue` 設定為 `false`) 接收預設 (null 或零) 資料。  
  
-   具有 `EmitDefaultValue` 設定為 `false` 的必要資料成員，無法用來序列化其預設值 (null 或零)，但是可以在還原序列化時接收此類的值。 如此會產生反覆存取的問題 (可以讀入資料，但卻無法接著將相同的資料寫出)。 因此，如果在某個版本內，`IsRequired` 為 `true`，且 `EmitDefaultValue` 為 `false`，則相同的組合應套用至所有其他版本，此類沒有資料合約的版本將能夠產生不會導致反覆存取的值。  
  
## <a name="schema-considerations"></a>結構描述的考量  
 如需何種結構描述產生資料合約類型的說明，請參閱[資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。  
  
 為資料合約類型產生的結構描述 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]不提供版本控制。 也就是說，從某些類型的版本所匯出的結構描述，只會包含該版本內存在的資料成員。 實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面不會變更類型的結構描述。  
  
 匯出至結構描述的資料成員，預設會做為選擇性項目。 亦即，`minOccurs` (XML 屬性) 值設定為 0。 必要的資料成員會以設定為 1 的 `minOccurs` 匯出。  
  
 如果要求嚴格遵循結構描述，則許多被視為是不中斷的變更實際上是中斷變更。 在上述範例中，只具有 `CarV1` 項目的 `Model` 執行個體會根據 `CarV2` 結構描述 (即具有 `Model` 和 `Horsepower` 兩者，但兩者皆是選用項目) 進行驗證。 不過，反向並不成立：`CarV2` 執行個體根據 `CarV1` 結構描述所進行的驗證則可能會失敗。  
  
 往返還需要一些其他考量。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「 結構描述考量 > 一節中[向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。  
  
### <a name="other-permitted-changes"></a>其他允許的變更  
 實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面為不中斷變更。 不過，實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 的版本之前的類型版本，並不存在反覆存取支援。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。  
  
## <a name="enumerations"></a>列舉  
 新增或移除列舉型別成員是中斷變更。 變更列舉型別成員的名稱是中斷變更，除非其合約名稱保持為與舊版中使用 `EnumMemberAtttribute` 屬性的名稱相同。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][列舉資料合約中的型別](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)。  
  
## <a name="collections"></a>集合  
 大多數的集合變更是不中斷的，因為大部份的集合類型可以在資料合約模型內互相交換。 不過，將非自訂的集合進行自訂 (反之亦然) 則是中斷變更。 同時，變更集合的自訂設定是中斷變更，也就是變更其資料合約名稱和命名空間、重複元素名稱、主要元素名稱，以及值元素名稱。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]集合自訂化，請參閱[集合資料合約中的型別](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)。  
當然，變更集合之內容的資料合約 (例如，從整數的清單變更為字串的清單) 是中斷變更。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.SerializationException>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 [版本相容序列化回呼](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [最佳做法：資料合約版本設定](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
