---
title: "如何︰ 使用 LINQ (Visual Basic) 轉換 XML |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9f97466727064ea275c051b5916b0fb297e9e23a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>如何：使用 LINQ 轉換 XML (Visual Basic)
[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)更容易讀取的 XML 從一個來源，並將其轉換為新的 XML 格式。 您可以利用 LINQ 查詢以擷取要轉換的內容，或將現有的文件中的內容變更為新的 XML 格式。  
  
 本主題中的範例轉換從 XML 來源文件將在瀏覽器中檢視的 HTML 內容。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-transform-an-xml-document"></a>轉換 XML 文件  
  
1.  在 Visual Studio 中建立新的 Visual Basic 專案中**主控台應用程式**專案範本。  
  
2.  按兩下要修改 Visual Basic 程式碼專案中建立的 Module1.vb 檔案。 加入下列程式碼以`Sub Main`的`Module1`模組。 此程式碼會建立來源 XML 文件當成<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument>  
  
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
  
     [如何︰ 從檔案、 字串或資料流載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)。  
  
3.  若要建立來源 XML 文件的程式碼，後面加入下列程式碼來擷取所有\<通訊錄 > 物件項目並將它們轉換成 HTML 文件。 清單\<通訊錄 > 項目所使用的 LINQ 查詢，傳回的集合<xref:System.Xml.Linq.XElement>物件包含已轉換的 HTML。</xref:System.Xml.Linq.XElement> 您可以使用內嵌的運算式值放在新的 XML 格式將來源文件。  
  
     產生的 HTML 文件寫入至檔案，需使用<xref:System.Xml.Linq.XElement.Save%2A>方法。</xref:System.Xml.Linq.XElement.Save%2A>  
  
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
  
4.  之後`Sub Main`的`Module1`，新增新方法 (`Sub`) 來轉換\<描述 > 節點插入指定的 HTML 格式。 這個方法稱為由上一個步驟中的程式碼和用來保留的格式\<描述 > 項目。  
  
     這個方法會取代的子元素\<描述 > 具有 HTML 項目。 `ReplaceWith`方法用來保留子元素的位置。 轉換後的內容\<描述 > 項目包含在 HTML 段落 (\<p >) 項目。 <xref:System.Xml.Linq.XContainer.Nodes%2A>屬性用來擷取轉換後的內容\<描述 > 項目。</xref:System.Xml.Linq.XContainer.Nodes%2A> 這可確保子元素，包含在轉換後的內容。  
  
     加入下列程式碼之後`Sub Main`的`Module1`。  
  
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
  
6.  按 f5 鍵執行的程式碼。 最後儲存的文件將會如下所示︰  
  
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
 [如何︰ 從檔案、 字串或資料流載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

