---
title: 匯入結構描述以產生類別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
ms.openlocfilehash: 68890a5d86d2781e3c8079c86e941144e3796ea6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228584"
---
# <a name="importing-schema-to-generate-classes"></a>匯入結構描述以產生類別
若要從可與 Windows Communication Foundation (WCF) 的結構描述產生類別，使用<xref:System.Runtime.Serialization.XsdDataContractImporter>類別。 這個主題將說明處理程序和變化。  
  
## <a name="the-import-process"></a>匯入程序
 結構描述匯入程序是從 <xref:System.Xml.Schema.XmlSchemaSet> 開始，並產生 <xref:System.CodeDom.CodeCompileUnit>。  
  
 `XmlSchemaSet` 是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的結構描述物件模型 (SOM) 的一部分，它代表一組 XML 結構描述定義語言 (Schema definition language，XSD) 結構描述文件。 如果要從一組 XSD 文件建立 `XmlSchemaSet` 物件，請還原序列化各文件至 <xref:System.Xml.Schema.XmlSchema> 物件中 (使用 <xref:System.Xml.Serialization.XmlSerializer>)，然後新增這些物件至新的 `XmlSchemaSet`。  
  
 `CodeCompileUnit` 是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的 Code Document Object Model (CodeDOM) 的一部分，它會以抽象方式表示 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 程式碼。 如果要從 `CodeCompileUnit` 產生實際的程式碼，請使用 <xref:System.CodeDom.Compiler.CodeDomProvider> 類別的子類別，例如 <xref:Microsoft.CSharp.CSharpCodeProvider> 或 <xref:Microsoft.VisualBasic.VBCodeProvider> 類別。  
  
### <a name="to-import-a-schema"></a>匯入結構描述  
  
1. 建立 <xref:System.Runtime.Serialization.XsdDataContractImporter>的執行個體。  
  
2. 選擇性。 傳遞建構函式中的 `CodeCompileUnit`。 在結構描述匯入期間產生的型別會新增至這個 `CodeCompileUnit` 執行個體，而不是從空白的 `CodeCompileUnit` 開始。  
  
3. 選擇性。 呼叫其中一個 <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> 方法。 此方法會判斷指定的結構描述是否為有效資料合約結構描述，且可以匯入。 `CanImport` 方法有和 `Import` 相同的多載 (下一個步驟)。  
  
4. 呼叫其中一個多載 `Import` 方法，例如 <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> 方法。  
  
     最簡單的多載是採用 `XmlSchemaSet`，並匯入在該結構描述集中找到的所有型別，包括匿名型別。 其他的多載可讓您指定要匯入的 XSD 型別或型別清單 (以 <xref:System.Xml.XmlQualifiedName> 或 `XmlQualifiedName` 物件集合的格式)。 在這個案例中，只會匯入指定的型別。 多載會採用匯入 <xref:System.Xml.Schema.XmlSchemaElement> 之特定項目的 `XmlSchemaSet`，以及其相關型別 (無論是否為匿名)。 這個多載會傳回 `XmlQualifiedName`，表示針對這個項目所產生之型別的資料合約名稱。  
  
     `Import` 方法的多個呼叫會造成將多個項目新增至相同的 `CodeCompileUnit`。 如果型別已經存在，便不會產生至 `CodeCompileUnit` 中。 請在相同的 `Import` 上多次呼叫 `XsdDataContractImporter`，而不要使用多個 `XsdDataContractImporter` 物件。 這是避免產生重複型別的建議方式。  
  
    > [!NOTE]
    > 如果在匯入期間發生失敗，`CodeCompileUnit` 將會處於無法預測的狀態。 使用源自失敗之匯入的 `CodeCompileUnit` 可能會讓您暴露在安全性弱點中。  
  
5. 請透過 `CodeCompileUnit` 屬性存取 <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> 。  
  
