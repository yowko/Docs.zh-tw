---
title: 使用 XPathNavigator 插入 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b9eedfab68dc6aeacf9ed51ffc7205b73c062ca
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2018
ms.locfileid: "45698334"
---
# <a name="insert-xml-data-using-xpathnavigator"></a>使用 XPathNavigator 插入 XML 資料
<xref:System.Xml.XPath.XPathNavigator> 類別提供一組方式，可在 XML 文件中插入同層級節點、子節點及屬性節點。 為了使用這些方法，<xref:System.Xml.XPath.XPathNavigator> 物件必須是可編輯的，也就是說，它的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性必須為 `true`。  
  
 可編輯 XML 文件的 <xref:System.Xml.XPath.XPathNavigator> 物件是由 <xref:System.Xml.XmlDocument.CreateNavigator%2A> 類別的 <xref:System.Xml.XmlDocument> 方法所建立。 由 <xref:System.Xml.XPath.XPathNavigator> 類別建立的 <xref:System.Xml.XPath.XPathDocument> 物件是唯讀的，而且如果嘗試使用由 <xref:System.Xml.XPath.XPathNavigator> 物件建立之 <xref:System.Xml.XPath.XPathDocument> 物件的編輯方法，則會導致 <xref:System.NotSupportedException>。  
  
 如需有關建立可編輯 <xref:System.Xml.XPath.XPathNavigator> 物件的詳細資訊，請參閱[使用 XPathDocument 和 XmlDocument 讀取 XML 資料](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)。  
  
## <a name="inserting-nodes"></a>插入節點  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供在 XML 文件中，插入同層級節點、子節點及屬性節點的方法。 下列各節中所說明的方法，可讓您將節點及屬性插入與 <xref:System.Xml.XPath.XPathNavigator> 物件之目前位置不同的位置。  
  
### <a name="inserting-sibling-nodes"></a>插入同層級節點  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供下列方法來插入同層級節點。  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 這些方法可在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在的節點前後，插入同層級節點。  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 及 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> 方法會多載，且接受 `string`、<xref:System.Xml.XmlReader> 物件或包含同層級節點的 <xref:System.Xml.XPath.XPathNavigator> 物件，以加入為參數。 這兩種方法還會傳回用於插入同層級節點的 <xref:System.Xml.XmlWriter> 物件。  
  
 <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> 及 <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> 方法會使用指定為參數的命名空間前置詞、區域名稱、命名空間 URI 及值，在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在的節點前後，插入單一的同層級節點。  
  
 在下列範例中，會在 `pages` 檔案之第一個 `price` 項目的 `book` 項目子系之前，插入新的 `contosoBooks.xml` 項目。  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 如需 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> 及 <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.XPath.XPathNavigator> 類別參考文件。  
  
### <a name="inserting-child-nodes"></a>插入子節點  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供下列方法來插入子節點。  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 這些方法會將子節點附加到 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的子節點清單結尾及開頭。  
  
 與＜插入同層級節點＞一節中的方法一樣，<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 及 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 方法也接受 `string`、<xref:System.Xml.XmlReader> 物件或包含子節點的 <xref:System.Xml.XPath.XPathNavigator> 物件，以加入為參數。 這兩種方法還會傳回用於插入子節點的 <xref:System.Xml.XmlWriter> 物件。  
  
 與＜插入同層級節點＞一節中的方法一樣，<xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> 及 <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> 方法也會使用指定為參數的命名空間前置詞、區域名稱、命名空間 URI 及值，在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的子節點清單結尾及開頭，插入單一子節點。  
  
 在下列範例中，會將新的 `pages` 項目子系附加至 `book` 檔案中第一個 `contosoBooks.xml` 項目的項目子系清單。  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 如需 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> 及 <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.XPath.XPathNavigator> 類別參考文件。  
  
### <a name="inserting-attribute-nodes"></a>插入屬性節點  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供下列方法來插入屬性節點。  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 這些方法可在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在的項目節點上，插入屬性節點。 <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 方法使用指定為參數的命名空間前置詞、區域名稱、命名空間 URI 及值，在 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在的項目節點上，建立屬性節點。 <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 方法會傳回用於插入屬性節點的 <xref:System.Xml.XmlWriter> 物件。  
  
 在下列範例中，會使用從 `discount` 方法傳回的 `currency` 物件，在 `price` 檔案中第一個 `book` 項目的 `contosoBooks.xml` 項目子系上，建立新的 <xref:System.Xml.XmlWriter> 及 <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 屬性。  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 如需 <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> 及 <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 方法的詳細資訊，請參閱 <xref:System.Xml.XPath.XPathNavigator> 類別參考文件。  
  
