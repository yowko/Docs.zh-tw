---
title: "匯入結構描述以產生類別 | Microsoft Docs"
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
  - "WCF, 結構描述匯入和匯出"
  - "XsdDataContractImporter 類別"
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 匯入結構描述以產生類別
從可在結構描述產生類別[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]，使用<xref:System.Runtime.Serialization.XsdDataContractImporter>類別。 這個主題將說明處理程序和變化。  
  
## <a name="the-import-process"></a>匯入程序  
 結構描述匯入程序一開始<xref:System.Xml.Schema.XmlSchemaSet> ，並產生<xref:System.CodeDom.CodeCompileUnit>。  
  
 `XmlSchemaSet` 是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的結構描述物件模型 (SOM) 的一部分，它代表一組 XML 結構描述定義語言 (Schema definition language，XSD) 結構描述文件。 若要建立`XmlSchemaSet`物件從一組 XSD 文件，還原序列化各文件至<xref:System.Xml.Schema.XmlSchema>物件 (使用<xref:System.Xml.Serialization.XmlSerializer>) 並將這些物件加入至新`XmlSchemaSet`。  
  
 `CodeCompileUnit` 是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的 Code Document Object Model (CodeDOM) 的一部分，它會以抽象方式表示 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 程式碼。 若要產生實際的程式碼從`CodeCompileUnit`，使用的子類別<xref:System.CodeDom.Compiler.CodeDomProvider>類別，例如<xref:Microsoft.CSharp.CSharpCodeProvider>或<xref:Microsoft.VisualBasic.VBCodeProvider>類別。  
  
#### <a name="to-import-a-schema"></a>匯入結構描述  
  
1.  建立的執行個體<xref:System.Runtime.Serialization.XsdDataContractImporter>。  
  
2.  選擇項。 傳遞建構函式中的 `CodeCompileUnit`。 在結構描述匯入期間產生的型別會新增至這個 `CodeCompileUnit` 執行個體，而不是從空白的 `CodeCompileUnit` 開始。  
  
3.  選擇項。 呼叫其中一種<xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A>方法。 此方法會判斷指定的結構描述是否為有效資料合約結構描述，且可以匯入。 `CanImport` 方法有和 `Import` 相同的多載 (下一個步驟)。  
  
4.  呼叫其中一個多載`Import`方法，例如<xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29>方法。  
  
     最簡單的多載是採用 `XmlSchemaSet`，並匯入在該結構描述集中找到的所有型別，包括匿名型別。 其他多載可讓您指定要匯入的 XSD 型別或型別的清單 (以<xref:System.Xml.XmlQualifiedName>或一群`XmlQualifiedName`物件)。 在這個案例中，只會匯入指定的型別。 多載接受<xref:System.Xml.Schema.XmlSchemaElement>匯入特定的項目超出`XmlSchemaSet`，以及其相關聯的型別 （它是否匿名）。 這個多載會傳回 `XmlQualifiedName`，表示針對這個項目所產生之型別的資料合約名稱。  
  
     `Import` 方法的多個呼叫會造成將多個項目新增至相同的 `CodeCompileUnit`。 如果型別已經存在，便不會產生至 `CodeCompileUnit` 中。 請在相同的 `Import` 上多次呼叫 `XsdDataContractImporter`，而不要使用多個 `XsdDataContractImporter` 物件。 這是避免產生重複型別的建議方式。  
  
    > [!NOTE]
    >  如果在匯入期間發生失敗，`CodeCompileUnit` 將會處於無法預測的狀態。 使用源自失敗之匯入的 `CodeCompileUnit` 可能會讓您暴露在安全性弱點中。  
  
5.  存取`CodeCompileUnit`透過<xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A>屬性。  
  
