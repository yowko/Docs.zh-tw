---
title: "使用 XmlSerializer 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XmlSerializer [WCF], 使用"
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 24
---
# 使用 XmlSerializer 類別
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 可以使用兩種不同的序列化技術，將您應用程式中的資料轉換成 XML，在用戶端和服務之間傳輸，這種處理稱為序列化。  
  
## DataContractSerializer 為預設值  
 根據預設，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 <xref:System.Runtime.Serialization.DataContractSerializer> 類別來序列化資料型別。 這個序列化程式支援下列型別：  
  
-   基本型別 \(例如，整數、字串和位元組陣列\) 以及一些特殊型別，例如 <xref:System.Xml.XmlElement> 和 <xref:System.DateTime>，它們被視為基本型別。  
  
-   資料合約類型 \(以 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性標示的類型\)。  
  
-   以 <xref:System.SerializableAttribute> 屬性標示的型別，包括實作 <xref:System.Runtime.Serialization.ISerializable> 介面的型別。  
  
-   實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的型別。  
  
-   許多常用的集合型別，包括許多泛型集合型別。  
  
 許多 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別屬於後兩種類別，因此是可序列化的。 可序列化型別的陣列也是可序列化的。 如需完整的清單，請參閱[指定服務合約中的資料傳輸](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。  
  
 搭配資料合約類型使用的 <xref:System.Runtime.Serialization.DataContractSerializer> 是寫入新 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的建議方式。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## 何時使用 XmlSerializer 類別  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也支援 <xref:System.Xml.Serialization.XmlSerializer> 類別。<xref:System.Xml.Serialization.XmlSerializer> 不是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 特有的類別， 它是 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務使用的同一個序列化引擎。<xref:System.Xml.Serialization.XmlSerializer> 類別支援的型別集範圍比 <xref:System.Runtime.Serialization.DataContractSerializer> 類別小多了，但允許對於結果 XML 有更多的控制權，並支援更多的 XML 結構描述定義語言 \(XSD\) 標準。 它在可序列化型別上也不需要任何宣告式屬性。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 文件中的「XML 序列化」主題。<xref:System.Xml.Serialization.XmlSerializer> 類別不支援資料合約類型。  
  
 當使用 Svcutil.exe 或 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中的 \[**加入服務參考**\] 功能來產生協力廠商服務的用戶端程式碼，或存取協力廠商結構描述時，會自動為您選擇適當的序列化程式。 如果結構描述與 <xref:System.Runtime.Serialization.DataContractSerializer> 不相容，便會選擇 <xref:System.Xml.Serialization.XmlSerializer>。  
  
## 手動切換至 XmlSerializer  
 有時候，您可能必須手動切換至 <xref:System.Xml.Serialization.XmlSerializer>。 例如，這會發生在下列案例中：  
  
-   將應用程式從 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務移轉到 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 時，您可能會想要重複使用現有的、與 <xref:System.Xml.Serialization.XmlSerializer> 相容的型別，來取代建立新的資料合約類型。  
  
-   當出現在訊息中 XML 的精確控制權很重要，但 Web 服務描述語言 \(WSDL\) 文件無法使用時，例如，當使用必須符合與 DataContractSerializer 不相容的特定標準化、已發行的結構描述來建立服務時。  
  
-   當建立遵循舊版 SOAP 編碼標準的服務時。  
  
 在這些案例和其他案例中，您可以將 <xref:System.Xml.Serialization.XmlSerializer> 屬性套用至您的服務，以手動切換至 `XmlSerializerFormatAttribute` 類別，如下列程式碼所示。  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## 安全性考量  
  
> [!NOTE]
>  當切換序列化引擎時，小心是很重要的。 根據所使用的序列化程式，相同的型別可以序列化為不同的 XML。 如果您不小心使用到錯誤的序列化程式，您可能會將您不想洩露的型別資訊洩露出來。  
  
 例如，當序列化資料合約類型時，<xref:System.Runtime.Serialization.DataContractSerializer> 類別只會序列化以 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性標示的成員。<xref:System.Xml.Serialization.XmlSerializer> 類別會序列化 Public 成員。 請參閱下列程式碼中的型別。  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 如果型別不慎用於已選擇 <xref:System.Xml.Serialization.XmlSerializer> 類別的服務合約中，便會序列化原先可能不想處理的 `creditCardNumber` 成員。  
  
 即使 <xref:System.Runtime.Serialization.DataContractSerializer> 類別是預設值，您仍然可以將 <xref:System.ServiceModel.DataContractFormatAttribute> 屬性套用至服務合約類型，明確地為服務選擇該類別 \(雖然永遠不會有這個需要\)。  
  
 用於此服務的序列化程式是合約的重要部分，且無法藉由選擇不同的繫結或變更其他組態設定來改變。  
  
 其他重要的安全性考量適用於 <xref:System.Xml.Serialization.XmlSerializer> 類別。 第一，強烈建議任何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 類別的 <xref:System.Xml.Serialization.XmlSerializer> 應用程式都要使用受保護不會洩漏的金鑰來簽章。 這個建議適用於執行手動切換至 <xref:System.Xml.Serialization.XmlSerializer> 時，以及 \(由 Svcutil.exe、「加入服務參考」或類似工具\) 執行自動切換時。 這是因為只要以和應用程式相同的金鑰來簽章，<xref:System.Xml.Serialization.XmlSerializer> 序列化引擎就會支援「*預先產生的序列化組件*」\(Pre\-generated Serialization Assembly\) 的載入。 未簽章的應用程式完全不受保護，如果惡意組件符合放在應用程式資料夾或全域組件快取中預先產生之序列化組件的預期名稱，便可能會受到攻擊。 當然，攻擊者必須先取得這兩個位置其中之一的寫入存取權，才能嘗試這個動作。  
  
 另一個每當您使用 <xref:System.Xml.Serialization.XmlSerializer> 時都會存在的威脅，是與系統暫存資料夾有關的寫入存取權。<xref:System.Xml.Serialization.XmlSerializer> 序列化引擎會建立並使用這個資料夾中的「*序列化組件*」\(Serialization Assembly\)。 您應該知道，暫存資料夾的任何寫入存取處理都可能會使用惡意程式碼來覆寫這些序列化組件。  
  
## XmlSerializer 支援的規則  
 您無法將與 <xref:System.Xml.Serialization.XmlSerializer> 相容的屬性直接套用至合約作業參數或傳回值。 然而，可以將它們套用至具型別的訊息 \(訊息合約本文部分\)，如下列程式碼所示。  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 當套用至具型別的訊息成員時，這些屬性會覆寫在具型別的訊息屬性上有衝突的屬性。 例如，在下列程式碼中，`ElementName` 會覆寫 `Name`。  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 當使用 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 時，不支援 <xref:System.Xml.Serialization.XmlSerializer> 屬性。  
  
> [!NOTE]
>  在這個案例中，<xref:System.Xml.Serialization.XmlSerializer> 會擲回下列例外狀況，它是在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 之前釋出的：「在結構描述最上層宣告的項目不可以擁有 `maxOccurs` \> 1。 經由使用 `XmlArray` 或 `XmlArrayItem`，而不使用 `XmlElementAttribute`，或使用 Wrapped 參數樣式，來提供 "more" 的包裝函式項目」。  
>   
>  如果您收到此類例外狀況，請查看這種情況是否適用。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不支援訊息合約和作業合約中的 <xref:System.Xml.Serialization.SoapIncludeAttribute> 和 <xref:System.Xml.Serialization.XmlIncludeAttribute> 屬性；請改用 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性。  
  
## 實作 IXmlSerializable 介面的型別  
 實作 `IXmlSerializable` 介面的型別完全受到 `DataContractSerializer` 的支援。<xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性應永遠套用至這些型別，以控制其結構描述。  
  
> [!WARNING]
>  如果您要序列化多型型別，必須將 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 套用至型別，以確保序列化正確型別。  
  
 實作 `IXmlSerializable` 的型別有三種：代表任意內容的型別、代表單一項目的型別以及舊版 <xref:System.Data.DataSet> 型別。  
  
-   內容型別是使用由 `XmlSchemaProviderAttribute` 屬性指定的結構描述提供者方法。 此方法不會傳回 `null`，而屬性 \(Attribute\) 上的 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> 屬性 \(Property\) 會保留為 `false` 的預設值。 這是 `IXmlSerializable` 型別最常見的使用。  
  
-   當 `IXmlSerializable` 型別必須控制自己的根項目名稱時，便會使用項目型別。 如果要將型別標示為項目型別，請將 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> 屬性 \(Attribute\) 上的 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 屬性 \(Property\) 設定為 `true`，或從結構描述提供者方法傳回 `null`。 對於項目型別，是否具有結構描述提供者方法是選擇性的 – 您可以在 `null` 中指定 `XmlSchemaProviderAttribute` 來取代方法名稱。 然而，如果 `IsAny` 是 `true` 並已指定結構描述提供者方法，則此方法必須傳回 `null`。  
  
-   舊版 <xref:System.Data.DataSet> 型別是沒有以 `IXmlSerializable` 屬性標示的 `XmlSchemaProviderAttribute` 型別。 相反地，它們是依賴 <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> 方法來產生結構描述。 在舊版 .NET Framework 中，這個模式是用於 `DataSet` 型別且其具型別的資料集會衍生類別，但這個模式現在已經過時且只為了舊版而支援。 請勿依賴這個模式，並永遠套用 `XmlSchemaProviderAttribute` 至您的 `IXmlSerializable` 型別。  
  
### IXmlSerializable 內容型別  
 當序列化實作 `IXmlSerializable` 且為上述定義的內容型別之型別的資料成員時，序列化程式會撰寫資料成員的包裝函式項目，並將控制權傳遞至 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法。<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 實作會撰寫任何 XML，包括將屬性加入至包裝函式項目。 在 `WriteXml` 完成之後，序列化程式會關閉項目。  
  
 當還原序列化實作 `IXmlSerializable` 且為上述定義的內容型別之型別的資料成員時，還原序列化程式會將 XML 讀取器放在資料成員的包裝函式項目上，並將控制權傳遞至 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法。 此方法必須讀取整個項目，包括開始和結束標記。 請確定您的 `ReadXml` 程式碼會處理項目是空白的案例。 此外，您的 `ReadXml` 實作不應依賴以特定的方式為包裝函式項目命名。 由序列化程式所選擇的名稱可能會有所不同。  
  
 允許將 `IXmlSerializable` 內容型別多型指派為如型別 <xref:System.Object> 的資料成員。 也允許型別執行個體為 null。 最後，可以使用 `IXmlSerializable` 型別並啟用物件圖形保留，以及搭配 <xref:System.Runtime.Serialization.NetDataContractSerializer>。 所有這些功能都需要 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 序列化程式將特定屬性附加至包裝函式項目中 \("nil" 和 "type" 是在 XML Schema Instance 命名空間中，而 "Id"、"Ref"、"Type" 和 "Assembly" 是在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 特定的命名空間中\)。  
  
#### 實作 ReadXml 時要忽略的屬性  
 在將控制項傳遞至您的 `ReadXml` 程式碼之前，還原序列化程式會檢查 XML 項目、偵測這些特殊的 XML 屬性並進行動作。 例如，如果 "nil" 為 `true`，便會還原序列化 null 值並且不會呼叫 `ReadXml`。 如果偵測到多型，則會還原序列化項目的內容，就如同它是不同的型別一樣。 會呼叫 `ReadXml` 的多型指派型別的實作。 在任何情況下，`ReadXml` 實作都應忽略這些特殊屬性，因為它們是由還原序列化程式所處理的。  
  
### IXmlSerializable 內容型別的結構描述考量  
 當匯出結構描述和 `IXmlSerializable` 內容型別時，會呼叫結構描述提供者方法。<xref:System.Xml.Schema.XmlSchemaSet> 會傳遞至結構描述提供者方法。 此方法會將有效的結構描述新增至結構描述集。 結構描述集包含在發生結構描述匯出時已知的結構描述。 當結構描述提供者方法必須將項目新增至結構描述集時，必須判斷有適當命名空間的 <xref:System.Xml.Schema.XmlSchema> 是否已經存在於此集合中。 如果是，結構描述提供者方法必須將新項目新增至現有的 `XmlSchema`。 否則，就必須建立新的 `XmlSchema` 執行個體。 如果是使用 `IXmlSerializable` 型別的陣列，這就很重要。 例如，如果您的 `IXmlSerializable` 型別在命名空間 "B" 中匯出為型別 "A"，就有可能在呼叫結構描述提供者方法時，結構描述集已經包含 "B" 的結構描述以保存 "ArrayOfA" 型別。  
  
 除了將型別新增至 <xref:System.Xml.Schema.XmlSchemaSet>，內容型別的結構描述提供者方法還必須傳回非 null 的值。 它會傳回 <xref:System.Xml.XmlQualifiedName>，指定用於指定的 `IXmlSerializable` 型別的結構描述型別的名稱。 這個限定名稱也會做為型別的資料合約名稱和命名空間。 當結構描述提供者方法傳回時，允許立即傳回不存在於結構描述集中的型別。 然而，預期在匯出所有相關型別時 \(在 <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> 上為所有相關型別呼叫 <xref:System.Runtime.Serialization.XsdDataContractExporter> 方法，並存取 <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> 屬性\)，此型別會存在於結構描述集中。 在完成所有相關 `Schemas` 呼叫之前存取 `Export` 屬性會造成 <xref:System.Xml.Schema.XmlSchemaException>。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]匯出程序的詳細資訊，請參閱[從類別匯出結構描述](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)。  
  
 結構描述提供者方法也可能傳回 <xref:System.Xml.Schema.XmlSchemaType> 以使用。 此型別可能是或不是匿名的。 如果是匿名的，每當使用 `IXmlSerializable` 型別做為資料成員時，便會將 `IXmlSerializable` 型別的結構描述匯出為匿名型別。`IXmlSerializable` 型別仍然會有資料合約名稱和命名空間。 \(這是依 [資料合約名稱](../../../../docs/framework/wcf/feature-details/data-contract-names.md) 中所述來判斷的，除了 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性無法用於自訂名稱\)。 如果不是匿名的，則必須是 `XmlSchemaSet` 中的其中一個型別。 這種情況等於傳回型別的 `XmlQualifiedName`。  
  
 此外，會匯出型別的全域項目宣告。 如果型別沒有套用 <xref:System.Xml.Serialization.XmlRootAttribute> 屬性 \(Attribute\)，項目會有和資料合約相同的名稱及命名空間，且其 "nillable" 屬性 \(Property\) 也會為 `true`。 這種情況唯一的例外是結構描述命名空間 \("http:\/\/www.w3.org\/2001\/XMLSchema"\) – 如果型別的資料合約是在此命名空間中，對應的全域項目將會在空白的命名空間中，因為禁止將新項目新增至結構描述命名空間。 如果型別已套用 `XmlRootAttribute` 屬性 \(Attribute\)，則會使用下列屬性 \(Property\) 匯出全域項目宣告：<xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>、<xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> 和 <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> 屬性 \(Property\)。 套用 `XmlRootAttribute` 的預設值是資料合約名稱、空白命名空間以及為 `true` 的 "nillable"。  
  
 相同的全域項目宣告規則亦適用於舊版資料集型別。 請注意，`XmlRootAttribute` 無法覆寫透過自訂程式碼新增的全域項目宣告，不論是使用結構描述提供者方法新增至 `XmlSchemaSet` 或透過舊版資料集型別的 `GetSchema`。  
  