## <a name="copying-nodes"></a>複製節點  
 在某些情況下，您可能要使用其他 XML 文件的內容，填入 XML 文件。 <xref:System.Xml.XPath.XPathNavigator> 類別及 <xref:System.Xml.XmlWriter> 類別可以從現有的 <xref:System.Xml.XmlDocument> 物件或 <xref:System.Xml.XmlReader> 物件，將節點複製到 <xref:System.Xml.XPath.XPathNavigator> 物件。  
  
 <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 方法都包含多載，它們可以接受 <xref:System.Xml.XPath.XPathNavigator> 物件或 <xref:System.Xml.XmlReader> 物件做為參數。  
  
 <xref:System.Xml.XmlWriter.WriteNode%2A> 類別的 <xref:System.Xml.XmlWriter> 方法包含可接受 <xref:System.Xml.XmlNode>、<xref:System.Xml.XmlReader> 或 <xref:System.Xml.XPath.XPathNavigator> 物件的多載。  
  
 下列範例會將所有 `book` 項目，從一個文件複製到另一個文件。  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a>插入值  
 <xref:System.Xml.XPath.XPathNavigator> 類別提供 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 及 <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 方法，以便在 <xref:System.Xml.XmlDocument> 物件中插入節點的值。  
  
### <a name="inserting-untyped-values"></a>插入不具型別值  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法只會插入做為參數傳遞的不具型別 `string` 值，並將其做為 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的值。 插入的值不具有任何型別，或未根據節點型別 (若提供結構描述資訊) 驗證新值的有效性。  
  
 在下列範例中，<xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 方法用於更新 `price` 檔案中的所有 `contosoBooks.xml` 項目。  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 範例將 `contosoBooks.xml` 檔案做為輸入。  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a>插入具型別值  
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
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml 及 OuterXml 屬性  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之節點的 XML 標記。  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及指定 XML `string` 的已剖析內容。 同樣地，<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性會變更 <xref:System.Xml.XPath.XPathNavigator> 物件目前所在之子節點的 XML 標記，以及目前節點本身。  
  
 除了本主題中所說明的方法之外，還可以使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性，將節點及值插入 XML 文件。 如需使用 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> 及 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> 屬性插入節點和值的詳細資訊，請參閱[使用 XPathNavigator 修改 XML 資料](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)主題。  
  
## <a name="namespace-and-xmllang-conflicts"></a>命名空間及 xml:lang 衝突  
 當使用 `xml:lang` 類別的 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> 及 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 方法 (其採用 <xref:System.Xml.XPath.XPathNavigator> 物件做為參數) 來插入 XML 資料時，可能會發生某些與命名空間的範圍及 <xref:System.Xml.XmlReader> 宣告相關的衝突。  
  
 下列是可能的命名空間衝突。  
  
-   如果 <xref:System.Xml.XmlReader> 物件的內容中包含範圍中的命名空間，其中命名空間 URI 對應的前置詞不在 <xref:System.Xml.XPath.XPathNavigator> 物件的內容中，則會將新命名空間宣告加入至新插入的節點。  
  
-   如果相同的命名空間 URI 在 <xref:System.Xml.XmlReader> 物件的內容及 <xref:System.Xml.XPath.XPathNavigator> 物件內容中都在範圍內，但它們在這兩個內容中擁有不同的對應前置詞，則會將新的命名空間宣告加入至新插入的節點，並從 <xref:System.Xml.XmlReader> 物件取得前置詞及命名空間 URI。  
  
-   如果相同的命名空間前置詞在 <xref:System.Xml.XmlReader> 物件的內容及 <xref:System.Xml.XPath.XPathNavigator> 物件的內容中都在範圍內，但在這兩個內容中擁有不同的對應命名空間 URI，則會將新的命名空間宣告加入至新插入的節點，該節點會以從 <xref:System.Xml.XmlReader> 物件取得之命名空間 URI 來重新宣告該前置詞。  
  
-   如果 <xref:System.Xml.XmlReader> 物件內容及 <xref:System.Xml.XPath.XPathNavigator> 物件內容中的前置詞及命名空間 URI 相同，則不會將新的命名空間宣告加入至新插入的節點。  
  
> [!NOTE]
>  上述說明還適用於將空白 `string` 做為前置詞的命名空間宣告 (例如，預設命名空間宣告)。  
  
 下列是可能的 `xml:lang` 衝突。  
  
-   如果在 `xml:lang` 物件的內容中包含範圍中的 <xref:System.Xml.XmlReader> 屬性，但 <xref:System.Xml.XPath.XPathNavigator> 物件的內容中沒有，則會將從 `xml:lang` 物件取得值的 <xref:System.Xml.XmlReader> 屬性加入至新插入的節點。  
  
-   如果 `xml:lang` 物件的內容及 <xref:System.Xml.XmlReader> 物件的內容都包含範圍中的 <xref:System.Xml.XPath.XPathNavigator> 屬性，但是屬性的值不同，則會將從 `xml:lang` 物件取得值的 <xref:System.Xml.XmlReader> 屬性加入至新插入的節點。  
  
