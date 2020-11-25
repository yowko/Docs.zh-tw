---
title: 序列化
ms.date: 10/22/2008
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
ms.openlocfilehash: 58ed937df5b60daf9fcbcb7610d6026c5e9805fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730925"
---
# <a name="serialization"></a>序列化

序列化是指將物件轉換成可以立即保存或傳輸的格式的程式。 例如，您可以將物件序列化、使用 HTTP 透過網際網路傳輸，並在目的地電腦上將它還原序列化。

 .NET Framework 提供針對各種序列化案例優化的三種主要序列化技術。 下表列出這些技術以及與這些技術相關的主要 Framework 型別。

|**技術名稱**|**主要類型**|**案例**|
|-------------------------|--------------------|-------------------|
|**資料合約序列化**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|一般持續性<br />Web 服務<br />JSON|
|**XML 序列化**|<xref:System.Xml.Serialization.XmlSerializer>|XML 格式具有 XML 圖形的完整控制權|
|**執行時間序列化 (二進位和 SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET 遠端處理|

 當您設計新的型別時，✔️要考慮序列化。

## <a name="choosing-the-right-serialization-technology-to-support"></a>選擇要支援的正確序列化技術

 如果您的型別實例可能需要在 Web 服務中保存或使用，✔️考慮支援資料合約序列化。

 如果您需要更充分地控制在序列化型別時所產生的 XML 格式，✔️請考慮支援 XML 序列化，而不是在資料合約序列化之外進行。

 在某些互通性案例中，您需要使用資料合約序列化不支援的 XML 結構，例如，產生 XML 屬性時，這可能是必要的。

 如果您的型別實例需要跨 .NET 遠端處理界限進行移動，✔️請考慮支援執行時間序列化。

 ❌ 基於一般持續性的理由，請避免支援執行時間序列化或 XML 序列化。 改為使用資料合約序列化。

## <a name="supporting-data-contract-serialization"></a>支援資料合約序列化

 型別可以藉由將套用至型別，然後將套用至類型的 <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> (欄位和屬性) ，來支援資料合約序列化。

 如果類型可以在部分信任中使用，則✔️考慮將型別的資料成員標記為 public。

 在完全信任中，資料合約序列化程式可以序列化和還原序列化非公用類型和成員，但是只有公用成員可以在部分信任中序列化和還原序列化。

 ✔️會對具有的所有屬性執行 getter 和 setter <xref:System.Runtime.Serialization.DataMemberAttribute> 。 資料合約序列化程式要求類型的 getter 和 setter 都必須視為可序列化。  (在 .NET Framework 3.5 SP1 中，某些集合屬性可以是唯讀的。 ) 如果類型不會在部分信任中使用，則其中一個或兩個屬性存取子可以是非公用的。

 ✔️考慮使用序列化回呼來初始化已還原序列化的實例。

 當還原序列化物件時，不會呼叫建構函式。  (規則有例外狀況。 標記為的集合的函式 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 會在還原序列化期間呼叫。 ) 因此，在一般結構期間執行的任何邏輯都必須實作為其中一個序列化回呼。

 `OnDeserializedAttribute` 是最常使用的回呼屬性。 此系列中的其他屬性為 <xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute> 和 <xref:System.Runtime.Serialization.OnSerializedAttribute>。 這些屬性可用來分別標記在還原序列化之前、序列化之前以及最後在序列化之後所執行的回呼。

 ✔️考慮使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 來表示將複雜物件圖形還原序列化時應該使用的具體類型。

 ✔️在建立或變更可序列化類型時，請考慮回溯和向前相容性。

 請牢記，型別之未來版本的序列化資料流可以還原序列化成該型別的目前版本，反之亦然。

 請確定您瞭解資料成員（甚至是私用和內部）無法變更其名稱、類型，或甚至是在型別的未來版本中的順序，除非特別小心使用資料合約屬性的明確參數來保留合約。

 對可序列化類型進行變更時，測試序列化的相容性。 請嘗試將新的版本還原序列化成舊的版本，反之亦然。

 ✔️考慮執行 <xref:System.Runtime.Serialization.IExtensibleDataObject> 以允許在不同版本的類型之間進行往返。

 此介面可讓序列化程式確保往返期間不會有任何資料遺失。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType>屬性是用來儲存目前版本未知之型別的未來版本中的任何資料，因此無法將它儲存在其資料成員中。 當目前版本接著序列化並還原序列化成未來版本時，其他資料將會在序列化資料流程中提供。

## <a name="supporting-xml-serialization"></a>支援 XML 序列化

 資料合約序列化是 .NET Framework 中的主要 (預設) 序列化技術，但有資料合約序列化不支援的序列化案例。 例如，它無法讓您完全控制序列化程式所產生或使用之 XML 的形狀。 如果需要這樣的精確控制，必須使用 XML 序列化，而且您需要設計您的類型以支援此序列化技術。

 ❌ 除非您有非常強大的理由來控制所產生之 XML 的形狀，否則請避免特別針對 XML 序列化設計您的類型。 這項序列化技術已經由前一節所討論的資料合約序列化所取代。

 <xref:System.Xml.Serialization.IXmlSerializable>如果您想要更充分地控制序列化 xml 的形狀，而不是套用 XML 序列化屬性所提供的功能，✔️請考慮採用該介面。 介面的兩個方法 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 和 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 可讓您完全控制序列化的 XML 資料流程。 您也可以藉由套用，來控制針對型別所產生的 XML 架構 `XmlSchemaProviderAttribute` 。

## <a name="supporting-runtime-serialization"></a>支援執行階段序列化

 執行時間序列化是 .NET 遠端處理所使用的技術。 如果您認為您的型別會使用 .NET 遠端處理傳輸，您必須確定它們支援執行時間序列化。

 您可以藉由套用來提供執行時間序列化的基本支援 <xref:System.SerializableAttribute> ，而且更高階的案例牽涉到執行簡單的執行時間可序列化模式， (執行 <xref:System.Runtime.Serialization.ISerializable> 和提供序列化的函式) 。

 如果您的型別將會搭配 .NET 遠端處理使用，✔️請考慮支援執行時間序列化。 例如， <xref:System.AddIn?displayProperty=nameWithType> 命名空間會使用 .Net 遠端處理，因此在增益集之間交換的所有類型都 `System.AddIn` 必須支援執行時間序列化。

 如果您想要完整控制序列化程式，✔️可考慮執行執行時間可序列化模式。 例如，如果您想要在資料序列化或還原序列化時加以轉換。

 此模式非常簡單。 您只需要實作 <xref:System.Runtime.Serialization.ISerializable> 介面，並提供還原序列化物件時使用的特殊建構函式。

 ✔️請將序列化的函式設為受保護，並提供兩個輸入的參數，並將其命名為完全如這裡範例所示。

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

 ✔️確實會 <xref:System.Runtime.Serialization.ISerializable> 明確地執行成員。

 ✔️會將連結要求套用至執行 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> 。 這可確保只有完全信任的核心和執行時間序列化程式才能存取成員。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [使用指導方針](usage-guidelines.md)
