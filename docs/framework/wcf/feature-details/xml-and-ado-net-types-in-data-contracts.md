---
title: 資料合約中的 XML 與 ADO.NET 型別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 0d052c0f178c2dc6e2eb5a740faa42239fb91068
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637223"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>資料合約中的 XML 與 ADO.NET 型別
Windows Communication Foundation (WCF) 資料合約模型支援直接代表 XML 特定類型。 當這些型別序列化為 XML 時，序列化程式會寫出這些型別的 XML 內容，而不做更進一步的處理。 支援的型別為 <xref:System.Xml.XmlElement>、<xref:System.Xml.XmlNode> 的陣列 (但不是 `XmlNode` 型別本身) 以及實作 <xref:System.Xml.Serialization.IXmlSerializable> 的型別。 <xref:System.Data.DataSet> 和 <xref:System.Data.DataTable> 型別以及具型別資料集都常用於資料庫程式撰寫中。 這些型別會實作 `IXmlSerializable` 介面，因此在資料合約模型中是可序列化的。 在本主題最後，會列出這些型別的一些特別考量。  
  
## <a name="xml-types"></a>XML 型別  
  
### <a name="xml-element"></a>Xml 項目  
 `XmlElement` 型別是使用它的 XML 內容來序列化。 以下列型別為例。  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 這會序列化為 XML，如下所示：  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 請注意，包裝函式資料成員項目 `<myDataMember>` 仍然存在。 不能在資料合約模型中移除這個項目。 處理這個模型 (<xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer>) 的序列化程式可能會發出特別的屬性到這個包裝函式項目內。 這些屬性包括標準的 XML Schema Instance "nil" 屬性 (允許 `XmlElement` 成為 `null`) 和 "type" 屬性 (允許多型使用 `XmlElement`)。 此外，下列的 XML 屬性專屬於 WCF:"Id"、"Ref"、"Type"和"Assembly"。 這些屬性可發出以支援使用 `XmlElement` 搭配已啟用的物件圖形保留模式，或使用 <xref:System.Runtime.Serialization.NetDataContractSerializer> (如需有關物件圖形保留模式的詳細資訊，請參閱 <<c0> [ 序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。)  
  
 `XmlElement` 的陣列或集合是被允許的，且處理方式和其他任何的陣列或集合相同。 也就是說，整個集合將會有包裝函式項目，而陣列中的各個 `<myDataMember>` 則會有不同的包裝函式項目 (與上例中的 `XmlElement` 類似)。  
  
 在還原序列化時，還原序列化程式會從傳入的 XML 建立 `XmlElement`。 還原序列化程式會提供有效的父 <xref:System.Xml.XmlDocument>。  
  
 請確定要還原序列化為 `XmlElement` 的 XML 片段會定義所使用的所有前置詞，並且不會依賴任何來自祖系項目的前置詞定義。 只有在使用 `DataContractSerializer` 從不同的 (非 `DataContractSerializer`) 來源存取 XML 時，這才是問題。  
  
 當搭配`DataContractSerializer`，則`XmlElement`可能多型指派，但只有對型別的資料成員<xref:System.Object>。 即使實作 <xref:System.Collections.IEnumerable>，`XmlElement` 仍然無法用來做為集合型別，且無法指派給 <xref:System.Collections.IEnumerable> 資料成員。 如同所有的多型指派`DataContractSerializer`發出資料合約名稱中所產生的 XML – 在此情況下，它是"XmlElement 在""http://schemas.datacontract.org/2004/07/System.Xml"命名空間。  
  
 使用 `NetDataContractSerializer`，會支援 `XmlElement` 之任何有效的多型指派 (至 `Object` 或 `IEnumerable`)。  
  
 請勿嘗試使用序列化程式與從 `XmlElement` 衍生的型別，不論是否為多型指派。  
  
### <a name="array-of-xmlnode"></a>XmlNode 的陣列  
 使用 <xref:System.Xml.XmlNode> 的陣列與使用 `XmlElement` 十分類似。 使用 `XmlNode` 的陣列比使用 `XmlElement` 更有彈性。 您可以在資料成員包裝項目內撰寫多個項目。 您也可以將項目以外的內容插入資料成員包裝項目內，例如 XML 註解。 最後，您可以將屬性置入包裝資料成員項目內。 這些都可以藉由將 `XmlNode` 的特定衍生類別 (例如 `XmlNode`、<xref:System.Xml.XmlAttribute> 或 `XmlElement`) 填入 <xref:System.Xml.XmlComment> 的陣列來達成。 以下列型別為例。  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 當序列化時，結果 XML 將會類似下列程式碼。  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
  <myDataMember myAttribute="myValue">  
     <!--myComment-->  
     <myElement xmlns="" myAttribute="myValue">  
 myContents  
     </myElement>  
     <myElement xmlns="" myAttribute="myValue">  
       myContents  
     </myElement>  
  </myDataMember>  
</MyDataContract>  
```  
  
 請注意，資料成員包裝函式項目 `<myDataMember>` 包含一個屬性、一個註解和兩個項目。 有四個已序列化的 `XmlNode` 執行個體。  
  
 無法序列化會造成無效 XML 的 `XmlNode` 陣列。 例如，兩個 `XmlNode` 執行個體的陣列 (其中第一個是 `XmlElement` 而第二個是 <xref:System.Xml.XmlAttribute>) 是無效的，因為這個序列沒有對應至任何有效的 XML 執行個體 (沒有位置可附加此屬性)。  
  
 在還原序列化 `XmlNode` 的陣列時，會建立節點並填入來自傳入的 XML 的資訊。 還原序列化程式會提供有效的父 <xref:System.Xml.XmlDocument>。 所有節點都會還原都序列化，包括任何屬性上的包裝函式資料成員項目，但不包括放在這裡的 WCF 序列化程式 （例如用來指出多型指派的屬性）。 有關定義 XML 片段中所有命名空間前置詞的警告適用於 `XmlNode` 陣列的還原序列化，就像還原序列化 `XmlElement` 一樣。  
  
 當使用序列化程式並開啟物件圖形保留時，物件相等性只會保留在 `XmlNode` 陣列的層級，而不是個別 `XmlNode` 執行個體的層級。  
  
 請勿嘗試序列化有一或多個節點設定為 `XmlNode` 之 `null` 的陣列。 允許整個陣列成員為 `null`，但陣列中包含的個別 `XmlNode` 則不允許。 如果整個陣列成員為 null，包裝函式資料成員項目便會包含特別的屬性，指出它為 null。 在還原序列化時，整個陣列成員也會變成 null。  
  
 序列化程式只會特別處理 `XmlNode` 的一般陣列。 宣告為包含 `XmlNode` 之其他集合型別的資料成員，或宣告為衍生自 `XmlNode` 之型別陣列的資料成員都不會受到特別的處理。 因此，它們通常是不可序列化的，除非它們也符合其他的序列化能力準則之一。  
  
 `XmlNode` 的陣列或陣列集合是被允許的。 整個集合會有包裝函式項目，而在外部陣列或集合中 `<myDataMember>` 之每個陣列則會有不同的包裝函式項目 (與上例中 `XmlNode` 類似)。  
  
 以 <xref:System.Array> 執行個體填入 `Object` 之型別 `Array` 的資料成員或 `IEnumerable` 的 `XmlNode` 不會造成資料成員被視為 `Array` 執行個體的 `XmlNode`。 每個陣列成員都會分開進行序列化。  
  
 當搭配 `DataContractSerializer` 使用時，可能會多型指派 `XmlNode` 的陣列，但只有對型別 `Object` 的資料成員。 即使實作 `IEnumerable`，`XmlNode` 的陣列仍然無法用來做為集合型別，並指派給 `IEnumerable` 資料成員。 如同所有的多型指派`DataContractSerializer`發出資料合約名稱中所產生的 XML – 在此情況下，它是"ArrayOfXmlNode 在""http://schemas.datacontract.org/2004/07/System.Xml"命名空間。 當搭配`NetDataContractSerializer`，任何有效的指派`XmlNode`支援陣列。  
  
### <a name="schema-considerations"></a>結構描述的考量  
 如需結構描述對應的 XML 類型的詳細資訊，請參閱[Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。 本節將提供重點摘要。  
  
 型別 `XmlElement` 的資料成員會對應至使用下列匿名型別定義的項目。  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 `XmlNode` 之型別陣列的資料成員會對應至使用下列匿名型別定義的項目。  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>實作 IXmlSerializable 介面的型別  
 實作 `IXmlSerializable` 介面的型別完全受到 `DataContractSerializer` 的支援。 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性應永遠套用至這些型別，以控制其結構描述。  
  
 實作 `IXmlSerializable` 的型別有三種：代表任意內容的型別、代表單一項目的型別以及舊版 <xref:System.Data.DataSet> 型別。  
  
- 內容型別是使用由 `XmlSchemaProviderAttribute` 屬性指定的結構描述提供者方法。 此方法不會傳回 `null`，而屬性上的 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> 屬性會留在 `false` 的預設值。 這是 `IXmlSerializable` 型別最常見的使用。  
  
- 當 `IXmlSerializable` 型別必須控制自己的根項目名稱時，便會使用項目型別。 如果要將型別標示為項目型別，請將 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> 屬性上的 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性設定為 `true`，或從結構描述提供者方法傳回 null。 對於項目型別，是否具有結構描述提供者方法是選擇性的 – 您可以在 `XmlSchemaProviderAttribute` 中指定 null 來取代方法名稱。 然而，如果 `IsAny` 是 `true` 並已指定結構描述提供者方法，則此方法必須傳回 null。  
  
- 舊版 <xref:System.Data.DataSet> 型別是沒有以 `IXmlSerializable` 屬性標示的 `XmlSchemaProviderAttribute` 型別。 相反地，它們是依賴 <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> 方法來產生結構描述。 在舊版 .NET Framework 中，這個模式是用於 `DataSet` 型別且其具型別的資料集會衍生類別，但這個模式現在已經過時且只為了舊版而支援。 請勿依賴這個模式，並永遠套用 `XmlSchemaProviderAttribute` 至您的 `IXmlSerializable` 型別。  
  
### <a name="ixmlserializable-content-types"></a>IXmlSerializable 內容型別  
 當序列化實作 `IXmlSerializable` 且為上述定義的內容型別之型別的資料成員時，序列化程式會撰寫資料成員的包裝函式項目，並將控制項傳遞至 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法。 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 實作會撰寫 XML，包括將屬性新增至包裝函式項目。 在 `WriteXml` 完成之後，序列化程式會關閉項目。  
  
 當還原序列化實作 `IXmlSerializable` 且為上述定義的內容型別之型別的資料成員時，還原序列化程式會將 XML 讀取器放在資料成員的包裝函式項目上，並將控制項傳遞至 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法。 此方法必須讀取整個項目，包括開始和結束標記。 請確定您的 `ReadXml` 程式碼會處理項目是空白的案例。 此外，您的 `ReadXml` 實作不應依賴以特定的方式為包裝函式項目命名。 由序列化程式所選擇的名稱可能會有所不同。  
  
 允許將 `IXmlSerializable` 內容型別多型指派為如型別 <xref:System.Object> 的資料成員。 也允許型別執行個體為 null。 最後，可以使用 `IXmlSerializable` 型別並啟用物件圖形保留，以及搭配 <xref:System.Runtime.Serialization.NetDataContractSerializer>。 所有這些功能都需要 WCF 序列化程式，將特定屬性附加至包裝函式項目 ("nil"和"type"中 XML Schema Instance 命名空間和"Id"、"Ref"、"Type"和"Assembly"WCF 特定命名空間中的)。  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>實作 ReadXml 時要忽略的屬性  
 在將控制項傳遞至您的 `ReadXml` 程式碼之前，還原序列化程式會檢查 XML 項目、偵測這些特殊的 XML 屬性並進行動作。 例如，如果 "nil" 為 `true`，便會還原序列化 null 值並且不會呼叫 `ReadXml`。 如果偵測到多型，則會還原序列化項目的內容，就如同它是不同的型別一樣。 會呼叫 `ReadXml` 的多型指派型別的實作。 在任何情況下，`ReadXml` 實作都應忽略這些特殊屬性，因為它們是由還原序列化程式所處理的。  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable 內容型別的結構描述考量  
 當匯出 `IXmlSerializable` 內容型別的結構描述時，會呼叫結構描述提供者方法。 <xref:System.Xml.Schema.XmlSchemaSet> 會傳遞至結構描述提供者方法。 此方法會將有效的結構描述新增至結構描述集。 結構描述集包含在發生結構描述匯出時已知的結構描述。 當結構描述提供者方法必須將項目新增至結構描述集時，必須判斷有適當命名空間的 <xref:System.Xml.Schema.XmlSchema> 是否已經存在於此集中。 如果是，結構描述提供者方法必須將新項目新增至現有的 `XmlSchema`。 否則，就必須建立新的 `XmlSchema` 執行個體。 如果是使用 `IXmlSerializable` 型別的陣列，這就很重要。 例如，如果您的 `IXmlSerializable` 型別在命名空間 "B" 中匯出為型別 "A"，就有可能在呼叫結構描述提供者方法時，結構描述集已經包含 "B" 的結構描述以保存 "ArrayOfA" 型別。  
  
 除了將型別新增至 <xref:System.Xml.Schema.XmlSchemaSet>，內容型別的結構描述提供者方法還必須傳回非 null 的值。 它會傳回 <xref:System.Xml.XmlQualifiedName>，指定用於指定的 `IXmlSerializable` 型別的結構描述型別的名稱。 這個限定名稱也會做為型別的資料合約名稱和命名空間。 當結構描述提供者方法傳回時，允許立即傳回不存在於結構描述集中的型別。 然而，預期在匯出所有相關型別時 (在 <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> 上為所有相關型別呼叫 <xref:System.Runtime.Serialization.XsdDataContractExporter> 方法，並存取 <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> 屬性)，此型別會存在於結構描述集中。 在完成所有相關 `Schemas` 呼叫之前存取 `Export` 屬性會造成 <xref:System.Xml.Schema.XmlSchemaException>。 如需有關匯出程序的詳細資訊，請參閱 <<c0> [ 匯出類別中的結構描述](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)。  
  
 結構描述提供者方法也可能傳回 <xref:System.Xml.Schema.XmlSchemaType> 以使用。 此型別可能是或不是匿名的。 如果是匿名的，每當使用 `IXmlSerializable` 型別做為資料成員時，便會將 `IXmlSerializable` 型別的結構描述匯出為匿名型別。 `IXmlSerializable` 型別仍然會有資料合約名稱和命名空間。 (這取決於中所述[Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md)不同之處在於<xref:System.Runtime.Serialization.DataContractAttribute>屬性無法用於自訂名稱。)如果不是匿名的，則必須是 `XmlSchemaSet` 中的其中一個型別。 這種情況等於傳回型別的 `XmlQualifiedName`。  
  
 此外，會匯出型別的全域項目宣告。 如果型別沒有套用 <xref:System.Xml.Serialization.XmlRootAttribute> 屬性，項目會有和資料合約相同的名稱及命名空間，且其 "nillable" 屬性也會為 true。 唯一的例外是結構描述命名空間 ("http://www.w3.org/2001/XMLSchema") – 因為禁止將新的項目新增至結構描述命名空間型別的資料合約是此命名空間中，如果對應的全域項目是空白的命名空間中。 如果型別已套用 `XmlRootAttribute` 屬性 (Attribute)，則會使用下列屬性 (Property) 匯出全域項目宣告：<xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>、<xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> 和 <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> 屬性 (Property)。 套用 `XmlRootAttribute` 的預設值是資料合約名稱、空白命名空間以及為 true 的 "nillable"。  
  
 相同的全域項目宣告規則亦適用於舊版資料集型別。 請注意，`XmlRootAttribute` 無法覆寫透過自訂程式碼新增的全域項目宣告，不論是使用結構描述提供者方法新增至 `XmlSchemaSet` 或透過舊版資料集型別的 `GetSchema`。  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable 項目型別  
 `IXmlSerializable` 項目型別會將 `IsAny` 屬性設定為 `true`，或讓其結構描述提供者方法傳回 `null`。  
  
 項目型別的序列化及還原序列化和內容型別的序列化及還原序列化十分類似。 然而，有一些重要的差異：  
  
- `WriteXml` 實作預期只撰寫一個項目 (其中當然可包含多個子項目)。 它不應在這個單一項目、多個同層項目或混合內容以外撰寫屬性。 此項目可能是空白的。  
  
- `ReadXml` 實作不應讀取包裝函式項目。 它預期會讀取 `WriteXml` 所產生的一個項目。  
  
- 當定期序列化項目型別時 (例如，做為資料合約中的資料成員)，序列化程式會在呼叫 `WriteXml` 之前輸出包裝函式項目，就像使用內容型別一樣。 然而，當在最上層序列化項目型別時，序列化程式通常完全不會輸出包含 `WriteXml` 撰寫之項目的包裝函式項目，除非在 `DataContractSerializer` 或 `NetDataContractSerializer` 建構函式中建構序列化程式時已明確指定根名稱和命名空間。 如需詳細資訊，請參閱 <<c0> [ 序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。  
  
- 當在最上層序列化項目型別，但在建構期間沒有指定根名稱和命名空間時，<xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> 和 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> 基本上不會執行任何動作，而 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> 會呼叫 `WriteXml`。 在這個模式中，正在序列化的物件不得為 null，且無法多型指派。 另外，物件圖形保留無法啟用，且 `NetDataContractSerializer` 無法使用。  
  
- 當在最上層還原序列化元素型別，但在建構期間沒有指定根名稱和命名空間時，如果可以找到任何元素的起始，<xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> 就會傳回 `true`。 <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> 參數設定為 `verifyObjectName` 的 `true` 在實際讀取物件之前，行為方式會和 `IsStartObject` 相同。 然後 `ReadObject` 就會將控制項傳遞給 `ReadXml` 方法。  
  
 項目型別匯出的結構描述和前一節中所述的 `XmlElement` 型別相同，除了結構描述提供者方法可以將其他結構描述新增至 <xref:System.Xml.Schema.XmlSchemaSet>，就像內容型別一樣。 不允許使用 `XmlRootAttribute` 屬性搭配項目型別，也永遠不會為這些型別發出全域項目宣告。  
  
### <a name="differences-from-the-xmlserializer"></a>與 XmlSerializer 的差異  
 `IXmlSerializable` 也會辨識 `XmlSchemaProviderAttribute` 介面和 `XmlRootAttribute` 和 <xref:System.Xml.Serialization.XmlSerializer> 屬性。 然而，在資料合約模型中對於它們的處理方式有一些差異。 重要差異摘要如下：  
  
- 結構描述提供者方法必須可公開在 `XmlSerializer` 中使用，但不必公開在資料合約模型中使用。  
  
- 當 `IsAny` 在資料合約模型中為 true，但未使用 `XmlSerializer` 時，便會呼叫結構描述提供者方法。  
  
- 當沒有出現內容或舊版資料集型別的 `XmlRootAttribute` 屬性時，`XmlSerializer` 會在空白命名空間中匯出全域項目宣告。 在資料合約模型中，所使用的命名空間通常是資料合約命名空間，如前所述。  
  
 在建立將搭配這兩種序列化技術使用的型別時，請注意這些差異。  
  
### <a name="importing-ixmlserializable-schema"></a>匯入 IXmlSerializable 結構描述  
 當匯入從 `IXmlSerializable` 型別產生的結構描述時，有一些可能性：  
  
- 產生的結構描述可能是有效的資料合約結構描述中所述[Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。 在這種情況中，結構描述會如平常般匯入，並產生一般資料合約類型。  
  
- 所產生的結構描述可能不是有效的資料合約結構描述。 例如，您的結構描述提供者方法可能會產生結構描述，其中包含資料合約模型中不支援的 XML 屬性。 在這種情況中，您可以將結構描述匯入為 `IXmlSerializable` 型別。 此匯入模式不在預設情況下，但可以輕鬆地啟用 – 例如，使用`/importXmlTypes`命令列參數[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 在將詳細說明這[匯入結構描述產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)。 請注意，您必須對您的型別執行個體直接使用 XML。 您可能也會考慮使用不同的序列化技術，支援範圍更廣的結構描述 – 請參閱有關使用 `XmlSerializer` 的主題。  
  
- 您可能會想要在 Proxy 中重複使用現有的 `IXmlSerializable` 型別，而非產生一個新的。 在這種情況中，「匯入結構描述以產生型別」主題中所說明的參照型別功能可用於指出要重複使用的型別。 這會對應至在 svcutil.exe 上使用 `/reference` 參數，指定包含要重複使用之型別的組件。  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>表示資料合約中的任意 XML  
 `XmlElement`、`XmlNode` 的陣列和 `IXmlSerializable` 型別可讓您將任意 XML 插入資料合約模型中。 `DataContractSerializer` 和 `NetDataContractSerializer` 會將此 XML 內容傳遞至使用中的 XML 寫入器，而不會干擾處理程序。 然而，XML 寫入器可能會對所撰寫的 XML 強加特定的限制。 特別是，下列是一些重要的範例：  
  
- XML 寫入器通常不會允許 XML 文件宣告 (例如\<？ xml 版本 ='1.0 '？ >) 在撰寫另一個文件。 您無法採用完整的 XML 文件並序列化為 `Array` 資料成員的 `XmlNode`。 如果要執行這項操作，您必須刪除文件宣告或使用您自己的編碼配置來表示它。  
  
- 所有 WCF 所提供的 XML 寫入器拒絕 XML 處理指示 (\<嗎？ … ？ >) 和文件類型定義 (\<！ … >)，因為它們不允許在 SOAP 訊息中。 同樣地，您可以使用您自己的編碼機制來解決這個限制。 如果您必須在結果 XML 中包含它們，可以撰寫自訂編碼器，使用支援它們的 XML 寫入器。  
  
- 當實作 `WriteXml` 時，請避免在 XML 寫入器上呼叫 <xref:System.Xml.XmlWriter.WriteRaw%2A> 方法。 WCF 會使用各種不同的 XML 編碼 （包括二進位），它是很難或根本不可能使用`WriteRaw`結果是可用於任何編碼。  
  
- 實作時`WriteXml`，請避免使用<xref:System.Xml.XmlWriter.WriteEntityRef%2A>和<xref:System.Xml.XmlWriter.WriteNmToken%2A>WCF 所提供的 XML 寫入器上不支援的方法。  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>使用 DataSet、Typed DataSet 和 DataTable  
 使用這些型別在資料合約模型中是受到完整支援的。 當使用這些型別時，請考慮下列各點：  
  
- 這些類型的結構描述 (尤其是<xref:System.Data.DataSet>和其具型別的衍生類別) 可能與某些非 WCF 平台，互通，或可能造成與這些平台搭配使用時的可用性不佳。 此外，使用 `DataSet` 型別可能會對效能有影響。 最後，它可能會讓您將來更難處理應用程式的版本。 請考慮使用明確定義的資料合約類型來取代您合約中的 `DataSet` 型別。  
  
- 當匯入 `DataSet` 或 `DataTable` 結構描述時，參照這些型別是很重要的。 使用 Svcutil.exe 命令列工具，這可藉由將 System.Data.dll 組件名稱，使`/reference`切換。 如果匯入具型別資料集結構描述，您必須參照具型別資料集的型別。 使用 Svcutil.exe，將具類型資料集的組件的位置傳遞`/reference`切換。 如需參考類型的詳細資訊，請參閱[匯入結構描述產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)。  
  
 支援資料合約模型中具有型別的資料集是受限制的。 具有型別的資料集可以序列化和還原序列化，並可以匯出其結構描述。 但是，資料合約結構描述匯入無法從結構描述產生新的具有型別資料集型別，因為它只會重複使用現有的資料集型別。 您可以在 Svcutil.exe 上使用 `/r` 參數來指向現有具有型別的資料集。 如果您嘗試在使用具型別資料集的服務上使用 Svcutil.exe，但不使用 `/r` 參數，則會自動選取替代的序列化程式 (XmlSerializer)。 如果您必須使用 DataContractSerializer，且必須從結構描述產生資料集，您可以使用下列程序：產生具有型別的資料集型別 (透過在服務上使用 Xsd.exe 工具並加上 `/d` 參數)、編譯該型別，然後在 Svcutil.exe 上使用 `/r` 參數來指向這些型別。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [資料合約序列化程式支援的類型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
