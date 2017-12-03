---
title: "序列化方針"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a695e10ae9b074f0f9dc913d2f687c82e00475dd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="serialization-guidelines"></a>序列化方針
本文件列出在設計要序列化的 API 時所要考量的指導方針。  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 .NET 提供已針對多個序列化案例最佳化的三個主要序列化技術。 下表列出這些技術以及與這些技術相關的主要 .NET 類型。  
  
|技術|相關類別|備註|  
|----------------|----------------------|-----------|  
|資料合約序列化|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|一般持續性<br /><br /> Web 服務<br /><br /> JSON|  
|XML 序列化|<xref:System.Xml.Serialization.XmlSerializer>|XML 格式 <br />(具有完全控制)|  
|執行階段 - 序列化 (二進位和 SOAP)|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET 遠端處理|  
  
 當您設計新的型別時，您應該決定這些型別必須支援哪些技術 (如果有的話)。 下列指導方針說明如何做出這項決定以及如何提供這類支援。 這些指導方針並不是為了幫助您選擇應該在應用程式或程式庫的實作中使用哪一種序列化技術。 這類指導方針與 API 設計沒有直接的關聯性，所以不在本主題的討論範圍內。  
  
## <a name="guidelines"></a>方針  
  
-   當您設計新的型別時，請務必考量序列化。  
  
     對任何型別而言，序列化都是重要的設計考量，因為程式可能需要保存或傳輸該型別的執行個體。  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a>選擇要支援的正確序列化技術  
 任何給定型別都可以支援零個、一個或多個序列化技術。  
  
-   如果可能需要在 Web 服務中持續保存或使用類型的執行個體，請考慮支援「資料合約序列化」。  
  
-   如果您需要針對序列化類型時所產生之 XML 格式的更大控制權，請考慮支援「XML 序列化」來取代資料合約序列化，或是兩者都支援。  
  
     在您需要使用資料合約序列化所不支援的 XML 建構的某些互通性情況下 (例如，為了產生 XML 屬性)，就可能需要這樣的處理方式。  
  
-   如果類別的執行個體需要橫跨 .NET 遠端處理界限，請考慮支援「執行階段序列化」。  
  
-   請避免針對一般持續性理由來支援執行階段序列化或 XML 序列化。 請改用資料合約序列化。  
  
#### <a name="supporting-data-contract-serialization"></a>支援資料合約序列化  
 類型可以將 <xref:System.Runtime.Serialization.DataContractAttribute> 套用至類型，並將 <xref:System.Runtime.Serialization.DataMemberAttribute> 套用至類型的成員 (欄位和屬性) 來支援資料合約序列化。  
  
 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]  
  
1.  如果可以在部分信任中使用型別，請考慮將型別的資料成員標記為 public。 在完全信任中，資料合約序列化程式可以序列化及還原序列化非 public 型別和成員，但是只有 public 成員可以在部分信任中序列化及還原序列化。  
  
2.  請針對具有 Data-MemberAttribute 的所有屬性實作 getter 和 setter。 資料合約序列化程式需要 getter 和 setter，才能考慮將此型別序列化。 如果此型別不會在部分信任中使用，則其中一個或兩個屬性存取子可以不是 public。  
  
     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]  
  
3.  請考慮針對還原序列化之執行個體的初始化使用序列化回呼。  
  
     當還原序列化物件時，不會呼叫建構函式。 因此，正常建構期間所執行的任何邏輯都需要實作為其中一個「序列化回呼」。  
  
     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]  
  
     <xref:System.Runtime.Serialization.OnDeserializedAttribute> 屬性是最常用的回呼屬性。 此系列中的其他屬性為 <xref:System.Runtime.Serialization.OnDeserializingAttribute>、    
    <xref:System.Runtime.Serialization.OnSerializingAttribute> 和 <xref:System.Runtime.Serialization.OnSerializedAttribute>。 這些屬性可用來分別標記在還原序列化之前、序列化之前以及最後在序列化之後所執行的回呼。  
  
4.  當您還原序列化複雜物件圖形時，請考慮使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 來指示應該使用的具象型別。  
  
     例如，如果還原序列化之資料成員的某個類型以抽象類別來表示，則序列化程式將需要「已知類型」資訊來決定哪一個具象類型要執行個體化以及指派給成員。 如果已知型別不是使用此屬性所指定，它需要明確傳遞給序列化程式 (您可以將已知型別傳遞給序列化程式建構函式來進行這項處理)，或者需要在組態檔中指定已知型別。  
  
     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]  
  
     如果已知類型清單無法以靜態方式得知 (編譯 **Person** 類別時)，**KnownTypeAttribute** 也可指向一個方法，此方法會在執行階段傳回已知類型清單。  
  
