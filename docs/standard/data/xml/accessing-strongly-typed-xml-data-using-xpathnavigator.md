---
title: "使用 XPathNavigator 存取強型別 XML 資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 651a8e11b5782227cdf5ffcc3d53cf2c75def031
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>使用 XPathNavigator 存取強型別 XML 資料
做為 XPath 2.0 資料模型的執行個體，<xref:System.Xml.XPath.XPathNavigator> 類別可以包含對應至 Common Language Runtime (CLR) 型別的強型別資料。 根據 XPath 2.0 資料模型，只有項目及屬性才可以包含強型別資料。 <xref:System.Xml.XPath.XPathNavigator> 類別提供可將 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件內的資料做為強型別資料進行存取的機制，以及將一種資料型別轉換為另一種型別的機制。  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>XPathNavigator 公開的型別資訊  
 就技術而言，XML 1.0 資料沒有型別，除非它是透過 DTD、XML 結構描述定義語言 (XSD) 結構描述或其他機制予以處理。 某些類別的型別資訊，可以與 XML 項目或屬性相關聯。  
  
-   簡單 CLR 型別：任何 XML 結構描述語言都無法直接支援 Common Language Runtime (CLR) 型別。 由於將簡單項目及屬性內容視為最適當的 CLR 型別很有用，因此在沒有結構描述資訊的情況下，所有的簡單內容都可以具有 <xref:System.String> 型別，並且任何加入的結構描述資訊都可能會將這個內容調整為更適當的型別。 您可以利用 <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> 屬性，找到與簡單項目及屬性內容最相符的 CLR 型別。 如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。  
  
-   簡單 (CLR) 型別清單：具有簡單內容的項目或屬性可包含以空白字元分隔的值清單。 這些值是透過 XML 結構描述指定為「清單型別」。 如果沒有 XML 結構描述，則會將此類簡單內容視為單一文字節點。 當有 XML 結構描述可用時，這個簡單內容可公開為一系列原子值，並且每個值都有對應至 CLR 物件集合的簡單型別。 如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。  
  
-   具型別值：具有簡單型別之已驗證結構描述的屬性或項目都會擁有具型別值。 這個值為基本型別，如數字、字串或日期型別。 XSD 中的所有內建簡單型別都可以對應至 CLR 型別，因為 CLR 型別可做為更適合提供節點值之存取權的型別，而不是只做為 <xref:System.String>。 具有屬性或項目子系的項目會視為複雜型別。 具有簡單內容之複雜型別的具型別值 (做為子系的唯一文字節點)，與其內容之簡單型別的具型別值相同。 具有複雜內容之複雜型別的具型別值 (一或多個項目子系)，是以 <xref:System.String> 型式傳回之所有子文字節點串連的字串值。 如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。  
  
-   結構描述語言特定的型別名稱：在大多數情況中，設為套用外部結構描述之副作用的 CLR 型別，都會用來提供節點值的存取權。 然而，有時您也可能想要檢查與套用至 XML 文件之特定結構描述相關聯的型別。 例如，您可能想要搜尋 XML 文件，擷取根據附加的結構描述判定其具有型別內容 PurchaseOrder 的所有項目。 這類資訊只會因結構描述驗證而加以設定，並且此資訊是透過 <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 屬性來進行存取。 如需詳細資訊，請參閱下面的＜後結構描述驗證資訊集 (PSVI)＞一節。  
  
-   結構描述語言特定的型別反映：在其他情況下，您可能要取得套用至 XML 文件之結構描述特定型別更詳細的資料。 例如，在讀取 XML 檔案時，可能要擷取 XML 文件中每個有效節點的 `maxOccurs` 屬性，以執行部份自訂計算。 因為此資訊只會透過結構描述驗證來予以設定，所以它會透過 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 屬性來進行存取。 如需詳細資訊，請參閱下面的＜後結構描述驗證資訊集 (PSVI)＞一節。  
  