### <a name="import-options-customizing-the-generated-types"></a>匯入選項：自訂產生的型別  
 您可以設定<xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A>屬性<xref:System.Runtime.Serialization.XsdDataContractImporter>的執行個體<xref:System.Runtime.Serialization.ImportOptions>類別，以控制匯入程序的各個層面。 選項的數目會直接影響到所產生的型別。  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>控制存取層級 (GenerateInternal 或 /internal 參數)  
 這會對應到**/ 內部**上切換[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
 一般來說，公用型別是從結構描述產生的，其中包含私用欄位和相符的公用資料成員屬性。 若要改為產生內部型別，將<xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A>屬性`true`。  
  
 下列範例顯示結構描述轉換成內部類別時<xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A>屬性設定為`true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>控制命名空間 (Namespaces 或 /namespace 參數)  
 這會對應到**/namespace**上切換`Svcutil.exe`工具。  
  
 一般來說，從結構描述產生的型別都會產生到[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]具有對應至特定的各個 XSD 命名空間的命名空間，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]命名空間中所述的對應根據[資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。 您可以自訂這個對應<xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A>屬性<xref:System.Collections.Generic.Dictionary%602>。\</TKey, TValue> 如果在目錄中找到指定的 XSD 命名空間，相符的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 命名空間也是取自您的目錄。  
  
 例如，請試想下列結構描述。  
  
 [!code[c_SchemaImportExport#10](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 下列範例是使用 `Namespaces` 屬性，將 "http://schemas.contoso.com/carSchema" 命名空間對應至 "Contoso.Cars"。  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>新增 SerializableAttribute (GenerateSerializable 或 /serializable 參數)  
 這會對應到**/ 序列化**上切換`Svcutil.exe`工具。  
  
 有時是很重要的結構描述產生的類型，可在[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]執行階段序列化引擎 (例如， <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName>和<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>類別)。 當針對 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 遠端使用型別時，這很有用。 若要啟用此功能，您必須套用<xref:System.SerializableAttribute>屬性設定為產生的型別，除了一般<xref:System.Runtime.Serialization.DataContractAttribute>屬性。 如果 `GenerateSerializable` 匯入選項設定為 `true`，便會自動產生此屬性。  
  
 下列範例會顯示由 `Vehicle` 匯入選項設定為 `GenerateSerializable` 所產生的 `true` 類別。  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>新增資料繫結支援 (EnableDataBinding 或 /enableDataBinding 參數)  
 這會對應到**/enableDataBinding** Svcutil.exe 工具上切換。  
  
 有時，您可能會想要將從結構描述產生的型別，繫結至圖形使用者介面元件，讓這些型別之執行個體的更新可以自動更新 UI。 `XsdDataContractImporter`可以產生型別可實作<xref:System.ComponentModel.INotifyPropertyChanged>介面中的任何屬性變更都會觸發事件的方式。 如果您要產生的用戶端 UI 程式設計環境支援這個介面的型別 (例如[!INCLUDE[avalon1](../../../../includes/avalon1-md.md)])，請將<xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A>屬性`true`啟用這項功能。  
  
 下列範例所示`Vehicle`類別以產生<xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A>設為`true`。  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>匯入選項：選擇集合型別  
 XML 中有兩種特殊模式表示項目的集合：項目的清單以及兩個項目之間的關聯。 以下是字串清單的範例。  
  
 [!code[C_SchemaImportExport#11](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 以下是字串和整數之間關聯的範例 (`city name` 和 `population`)。  
  
 [!code[C_SchemaImportExport#12](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  任何關聯也都可以視為是清單。 例如，您可以將前述關聯視為是剛好有兩個欄位 (字串欄位和整數欄位) 之複雜 `city` 物件的清單。 這兩種模式在 XSD 結構描述中都有表示法。 由於並沒有方法可以區分清單和關聯，因此這類模式永遠會被視為是清單，除非結構描述中有 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 特定的特別附註。 附註會指出指定的模式表示關聯。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。  
  
 一般來說，會匯入清單做為衍生自泛型清單的集合資料合約或做為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 陣列，視結構描述是否遵循集合的標準命名樣式而定。 這更詳細地描述[集合資料合約中的型別](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)。 關聯是通常被匯入做<xref:System.Collections.Generic.Dictionary%602>或衍生自目錄物件的集合資料合約。\</TKey, TValue> 例如，請試想下列結構描述。  
  
 [!code[c_SchemaImportExport#13](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 其匯入如下所示 (顯示欄位而非屬性以具可讀性)。  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 您可以自訂為此類結構描述模式所產生的集合型別。 例如，您可能要產生衍生自集合<xref:System.ComponentModel.BindingList%601>而不是<xref:System.Collections.Generic.List%601>集合的內容變更時，會自動更新以便繫結到清單方塊的類型，並讓它的類別。 若要這樣做，請設定<xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>屬性<xref:System.Runtime.Serialization.ImportOptions>類別清單的使用 （之後稱為參照型別） 的集合型別。 當匯入集合時，便會掃描這份參照集合型別的清單，並使用最符合的集合 (如果找得到的話)。 只針對實作一般性或非泛型型別比對關聯<xref:System.Collections.IDictionary>介面清單比對任何支援的集合型別。  
  
 例如，如果<xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>屬性設定為<xref:System.ComponentModel.BindingList%601>、`people`在上述範例中的型別便會產生如下。  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 封閉式泛型被視為最符合的型別。 例如，如果型別`BindingList(Of Integer)`和<xref:System.Collections.ArrayList>會傳遞至參照型別任何的集合結構描述中找到整數清單都會匯入做`BindingList(Of Integer)`。 任何其他清單 (例如 `List(Of String)`) 都會匯入做為 `ArrayList`。  
  
 如果將實作泛型 `IDictionary` 介面的型別新增至參照型別的集合，其型別參數必須是完全開啟或完全封閉的。  
  
 不允許重複。 例如，您無法同時將 `List(Of Integer)` 和 `Collection(Of Integer)` 新增至參照型別。 這會讓它無法判斷當在結構描述中找到整數清單時，應使用何者。 只有當結構描述中有公開重複問題的型別時，才會偵測到重複。 例如，如果匯入的結構描述不包含整數的清單，便會允許它在參照型別集合中有 `List(Of Integer)` 和 `Collection(Of Integer)`，但是這兩者不會造成任何影響。  
  
 所參照集合型別機制對於複雜型別的集合 (包括其他集合的集合)，運作效果都一樣好，而不只是適合基本型別的集合。  
  
 `ReferencedCollectionTypes`屬性會對應至**/collectionType** SvcUtil.exe 工具上切換。 請注意，如果要參照多個集合型別， **/collectionType**參數必須指定多次。 如果型別不在 MsCorLib.dll 中，其參考組件必須也是使用**/參考**切換。  
  
#### <a name="import-options-referencing-existing-types"></a>匯入選項：參照現有型別  
 結構描述中的型別偶而會對應至現有的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別，而不需要從頭開始產生這些型別  (本節只適用於非集合型別。 對於集合型別，請參閱上一節)。  
  
 例如，您可能會有標準的全公司「人員」資料合約類型，固定用於表示人員。 只要有服務使用這個型別，且其結構描述出現在服務中繼資料中，當匯入這個結構描述時，您可能會想要重複使用現有的 `Person` 型別，而非為每個服務產生新的型別。  
  
 若要這樣做，請將傳遞一份[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]您想要插入集合中重複使用的型別<xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A>屬性會傳回在<xref:System.Runtime.Serialization.ImportOptions>類別。 如果其中任何型別的資料合約名稱和命名空間符合結構描述型別的名稱和命名空間，便會執行結構比較。 如果判斷出型別同時具有相符的名稱和結構，便會重複使用現有的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別，而非產生新的型別。 如果只有名稱符合，但結構不符合，則會擲回例外狀況。 請注意，當參照型別時，不允許進行版本控制 (例如，新增選擇性資料成員)。 結構必須完全相符。  
  
 將多個有相同資料合約名稱和命名空間的型別新增至參照型別集合是合法的，只要沒有結構描述型別使用該名稱和命名空間匯入即可。 這可讓您輕鬆地將組件中的所有型別新增至集合，而不需擔心並未實際發生在結構描述中的型別有重複。  
  
 `ReferencedTypes`屬性會對應至**/參考**切換移入特定的 Svcutil.exe 工具的作業模式。  
  
> [!NOTE]
>  當使用 Svcutil.exe 或 (在[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)])**加入服務參考**會自動參照 MsCorLib.dll 中的型別所有的工具。  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>匯入選項：匯入非 DataContract 結構描述做為 IXmlSerializable 型別  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>支援結構描述的有限的子集。 如果有不支援的結構描述建構存在 (例如，XML 屬性)，匯入嘗試便會失敗並有例外狀況。 不過，設定<xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>屬性`true`延伸結構描述支援的範圍。 當設定為`true`、 <xref:System.Runtime.Serialization.XsdDataContractImporter>實作的型別會產生<xref:System.Xml.Serialization.IXmlSerializable>介面。 如此可直接存取這些型別的 XML 表示法。  
  
##### <a name="design-considerations"></a>設計考量  
  
-   直接使用較弱型別的 XML 表示法可能會很困難。 請考慮使用另一種序列化引擎，例如<xref:System.Xml.Serialization.XmlSerializer>，若要使用的結構描述不相容的資料合約的強型別的方式。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][使用 XmlSerializer 類別](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)。  
  
-   有些結構描述建構無法由匯入<xref:System.Runtime.Serialization.XsdDataContractImporter>時，即使<xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>屬性設定為`true`。 同樣地，請考慮使用<xref:System.Xml.Serialization.XmlSerializer>這種情況下。  
  
-   確切的結構描述建構將會同時支援時<xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>是`true`或`false`述[資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。  
  
-   結構描述產生<xref:System.Xml.Serialization.IXmlSerializable>類型不會保留逼真度匯入和匯出時。 也就是說，從產生的型別匯出結構描述然後匯入做為類別並不會傳回原始的結構描述。  
  
 可以結合<xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>選項與<xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A>先前所述的選項。 必須產生做為具有型別的<xref:System.Xml.Serialization.IXmlSerializable>使用時，會略過實作中，結構化的核取<xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A>功能。  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>選項對應至**/importXmlTypes** Svcutil.exe 工具上切換。  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>使用所產生的 IXmlSerializable 型別  
 產生`IXmlSerializable`型別包含名為"nodesField"的私用欄位，傳回的陣列<xref:System.Xml.XmlNode>物件。 當還原序列化此類型別的執行個體時，您可以使用 XML 文件物件模型，透過這個欄位直接存取 XML 資料。 當序列化這個型別的執行個體時，您可以將這個欄位設定為需要的 XML 資料，且它將會序列化。  
  
 這是透過 `IXmlSerializable` 實作完成的。 在產生`IXmlSerializable`型別， <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>實作會呼叫<xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A>方法<xref:System.Runtime.Serialization.XmlSerializableServices>類別。 方法是 helper 方法，可透過提供的 XML 轉換為<xref:System.Xml.XmlReader>陣列<xref:System.Xml.XmlNode>物件。 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>實作會執行相反的並將陣列轉換成`XmlNode`物件的序列<xref:System.Xml.XmlWriter>呼叫。 這利用完成<xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A>方法。  
  
 您或許可以在所產生的 `IXmlSerializable` 類別上執行結構描述匯出處理程序。 如前所述，將不會傳回原始的結構描述。 相反地，您會收到 “anyType” 標準 XSD 型別，這是任何 XSD 型別的萬用字元。  
  
 這可以藉由套用<xref:System.Xml.Serialization.XmlSchemaProviderAttribute>屬性設定為產生`IXmlSerializable`類別，並指定方法呼叫<xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A>方法以產生"anyType"型別。  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices>為了支援這項特定功能而單獨存在的型別。 並不建議用於其他方面。  
  
#### <a name="import-options-advanced-options"></a>匯入選項：進階選項  
 以下是進階匯入選項：  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>屬性。 指定<xref:System.CodeDom.Compiler.CodeDomProvider>用來產生的程式碼產生的類別。 匯入機制會嘗試避免功能<xref:System.CodeDom.Compiler.CodeDomProvider>不支援。 例如，J# 語言不支援泛型。 如果您在這個屬性中指定 J# 程式碼提供者，沒有泛型型別來產生匯入工具的<xref:System.CodeDom.CodeCompileUnit>。 如果<xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>未設定，則整組[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]功能使用不受限制。  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>屬性。 <xref:System.Runtime.Serialization.IDataContractSurrogate>實作可以使用這個屬性來指定。 <xref:System.Runtime.Serialization.IDataContractSurrogate>自訂匯入處理程序。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][資料合約 Surrogate](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)。 根據預設，不會使用 Surrogate。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.XsdDataContractImporter>   
 <xref:System.Runtime.Serialization.XsdDataContractExporter>   
 <xref:System.Runtime.Serialization.ImportOptions>   
 [資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)   
 [資料合約代理](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)   
 [結構描述匯入和匯出](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)   
 [從類別匯出結構描述](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)   
 [資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)