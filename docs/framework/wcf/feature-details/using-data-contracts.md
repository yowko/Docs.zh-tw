---
title: 使用資料合約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 992f35a9f7406ac161ddb5e31fdaf85756bfe31f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-data-contracts"></a>使用資料合約
「 *資料合約* 」(Data Contract) 是服務與用戶端之間的正式合約，其中會抽象地描述要交換的資料。 也就是說，若要進行通訊，用戶端與服務並不需要共用相同的型別，而只需要共用相同的資料合約。 資料合約會針對每個參數或傳回型別精確地定義哪些資料要序列化 (變成 XML) 才能進行交換。  
  
## <a name="data-contract-basics"></a>資料合約基本概念  
 Windows Communication Foundation (WCF) 會使用預設會呼叫資料合約序列化程式 」 的序列化引擎來序列化和還原序列化 （將它與 XML） 的資料。 包括像是整數和字串的所有 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 基本型別 (Primitive Type)，以及被視為基本型別的特定型別，例如 <xref:System.DateTime> 和 <xref:System.Xml.XmlElement>，都可以不用經過其他準備即加以序列化，而且會被視為具有預設的資料合約。 許多 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別也具有現有的資料合約。 如需可序列化型別的完整清單，請參閱 [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)。  
  
 您建立的新複雜型別必須具有已針對其所定義的資料合約，才能夠進行序列化。 根據預設， <xref:System.Runtime.Serialization.DataContractSerializer> 會推斷資料合約，並且會序列化所有公開可見的型別。 型別的所有公用讀取/寫入屬性 (Property) 和欄位都會序列化。 您可以藉由使用 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>，選擇不序列化成員。 您也可以使用 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute) 明確建立資料合約。 通常將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至該型別即可達成這點。 這個屬性可以套用至類別、結構和列舉型別 (Enumeration)。 然後， <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性必須套用至資料合約型別的各個成員，以表示其為「 *資料成員*」(Data Member)，也就是這個成員應該要加以序列化。 如需詳細資訊，請參閱[可序列化型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)。  
  
### <a name="example"></a>範例  
 下列範例會示範已經明確套用 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 屬性的服務合約 (介面)。 此範例會示範基本型別不需要資料合約，而複雜型別則需要。  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 下列範例會示範如何透過將 `MyTypes.PurchaseOrder` 和 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類別及其成員，以便建立 <xref:System.Runtime.Serialization.DataMemberAttribute> 型別的資料合約。  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>注意  
 下列注意事項提供在建立資料合約時的考慮項目：  
  
-   <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 屬性只有在搭配未標記的型別使用時才會被接受。 其中包含未使用 <xref:System.Runtime.Serialization.DataContractAttribute>、 <xref:System.SerializableAttribute>、 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>或 <xref:System.Runtime.Serialization.EnumMemberAttribute> 屬性其中一個所標記的型別，或未透過任何其他方式 (例如 <xref:System.Xml.Serialization.IXmlSerializable>) 標記為可序列化的型別。  
  
-   您可以將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute) 套用至欄位和屬性 (Property)。  
  
-   成員存取層級 (內部、私密、保護或公用) 不會以任何形式影響資料合約。  
  
-   <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性在套用至靜態成員時會遭到忽略。  
  
-   取得屬性 (property-get) 的程式碼會在進行序列化時呼叫，以便讓屬性資料成員取得要進行序列化之屬性的值。  
  
-   在進行還原序列化時會先建立未初始化的物件，而不會呼叫該型別上的任何建構函式 (Constructor)。 接下來，所有的資料成員都會還原序列化。  
  
-   設定屬性 (property-set) 的程式碼會在進行還原序列化時呼叫，以便讓屬性資料成員設定要進行還原序列化之屬性的值。  
  
-   若是有效的資料合約，該資料合約肯定是可能會序列化其所有資料成員。 如需可序列化型別的完整清單，請參閱 [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)。  
  
     對於泛型型別的處理方式與非泛型型別完全相同。 對於泛型參數沒有特殊的需求。 以下列型別為例：  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 無論用於泛型型別參數 (`T`) 的型別是否為可序列化的型別，這個型別都是可序列化的型別。 由於其一定可以序列化所有的資料成員，所以下列型別只有在泛型型別參數也屬於可序列化時才能進行序列化，如下列程式碼所示。  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 如需定義資料合約的 WCF 服務完整程式碼範例，請參閱 [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) 範例。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [可序列化類型](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [資料合約名稱](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [資料成員順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [資料合約已知類型](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [資料合約版本控制](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [版本相容序列化回呼](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [資料成員預設值](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)  
 [資料合約序列化程式支援的類型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
 [如何：建立類別或結構的基本資料合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
