---
title: 序列化
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: 0259bf82e74cbca7df8da246ca2e6ba7ef4542b3
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868531"
---
# <a name="serialization"></a>序列化
序列化是將物件轉換成可輕鬆保存或傳輸之格式的程式。 例如, 您可以將物件序列化, 使用 HTTP 透過網際網路傳輸它, 並在目的地電腦上將它還原序列化。  
  
 .NET Framework 提供三個針對各種序列化案例優化的主要序列化技術。 下表列出這些技術以及與這些技術相關的主要 Framework 型別。  
  
|**技術名稱**|**主要類型**|**場景**|  
|-------------------------|--------------------|-------------------|  
|**資料合約序列化**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|一般持續性<br />Web 服務<br />JSON|  
|**XML 序列化**|<xref:System.Xml.Serialization.XmlSerializer>|具有 XML 圖形完整控制權的 XML 格式|  
|**執行時間序列化 (二進位和 SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET 遠端處理|  
  
 **✓ DO** 考慮序列化，當您設計新的類型。  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>選擇要支援的正確序列化技術  
 **✓ CONSIDER** 支援資料合約序列化，如果您的型別執行個體可能需要保存或用於 Web 服務。  
  
 **✓ CONSIDER** 支援之 XML 序列化，而不是，或除了資料合約序列化，如果您需要更充分掌控型別序列化時所產生的 XML 格式。  
  
 當您需要使用資料合約序列化不支援的 XML 結構, 例如產生 XML 屬性時, 在某些互通性案例中可能會需要此功能。  
  
 **✓ CONSIDER** 支援執行階段序列化，如果需要行經.NET 遠端處理界限類型執行個體。  
  
 **X AVOID** 支援執行階段序列化或 XML 序列化，只會針對一般的持續性的原因。 建議改為使用資料合約序列化。  
  
## <a name="supporting-data-contract-serialization"></a>支援資料合約序列化  
 類型可以藉由<xref:System.Runtime.Serialization.DataContractAttribute>將套用至型別<xref:System.Runtime.Serialization.DataMemberAttribute> , 並將套用至型別的成員 (欄位和屬性) 來支援資料合約序列化。  
  
 **✓ CONSIDER** 標示的型別公開的資料成員，如果型別可以用在部分信任中。  
  
 在完全信任的情況下, 資料合約序列化程式可以將非公用類型和成員序列化和還原序列化, 但只有公用成員可以在部分信任中序列化和還原序列化。  
  
 **✓ DO** 實作上擁有的所有屬性的 getter 和 setter <xref:System.Runtime.Serialization.DataMemberAttribute>。 資料合約序列化程式需要 getter 和 setter, 才能將類型視為可序列化。 (在 .NET Framework 3.5 SP1 中, 某些集合屬性可以是僅限取得)。如果此型別不會在部分信任中使用，則其中一個或兩個屬性存取子可以不是 public。  
  
 **✓ CONSIDER** 序列化回呼使用已還原序列化的執行個體的初始設定。  
  
 當還原序列化物件時，不會呼叫建構函式。 (規則有例外狀況。 在還原序列化期間, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>會呼叫以標記的集合的構造函式。)因此, 在正常結構中執行的任何邏輯都必須實作為其中一個序列化回呼。  
  
 `OnDeserializedAttribute`是最常使用的回呼屬性。 此系列中的其他屬性為 <xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute> 和 <xref:System.Runtime.Serialization.OnSerializedAttribute>。 這些屬性可用來分別標記在還原序列化之前、序列化之前以及最後在序列化之後所執行的回呼。  
  
 **✓ CONSIDER** 使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 表示還原序列化複雜物件圖形時，應使用的具象類型。  
  
 **✓ DO** 考慮向後和向前相容性時建立或變更可序列化型別。  
  
 請牢記，型別之未來版本的序列化資料流可以還原序列化成該型別的目前版本，反之亦然。  
  
 請確定您瞭解資料成員 (甚至是私用和內部) 無法在類型的未來版本中變更其名稱、類型或甚至順序, 除非採取特別的方式來保留使用資料合約屬性之明確參數的合約.  
  
 對 serializable 類型進行變更時, 測試序列化的相容性。 請嘗試將新的版本還原序列化成舊的版本，反之亦然。  
  
 **✓ CONSIDER** 實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 允許之類型的不同版本之間的往返。  
  
 此介面可讓序列化程式確保往返期間不會有任何資料遺失。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType>屬性是用來儲存目前版本未知之未來版本的任何資料, 因此無法將它儲存在其資料成員中。 當目前版本接著序列化並還原序列化成未來版本時, 其他資料將會在序列化資料流程中提供。  
  
## <a name="supporting-xml-serialization"></a>支援 XML 序列化  
 資料合約序列化是 .NET Framework 中的主要 (預設) 序列化技術, 但有資料合約序列化不支援的序列化案例。 例如，它無法讓您完全控制序列化程式所產生或使用之 XML 的形狀。 如果需要這樣的控制, 則必須使用 XML 序列化, 而且您必須設計您的類型來支援此序列化技術。  
  
 **X AVOID** 專為 XML 序列化，設計您的型別，除非您有非常強大的理由，來控制 XML 的外觀產生。 這項序列化技術已經由前一節所討論的資料合約序列化所取代。  
  
 **✓ CONSIDER** 實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面，如果您想要比藉由套用 XML 序列化屬性提供的哪些序列化的 XML 外觀的更多控制權。 介面的兩個方法 ( <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>和<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>) 可讓您完全控制已序列化的 XML 資料流程。 您也可以藉由`XmlSchemaProviderAttribute`套用來控制為類型產生的 XML 架構。  
  
## <a name="supporting-runtime-serialization"></a>支援執行階段序列化  
 執行時間序列化是 .NET 遠端處理所使用的技術。 如果您認為您的類型會使用 .NET 遠端處理來傳輸, 您必須確定它們支援執行時間序列化。  
  
 藉由<xref:System.SerializableAttribute>套用, 可提供執行時間序列化的基本支援, 而更先進的案例則牽涉到執行簡單的執行時間<xref:System.Runtime.Serialization.ISerializable> Serializable 模式 (實和提供序列化的函數)。  
  
 **✓ CONSIDER** 支援執行階段序列化，如果您的型別會使用與.NET 遠端處理。 例如, 命名空間<xref:System.AddIn?displayProperty=nameWithType>會使用 .net 遠端處理, 因此在增益集之間`System.AddIn`交換的所有類型都必須支援執行時間序列化。  
  
 **✓ CONSIDER** 實作的執行階段序列化模式，如果您想要完整控制序列化程序。 例如，如果您想要在資料序列化或還原序列化時加以轉換。  
  
 此模式非常簡單。 您只需要實作 <xref:System.Runtime.Serialization.ISerializable> 介面，並提供還原序列化物件時使用的特殊建構函式。  
  
 **✓ DO** 進行保護序列化建構函式，並提供兩個參數類型和名為完全依照此處的範例所示。  
  
```csharp
[Serializable]  
public class Person : ISerializable
{  
    protected Person(SerializationInfo info, StreamingContext context)
    {  
        // ...  
    }  
}  
```
  
 **✓ DO** 實作 <xref:System.Runtime.Serialization.ISerializable> 成員明確。  
  
 **✓ DO** 套用連結要求即可 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> 實作。 這可確保只有完全信任的核心和執行時間序列化程式可以存取該成員。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *從[架構設計方針轉載已獲得皮耳森教育, inc. 的許可權:Krzysztof Cwalina 和 Brad Abrams 可重複使用的 .net 程式庫第](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 2 版的慣例、慣用語和模式, 已于2008年10月22日發行, 屬於 Microsoft Windows 開發系列的 Addison-Wesley Professional。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
