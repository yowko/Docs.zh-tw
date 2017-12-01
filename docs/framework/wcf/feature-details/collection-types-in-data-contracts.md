---
title: "資料合約中的集合型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8591f1c7c3aa123acd17a9e3ab22cf950275f588
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="collection-types-in-data-contracts"></a>資料合約中的集合型別
「 *集合* 」(Collection) 是特定型別之項目的清單。 在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]中，可以使用陣列或其他多種型別 (泛型清單、泛型 <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>或 <xref:System.Collections.ArrayList>) 來表示這類清單。 例如，集合可能含有特定「客戶」的地址清單。 不論實際型別為何，這些集合統稱為「 *清單集合*」(List Collection)。  
  
 特殊形式的集合可以用來表示一個項目 (「索引鍵」) 與另一個項目 (「值」) 之間的關聯。 在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]中，這些集合將表示成 <xref:System.Collections.Hashtable> 及泛型字典等型別。 例如，關聯集合可能會將城市 (「索引鍵」) 對應到其人口數目 (「值」)。 不論實際型別為何，這些集合統稱為「 *字典集合*」(Dictionary Collection)。  
  
 集合在資料合約模型中會受到特殊處理。  
  
 包括陣列與泛型集合等實作 <xref:System.Collections.IEnumerable> 介面的型別，都會識別為集合。 在這些型別中，實作 <xref:System.Collections.IDictionary> 或泛型 <xref:System.Collections.Generic.IDictionary%602> 介面的型別屬於字典集合，而其他所有型別則屬於清單集合。  
  
 關於集合型別的其他需求，例如包含稱為 `Add` 的方法和預設建構函式 (Constructor)，都會在下列各節中詳細討論。 這樣便可確保集合型別能夠序列化與還原序列化。 這表示不直接支援某些集合，例如泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (因為沒有預設建構函式)。 不過，如需規避這些限制的詳細資訊，請參閱本主題稍後的「使用集合介面型別和唯讀集合」一節。  
  
 包含在集合中的型別必須是資料合約類型，否則必須是可序列化的型別。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][資料合約序列化程式所支援的型別](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 被視為有效集合的條件以及如何序列化集合的詳細資訊，請參閱本主題「進階集合規則」一節中有關序列化集合的資訊。  
  
## <a name="interchangeable-collections"></a>可互換的集合  
 相同型別的所有清單集合，都會被視為具有相同的資料合約 (除非有使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性來自訂這些集合，如本主題稍後所討論)。 例如，下列資料合約是相等的。  
  
 [!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
 [!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]  
  
 這兩個資料合約都會產生與下列程式碼類似的 XML。  
  
```xml  
<PurchaseOrder>  
    <customerName>...</customerName>  
    <items>  
        <Item>...</Item>  
        <Item>...</Item>  
        <Item>...</Item>  
        ...  
    </items>  
    <comments>  
        <string>...</string>  
        <string>...</string>  
        <string>...</string>  
        ...  
    </comments>  
</PurchaseOrder>  
```  
  
 集合可互換性讓您能夠使用像是已針對伺服器效能完成最佳化的集合型別，以及設計用來繫結至用戶端上之使用者介面元件的集合型別。  
  
 類似於清單集合，具有相同索引鍵和值型別的所有字典集合都會被視為具有相同的資料合約 (除非已由 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性自訂)。  
  
 就考慮集合的相等性而言，只有資料合約類型 (而非 .NET 型別) 會有影響。 也就是說，如果 Type1 集合與 Type2 集合擁有相同的資料合約，Type1 與 Type2 就會被視為相等。  
  
 非泛型集合也會被視為與 `Object`型別的泛型集合具有相同的資料合約 (例如， <xref:System.Collections.ArrayList> 與 <xref:System.Collections.Generic.List%601> 之泛型 `Object` 的資料合約都是相等的)。  
  
## <a name="using-collection-interface-types-and-read-only-collections"></a>使用集合介面型別和唯讀集合  
 集合介面型別 (<xref:System.Collections.IEnumerable>、 <xref:System.Collections.IDictionary>、泛型 <xref:System.Collections.Generic.IDictionary%602>，或是從這些介面衍生的介面) 也會被視為與實際集合型別具有相等的集合資料合約。 這樣一來，便可將要序列化的型別宣告成集合介面型別，而其結果相同於假設是使用實際的集合型別的結果。 例如，下列資料合約是相等的。  
  
 [!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
 [!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]  
  
 在進行序列化期間，當宣告的型別為介面時，使用的實際執行個體型別就可以是實作該介面的任何型別。 先前所討論的限制 (包含預設建構函式和 `Add` 方法) 並不適用。 例如，您可以將 Customer2 中的地址設定為地址之泛用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 的執行個體，即使無法直接宣告泛用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>型別的資料成員也是如此。  
  
 在進行還原序列化期間，如果宣告的型別為介面，序列化引擎便會選擇實作宣告之介面的型別，而且該型別會具現化。 在此，已知的型別機制 (在 [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)中有所描述) 不會有任何效果；型別的選項已建置於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="customizing-collection-types"></a>自訂集合型別  
 您可以使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性來自訂集合型別，此屬性有數種用法。  
  
 請注意，自訂集合類型會影響集合的可互換性，所以我們一般會建議您盡可能避免套用這個屬性。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 這個問題的詳細資訊，請參閱本主題稍後的＜進階集合規則＞一節。  
  
### <a name="collection-data-contract-naming"></a>集合資料合約命名  
 如 [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md)中所述，命名集合型別的規則與命名一般資料合約類型的規則相似，不過其中仍有某些重要差異：  
  
-   使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性來自訂名稱，而不是使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性。 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性 (Attribute) 也有 `Name` 和 `Namespace` 屬性 (Property)。  
  
-   在未套用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性時，集合型別的預設名稱和命名空間 (Namespace) 會取決於集合內所包含型別的名稱和命名空間。 它們都不會被集合型別本身的名稱和命名空間影響。 如需範例，請參閱下列型別。  
  
    ```  
    public CustomerList1 : Collection<string> {}  
    public StringList1 : Collection<string> {}  
    ```  
  
 這兩個型別的資料合約名稱都是 "ArrayOfstring"，而不是 "CustomerList1" 或 "StringList1"。 這表示在根層級序列化其中任何一個型別時，都會產生與下列程式碼相似的 XML。  
  
```xml  
<ArrayOfstring>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</ArrayOfstring>  
```  
  
 選擇這個命名規則的原因，在於要確保表示字串清單的任何非自訂型別都具有相同的資料合約與 XML 表示。 這樣集合便可進行互換。 在此範例中，CustomerList1 和 StringList1 完全可以互換。  
  
 不過，當套用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性 (Attribute) 時，集合會成為自訂的集合資料合約，即使未在此屬性上設定任何屬性 (Property) 也是如此。 這樣一來，集合資料合約的名稱與命名空間便會取決於集合型別本身。 如需範例，請參閱下列型別。  
  
 [!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
 [!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]  
  
 在經過序列化之後，會產生與下列相似的 XML。  
  
```xml  
<CustomerList2>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</CustomerList2>  
```  
  
 請注意，這種 XML 已經不再相同於非自訂化型別的 XML 表示。  
  
-   您可以使用 `Name` 和 `Namespace` 屬性來進一步自訂命名。 請參閱下列類別。  
  
     [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
     [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]  
  
 產生的 XML 與下列程式碼相似。  
  
```xml  
<cust_list>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</cust_list>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] 本主題稍後的「進階集合規則」一節。  
  
### <a name="customizing-the-repeating-element-name-in-list-collections"></a>自訂清單集合中的重複項目名稱  
 清單集合包含一些重複的項目。 通常，每個重複項目都會以項目表示，該項目會根據集合內所包含型別的資料合約名稱來命名。  
  
 在 `CustomerList` 範例中，集合包含的是字串。 資料合約名稱字串基本類型是 「 字串 」，因此重複的項目為"\<字串 >"。  
  
 不過，只要在 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> 屬性 (Attribute) 上使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性 (Property)，即可自訂這個重複項目。 如需範例，請參閱下列型別。  
  
 [!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
 [!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]  
  
 產生的 XML 與下列程式碼相似。  
  
```xml  
<CustomerList4>  
    <customer>...</customer>  
    <customer>...</customer>  
    <customer>...</customer>  
    ...  
</CustomerList4>  
```  
  
 重複項目的命名空間永遠都會與集合資料合約的命名空間相同，而就像先前所述，使用 `Namespace` 屬性便可自訂此命名空間。  
  
### <a name="customizing-dictionary-collections"></a>自訂字典集合  
 字典集合基本上就是項目清單，其中的每個項目都有後接一個值的索引鍵。 就像是在使用一般清單，您可以使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> 屬性來變更重複項目的對應項目名稱。  
  
 此外，您也可以使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> 和 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> 屬性來變更表示索引鍵與值的項目名稱。 這些項目的命名空間都與集合資料合約的命名空間相同。  
  
 如需範例，請參閱下列型別。  
  
 [!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
 [!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]  
  
 在經過序列化之後，會產生與下列相似的 XML。  
  
```xml  
<CountriesOrRegionsWithCapitals>  
    <entry>  
        <countryorregion>USA</countryorregion>  
        <capital>Washington</capital>  
    </entry>  
    <entry>  
        <countryorregion>France</countryorregion>  
        <capital>Paris</capital>  
    </entry>  
    ...  
</CountriesOrRegionsWithCapitals>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 字典集合的詳細資訊，請參閱本主題稍後的「進階集合規則」一節。  
  
## <a name="collections-and-known-types"></a>集合與已知型別  
 當使用多型方式，將集合取代其他集合或集合介面時，您並不需要將集合型別新增到已知型別中。 例如，如果您宣告 <xref:System.Collections.IEnumerable> 型別的資料成員，並使用該成員傳送 <xref:System.Collections.ArrayList>的執行個體，這時您並不需要將 <xref:System.Collections.ArrayList> 新增到已知型別。  
  
 當您以多型方式使用集合來取代非集合型別時，這些集合就必須加入至已知型別中。 例如，如果您宣告 `Object` 型別的資料成員，並使用該成員來傳送 <xref:System.Collections.ArrayList>的執行個體，請將 <xref:System.Collections.ArrayList> 加入至已知型別。  
  
 這時您無法以多型方式來序列化任何相等的集合。 例如，在上一個範例中，當您將 <xref:System.Collections.ArrayList> 加入至已知型別清單時，這樣無法讓您指派 `Array of Object` 類別，即使此類別具有相等的資料合約也是如此。 這點與非集合型別進行序列化時的一般已知型別行為並無不同，但是由於集合經常都是相等的，因此最好特別弄清楚這樣對集合而言的意義為何。  
  
 在序列化期間，任何資料合約的任何範圍中只能有一個已知的型別，而且相等的集合都會具有相同的資料合約。 這表示在先前的範例中，您不可以將 <xref:System.Collections.ArrayList> 和 `Array of Object` 同時加入至相同範圍中的已知型別。 同樣地，這個行為相同於非集合型別的已知型別行為，但是您要特別弄清楚這樣對於集合的意義為何。  
  
 集合的內容也可能需要已知型別。 例如，如果實際上 <xref:System.Collections.ArrayList> 是包含 `Type1` 與 `Type2`的執行個體，這兩個型別就應該要同時新增到已知型別。  
  
 下列範例會示範使用集合與已知型別而正確建構的物件圖形。 這個範例有點不自然，因為在實際的應用程式中，您通常不會將下列資料成員定義為 `Object`，並因此不會有任何已知型別/多型問題。  
  
 [!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
 [!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]  
  
 在進行還原序列化時，如果宣告的型別是集合型別，則無論實際傳送的型別為何，這個已宣告型別都會完成具現化。 如果宣告的型別是集合介面，還原序列化程式就會挑選要具現化的型別而不管已知型別為何。  
  
 另外，在還原序列化期間，如果宣告的型別不是集合型別，但是正在傳送的卻是某個集合型別，這時會從已知型別清單中挑選符合的集合型別。 您也可以在進行還原序列化時，將集合介面型別新增到已知型別的清單中。 同樣地，在此情況下，還原序列化引擎會挑選要具現化的型別。  
  
## <a name="collections-and-the-netdatacontractserializer-class"></a>集合與 NetDataContractSerializer 類別  
 當使用 <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別時，不是陣列的非自訂化集合型別 (不含 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性) 會失去其特殊意義。  
  
 已標示 <xref:System.SerializableAttribute> 屬性的非自訂化集合型別，依然可由 <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別根據 <xref:System.SerializableAttribute> 屬性或 <xref:System.Runtime.Serialization.ISerializable> 介面規則加以序列化。  
  
 即使此時是使用 <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別，自訂的集合型別、集合介面及陣列依然會被視為集合。  
  
## <a name="collections-and-schema"></a>集合與結構描述  
 所有相等的集合都具有相同的 XML 結構描述定義語言 (XSD) 結構描述表示方式。 基於這點，通常您由所產生用戶端程式碼所取得的集合型別，並不相同於伺服器上的集合型別。 例如，伺服器可能會搭配使用資料合約與整數資料成員的泛型 <xref:System.Collections.Generic.List%601> ，但是在產生的用戶端程式碼中，該相同資料成員可能會成為整數陣列。  
  
 字典集合都會以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]特定結構描述附註標示，以表示這些集合是字典。否則，將無法區別這些集合與包含有索引鍵與值之項目的簡單清單。 如需集合透過資料合約結構描述之表示方式的詳細描述，請參閱 [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)。  
  
 根據預設，不會針對已匯入程式碼中的非自訂集合產生型別。 清單集合型別的資料成員都會當做陣列匯入，而字典集合型別的資料成員會當做泛型字典匯入。  
  
 不過，對於自訂集合則會產生個別的型別，並標示 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性。 (採用結構描述的自訂集合型別，就是不使用預設命名空間、名稱、重複項目名稱或索引鍵/值項目名稱的型別)。這些型別是從清單型別的泛型 <xref:System.Collections.Generic.List%601> 或是字典型別的泛型字典所衍生的空型別。  
  
 例如，您在伺服器上可能擁有下列型別。  
  
 [!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
 [!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]  
  
 當匯出結構描述並再度將其匯入時，會產生與下列類似的用戶端程式碼 (此時顯示欄位而非屬性以提高可讀性)。  
  
 [!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
 [!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]  
  
 您可能希望使用所產生程式碼中的不同型別，而不要使用預設的型別。 例如，您可能希望對資料成員使用泛型 <xref:System.ComponentModel.BindingList%601> 而不要使用一般陣列，以便更輕鬆地將成員繫結至使用者介面元件。  
  
 若要選擇要產生的集合型別，請在匯入結構描述時，將您要使用的集合型別清單傳入 <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> 物件的 <xref:System.Runtime.Serialization.ImportOptions> 屬性。 這些型別稱為「 *參照集合型別*」(Referenced Collection Type)。  
  
 如果是要參考泛型型別，這些型別必須是完全開放式的泛型，或是完全封閉式的泛型。  
  
> [!NOTE]
>  當使用 Svcutil.exe 工具時，即可使用 **/collectionType** 命令列參數完成這項參考作業 (簡短形式： **/ct**)。 請記住，您必須同時使用 **/reference** 參數 (簡短形式： **/r**) 來指定參照集合型別的組件 (Assembly)。 如果該型別為泛型，後面就會接上反引號 (`) 與泛型參數的數目。 請勿混淆反引號 (`) 與單引號 (‘) 字元。 您可以多次使用 **/collectionType** 參數來指定多個參照集合型別。  
  
 例如，使所有清單都當做泛型 <xref:System.Collections.Generic.List%601>匯入。  
  
```  
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1  
```  
  
 匯入任何集合時，就會掃描這份參照集合型別清單，並且在找到一個型別時，將最符合的集合當做資料成員型別 (適用於非自訂集合) 來使用，或是當做要從其中衍生的基底型別 (Base Type) (適用於自訂集合)。 字典只會與字典比對，清單也只會與清單比對。  
  
 例如，如果您將泛型 <xref:System.ComponentModel.BindingList%601> 與 <xref:System.Collections.Hashtable> 新增到參考型別的清單，上述範例會產生與下列相似的用戶端程式碼。  
  
 [!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
 [!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]  
  
 您可以指定集合介面型別做為參照集合型別的一部分，不過您不能指定無效的集合型別 (例如沒有 `Add` 方法或公用建構函式的型別)。  
  
 封閉式泛型會被視為最符合的型別 (非泛型型別則會被視為相等於 `Object`的封閉式泛型)。 例如，如果 <xref:System.Collections.Generic.List%601> 的泛型 <xref:System.DateTime>、泛型 <xref:System.ComponentModel.BindingList%601> (開放式泛型) 和 <xref:System.Collections.ArrayList> 都是參照集合型別，便會產生下列結果。  
  
 [!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
 [!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]  
  
 若是清單集合，則只支援下表中的清況。  
  
|參考型別|由參考型別實作的介面|範例|型別的處理方式：|  
|---------------------|----------------------------------------------|-------------|----------------------|  
|非泛型或封閉式泛型 (任何參數數目)|非泛型|`MyType : IList`<br /><br /> 或<br /><br /> `MyType<T> : IList`<br /><br /> 其中 T= `int`|`Object` 的封閉式泛型 (例如， `IList<object>`)|  
|非泛型或封閉式泛型 (任何數目之不需要符合集合型別的參數)|封閉式泛型|`MyType : IList<string>`<br /><br /> 或<br /><br /> `MyType<T> : IList<string>` 其中 T=`int`|封閉式泛型 (例如， `IList<string>`)|  
|具有任何參數數目的封閉式泛型|使用型別之任何一個參數的開放式泛型|`MyType<T,U,V> : IList<U>`<br /><br /> 其中 T=`int`，U=`string`，V=`bool`|封閉式泛型 (例如， `IList<string>`)|  
|具有一個參數的開放式泛型|使用型別之參數的開放式泛型|`MyType<T> : IList<T>`，T 是開放式的|開放式泛型 (例如， `IList<T>`)|  
  
 如果型別實作一個以上的清單集合介面，則會套用下列限制：  
  
-   如果型別針對不同型別多次實作泛型 <xref:System.Collections.Generic.IEnumerable%601> (或其衍生的介面)，該型別就不會被視為有效的參照集合型別，並將遭到忽略。 即使其中一些實作為無效或是使用開放式泛型，也是如此。 例如，實作 <xref:System.Collections.Generic.IEnumerable%601> 之泛型 `int` 與 T 之泛型 <xref:System.Collections.Generic.IEnumerable%601> 的型別一律不會當做 `int` 或任何其他型別的參照集合使用，無論該型別是否具有接受 `Add` 的 `int` 方法，或是具有接受型別 T 參數的 `Add` 方法。  
  
-   如果型別實作泛型集合介面和 <xref:System.Collections.IList>，除非該泛型集合介面是型別 <xref:System.Object>的封閉式泛型，否則該型別永遠不會用來當做參照集合型別。  
  
 若是字典集合，則只支援下表中的清況。  
  
|參考型別|由參考型別實作的介面|範例|型別的處理方式|  
|---------------------|----------------------------------------------|-------------|---------------------|  
|非泛型或封閉式泛型 (任何參數數目)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> 或<br /><br /> `MyType<T> : IDictionary` 其中 T=`int`|封閉式泛型 `IDictionary<object,object>`|  
|封閉式泛型 (任何參數數目)|<xref:System.Collections.Generic.IDictionary%602>，封閉式|`MyType<T> : IDictionary<string, bool>`其中 T =`int`|封閉式泛型 (例如，`IDIctionary<string,bool>`)|  
|封閉式泛型 (任何參數數目)|泛型 <xref:System.Collections.Generic.IDictionary%602>，其中一個索引鍵或值屬封閉式，另一個則為開放式並使用型別的一個參數|`MyType<T,U,V> : IDictionary<string,V>`其中 T =`int`，U =`float`，V =`bool`<br /><br /> 或<br /><br /> `MyType<Z> : IDictionary<Z,bool>`其中 Z =`string`|封閉式泛型 (例如，`IDictionary<string,bool>`)|  
|封閉式泛型 (任何參數數目)|泛型 <xref:System.Collections.Generic.IDictionary%602>，索引鍵與值都屬開放式，而且每一個都會使用型別的一個參數|`MyType<T,U,V> : IDictionary<V,U>`，其中 T=`int`，U=`bool`，V=`string`|封閉式泛型 (例如，`IDictionary<string,bool>`)|  
|開放式泛型 (兩個參數)|泛型 <xref:System.Collections.Generic.IDictionary%602>，開放式，依照型別之泛型參數的出現順序來同時使用這兩個參數|`MyType<K,V> : IDictionary<K,V>`，K 與 V 都屬開放式|開放式泛型 (例如，`IDictionary<K,V>`)|  
  
 如果型別同時實作 <xref:System.Collections.IDictionary> 與泛型 <xref:System.Collections.Generic.IDictionary%602>，這時就只會考慮泛型 <xref:System.Collections.Generic.IDictionary%602> 。  
  
 不支援參考部分的泛型型別。  
  
 不允許重複。例如，您不能將 <xref:System.Collections.Generic.List%601> 的泛型 `Integer` 和 `Integer` 的泛型集合同時加入至 <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>，否則會造成當結構描述中出現整數清單時無法判斷要使用哪一個集合的問題。 只有當結構描述中有公開重複問題的型別時，才會偵測到重複。 例如，如果要匯入的結構描述不包含整數的清單，才能允許將 <xref:System.Collections.Generic.List%601> 的泛型 `Integer` 與 `Integer` 的泛型集合新增到 <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>，不過沒有一個會具有作用。  
  
## <a name="advanced-collection-rules"></a>進階集合規則  
  
### <a name="serializing-collections"></a>序列化集合  
 下面是序列化之集合規則的清單：  
  
-   允許結合集合型別 (即新增集合的集合)。 不規則陣列會被視為集合的集合。 不支援多維陣列。  
  
-   位元組的陣列與 <xref:System.Xml.XmlNode> 的陣列，都是會被視為基本型別 (而非集合) 的特殊陣列型別。 序列化位元組陣列時，會產生含有 Base64 編碼資料區塊的單一 XML 元素，而不是針對各個位元組產生個別元素。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 如何處理 <xref:System.Xml.XmlNode> 陣列的詳細資訊，請參閱 [XML and ADO.NET Types in Data Contracts](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). 當然，這些特殊型別本身可以參與集合：位元組陣列的陣列會產生多個 XML 項目，其中每個項目會包含 Base64 編碼資料的區塊。  
  
-   如果集合型別套用了 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性，該型別就會被視為一般資料合約類型，而不是集合。  
  
-   如果集合型別實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面，則會套用下列規則，並指型別為 `myType:IList<string>, IXmlSerializable`：  
  
    -   如果宣告的型別為 `IList<string>`，則型別會序列化為清單。  
  
    -   如果宣告的型別為 `myType`，它會序列化為 `IXmlSerializable`。  
  
    -   如果宣告的型別為 `IXmlSerializable`，則它會序列化為 `IXmlSerializable`，但只有在您將 `myType` 新增至已知型別的清單中才會這麼做。  
  
-   集合會透過下表中的方法來加以序列化與還原序列化。  
  
|實作的集合型別|進行序列化時呼叫的方法|進行還原序列化時呼叫的方法|  
|--------------------------------|-----------------------------------------|-------------------------------------------|  
|泛型 <xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|泛型 Add|  
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|  
|泛型 <xref:System.Collections.Generic.IList%601>|泛型 <xref:System.Collections.Generic.IList%601> 索引子|泛型 Add|  
|泛型 <xref:System.Collections.Generic.ICollection%601>|列舉值|泛型 Add|  
|<xref:System.Collections.IList>|<xref:System.Collections.IList> 索引子|`Add`|  
|泛型 <xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|稱為 `Add` 的非靜態方法，其會接受一個適當型別 (泛型參數型別或是它的一個基底型別) 的參數。 序列化程式必須配合這種方法，才能在進行序列化與還原序列化時將集合型別視為集合來處理。|  
|<xref:System.Collections.IEnumerable> (以及衍生自該項的 <xref:System.Collections.ICollection>)|`GetEnumerator`|稱為 `Add` 的非靜態方法，其會接受一個型別為 `Object`的參數。 序列化程式必須配合這種方法，才能在進行序列化與還原序列化時將集合型別視為集合來處理。|  
  
 上面表格是依遞減的優先順序來列出集合介面。 這表示，如果型別同時實作 <xref:System.Collections.IList> 與泛型 <xref:System.Collections.Generic.IEnumerable%601>，該集合便會根據 <xref:System.Collections.IList> 規則完成序列化與還原序列化：  
  
-   在進行還原序列化時，所有集合在進行還原序列化時，都會先透過呼叫預設建構函式來建立該型別的執行個體，而序列化程式一定要配合此預設建構函式，才能在進行序列化與還原序列化時將集合型別視為集合來處理。  
  
-   如果超過一次地實作相同的泛型集合介面 (例如，如果型別同時實作 <xref:System.Collections.Generic.ICollection%601> 的泛型 `Integer` 與 <xref:System.Collections.Generic.ICollection%601> 的泛型 <xref:System.String>)，而且找不到較高優先順序的介面，這時集合就無法被視為有效的集合。  
  
-   這些集合型別都可以將 <xref:System.SerializableAttribute> 屬性套用到本身，而且可以實作 <xref:System.Runtime.Serialization.ISerializable> 介面。 這兩者都會遭到忽略。 不過，如果型別沒有完全符合集合型別需求 (例如，遺失了 `Add` 方法)，該型別就不會被視為集合型別，而且這樣一來， <xref:System.SerializableAttribute> 屬性與 <xref:System.Runtime.Serialization.ISerializable> 介面就會用來判斷型別是否可序列化。  
  
-   將 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性套用至集合以自訂集合時，會移除上述的 <xref:System.SerializableAttribute> 後援機制。 相反地，如果自訂的集合未能符合集合型別需求，便會擲回 <xref:System.Runtime.Serialization.InvalidDataContractException> 例外狀況 (Exception)。 例外狀況字串通常會包含資訊，說明指定型別為何未被視為有效的集合 (沒有 `Add` 方法、沒有預設建構函式，以及其他原因)，因此通常為偵錯目的而套用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性的做法會很有用。  
  
### <a name="collection-naming"></a>集合命名  
 下面是集合命名規則的清單：  
  
-   除非已使用 Namespace 覆寫，否則所有字典集合資料合約以及包含基本型別之清單集合資料合約的預設命名空間，都會是 http://schemas.microsoft.com/2003/10/Serialization/Arrays。 對應至內建 XSD 型別，以及 `char`、 `Timespan`與 `Guid` 型別的型別，都會因此目的而被視為基本型別。  
  
-   除非已使用 Namespace 覆寫，否則包含非基本型別之集合型別的預設命名空間，就是集合中所包含之型別的資料合約命名空間。  
  
-   除非已使用 Name 覆寫，否則清單集合資料合約的預設名稱，就會是 "ArrayOf" 字串與集合中所包含型別之資料合約名稱的組合。 例如，整數泛型清單的資料合約名稱是 "ArrayOfint"。 請記住， `Object` 的資料合約名稱是 "anyType"，因此非泛型清單 (例如， <xref:System.Collections.ArrayList> ) 的資料合約名稱會是 "ArrayOfanyType"。  
  
 除非已使用 `Name`覆寫，否則字典集合資料合約的預設名稱，就會是 "ArrayOfKeyValueOf" 字串與索引鍵型別之資料合約名稱加上值型別之資料合約名稱的組合。 例如，字串與整數之泛型字典的資料合約名稱為 "ArrayOfKeyValueOfstringint"。 此外，如果索引鍵或值型別其中一個不是基本型別，便會在名稱後附加索引鍵與值型別之資料合約命名空間的命名空間雜湊。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 命名空間雜湊的詳細資訊，請參閱 [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 每個字典集合資料合約都具有表示字典中一個項目的附屬資料合約。 除了 "ArrayOf" 的前置詞以外，該合約的名稱與字典資料合約的名稱相同，而且其命名空間也與字典資料合約相同。 例如，對於 "ArrayOfKeyValueOfstringint" 字典資料合約，"KeyValueofstringint" 資料合約表示字典中的一個項目。 您可以使用 `ItemName` 屬性來自訂這個資料合約的名稱，如下節所示。  
  
 如 [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md)中所述，泛型型別命名規則會完全套用到集合型別，也就是說，您可以在名稱內使用大括號來表示泛型型別參數。 不過，在大括號內的數字是指泛型參數數目，而非集合內所包含型別的數目。  
  
## <a name="collection-customization"></a>集合自訂化  
 禁止以下列方式使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性，否則會造成 <xref:System.Runtime.Serialization.InvalidDataContractException> 例外狀況：  
  
-   將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至已套用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性的型別，或是套用至它的一個衍生型別。  
  
-   將 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性套用至實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面的型別。  
  
-   將 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性套用至非集合型別。  
  
-   嘗試在已套用至非字典型別的 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> 屬性上設定 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> 或 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 。  
  
### <a name="polymorphism-rules"></a>多型規則  
 正如先前所述，使用 <xref:System.Runtime.Serialization.CollectionDataContractAttribute> 屬性來自訂集合可能會干擾集合的可互換性。 唯有兩個自訂集合型別的名稱、命名空間、項目名稱，以及索引鍵與值名稱 (如果是字典集合) 彼此相符時，這兩個集合型别才能被視為相等。  
  
 由於自訂化的關係，有可能會發生應該使用某個集合資料合約，但卻不慎使用另一個集合資料合約的情形。 對此應該要設法避免。 請參閱下列型別。  
  
 [!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
 [!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]  
  
 在此範例中， `Marks1` 的執行個體可以指派到 `testMarks`。 但是，不應使用 `Marks2` ，因為其資料合約不被視為相等於 `IList<int>` 資料合約。 資料合約名稱是"Marks2"而非"ArrayOfint，"，重複的項目名稱"\<標記 >"而非"\<int > 」。  
  
 下表中的規則適用於集合的多型指派。  
  
|宣告的型別|指派非自訂的集合|指派自訂的集合|  
|-------------------|--------------------------------------------|---------------------------------------|  
|Object|合約名稱已經序列化。|合約名稱已經序列化。<br /><br /> 已使用自訂。|  
|集合介面|合約名稱未序列化。|合約名稱未序列化。<br /><br /> 未使用自訂。*|  
|非自訂的集合|合約名稱未序列化。|合約名稱已經序列化。<br /><br /> 已使用自訂。**|  
|自訂的集合|合約名稱已經序列化。 未使用自訂。**|合約名稱已經序列化。<br /><br /> 已使用所指派型別的自訂。**|  
  
 *在此情況下是透過 <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別來使用自訂。 在此情況下， <xref:System.Runtime.Serialization.NetDataContractSerializer> 類別也會序列化實際的型別名稱，以便讓還原序列化如預期地運作。  
  
 **這些情況會產生結構描述無效的執行個體，因此應該盡量避免。  
  
 在合約名稱已經序列化的情況下，所指派的集合型別應該會在已知型別的清單中。 反之亦然：因為在名稱未經序列化的情況下，並不需要將型別加入至已知型別清單中。  
  
 衍生型別的陣列可以指派給基底型別的陣列。 在此情況下，衍生型別的合約名稱會針對每個重複項目加以序列化。 例如，如果型別 `Book` 是衍生自型別 `LibraryItem`，您就可以將 `Book` 的陣列指派到 `LibraryItem`的陣列。 這點並不適用於其他集合型別。 例如，您無法將 `Generic List of Book` 指派到 `Generic List of LibraryItem`。 不過，您可以指派包含 `Generic List of LibraryItem` 執行個體的 `Book` 。 在陣列與非陣列的兩種情況下， `Book` 都應該會在已知型別清單中。  
  
## <a name="collections-and-object-reference-preservation"></a>集合與物件參考保留  
 當序列化程式在保留物件參考的模式下運作時，物件參考保留也會套用到集合。 具體來說，就是整個集合與集合中所包含的個別項目都會保留其物件身分識別。 若是字典，則會針對索引鍵/值組物件以及個別的索引鍵和值物件保留物件身分識別。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