### IXmlSerializable 項目型別  
 `IXmlSerializable` 項目型別會將 `IsAny` 屬性設定為 `true`，或讓其結構描述提供者方法傳回 `null`。  
  
 項目型別的序列化及還原序列化和內容型別的序列化及還原序列化十分類似。 然而，有一些重要的差異：  
  
-   `WriteXml` 實作預期只撰寫一個項目 \(其中當然可包含多個子項目\)。 它不應在這個單一項目、多個同層項目或混合內容以外撰寫屬性。 此項目可能是空白的。  
  
-   `ReadXml` 實作不應讀取包裝函式項目。 它預期會讀取 `WriteXml` 所產生的一個項目。  
  
-   當定期序列化項目型別時 \(例如，做為資料合約中的資料成員\)，序列化程式會在呼叫 `WriteXml` 之前輸出包裝函式項目，就像使用內容型別一樣。 然而，當在最上層序列化項目型別時，序列化程式通常完全不會輸出包含 `WriteXml` 撰寫之項目的包裝函式項目，除非在 `DataContractSerializer` 或 `NetDataContractSerializer` 建構函式中建構序列化程式時已明確指定根名稱和命名空間。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   當在最上層序列化項目型別，但在建構期間沒有指定根名稱和命名空間時，<xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> 和 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> 基本上不會執行任何動作，而 <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> 會呼叫 `WriteXml`。 在這個模式中，正在序列化的物件不得為 `null`，且無法多型指派。 另外，物件圖形保留無法啟用，且 `NetDataContractSerializer` 無法使用。  
  
