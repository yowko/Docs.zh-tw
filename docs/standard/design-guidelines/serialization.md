---
title: 序列化
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
ms.openlocfilehash: d29a7bc9f304b8d19e8af593166b8d847117424f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743640"
---
# <a name="serialization"></a>序列化
序列化是將物件轉換成可輕鬆保存或傳輸之格式的程式。 例如，您可以將物件序列化，使用 HTTP 透過網際網路傳輸它，並在目的地電腦上將它還原序列化。

 .NET Framework 提供三個針對各種序列化案例優化的主要序列化技術。 下表列出這些技術以及與這些技術相關的主要 Framework 型別。

|**技術名稱**|**主要類型**|**案例**|
|-------------------------|--------------------|-------------------|
|**資料合約序列化**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|一般持續性<br />Web 服務<br />JSON|
|**XML 序列化**|<xref:System.Xml.Serialization.XmlSerializer>|具有 XML 圖形完整控制權的 XML 格式|
|**執行時間序列化（二進位和 SOAP）**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET 遠端處理|

 ✔️在設計新的類型時，請考慮序列化。

## <a name="choosing-the-right-serialization-technology-to-support"></a>選擇要支援的正確序列化技術
 如果您的類型實例可能需要保存或用於 Web 服務，✔️考慮支援資料合約序列化。

 如果您需要更充分掌控在序列化型別時所產生的 XML 格式，✔️可以考慮支援 XML 序列化，而不是或除了資料合約序列化以外。

 當您需要使用資料合約序列化不支援的 XML 結構，例如產生 XML 屬性時，在某些互通性案例中可能會需要此功能。

 如果您的型別實例需要跨 .NET 遠端處理界限進行移動，✔️請考慮支援執行時間序列化。

 ❌ 避免因為一般持續性原因而支援執行時間序列化或 XML 序列化。 建議改為使用資料合約序列化。

## <a name="supporting-data-contract-serialization"></a>支援資料合約序列化
 類型可以藉由將 <xref:System.Runtime.Serialization.DataContractAttribute> 套用至類型，並將 <xref:System.Runtime.Serialization.DataMemberAttribute> 套用至類型的成員（欄位和屬性）來支援資料合約序列化。

 如果類型可以在部分信任中使用，✔️請考慮將類型的資料成員標示為公用。

 在完全信任的情況下，資料合約序列化程式可以將非公用類型和成員序列化和還原序列化，但只有公用成員可以在部分信任中序列化和還原序列化。

 ✔️確實在所有具有 <xref:System.Runtime.Serialization.DataMemberAttribute>的屬性上執行 getter 和 setter。 資料合約序列化程式需要 getter 和 setter，才能將類型視為可序列化。 （在 .NET Framework 3.5 SP1 中，某些集合屬性可以是僅限取得）。如果類型不會在部分信任中使用，則其中一個或兩個屬性存取子可以是非公用的。

 ✔️考慮使用序列化回呼來初始化已還原序列化的實例。

 當還原序列化物件時，不會呼叫建構函式。 （規則有例外狀況。 在還原序列化期間，會呼叫以 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 標記的集合的構造函式。）因此，在正常結構中執行的任何邏輯都必須實作為其中一個序列化回呼。

 `OnDeserializedAttribute` 是最常使用的回呼屬性。 此系列中的其他屬性為 <xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute> 和 <xref:System.Runtime.Serialization.OnSerializedAttribute>。 這些屬性可用來分別標記在還原序列化之前、序列化之前以及最後在序列化之後所執行的回呼。

 ✔️考慮使用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 來指示還原序列化複雜物件圖形時，應該使用的具體類型。

 ✔️在建立或變更可序列化型別時，請考慮回溯和回溯相容性。

 請牢記，型別之未來版本的序列化資料流可以還原序列化成該型別的目前版本，反之亦然。

 請確定您瞭解資料成員（甚至是私用和內部）無法在類型的未來版本中變更其名稱、類型或甚至順序，除非採取特別的方式來保留使用資料合約屬性之明確參數的合約.

 對 serializable 類型進行變更時，測試序列化的相容性。 請嘗試將新的版本還原序列化成舊的版本，反之亦然。

 ✔️考慮執行 <xref:System.Runtime.Serialization.IExtensibleDataObject>，以允許在類型的不同版本之間進行往返。

 此介面可讓序列化程式確保往返期間不會有任何資料遺失。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> 屬性是用來儲存來自目前版本未知之類型的未來版本中的任何資料，因此無法將它儲存在其資料成員中。 當目前版本接著序列化並還原序列化成未來版本時，其他資料將會在序列化資料流程中提供。

## <a name="supporting-xml-serialization"></a>支援 XML 序列化
 資料合約序列化是 .NET Framework 中的主要（預設）序列化技術，但有資料合約序列化不支援的序列化案例。 例如，它無法讓您完全控制序列化程式所產生或使用之 XML 的形狀。 如果需要這樣的控制，則必須使用 XML 序列化，而且您必須設計您的類型來支援此序列化技術。

 ❌ 避免特別設計 XML 序列化的型別，除非您有很大的理由可以控制所產生之 XML 的形狀。 這項序列化技術已經由前一節所討論的資料合約序列化所取代。

 如果您想要進一步控制序列化 XML 的圖形，而不是套用 XML 序列化屬性所提供的功能，✔️請考慮執行 <xref:System.Xml.Serialization.IXmlSerializable> 介面。 介面的兩個方法，<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 和 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>，可讓您完全控制已序列化的 XML 資料流程。 您也可以藉由套用 `XmlSchemaProviderAttribute`，來控制為類型產生的 XML 架構。

## <a name="supporting-runtime-serialization"></a>支援執行階段序列化
 執行時間序列化是 .NET 遠端處理所使用的技術。 如果您認為您的類型會使用 .NET 遠端處理來傳輸，您必須確定它們支援執行時間序列化。

 您可以藉由套用 <xref:System.SerializableAttribute>來提供執行時間序列化的基本支援，而更先進的案例則牽涉到執行簡單的執行時間 Serializable 模式（實 <xref:System.Runtime.Serialization.ISerializable> 並提供序列化的方法）。

 如果您的型別將搭配 .NET 遠端處理使用，✔️考慮支援執行時間序列化。 例如，<xref:System.AddIn?displayProperty=nameWithType> 命名空間會使用 .NET 遠端處理，因此 `System.AddIn` 增益集之間交換的所有類型都必須支援執行時間序列化。

 如果您想要完整控制序列化程式，✔️請考慮執行執行時間 Serializable 模式。 例如，如果您想要在資料序列化或還原序列化時加以轉換。

 此模式非常簡單。 您只需要實作 <xref:System.Runtime.Serialization.ISerializable> 介面，並提供還原序列化物件時使用的特殊建構函式。

 ✔️確實會保護序列化的函式，並提供兩個輸入和命名的參數，如這裡的範例所示。

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

 ✔️確實要明確地執行 <xref:System.Runtime.Serialization.ISerializable> 的成員。

 ✔️確實會將連結需求套用至 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> 的執行。 這可確保只有完全信任的核心和執行時間序列化程式可以存取該成員。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
