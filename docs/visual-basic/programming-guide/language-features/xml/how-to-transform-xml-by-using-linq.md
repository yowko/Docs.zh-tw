---
title: "How to: Transform XML by Using LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML [Visual Basic], transforming"
  - "LINQ to XML [Visual Basic], transforming XML"
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Transform XML by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)可讓您輕鬆地讀取某個來源中的 XML 並將它轉換成新的 XML 格式。  您可以利用 LINQ 查詢來擷取要轉換的內容，或者將現有文件的內容變更為新的 XML 格式。  
  
 本主題中的範例會將 XML 來源文件中的內容轉換成可在瀏覽器中檢視的 HTML 文件。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要轉換 XML 文件  
  
1.  在 Visual Studio 中，以 \[**主控台應用程式**\] 專案範本建立新的 Visual Basic 專案。  
  
2.  按兩下專案中建立的 Module1.vb 檔案，修改 Visual Basic 程式碼。  將下列程式碼加入至 `Module1` 模組的 `Sub Main`。  這個程式碼會以 <xref:System.Xml.Linq.XDocument> 物件建立來源 XML 文件。  
  
    ```vb#  
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
  
     [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3.  在用以建立來源 XML 文件的程式碼後面加入下列程式碼，以擷取物件中所有的 \<Book\> 項目並將之轉換成 HTML 文件。  \<Book\> 項目的清單是利用 LINQ 查詢建立而成，這個查詢會傳回一組包含轉換後 HTML 的 <xref:System.Xml.Linq.XElement> 物件。  您可以使用內嵌運算式將來源文件中的值編排成新的 XML 格式。  
  
     產生的 HTML 文件是透過 <xref:System.Xml.Linq.XElement.Save%2A> 方法寫入至檔案。  
  
    ```vb#  
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
  
4.  在 `Module1` 的 `Sub Main` 後面加入新方法 \(`Sub`\)，將 \<Description\> 節點轉換成指定的 HTML 格式。  上一個步驟中的程式碼會呼叫這個方法，用以保留 \<Description\> 項目的格式。  
  
     這個方法會將 \<Description\> 項目的子項目取代為 HTML。  `ReplaceWith` 方法會用來保留子項目的位置。  \<Description\> 項目轉換後的內容會包含在 HTML 段落 \(\<p\>\) 項目中。  <xref:System.Xml.Linq.XContainer.Nodes%2A> 屬性則用來擷取 \<Description\> 項目轉換後的內容。  這可確保子項目包含在轉換後的內容中。  
  
     在 `Module1` 的 `Sub Main` 後面加入下列程式碼。  
  
    ```vb#  
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
  
5.  儲存您所作的變更。  
  
6.  按 F5 執行程式碼。  最後儲存的文件將與底下類似：  
  
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
  
## 請參閱  
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)