-   如果 `xml:lang` 物件的內容及 <xref:System.Xml.XmlReader> 物件的內容都包含範圍中的 <xref:System.Xml.XPath.XPathNavigator> 屬性，但是屬性的值相同，則不會將新的 `xml:lang` 屬性加入新插入的節點。  
  
-   如果 `xml:lang` 物件的內容包含範圍中的 <xref:System.Xml.XPath.XPathNavigator> 屬性，但是在 <xref:System.Xml.XmlReader> 物件的內容中沒有，則不會將 `xml:lang` 屬性加入至新插入的節點。  
  
## <a name="inserting-nodes-with-xmlwriter"></a>使用 XmlWriter 插入節點  
 多載＜插入節點及值＞一節中說明之用於插入同層級節點、子節點及屬性節點的方法。 <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 及 <xref:System.Xml.XPath.XPathNavigator> 方法會傳回用於插入節點的 <xref:System.Xml.XmlWriter> 物件。  
  
### <a name="unsupported-xmlwriter-methods"></a>不支援的 XmlWriter 方法  
 由於 XPath 資料模型與文件物件模型 (DOM) 之間的差異，<xref:System.Xml.XmlWriter> 類別並不支援所有使用 <xref:System.Xml.XPath.XPathNavigator> 類別將資訊寫入 XML 文件的方法。  
  
 下表說明 <xref:System.Xml.XmlWriter> 類別不支援的 <xref:System.Xml.XPath.XPathNavigator> 類別方法。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|會擲回 <xref:System.NotSupportedException> 例外狀況。|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|在根層級會被忽略，如果在 XML 文件的任何其他層級呼叫，則擲回 <xref:System.NotSupportedException> 例外狀況。|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|視為對等字元之 <xref:System.Xml.XmlWriter.WriteString%2A> 方法的呼叫。|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|視為對等字元之 <xref:System.Xml.XmlWriter.WriteString%2A> 方法的呼叫。|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|視為對等字元之 <xref:System.Xml.XmlWriter.WriteString%2A> 方法的呼叫。|  
  
 如需 <xref:System.Xml.XmlWriter> 類別的詳細資訊，請參閱 <xref:System.Xml.XmlWriter> 類別參考文件。  
  
### <a name="multiple-xmlwriter-objects"></a>多個 XmlWriter 物件  
 可能有多個 <xref:System.Xml.XPath.XPathNavigator> 物件指向包含一個或多個開啟 <xref:System.Xml.XmlWriter> 物件之 XML 文件的不同部分。 單一執行緒案例中允許並支援多個 <xref:System.Xml.XmlWriter> 物件。  
  
 下列各項是使用多個 <xref:System.Xml.XmlWriter> 物件時，需要考慮的重要注意事項。  
  
-   當呼叫每個 <xref:System.Xml.XmlWriter> 物件的 <xref:System.Xml.XmlWriter.Close%2A> 方法時，會將由 <xref:System.Xml.XmlWriter> 物件寫入的 XML 片段加入至 XML 文件。 直到那時，<xref:System.Xml.XmlWriter> 物件會寫入中斷連接的片段。 如果在 XML 文件上執行作業，則不會影響在呼叫 <xref:System.Xml.XmlWriter> 之前，由 <xref:System.Xml.XmlWriter.Close%2A> 物件寫入的任何片段。  
  
-   如果在特定 XML 子樹狀目錄上有開啟 <xref:System.Xml.XmlWriter> 物件，而該子樹狀目錄已刪除，則 <xref:System.Xml.XmlWriter> 物件仍然會加入至該子樹狀目錄。 該子樹狀目錄只是變成已刪除的片段。  
  
-   如果在 XML 文件中同時開啟多個 <xref:System.Xml.XmlWriter> 物件，則會依照關閉 <xref:System.Xml.XmlWriter> 物件的順序 (而非開啟它們的順序)，將它們加入至 XML 文件。  
  
 下列範例會建立 <xref:System.Xml.XmlDocument> 物件及 <xref:System.Xml.XPath.XPathNavigator> 物件，然後使用由 <xref:System.Xml.XmlWriter> 方法傳回的 <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> 物件，在 `books.xml` 檔案建立第一本書的結構。 之後，範例會將其儲存為 `book.xml` 檔案。  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a>儲存 XML 文件  
 使用 <xref:System.Xml.XmlDocument> 類別的方法，將用本主題中說明之方法對 <xref:System.Xml.XmlDocument> 物件所做的變更儲存下來。 如需儲存 <xref:System.Xml.XmlDocument> 物件之變更的詳細資訊，請參閱[儲存與寫入文件](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [使用 XPath 資料模型處理 XML 資料](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [使用 XPathNavigator 修改 XML 資料](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
- [使用 XPathNavigator 移除 XML 資料](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