-   當在最上層還原序列化元素型別，但在建構期間沒有指定根名稱和命名空間時，如果可以找到任何元素的起始，<xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> 就會傳回 `true`。<xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> 參數設定為 `verifyObjectName` 的 `true` 在實際讀取物件之前，行為方式會和 `IsStartObject` 相同。 然後 `ReadObject` 就會將控制項傳遞給 `ReadXml` 方法。  
  
 項目型別匯出的結構描述和前一節中所述的 `XmlElement` 型別相同，除了結構描述提供者方法可以將其他結構描述新增至 <xref:System.Xml.Schema.XmlSchemaSet>，就像內容型別一樣。 不允許使用 `XmlRootAttribute` 屬性搭配項目型別，也永遠不會為這些型別發出全域項目宣告。  
  
### 與 XmlSerializer 的差異  
 `IXmlSerializable` 也會辨識 `XmlSchemaProviderAttribute` 介面和 `XmlRootAttribute` 和 <xref:System.Xml.Serialization.XmlSerializer> 屬性。 然而，在資料合約模型中對於它們的處理方式有一些差異。 下表顯示重要差異的摘要：  
  
-   結構描述提供者方法必須可公開在 `XmlSerializer` 中使用，但不必公開在資料合約模型中使用。  
  
-   當 `IsAny` 在資料合約模型中為 `true`，但未使用 `XmlSerializer` 時，便會呼叫結構描述提供者方法。  
  