## <a name="xpathnavigator-typed-accessors"></a>XPathNavigator 具型別存取子  
 下表顯示可用於存取節點相關型別資訊之 <xref:System.Xml.XPath.XPathNavigator> 類別的各種屬性及方法。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|包含有效節點的 XML 結構描述型別資訊。|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|包含驗證後加入之節點的後結構描述驗證資訊集。 包含 XML 結構描述型別資訊，以及有效性資訊。|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|節點之具型別值的 CLR 型別。|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|其型別最符合節點之 XML 結構描述型別的一或多個 CLR 值的節點內容。|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.Boolean> 值之目前節點的 `xs:boolean` 值。|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.DateTime> 值之目前節點的 `xs:datetime` 值。|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.Double> 值之目前節點的 `xsd:double` 值。|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.Int32> 值之目前節點的 `xs:integer` 值。|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|根據 <xref:System.String> 的 XPath 2.0 轉換規則，轉換為 <xref:System.Int64> 值之目前節點的 `xs:integer` 值。|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|根據 XPath 2.0 轉換規則，轉換為目標型別之節點的內容。|  
  
 如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>後結構描述驗證資訊集 (PSVI)  
 XML 結構描述處理器接受使用 XML 資訊集做為輸入，並將其轉換為後結構描述驗證資訊集 (PSVI)。 PSVI 為原始輸入 XML 資訊集，內含在現有資訊項目中加入新的資訊項目及新屬性。 有三大資訊類別會加入至 PSVI 中的 XML 資訊集，並且這些資訊是由 <xref:System.Xml.XPath.XPathNavigator> 公開。  
  
1.  驗證結果：是否已成功驗證項目或屬性的相關資訊。 由 <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> 類別之 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 屬性的 <xref:System.Xml.XPath.XPathNavigator> 屬性公開。  
  
2.  預設資訊：是否已透過結構描述中指定的預設值，取得項目或屬性值的相關指示。 由 <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> 類別之 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 屬性的 <xref:System.Xml.XPath.XPathNavigator> 屬性公開。  
  
3.  型別附註：可能是型別定義或項目及屬性宣告之結構描述元件的參考。 <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 的 <xref:System.Xml.XPath.XPathNavigator> 屬性包含有效節點的特定型別資訊。 如果節點的有效性是未知的 (例如在完成驗證後，又進行了編輯時)， 則 <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 屬性會設為 `null`，但仍可從 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 類別之 <xref:System.Xml.XPath.XPathNavigator> 屬性中的各種屬性取得型別資訊。  
  
 下列範例會說明如何使用 <xref:System.Xml.XPath.XPathNavigator> 所公開之後結構描述驗證資訊集中的資訊。  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 該範例採用 `books.xml` 檔案做為輸入。  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 該範例也會採用 `books.xsd` 結構描述做為輸入。  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"   
attributeFormDefault="unqualified" elementFormDefault="qualified"   
targetNamespace="http://www.contoso.com/books"   
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a>使用 ValueAs 屬性取得具型別值  
 節點的具型別值可藉由存取 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 的 <xref:System.Xml.XPath.XPathNavigator> 屬性來擷取。 在某些情況下，您可能要將節點的具型別值轉換為不同的型別。 常見的範例是從 XML 節點取得數值。 例如，請考量下列未經驗證且不具型別的 XML 文件。  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 如果 <xref:System.Xml.XPath.XPathNavigator> 定位於 `price` 項目中，則 <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> 屬性為 `null`，<xref:System.Xml.XPath.XPathNavigator.ValueType%2A> 屬性為 <xref:System.String>，以及 <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> 屬性為字串 `10.00`。  
  
 然而，仍有可能使用 <xref:System.Xml.XPath.XPathItem.ValueAs%2A>、<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>、<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> 或 <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> 方法及屬性，將該值擷取為數值。 下列範例說明如何使用 <xref:System.Xml.XPath.XPathItem.ValueAs%2A> 方法來執行此類轉換。  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 如需從結構描述內建型別對應至 CLR 型別的詳細資訊，請參閱 [System.Xml 類別中的型別支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [System.Xml 類別中的類型支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [使用 XPathNavigator 導覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [使用 XPathNavigator 導覽屬性和命名空間節點](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [使用 XPathNavigator 擷取 XML 資料](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
