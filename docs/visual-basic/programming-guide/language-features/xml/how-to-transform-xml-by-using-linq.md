---
title: 如何：使用 LINQ 轉換 XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: 94ad5180c7921a5ace09f9161de5f275475e46d4
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924905"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>如何：使用 LINQ 轉換 XML (Visual Basic)
[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)輕鬆地從一個來源讀取 XML 並將其轉換為新的 XML 格式。 您可以利用 LINQ 查詢來擷取要轉換的內容，或將現有的文件中的內容變更為新的 XML 格式。  
  
 本主題中的範例轉換為 HTML 在瀏覽器中檢視從 XML 來源文件內容。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>要轉換的 XML 文件  
  
1.  在 Visual Studio 中建立新的 Visual Basic 專案中**主控台應用程式**專案範本。  
  
2.  按兩下 Module1.vb 檔案來修改 Visual Basic 程式碼專案中建立。 將下列程式碼加入`Sub Main`的`Module1`模組。 此程式碼會建立來源 XML 文件<xref:System.Xml.Linq.XDocument>物件。  
  
    ```vb  
    Dim catalog =   
      <?xml version="1.0"?>  
        <Catalog>  
          <Book id="bk101">  
            <Author>Garghentini, Davide</Author>  
            <Title>XML Developer's Guide</Title>  
            <Price>44.95</Price>  
            <Description>  
              An in-depth look at creating applications  
              with <technology>XML</technology>. For   
              <audience>beginners</audience> or   
              <audience>advanced</audience> developers.  
            </Description>  
          </Book>  
          <Book id="bk331">  
            <Author>Spencer, Phil</Author>  
            <Title>Developing Applications with Visual Basic .NET</Title>  
            <Price>45.95</Price>  
            <Description>  
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     [如何： 從檔案、 字串或 Stream 載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)。  
  
3.  若要建立來源 XML 文件的程式碼之後, 新增下列程式碼來擷取所有\<書籍 > 物件項目並將它們轉換成 HTML 文件。 清單\<書籍 > 項目由使用 LINQ 查詢所傳回的集合<xref:System.Xml.Linq.XElement>物件，包含已轉換的 HTML。 您可以使用內嵌的運算式將值放在新的 XML 格式將來源文件。  
  
     產生的 HTML 文件就會寫入檔案中，使用<xref:System.Xml.Linq.XElement.Save%2A>方法。  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4.  在後`Sub Main`的`Module1`，新增新方法 (`Sub`) 來轉換\<描述 > 節點插入指定的 HTML 格式。 這個方法稱為由上一個步驟中的程式碼和用來保留格式\<描述 > 項目。  
  
     這個方法會取代的子元素\<描述 > 具有 HTML 項目。 `ReplaceWith`方法用來保留子元素的位置。 轉換後的內容\<描述 > 項目包含在 HTML 段落 (\<p >) 項目。 <xref:System.Xml.Linq.XContainer.Nodes%2A>屬性用來擷取已轉換的內容\<描述 > 項目。 這可確保在轉換後的內容中，包含子元素。  
  
     新增下列程式碼後的`Sub Main`的`Module1`。  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5.  儲存您的變更。  
  
6.  按 f5 鍵執行程式碼。 最後儲存的文件將會如下所示：  
  
    ```  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [如何：從檔案、字串或資料流載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