-   當沒有出現內容或舊版資料集型別的 `XmlRootAttribute` 屬性時，`XmlSerializer` 會在空白命名空間中匯出全域項目宣告。 在資料合約模型中，所使用的命名空間通常是資料合約命名空間，如前所述。  
  
 在建立將搭配這兩種序列化技術使用的型別時，請注意這些差異。  
  
### 匯入 IXmlSerializable 結構描述  
 當匯入從 `IXmlSerializable` 型別產生的結構描述時，有一些可能性：  
  
-   所產生的結構描述可能是有效的資料合約結構描述，如[資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)中所述。 在這種情況中，結構描述會如平常般匯入，並產生一般資料合約類型。  
  
-   所產生的結構描述可能不是有效的資料合約結構描述。 例如，您的結構描述提供者方法可能會產生結構描述，其中包含資料合約模型中不支援的 XML 屬性。 在這種情況中，您可以將結構描述匯入為 `IXmlSerializable` 型別。 這個匯入模式並未預設為開啟，但可以很容易啟用 – 例如，使用 `/importXmlTypes` 命令列參數啟用至 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 這在 [匯入結構描述以產生類別](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md) 中有詳細的說明。 請注意，您必須對您的型別執行個體直接使用 XML。 您可能也會考慮使用不同的序列化技術，支援範圍更廣的結構描述 – 請參閱有關使用 `XmlSerializer` 的主題。  
  
