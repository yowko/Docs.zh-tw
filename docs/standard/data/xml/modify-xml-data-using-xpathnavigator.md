---
title: 使用 XPathNavigator 修改 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb31c2ea504472a8707d700ff84b8c367467b607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="modify-xml-data-using-xpathnavigator"></a>使用 XPathNavigator 修改 XML 資料
<xref:System.Xml.XPath.XPathNavigator> 類別提供一組可用於修改 XML 文件中節點及值的方法。 為了使用這些方法，<xref:System.Xml.XPath.XPathNavigator> 物件必須是可編輯的，也就是說，它的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性必須為 `true`。  
  
 可編輯 XML 文件的 <xref:System.Xml.XPath.XPathNavigator> 物件是由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 類別的 <xref:System.Xml.XmlDocument> 方法所建立。 由 <xref:System.Xml.XPath.XPathNavigator> 類別建立的 <xref:System.Xml.XPath.XPathDocument> 物件是唯讀的，而且如果嘗試使用由 <xref:System.Xml.XPath.XPathNavigator> 物件建立之 <xref:System.Xml.XPath.XPathDocument> 物件的編輯方法，則會導致 <xref:System.NotSupportedException>。  
  
 如需有關建立可編輯 <xref:System.Xml.XPath.XPathNavigator> 物件的詳細資訊，請參閱[使用 XPathDocument 和 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)。  
  
## <a name="modifying-nodes"></a>修改節點  
 一種變更節點值的簡單技術是使用 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 方法。  
  
 下表列出了這些方法對不同節點型別的影響。  
  
|<xref:System.Xml.XPath.XPathNodeType>|資料變更|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|不支援。|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|項目的內容。|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|屬性的值。|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|文字內容。|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|內容 (目標除外)。|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|註解的內容。|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|不支援。|  
  
> [!NOTE]
>  不支援編輯 <xref:System.Xml.XPath.XPathNodeType.Namespace> 節點或 <xref:System.Xml.XPath.XPathNodeType.Root> 節點。  
  
 <xref:System.Xml.XPath.XPathNavigator> 類別還提供一組可用於插入及移除節點的方法。 如需有關從n XML 文件插入和移除節點的詳細資訊，請參閱[使用 XPathNavigator 插入 XML 資料](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)和[使用 XPathNavigator 移除 XML 資料](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)主題。  
  
### <a name="modifying-untyped-values"></a>修改不具型別值  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只會插入做為參數傳遞的不具型別 `string` 值，並將其做為 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的值。 插入的值不具有任何型別，或未根據節點型別 (若提供結構描述資訊) 驗證新值的有效性。  
  
 在下列範例中，<xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法用於更新 `price` 檔案中的所有 `contosoBooks.xml` 項目。  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>修改具型別值  
 當節點的型別為 W3C XML 結構描述簡單型別時，會根據簡單型別的 Facet，對 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法插入的新值執行設定前的檢查。 如果根據節點的型別，新值無效 (例如，在型別為 `-1` 的項目上設定 `xs:positiveInteger` 值)，則會導致例外狀況。  
  
 下列範例會嘗試將 `price` 檔案中第一個 `book` 項目之 `contosoBooks.xml` 項目的值，變更為 <xref:System.DateTime> 值。 因為在 `price` 檔案中將 `xs:decimal` 項目的 XML 結構描述型別定義為 `contosoBooks.xsd`，所以這個動作會擲回例外狀況。  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 該範例還採用 `contosoBooks.xsd` 做為輸入。  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>編輯強型別 XML 資料的影響  
 <xref:System.Xml.XPath.XPathNavigator> 類別使用 W3C XML 結構描述，做為說明強型別 XML 的基礎。 根據對 W3C XML 結構描述文件的驗證，可為項目及屬性加上型別資訊標註。 可包含其他項目或屬性的項目稱為複雜型別，而那些僅包含文字內容的則稱為簡單型別。  
  
> [!NOTE]
>  屬性僅可具有簡單型別。  
  
 如果項目或屬性符合其型別定義的所有特定規則，則認為是結構描述有效。 具有簡單型別 `xs:int` 的項目必須包含 -2147483648 與 2147483647 之間的數值，才為結構描述有效。 對於複雜型別，項目的結構描述有效性取決於其項目子系及屬性的結構描述有效性。 因此，如果項目對其複雜型別定義有效，則其所有項目子系及屬性對其型別定義都有效。 同樣地，如果項目中有一個項目子系或屬性對其型別定義無效或有效性不明，則該項目也會無效或具有不明有效性。  
  
 如果項目的有效性取決於其項目子系及屬性的有效性，則修改任何一項都會導致變更項目的有效性 (如果先前已為有效)。 特別是當插入、更新或刪除項目的項目子系或屬性時，項目的有效性會變為不明。 此由項目 <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> 屬性的 <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> 屬性設為 <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown> 來表示。 而且，此影響還會按階層向上遞迴處理整個 XML 文件，因為項目的父項目 (及其父項目等) 有效性也會變為不明。  
  
 如需結構描述驗證及 <xref:System.Xml.XPath.XPathNavigator> 類別的詳細資訊，請參閱[使用 XPathNavigator 進行結構描述驗證](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)。  
  