5.  當建立或變更可序列化的型別時，請務必考慮回溯相容性與向前相容性。  
  
     請牢記，型別之未來版本的序列化資料流可以還原序列化成該型別的目前版本，反之亦然。 請務必了解資料成員 (即使是 private 和內部成員) 在型別的未來版本中無法變更其名稱、型別或甚至是順序，除非採取特別的步驟，利用資料合約屬性的明確參數來保留合約。在變更可序列化的型別時，請測試序列化的相容性。 請嘗試將新的版本還原序列化成舊的版本，反之亦然。  
  
6.  請考慮實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面來允許在型別的不同版本之間往返。  
  
     此介面可讓序列化程式確保往返期間不會有任何資料遺失。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> 屬性會儲存來自目前版本未知之型別的未來版本中的任何資料。 當目前版本接著序列化並還原序列化成未來版本時，其他資料將會透過 **ExtensionData** 屬性值在序列化資料流中提供。  
  
     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]  
  
     如需詳細資訊，請參閱[向前相容資料合約](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。  
  
#### <a name="supporting-xml-serialization"></a>支援 XML 序列化  
 資料合約序列化是 .NET Framework 中的主要 (預設) 序列化技術，但是資料合約序列化不支援一些序列化情節。 例如，它無法讓您完全控制序列化程式所產生或使用之 XML 的形狀。 如果需要這樣的精確控制，必須使用「XML 序列化」，而且您需要設計您的類型來支援這項序列化技術。  
  
1.  請避免專門為了 XML 序列化來設計型別，除非您有非常強烈的理由為了控制所產生之 XML 的形狀。 這項序列化技術已經由前一節所討論的資料合約序列化所取代。  
  
     換句話說，請勿將 <xref:System.Runtime.Serialization> 命名空間中的屬性套用至新的型別，除非您知道此型別將會搭配 XML 序列化使用。 下列範例示範如何使用 **System.Xml.Serialization** 來控制所產生 XML 的圖形。  
  
     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]  
  
2.  如果您希望對序列化 XML 的形狀有更大的控制權，而不是套用 XML 序列化屬性來使用提供的控制權，請考慮實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面。 兩個介面方法<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>和<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>，讓您完整控制序列化的 XML 資料流。 您也可以藉由套用 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性來控制為此型別產生的 XML 結構描述。  
  
#### <a name="supporting-runtime-serialization"></a>支援執行階段序列化  
 「執行階段序列化」是 .NET 遠端處理所使用的技術。 如果您認為您的型別將會使用 .NET 遠端處理來傳輸，則需要確定型別有支援執行階段序列化。  
  
 「執行階段序列化」的基本支援可以藉由套用 <xref:System.SerializableAttribute> 屬性來提供，而更進階的案例則牽涉到實作簡單的「執行階段可序列化模式」(實作 -<xref:System.Runtime.Serialization.ISerializable> 並提供序列化建構函式)。  
  
1.  如果您的型別將會搭配 .NET 遠端處理使用，請考慮支援執行階段序列化。 例如，<xref:System.AddIn> 命名空間會使用 .NET 遠端處理，因此在 **System.AddIn** 增益集之間交換的所有類型都需要支援執行階段序列化。  
  
     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]  
  
2.  如果您想要擁有序列化處理序的完整控制權，請考慮實作「執行階段可序列化模式」。 例如，如果您想要在資料序列化或還原序列化時加以轉換。  
  
     此模式非常簡單。 您只需要實作 <xref:System.Runtime.Serialization.ISerializable> 介面，並提供還原序列化物件時使用的特殊建構函式。  
  
     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]  
  
3.  請讓序列化建構函式處於受保護狀態，並提供兩個參數，這兩個參數的型別與名稱與此處範例所顯示的一模一樣。  
  
     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]  
  
4.  請務必明確實作 ISerializable 成員。  
  
     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]  
  
5.  DO 會將連結要求套用至 **ISerializable.GetObjectData** 實作。 如此可確保只有完全受信任的核心和執行階段序列化程式可存取此成員。  
  
     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]  
  
## <a name="see-also"></a>請參閱  
 [使用資料合約](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [資料合約序列化程式](../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 [資料合約序列化程式所支援的類型](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
 [二進位序列化](binary-serialization.md)  
 [遠端物件](http://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)  
 [XML 和 SOAP 序列化](xml-and-soap-serialization.md)  
 [安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)