-   您可能會想要在 Proxy 中重複使用現有的 `IXmlSerializable` 型別，而非產生一個新的。 在這種情況中，「匯入結構描述以產生型別」主題中所說明的參照型別功能可用於指出要重複使用的型別。 這會對應至在 svcutil.exe 上使用 `/reference` 參數，指定包含要重複使用之型別的組件。  
  
### XmlSerializer 舊版行為  
 在 .NET Framework 4.0 及更早版本中，XmlSerializer 會將 C\# 程式碼寫入檔案中，以產生暫時的序列化組件。 接著將這個檔案編譯成組件。  這種行為有一些不良的後果，例如減慢序列化程式的啟動時間。 在 .NET Framework 4.5 中，這種行為已變更，不需要使用編譯器就可以產生組件。 某些開發人員可能會想要查看產生的 C\# 程式碼。 您可以藉由下列組態指定使用這個舊版行為：  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />  
  </system.xml.serialization>  
  <system.diagnostics>  
    <switches>  
      <add name="XmlSerialization.Compilation" value="1" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
  
```  
  
## 請參閱  
 <xref:System.ServiceModel.DataContractFormatAttribute>   
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Xml.Serialization.XmlSerializer>   
 <xref:System.ServiceModel.MessageHeaderArrayAttribute>   
 [指定服務合約中的資料傳輸](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)   
 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)   
 [HOW TO：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)