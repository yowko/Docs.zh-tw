---
title: Serialization1
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db06feefdd9697fd53d64bce60ae11c7e74f8c88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578062"
---
# <a name="serialization"></a>序列化
序列化是將物件轉換成可以輕易地保存或傳輸之格式的程序。 例如，您可以將物件序列化、 傳輸透過網際網路使用 HTTP，並還原序列化該目的地電腦上。  
  
 .NET Framework 提供三種主要的序列化技術，適用於各種序列化案例。 下表列出這些技術以及與這些技術相關的主要 Framework 型別。  
  
|**技術名稱**|**主要類型**|**案例**|  
|-------------------------|--------------------|-------------------|  
|**資料合約序列化**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|一般持續性<br />Web 服務<br />JSON|  
|**XML 序列化**|<xref:System.Xml.Serialization.XmlSerializer>|XML 格式的 XML 外觀的完整控制權|  
|**執行階段序列化 （二進位檔和 SOAP）**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET 遠端處理|  
  
 **✓ DO**考慮序列化，當您設計新的類型。  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>選擇要支援的正確序列化技術  
 **✓ CONSIDER**支援資料合約序列化，如果您的型別執行個體可能需要保存或用於 Web 服務。  
  
 **✓ CONSIDER**支援之 XML 序列化，而不是，或除了資料合約序列化，如果您需要更充分掌控型別序列化時所產生的 XML 格式。  
  
 這可能需要一些不支援資料合約序列化，比方說，若要產生的 XML 屬性的互通性案例中，您需要使用 XML 建構中。  
  
 **✓ CONSIDER**支援執行階段序列化，如果需要行經.NET 遠端處理界限類型執行個體。  
  
 **X AVOID**支援執行階段序列化或 XML 序列化，只會針對一般的持續性的原因。 偏好改為使用資料合約序列化。  
  
## <a name="supporting-data-contract-serialization"></a>支援資料合約序列化  
 型別可以藉由套用支援資料合約序列化<xref:System.Runtime.Serialization.DataContractAttribute>型別和<xref:System.Runtime.Serialization.DataMemberAttribute>類型成員 （欄位和屬性）。  
  
 **✓ CONSIDER**標示的型別公開的資料成員，如果型別可以用在部分信任中。  
  
 在完全信任，資料合約序列化程式可以序列化和還原序列化非公用類型和成員，但只有公用成員可以序列化，並且在部分信任中還原序列化。  
  
 **✓ DO**實作上擁有的所有屬性的 getter 和 setter <xref:System.Runtime.Serialization.DataMemberAttribute>。 資料合約序列化程式會要求 getter 和 setter，才會被視為可序列化類型。 （在.NET Framework 3.5 SP1，有些集合屬性可以是僅。）如果此型別不會在部分信任中使用，則其中一個或兩個屬性存取子可以不是 public。  
  
 **✓ CONSIDER**序列化回呼使用已還原序列化的執行個體的初始設定。  
  
 當還原序列化物件時，不會呼叫建構函式。 （沒有規則的例外狀況。 建構函式的集合標記為<xref:System.Runtime.Serialization.CollectionDataContractAttribute>會還原序列化期間呼叫。)因此，任何標準建構期間執行的邏輯必須實作為其中一個序列化回呼。  
  
 `OnDeserializedAttribute` 是最常使用的回呼屬性。 此系列中的其他屬性為 <xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute> 和 <xref:System.Runtime.Serialization.OnSerializedAttribute>。 這些屬性可用來分別標記在還原序列化之前、序列化之前以及最後在序列化之後所執行的回呼。  
  
 **✓ CONSIDER**使用<xref:System.Runtime.Serialization.KnownTypeAttribute>表示還原序列化複雜物件圖形時，應使用的具象類型。  
  
 **✓ DO**考慮向後和向前相容性時建立或變更可序列化型別。  
  
 請牢記，型別之未來版本的序列化資料流可以還原序列化成該型別的目前版本，反之亦然。  
  
 請確定您了解，資料成員，即使私用和內部的無法變更其名稱、 類型或即使它們在未來版本的型別中的順序除非特別注意會被保留合約使用明確的參數，對資料合約屬性.  
  
 變更可序列化型別時，請測試相容性的序列化。 請嘗試將新的版本還原序列化成舊的版本，反之亦然。  
  
 **✓ CONSIDER**實作<xref:System.Runtime.Serialization.IExtensibleDataObject>允許之類型的不同版本之間的往返。  
  
 此介面可讓序列化程式確保往返期間不會有任何資料遺失。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType>屬性用來儲存任何資料，從未來版本的最新版本，無法辨識的型別，因此它不能將它儲存在其資料成員。 當目前的版本是後續序列化和還原序列化到未來的版本時，其他資料可序列化資料流中使用。  
  
## <a name="supporting-xml-serialization"></a>支援 XML 序列化  
 資料合約序列化即為主要 （預設值） 的序列化技術，在.NET Framework 中，但是有資料合約序列化不支援的序列化情況。 例如，它無法讓您完全控制序列化程式所產生或使用之 XML 的形狀。 如果需要這類良好的控制，XML 序列化必須使用，而且您必須設計您的型別支援這種序列化技術。  
  
 **X AVOID**專為 XML 序列化，設計您的型別，除非您有非常強大的理由，來控制 XML 的外觀產生。 這項序列化技術已經由前一節所討論的資料合約序列化所取代。  
  
 **✓ CONSIDER**實作<xref:System.Xml.Serialization.IXmlSerializable>介面，如果您想要比藉由套用 XML 序列化屬性提供的哪些序列化的 XML 外觀的更多控制權。 兩個介面方法<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>和<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>，讓您完整控制序列化的 XML 資料流。 您也可以控制所套用的類型取得產生的 XML 結構描述`XmlSchemaProviderAttribute`。  
  
## <a name="supporting-runtime-serialization"></a>支援執行階段序列化  
 執行階段序列化是由.NET 遠端處理的技術。 如果您認為您的型別會使用.NET 遠端處理傳輸，您需要確定它們支援執行階段序列化。  
  
 可提供執行階段序列化的基本支援，請套用<xref:System.SerializableAttribute>，而且更進階的案例涉及實作簡單的執行階段序列化模式 (實作<xref:System.Runtime.Serialization.ISerializable>並提供序列化建構函式)。  
  
 **✓ CONSIDER**支援執行階段序列化，如果您的型別會使用與.NET 遠端處理。 例如，<xref:System.AddIn?displayProperty=nameWithType>命名空間會使用.NET 遠端處理，並讓所有的型別之間交換`System.AddIn`增益集必須支援執行階段序列化。  
  
 **✓ CONSIDER**實作的執行階段序列化模式，如果您想要完整控制序列化程序。 例如，如果您想要在資料序列化或還原序列化時加以轉換。  
  
 此模式非常簡單。 您只需要實作 <xref:System.Runtime.Serialization.ISerializable> 介面，並提供還原序列化物件時使用的特殊建構函式。  
  
 **✓ DO**進行保護序列化建構函式，並提供兩個參數類型和名為完全依照此處的範例所示。  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 **✓ DO**實作`ISerializable`成員明確。  
  
 **✓ DO**套用連結要求即可<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType>實作。 這可確保只有完全信任的核心和執行階段序列化程式可以存取的成員。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