### <a name="modifying-attributes"></a>修改屬性  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法可用於修改不具型別與具型別屬性節點，以及＜修改節點＞一節中列出的其他節點型別。  
  
 下列範例會變更 `genre` 檔案中第一個 `book` 項目的 `books.xml` 屬性值。  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 如需 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法的詳細資訊，請參閱＜修改不具型別值＞與＜修改具型別值＞這兩節。  
  
## <a name="innerxml-and-outerxml-properties"></a>InnerXml 及 OuterXml 屬性  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的 XML 標記。  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及指定 XML `string` 的已剖析內容。 同樣地，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及目前節點本身。  
  
 下列範例使用 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性來修改 `price` 項目的值，並在 `discount` 檔案中的第一個 `book` 項目上插入新的 `contosoBooks.xml` 屬性。  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>修改命名空間節點  
 在文件物件模型 (DOM) 中，可將命名空間宣告視為可插入、更新及刪除的一般屬性來處理。 <xref:System.Xml.XPath.XPathNavigator> 類別不允許對命名空間節點執行此類作業，原因是變更命名空間節點的值可能會變更命名空間節點範圍內項目及屬性的識別，如下列範例所示。  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 如果上述 XML 範例變更為下列方式，那麼由於變更了每個項目的命名空間 URI 值，所以會有效地重新命名文件中的每個項目。  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <xref:System.Xml.XPath.XPathNavigator> 類別允許插入命名空間節點，但這些命名空間節點不可與其插入所在範圍的命名空間宣告衝突。 此情況下的命名空間宣告並不是在 XML 文件中的較低範圍處宣告的，因此不會導致重新命名，如下列範例所示。  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 如果上述 XML 範例變更為下列方式，則命名空間宣告便可在 XML 文件中其他命名空間宣告範圍的下面正確傳播。  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 在上述 XML 範例中，屬性 `a:parent-id` 是插入在 `parent` 命名空間中的 `http://www.contoso.com/parent-id` 項目上。 <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 方法用於在定位於 `parent` 項目上時插入屬性。 `http://www.contoso.com` 類別會自動插入 <xref:System.Xml.XPath.XPathNavigator> 命名空間宣告，以保持 XML 文件其餘內容的一致性。  
  
## <a name="modifying-entity-reference-nodes"></a>修改實體參考節點  
 <xref:System.Xml.XmlDocument> 物件中的實體參考節點是唯讀的，無法使用 <xref:System.Xml.XPath.XPathNavigator> 或 <xref:System.Xml.XmlNode> 類別進行編輯。 任何修改實體參考節點的嘗試都會導致擲回 <xref:System.InvalidOperationException>。  
  
## <a name="modifying-xsinil-nodes"></a>修改 xsi:nil 節點  
 W3C XML 結構描述建議事項中引進了 Nillable 項目的概念。 當項目為 Nillable 時，有可能項目沒有內容但也有效。 Nillable 項目的概念與 `null` 物件的概念類似。 主要區別在於任何方式都無法存取 `null` 物件，而 `xsi:nil` 項目仍具有可存取的屬性 (Property)，如屬性 (Attribute)，但沒有內容 (項目子系或文字)。 如果 XML 文件中有某個項目的 `xsi:nil` 屬性值為 `true`，則表示該項目沒有內容。  
  
 如果使用 <xref:System.Xml.XPath.XPathNavigator> 物件將內容加入至 `xsi:nil` 屬性值為 `true` 的有效項目，則會將其 `xsi:nil` 屬性值設為 `false`。  
  
> [!NOTE]
>  對於 `xsi:nil` 屬性設為 `false` 的項目，即使刪除其內容，該屬性的值也不會變更為 `true`。  
  
## <a name="saving-an-xml-document"></a>儲存 XML 文件  
 儲存對 <xref:System.Xml.XmlDocument> 物件所進行的變更 (由本主題中說明的編輯方法所導致) 是使用 <xref:System.Xml.XmlDocument> 類別的方法來執行。 如需儲存 <xref:System.Xml.XmlDocument> 物件之變更的詳細資訊，請參閱[儲存與寫入文件](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [使用 XPathNavigator 插入 XML 資料](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 [使用 XPathNavigator 移除 XML 資料](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
