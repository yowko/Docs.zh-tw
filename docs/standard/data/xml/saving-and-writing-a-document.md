---
title: 儲存與寫入文件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83aad5d45dda1784069839662486f7dbcc307542
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879512"
---
# <a name="saving-and-writing-a-document"></a>儲存與寫入文件
載入及儲存 <xref:System.Xml.XmlDocument> 時，儲存的文件與原始文件在下列方面可能不同：  
  
-   如果在呼叫 <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> 方法之前將 `true` 屬性設為 <xref:System.Xml.XmlDocument.Save%2A>，則在輸出中會保留文件中的泛空白字元；如果此屬性為 `false`，則 <xref:System.Xml.XmlDocument> 會自動縮排輸出。  
  
-   屬性之間的所有泛空白字元會縮減為單一空格字元。  
  
-   變更項目之間的泛空白字元。 保留顯著的泛空白字元，但不保留不顯著的泛空白字元。 不過，在儲存文件時，依預設會使用 <xref:System.Xml.XmlTextWriter> **Indenting** 模式將輸出整齊列印出來，使其易於讀取。  
  
-   依預設，會將屬性值周圍的引號字元變更為雙引號。 您可以使用 <xref:System.Xml.XmlTextReader.QuoteChar%2A> 上的 <xref:System.Xml.XmlTextWriter> 屬性，將引號字元設為雙引號或單引號。  
  
-   依預設，會展開 `{` 之類的數字字元實體。  
  
-   不保留在輸入文件中發現的位元組順序標記。 除非您明確建立指定不同編碼的 XML 宣告，否則會將 UCS-2 儲存為 UTF-8。  
  
-   如果您要將 <xref:System.Xml.XmlDocument> 寫入檔案或資料流，則寫出的輸出與文件的內容相同。 換言之，唯有當文件中已包含一個 <xref:System.Xml.XmlDeclaration> 時，才會將其寫出，而且寫出文件時所使用的編碼與宣告節點中指定的編碼相同。  
  
## <a name="writing-an-xmldeclaration"></a>寫入 XmlDeclaration  
 除了 <xref:System.Xml.XmlDocument> 及 <xref:System.Xml.XmlDeclaration> 的 <xref:System.Xml.XmlNode.OuterXml%2A> 方法之外，<xref:System.Xml.XmlNode.InnerXml%2A>、<xref:System.Xml.XmlNode.WriteTo%2A> 及 <xref:System.Xml.XmlDocument> 的<xref:System.Xml.XmlDocument.Save%2A> 及 <xref:System.Xml.XmlDocument.WriteContentTo%2A> 成員也會建立 XML 宣告。  
  
 對於 <xref:System.Xml.XmlDocument>、<xref:System.Xml.XmlNode.OuterXml%2A> 與 <xref:System.Xml.XmlDocument.InnerXml%2A>、<xref:System.Xml.XmlDocument.Save%2A> 及 <xref:System.Xml.XmlDocument.WriteTo%2A> 方法的 <xref:System.Xml.XmlDocument.WriteContentTo%2A> 屬性，XML 宣告中寫出的編碼取自 <xref:System.Xml.XmlDeclaration> 節點。 如果不存在 <xref:System.Xml.XmlDeclaration> 節點，則不會寫出 <xref:System.Xml.XmlDeclaration>。如果 <xref:System.Xml.XmlDeclaration> 節點中沒有編碼，則不會在 XML 宣告中寫出編碼。  
  
 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> 及 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> 方法始終會寫出 <xref:System.Xml.XmlDeclaration>。 這些方法從其正寫入的寫入器取得編碼。 換言之，寫入器上的編碼值會覆寫文件上及 <xref:System.Xml.XmlDeclaration> 中的編碼。 例如，下列程式碼不會將編碼寫入輸出檔案 `out.xml` 中發現的 XML 宣告。  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 針對 <xref:System.Xml.XmlDocument.Save%2A> 方法，會使用 <xref:System.Xml.XmlWriter.WriteStartDocument%2A> 類別中的 <xref:System.Xml.XmlWriter> 方法寫出 XML 宣告。 因此，覆寫 <xref:System.Xml.XmlWriter.WriteStartDocument%2A> 方法會變更文件開頭的寫入方式。  
  
 針對 <xref:System.Xml.XmlDeclaration>、<xref:System.Xml.XmlNode.OuterXml%2A> 及 <xref:System.Xml.XmlDeclaration.WriteTo%2A> 的 <xref:System.Xml.XmlNode.InnerXml%2A> 成員，如果未設定 <xref:System.Xml.XmlDeclaration.Encoding%2A> 屬性，則不會寫出編碼。否則，在 XML 宣告中寫出的編碼與在 <xref:System.Xml.XmlDeclaration.Encoding%2A> 屬性中發現的編碼相同。  
  
## <a name="writing-document-content-using-the-outerxml-property"></a>使用 OuterXml 屬性寫入文件內容  
 <xref:System.Xml.XmlNode.OuterXml%2A> 屬性是全球資訊網協會 (W3C) XML 文件物件模型 (DOM) 標準的 Microsoft 擴充程式。 <xref:System.Xml.XmlNode.OuterXml%2A> 屬性可用於取得整個 XML 文件的標記，或僅取得單一節點及其子節點的標記。 <xref:System.Xml.XmlNode.OuterXml%2A> 會傳回表示給定節點及其所有子節點的標記。  
  
 下列程式碼範例顯示如何將整個文件儲存為字串。  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 下列程式碼範例顯示如何只儲存文件項目。  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 相反地，如果您需要子節點的內容，則可使用 <xref:System.Xml.XmlNode.InnerText%2A> 屬性。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