### <a name="import-options-customizing-the-generated-types"></a>匯入選項：自訂產生的型別  
 您可以將 <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> 的 <xref:System.Runtime.Serialization.XsdDataContractImporter> 屬性設定為 <xref:System.Runtime.Serialization.ImportOptions> 類別的執行個體，以控制匯入處理程序的各方面。 選項的數目會直接影響到所產生的型別。  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>控制存取層級 (GenerateInternal 或 /internal 參數)  
 這會對應至 **/ 內部**上切換[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
 一般來說，公用型別是從結構描述產生的，其中包含私用欄位和相符的公用資料成員屬性。 如果要改為產生內部型別，請將 <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> 屬性設定為 `true`。  
  
 下列範例示範結構描述轉換成內部類別時<xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A>屬性設定為 `true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>控制命名空間 (Namespaces 或 /namespace 參數)  
 這會對應至 **/namespace**切換成開啟`Svcutil.exe`工具。  
  
 一般來說，從結構描述產生的型別會產生至[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]命名空間，與每個對應至特定的 XSD 命名空間[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]中所述的對應根據的命名空間[Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). 您可以將 <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> 屬性設定為 <xref:System.Collections.Generic.Dictionary%602>，以自訂這個對應。 如果在目錄中找到指定的 XSD 命名空間，相符的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 命名空間也是取自您的目錄。  
  
 例如，請試想下列結構描述。  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 下列範例會使用`Namespaces`屬性來對應`http://schemas.contoso.com/carSchema`至"Contoso.Cars"的命名空間。  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>新增 SerializableAttribute (GenerateSerializable 或 /serializable 參數)  
 這會對應至 **/serializable**切換成開啟`Svcutil.exe`工具。  
  
 有時對於從結構描述產生的型別來說，可在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 執行階段序列化引擎中使用是很重要的 (例如，<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> 和 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> 類別)。 當針對 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 遠端使用型別時，這很有用。 如果要啟用，除了一般的 <xref:System.SerializableAttribute> 屬性之外，您還必須將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至所產生的型別。 如果 `GenerateSerializable` 匯入選項設定為 `true`，便會自動產生此屬性。  
  
 下列範例會顯示由 `Vehicle` 匯入選項設定為 `GenerateSerializable` 所產生的 `true` 類別。  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>新增資料繫結支援 (EnableDataBinding 或 /enableDataBinding 參數)  
 這會對應至 **/enableDataBinding** Svcutil.exe 工具上切換。  
  
 有時，您可能會想要將從結構描述產生的型別，繫結至圖形使用者介面元件，讓這些型別之執行個體的更新可以自動更新 UI。 `XsdDataContractImporter` 可以產生以任何屬性變更都會觸發事件的方式實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的型別。 如果您要產生用於用戶端 UI 程式設計環境，以支援這個介面 (例如 Windows Presentation Foundation (WPF)) 的類型，設定<xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A>屬性設`true`啟用這項功能。  
  
 下列範例會顯示由 `Vehicle` 設定為 <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> 所產生的 `true` 類別。  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>匯入選項：選擇集合型別  
 XML 中有兩種特殊模式表示項目的集合：項目的清單以及兩個項目之間的關聯。 以下是字串清單的範例。  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 以下是字串和整數之間關聯的範例 (`city name` 和 `population`)。  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  任何關聯也都可以視為是清單。 例如，您可以將前述關聯視為是剛好有兩個欄位 (字串欄位和整數欄位) 之複雜 `city` 物件的清單。 這兩種模式在 XSD 結構描述中都有表示法。 沒有任何方法可以區分清單和關聯，因此這種模式都被視為清單除非特定 wcf 的特殊註釋是出現在結構描述。 附註會指出指定的模式表示關聯。 如需詳細資訊，請參閱 < [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。  
  
 一般來說，會匯入清單做為衍生自泛型清單的集合資料合約或做為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 陣列，視結構描述是否遵循集合的標準命名樣式而定。 這描述更詳細地[集合 Types in Data Contracts](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)。 關聯通常會被匯入做為 <xref:System.Collections.Generic.Dictionary%602> 或衍生自目錄物件的集合資料合約。 例如，請試想下列結構描述。  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 其匯入如下所示 (顯示欄位而非屬性以具可讀性)。  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 您可以自訂為此類結構描述模式所產生的集合型別。 例如，您可能會想要產生衍生自 <xref:System.ComponentModel.BindingList%601> 而非 <xref:System.Collections.Generic.List%601> 類別的集合，以便將型別繫結至清單方塊，並讓它在集合的內容變更時自動更新。 如果要執行這項操作，請將 <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> 類別的 <xref:System.Runtime.Serialization.ImportOptions> 屬性設定為要使用之集合型別的清單 (之後稱為參照型別)。 當匯入集合時，便會掃描這份參照集合型別的清單，並使用最符合的集合 (如果找得到的話)。 關聯只會針對實作一般性或非一般性 <xref:System.Collections.IDictionary> 介面的型別進行對應，而清單會針對任何支援的集合型別進行對應。  
  
 例如，如果 <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> 屬性設定為 <xref:System.ComponentModel.BindingList%601>，前例中的 `people` 型別便會產生如下。  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 封閉式泛型被視為最符合的型別。 例如，如果型別 `BindingList(Of Integer)` 和 <xref:System.Collections.ArrayList> 傳遞至參照型別的集合，在結構描述中找到的任何整數清單都會匯入做為 `BindingList(Of Integer)`。 任何其他清單 (例如 `List(Of String)`) 都會匯入做為 `ArrayList`。  
  
 如果將實作泛型 `IDictionary` 介面的型別新增至參照型別的集合，其型別參數必須是完全開啟或完全封閉的。  
  
 不允許重複。 例如，您無法同時將 `List(Of Integer)` 和 `Collection(Of Integer)` 新增至參照型別。 這會讓它無法判斷當在結構描述中找到整數清單時，應使用何者。 只有當結構描述中有公開重複問題的型別時，才會偵測到重複。 例如，如果匯入的結構描述不包含整數的清單，便會允許它在參照型別集合中有 `List(Of Integer)` 和 `Collection(Of Integer)`，但是這兩者不會造成任何影響。  
  
 所參照集合型別機制對於複雜型別的集合 (包括其他集合的集合)，運作效果都一樣好，而不只是適合基本型別的集合。  
  
 `ReferencedCollectionTypes`屬性會對應至 **/collectionType** SvcUtil.exe 工具上切換。 請注意，如果要參照多個集合的型別， **/collectionType**參數必須指定多次。 如果類型不在 MsCorLib.dll 中，其參考組件必須也是使用 **/參考**切換。  
  
#### <a name="import-options-referencing-existing-types"></a>匯入選項：參照現有型別  
 結構描述中的型別偶而會對應至現有的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別，而不需要從頭開始產生這些型別  (本節只適用於非集合型別。 對於集合型別，請參閱上一節)。  
  
 例如，您可能會有標準的全公司「人員」資料合約類型，固定用於表示人員。 只要有服務使用這個型別，且其結構描述出現在服務中繼資料中，當匯入這個結構描述時，您可能會想要重複使用現有的 `Person` 型別，而非為每個服務產生新的型別。  
  
 如果要執行這項操作，請將您要重複使用之 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別的清單傳遞至 <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> 類別上 <xref:System.Runtime.Serialization.ImportOptions> 屬性傳回的集合中。 如果其中任何型別的資料合約名稱和命名空間符合結構描述型別的名稱和命名空間，便會執行結構比較。 如果判斷出型別同時具有相符的名稱和結構，便會重複使用現有的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別，而非產生新的型別。 如果只有名稱符合，但結構不符合，則會擲回例外狀況。 請注意，當參照型別時，不允許進行版本控制 (例如，新增選擇性資料成員)。 結構必須完全相符。  
  
 將多個有相同資料合約名稱和命名空間的型別新增至參照型別集合是合法的，只要沒有結構描述型別使用該名稱和命名空間匯入即可。 這可讓您輕鬆地將組件中的所有型別新增至集合，而不需擔心並未實際發生在結構描述中的型別有重複。  
  
 `ReferencedTypes`屬性會對應至 **/參考**切換移入特定的 Svcutil.exe 工具的作業模式。  
  
> [!NOTE]
>  當使用 Svcutil.exe 或 （在 Visual Studio)**加入服務參考**會自動參照 MsCorLib.dll 中的類型的所有工具。  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>匯入選項：匯入非 DataContract 結構描述，做為 IXmlSerializable 型別  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> 支援結構描述的有限子集。 如果有不支援的結構描述建構存在 (例如，XML 屬性)，匯入嘗試便會失敗並有例外狀況。 然而，將 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> 屬性設定為 `true` 可延伸受支援的結構描述範圍。 當設定為 `true` 時，<xref:System.Runtime.Serialization.XsdDataContractImporter> 會產生實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的型別。 如此可直接存取這些型別的 XML 表示法。  
  
##### <a name="design-considerations"></a>設計考量  
  
-   直接使用較弱型別的 XML 表示法可能會很困難。 請考慮使用另一種序列化引擎 (例如 <xref:System.Xml.Serialization.XmlSerializer>) 以強型別方式來使用與資料合約不相容的結構描述。 如需詳細資訊，請參閱 <<c0> [ 使用 XmlSerializer 類別](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)。  
  
-   即使 <xref:System.Runtime.Serialization.XsdDataContractImporter> 屬性設定為 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>，有些結構描述建構仍然無法由 `true` 匯入。 請再次考慮針對此類案例使用 <xref:System.Xml.Serialization.XmlSerializer>。  
  
-   確切的結構描述建構將會同時支援時<xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>是`true`或是`false`所述[Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。  
  
-   所產生的 <xref:System.Xml.Serialization.IXmlSerializable> 型別的結構描述在匯入和匯出時不會保留逼真度。 也就是說，從產生的型別匯出結構描述然後匯入做為類別並不會傳回原始的結構描述。  
  
 您或許可以結合 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> 選項與之前所述的 <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> 選項。 對於必須產生做為 <xref:System.Xml.Serialization.IXmlSerializable> 實作的型別，會在使用 <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> 功能時跳過結構檢查。  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>選項對應至 **/importXmlTypes** Svcutil.exe 工具上切換。  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>使用所產生的 IXmlSerializable 型別  
 所產生的 `IXmlSerializable` 型別包含名為 "nodesField" 的私用欄位，它會傳回 <xref:System.Xml.XmlNode> 物件的陣列。 當還原序列化此類型別的執行個體時，您可以使用 XML 文件物件模型，透過這個欄位直接存取 XML 資料。 當序列化這個型別的執行個體時，您可以將這個欄位設定為需要的 XML 資料，且它將會序列化。  
  
 這是透過 `IXmlSerializable` 實作完成的。 在所產生的 `IXmlSerializable` 型別中，<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 實作會呼叫 <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> 類別的 <xref:System.Runtime.Serialization.XmlSerializableServices> 方法。 此方法是 Helper 方法，會將透過 <xref:System.Xml.XmlReader> 提供的 XML 轉換為 <xref:System.Xml.XmlNode> 物件的陣列。 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 實作會執行相反的操作，並將 `XmlNode` 物件的陣列轉換成 <xref:System.Xml.XmlWriter> 呼叫的序列。 這是使用 <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> 方法完成的。  
  
 您或許可以在所產生的 `IXmlSerializable` 類別上執行結構描述匯出處理程序。 如前所述，將不會傳回原始的結構描述。 相反地，您會收到"anyType"標準 XSD 型別，也就是任何 XSD 型別的萬用字元。  
  
 這可以藉由套用<xref:System.Xml.Serialization.XmlSchemaProviderAttribute>屬性設定為產生`IXmlSerializable`類別，並指定方法的呼叫<xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A>方法以產生"anyType"型別。  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices> 型別是為了支援這項特定功能而單獨存在的。 並不建議用於其他方面。  
  
#### <a name="import-options-advanced-options"></a>匯入選項：進階選項  
 以下是進階匯入選項：  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> 屬性。 請指定 <xref:System.CodeDom.Compiler.CodeDomProvider>，用於為所產生的類別產生程式碼。 匯入機制會嘗試避免 <xref:System.CodeDom.Compiler.CodeDomProvider> 不支援的功能。 如果沒有設定 <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>，使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的完整功能便沒有限制。  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> 屬性。 <xref:System.Runtime.Serialization.IDataContractSurrogate> 實作可以使用這個屬性來指定。 <xref:System.Runtime.Serialization.IDataContractSurrogate> 會自訂匯入處理程序。 如需詳細資訊，請參閱 <<c0> [ 資料合約代理](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)。 根據預設，不會使用 Surrogate。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- <xref:System.Runtime.Serialization.ImportOptions>
- [資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
- [資料合約代理](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)
- [結構描述匯入和匯出](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [從類別匯出結構描述](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
- [資料合約結構描述參考](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
