---
title: 序列化和還原序列化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: 87788906cfbf5b230c3b976395d9a40c655ae41a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591655"
---
# <a name="serialization-and-deserialization"></a>序列化和還原序列化
Windows Communication Foundation (WCF) 包含新的序列化引擎， <xref:System.Runtime.Serialization.DataContractSerializer>。 <xref:System.Runtime.Serialization.DataContractSerializer> .NET Framework 物件與 XML 之間轉譯兩個方向。 本主題會說明序列化程式的運作方式。  
  
 在序列化.NET Framework 物件，序列化程式了解各種不同的程式設計模型，包括新的序列化*資料合約*模型。 如需完整的支援型別清單，請參閱 [Types Supported by the Data Contract Serializer](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)。 如需資料合約的簡介，請參閱 [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。  
  
 還原序列化 XML 時，序列化程式會使用 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 類別。 它也支援<xref:System.Xml.XmlDictionaryReader>和<xref:System.Xml.XmlDictionaryWriter>類別，讓它能夠產生最佳化 XML，在某些情況下，例如當使用 WCF 二進位 XML 格式。  
  
 WCF 也包含搭配的序列化程式， <xref:System.Runtime.Serialization.NetDataContractSerializer>。 <xref:System.Runtime.Serialization.NetDataContractSerializer>大致<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>和<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>序列化程式因為它同時會發出的.NET Framework 型別名稱做為序列化資料的一部分。 當序列化和還原序列化兩端共用相同的型別時，就會使用它。 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer> 兩者同時衍生自一般基底類別， <xref:System.Runtime.Serialization.XmlObjectSerializer>。  
  
> [!WARNING]
>  <xref:System.Runtime.Serialization.DataContractSerializer> 會將包含十六進位值低於 20 之控制字元的字串序列化成 XML 實體。 將這類資料傳送至 WCF 服務時，這可能會導致非 WCF 用戶端的問題。  
  
## <a name="creating-a-datacontractserializer-instance"></a>建立 DataContractSerializer 執行個體  
 建構 <xref:System.Runtime.Serialization.DataContractSerializer> 的執行個體是很重要的步驟。 建構完成之後，您將無法變更任何設定。  
  
### <a name="specifying-the-root-type"></a>指定根型別  
 「 *根型別* 」(Root Type) 是指已序列化或還原序列化之執行個體的型別。 <xref:System.Runtime.Serialization.DataContractSerializer> 包含許多建構函式多載，但是，根型別至少必須透過 `type` 參數來提供。  
  
 針對特定根型別所建立的序列化程式無法用來序列化 (或還原序列化) 另一種型別，除非該型別衍生自根型別。 以下範例顯示兩個類別。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 這個程式碼所建構的 `DataContractSerializer` 執行個體只能用來序列化或還原序列化 `Person` 類別的執行個體。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>指定已知型別  
 如果透過 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性或其他一些機制來序列化尚未處理的型別時運用了多型 (Polymorphism)，則必須透過 `knownTypes` 參數將可能的已知型別清單傳遞至序列化程式的建構函式中。 如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。  
  
 下列範例說明類別 ( `LibraryPatron`)，其中包含了特定型別的集合 ( `LibraryItem`)。 第二個類別定義了 `LibraryItem` 型別。 第三與第四個類別 (`Book` 和 `Newspaper`) 則繼承了 `LibraryItem` 類別。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 下列程式碼會透過 `knownTypes` 參數來建構序列化程式的執行個體。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>指定預設的根名稱與命名空間  
 一般來說，在序列化物件時，最外部 XML 項目的預設名稱與命名空間會依據資料合約名稱與命名空間來決定。 所有內部項目的名稱都會從資料成員名稱中決定，而其命名空間則是資料合約的命名空間。 下列範例會在 `Name` 和 `Namespace` 類別的建構函式中設定 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 值。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 序列化 `Person` 類別的執行個體會產生類似下列的 XML。  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 但是，您可以將 `rootName` 和 `rootNamespace` 的參數值傳遞至 <xref:System.Runtime.Serialization.DataContractSerializer> 建構函式中，以自訂根項目的預設名稱和命名空間。 請注意， `rootNamespace` 不會影響包含的項目 (對應至資料成員) 命名空間。 它只會影響最外部項目的命名空間。  
  
 這些值都可以傳遞做為 <xref:System.Xml.XmlDictionaryString> 類別的字串或執行個體，以便透過二進位 XML 格式加以最佳化。  
  
### <a name="setting-the-maximum-objects-quota"></a>設定最大物件數量配額  
 某些 `DataContractSerializer` 建構函式多載包含有 `maxItemsInObjectGraph` 參數。 這項參數可決定序列化程式在單一 <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> 方法呼叫中能夠序列化或還原序列化的最大物件數量 (此方法一定會讀取一個根物件，但是這個物件可能會在其資料成員中又有其他物件。 這些物件可能又會有其他物件，依此類推)。預設值為 65536。 請注意，當序列化或還原序列化陣列時，每個陣列項目都視為個別物件。 另外請注意，有些物件可能有大量記憶體表示，因此只有這個配額可能不足以防止阻絕服務攻擊。 如需詳細資訊，請參閱 <<c0> [ 資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。 如果您需要將這個配額調高到預設值以上，請在傳送 (序列化) 和接收 (還原序列化) 端都執行這項操作，因為它會在讀取與寫入資料時同時套用。  
  
### <a name="round-trips"></a>來回行程  
 在一個作業中還原序列化物件後重新加以序列化的程序，我們稱為「 *來回行程* 」(Round Trip)。 因此，它會從 XML 變成物件執行個體，並回到原本的 XML 資料流。  
  
 某些 `DataContractSerializer` 建構函式多載包含有 `ignoreExtensionDataObject` 參數 (預設為 `false` )。 在此預設模式中，只要資料合約實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面，資料就可以從較新版的資料合約一路經由較舊版本的資料合約再傳回較新版的資料合約來完成無資料損失的來回行程。 例如，假定 `Person` 資料合約的第 1 版包含 `Name` 和 `PhoneNumber` 資料成員，而第 2 版新增了 `Nickname` 成員。 如果實作了 `IExtensibleDataObject` ，則當從第 2 版傳送資訊到第 1 版時，會儲存 `Nickname` 資料，然後在資料序列化期間重新將它發出，這樣一來，來回行程期間就不會損失任何資料。 如需詳細資訊，請參閱 <<c0> [ 向前相容資料合約](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)並[資料合約版本控制](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)。  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>來回行程的安全性與結構描述有效性考量  
 來回行程可能包含一些安全性意涵。 例如，還原序列化與儲存大量的非直接關聯資料時，可能會帶來安全性風險。 由於重新發出這項資料時並無法加以驗證，特別是當牽涉到數位簽章時，因此可能會有一些安全上的考量。 例如，在之前的案例中，第 1 版的端點可能會簽署包含惡意資料的 `Nickname` 值。 最後，還是可能有一些結構描述上的有效性考量：端點可能想要一直發出能夠恪遵其陳述的合約規定，而非其他額外值的資料。 在先前的範例中，第 1 版端點的合約告知僅發出 `Name` 和 `PhoneNumber`，而且假如使用結構描述驗證法的話，發出額外的 `Nickname` 值將讓驗證失敗。  
  
#### <a name="enabling-and-disabling-round-trips"></a>啟用和停用來回行程  
 若要關閉來回行程，請勿實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面。 如果您無法掌控型別，請將 `ignoreExtensionDataObject` 參數設定為 `true` 來達到相同的效果。  
  
### <a name="object-graph-preservation"></a>物件圖形保留  
 一般來說，序列化程式並不關心物件身分識別，如下列程式碼所示。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 下列程式碼會建立採購單。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 請注意， `billTo` 和 `shipTo` 欄位都已設定為相同的物件執行個體。 但是，產生的 XML 卻重複產生了資訊，而且看起來就像下列 XML 一樣。  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 但是，這種方法具有下列特性，而這些特性有時候可能會造成反效果：  
  
- 效能。 複寫資料沒有效率。  
  
- 循環參照。 如果物件參照到它們，就算是經由其他物件來參照，藉由複寫作業來序列化會導致無限的迴圈 (如果發生這種情況的話，序列化程式會擲回 <xref:System.Runtime.Serialization.SerializationException> )。  
  
- 語意。 有時候兩個參照是針對同一個物件，而不是針對兩個一樣的物件，這點要特別注意。  
  
 因此，某些 `DataContractSerializer` 建構函式多載包含有 `preserveObjectReferences` 參數 (預設為 `false`)。 當此參數設定為`true`，使用編碼物件的參考，其中唯一的 WCF 了解，特殊方法。 設定為 `true`時，XML 程式碼範例就會類似如下所示。  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 "Ser"命名空間是指標準序列化命名空間， `http://schemas.microsoft.com/2003/10/Serialization/`。 每個資料片段只會序列化一次，並賦予一個 ID 號碼，後續使用時會導致參照到已經序列化的資料。  
  
> [!IMPORTANT]
>  如果 "id" 及 "ref" 這兩個屬性都出現在資料合約 `XMLElement`中，那麼會接受 "ref" 屬性而忽略 "id" 屬性。  
  
 了解此模式的限制是很重要的：  
  
- `DataContractSerializer` 產生的 XML ( `preserveObjectReferences` 設定為 `true` ) 無法與其他任何技術互通，而且只能由另一個 `DataContractSerializer` 執行個體存取 ( `preserveObjectReferences` 同樣設定為 `true`)。  
  
- 此功能不支援中繼資料 (結構描述)。 產生的結構描述只有在 `preserveObjectReferences` 設定為 `false`時，才會有效。  
  
- 這項功能會導致序列化與還原序列化處理序執行得較慢。 雖然不需要複製資料，還是需要透過此模式來執行額外的物件比較。  
  
> [!CAUTION]
>  啟用 `preserveObjectReferences` 模式時，請將 `maxItemsInObjectGraph` 值設定為正確的配額，這點請您要特別注意。 因為陣列在此模式中的處理方式不同，攻擊者很容易就能夠建構小型的惡意訊息，導致大量的記憶體取用只受到 `maxItemsInObjectGraph` 配額的限制。  
  
### <a name="specifying-a-data-contract-surrogate"></a>指定資料合約代理  
 某些 `DataContractSerializer` 建構函式多載包含有 `dataContractSurrogate` 參數 (可能會設定為 `null`)。 另一方面，您可以用它來指定「 *資料合約代理*」(Data Contract Surrogate)，這是一種可實作 <xref:System.Runtime.Serialization.IDataContractSurrogate> 介面的型別。 您可以接著使用此介面來自訂序列化與還原序列化處理序。 如需詳細資訊，請參閱 <<c0> [ 資料合約代理](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)。  
  
## <a name="serialization"></a>序列化  
 下列資訊將套用至任何繼承自 <xref:System.Runtime.Serialization.XmlObjectSerializer>的類別，包括 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別。  
  
### <a name="simple-serialization"></a>簡單序列化  
 序列化物件的最基本方式，就是將它傳遞給 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> 方法。 有三種多載，各自負責寫入至 <xref:System.IO.Stream>、 <xref:System.Xml.XmlWriter>，或是 <xref:System.Xml.XmlDictionaryWriter>。 在使用 <xref:System.IO.Stream> 多載的情況下，將輸出 UTF-8 編碼格式的 XML。 在使用 <xref:System.Xml.XmlDictionaryWriter> 多載的情況下，序列化程式會最佳化二進位 XML 的輸出。  
  
 當使用<xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A>方法，序列化程式的包裝函式項目使用的預設名稱和命名空間，並與 （請參閱上的 「 指定預設的根名稱和命名空間 」 一節） 的內容一起寫出。  
  
 下列範例示範使用 <xref:System.Xml.XmlDictionaryWriter>來寫入。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 這會產生如下所示的 XML。  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>逐步序列化  
 請使用 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>、 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>，以及 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> 方法來分別寫入結束項目、物件內容，並關閉包裝函式項目。  
  
> [!NOTE]
>  這些方法不包含 <xref:System.IO.Stream> 多載。  
  
 這項逐步序列化含有兩個常見的用途。 其中一個就是在 `WriteStartObject` 和 `WriteObjectContent`之間插入屬性或註解之類的內容，如下列範例所示。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 這會產生如下所示的 XML。  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 另一個常見用途就是避免使用整個 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> 和 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> ，並寫入您自己的自訂包裝函式項目 (或甚至一起略過不寫入包裝函式)，如下列程式碼所示。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 這會產生如下所示的 XML。  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
>  使用逐步序列化可能產生結構描述無效的 XML。  
  
## <a name="deserialization"></a>還原序列化  
 下列資訊將套用至任何繼承自 <xref:System.Runtime.Serialization.XmlObjectSerializer>的類別，包括 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別。  
  
 還原序列化物件的最基本方式，就是呼叫其中一個 <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> 方法多載。 有三種多載，各自負責使用 <xref:System.Xml.XmlDictionaryReader>、 `XmlReader`，或是 `Stream`來讀取。 請注意， `Stream` 多載會建立未由任何配額保護的文字 <xref:System.Xml.XmlDictionaryReader> ，而且只能用來讀取受信任資料。  
  
 同時請注意， `ReadObject` 方法傳回的物件必須轉換成適當的型別。  
  
 下列程式碼會建構 <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Xml.XmlDictionaryReader>的執行個體，然後還原序列化 `Person` 執行個體。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 在呼叫 <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> 方法之前，請將 XML 讀取器置於包裝函式項目或是位於包裝函式項目之前的非內容節點上。 您可以呼叫 <xref:System.Xml.XmlReader.Read%2A> 或其衍生的 <xref:System.Xml.XmlReader> 方法，然後測試 <xref:System.Xml.XmlReader.NodeType%2A>來達到這個目的，如下列程式碼所示。  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 請注意，在將讀取器交給 `ReadObject`之前，可以讀取此包裝函式項目的屬性。  
  
 當使用其中一種簡單`ReadObject`多載，還原序列化程式會尋找預設名稱和命名空間上的包裝函式項目 （請參閱上一節 「 指定預設的根名稱和命名空間 」），並擲回例外狀況，如果它找到未知項目。 在先前的範例中，預期會使用 `<Person>` 包裝函式項目。 <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> 方法會被呼叫，以驗證讀取器位於如預期命名的項目上。  
  
 有一種方式可以停用此包裝函式項目名稱檢查；某些 `ReadObject` 方法的多載會採用布林參數 `verifyObjectName`(預設會設定為 `true` )。 一旦設定為 `false`，就會忽略包裝函式項目的名稱與命名空間。 讀取以先前所述之逐步序列化機制撰寫的 XML 時，這種方式很有用。  
  
## <a name="using-the-netdatacontractserializer"></a>使用 NetDataContractSerializer  
 主要差異`DataContractSerializer`而<xref:System.Runtime.Serialization.NetDataContractSerializer>在於`DataContractSerializer`會使用資料合約名稱，而`NetDataContractSerializer`輸出完整序列化的 XML 中的.NET Framework 組件和類型名稱。 也就是說，序列化與還原序列化端點兩者必須共用完全相同的型別。 這表示 `NetDataContractSerializer` 並不需要已知型別機制，因為要還原序列化的完全相同型別一律呈現已知狀態。  
  
 但是，還是會發生一些問題：  
  
- 安全性： 在還原序列化的 XML 中找到的任何型別會被載入。 攻擊者會利用這個漏洞來強制載入惡意型別。 只有在使用「 `NetDataContractSerializer` 序列化繫結器 *」(Serialization Binder) 時，才應該針對不受信任的資料使用* (透過 <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> 屬性或建構函式參數)。 繫結器只允許載入安全型別。 繫結器機制與 <xref:System.Runtime.Serialization> 命名空間用途中的型別相同。  
  
- 版本控制。 在 XML 中使用完整的型別與組件名稱會嚴格限制型別的版本設定。 下列為無法變更的項目：型別名稱、命名空間、組件名稱以及組件版本。 將 <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> 屬性或建構函式設定為 <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> (而不是 <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> 的預設值) 可允許組件版本變更，但不適用於泛型參數型別。  
  
- 互通性。 在 XML 中包含.NET Framework 型別和組件名稱，因為.NET Framework 以外的平台無法存取產生的資料。  
  
- 效能。 寫出型別和組件名稱會大幅增加最後 XML 的大小。  
  
 這項機制是二進位或 SOAP 序列化的.NET Framework 遠端處理所使用的類似 (具體而言，<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>而<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>)。  
  
 使用 `NetDataContractSerializer` 類似於使用 `DataContractSerializer`，除了下列幾點差異以外：  
  
- 建構函式不會要求您指定根型別。 您可以使用相同的 `NetDataContractSerializer`執行個體來序列化任何型別。  
  
- 建構函式不接收已知型別清單。 如果型別名稱已經序列化為 XML，就不需要建構函式機制。  
  
- 建構函式不接受資料合約代理。 反之，它們接受名為 <xref:System.Runtime.Serialization.ISurrogateSelector> (對應至 `surrogateSelector` 屬性) 的 <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> 參數。 這是一項傳統的代理機制。  
  
- 建構函式接受 `assemblyFormat` 中 (對應至 <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> 屬性) 名為 <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> 的參數。 如先前所述，它可用來加強序列化程式的版本控制功能。 這與二進位或 SOAP 序列化中的 <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> 機制相同。  
  
- 建構函式接受稱為 <xref:System.Runtime.Serialization.StreamingContext> (對應至 `context` 屬性) 的 <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> 參數。 您可以透過這項參數將資訊傳遞至正要序列化的型別中。 這項用法與其他 <xref:System.Runtime.Serialization.StreamingContext> 類別使用的 <xref:System.Runtime.Serialization> 機制用法相同。  
  
- <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> 和 <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> 方法都是 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> 和 <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> 方法的別名。 這些都是為了在使用二進位或 SOAP 序列化時提供更一致的程式設計模型而存在的。  
  
 如需這些功能的詳細資訊，請參閱[二進位序列化](../../../../docs/standard/serialization/binary-serialization.md)。  
  
 `NetDataContractSerializer` 和 `DataContractSerializer` 使用的 XML 格式一般都不相容。 亦即，不支援使用其中一個序列化程式來序列化，並以另一個序列化程式來還原序列化的情況。  
  
 另請注意，`NetDataContractSerializer`不會輸出物件圖形中每個節點的.NET Framework 型別和組件名稱完整。 它只會針對不夠清楚的部分來輸出資訊。 亦即，它會在根物件層級以及任何多型案例中輸出。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [二進位序列化](../../../../docs/standard/serialization/binary-serialization.md)
- [資料合約序列化程式支援的類型](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
