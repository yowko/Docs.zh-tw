---
title: 如何：使用 LINQ 轉換 XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: dab394ec45567589e002b5d2ac76ec19fb0f76c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374877"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>如何：使用 LINQ 轉換 XML (Visual Basic)

[Xml 常](../../../language-reference/xml-literals/index.md)值可讓您輕鬆地從一個來源讀取 xml，並將它轉換成新的 xml 格式。 您可以利用 LINQ 查詢來抓取要轉換的內容，或將現有檔中的內容變更為新的 XML 格式。

本主題中的範例會將 XML 來源文件中的內容轉換成 HTML，以便在瀏覽器中查看。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a>轉換 XML 檔

1. 在 Visual Studio 中，于 [**主控台應用程式**] 專案範本中建立新的 Visual Basic 專案。

2. 按兩下專案中建立的 [Module1] 檔案，以修改 Visual Basic 程式碼。 將下列程式碼新增至 `Sub Main` 模組的 `Module1` 。 此程式碼會建立來源 XML 檔做為 <xref:System.Xml.Linq.XDocument> 物件。

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

     [如何：從檔案、字串或資料流程載入 XML](how-to-load-xml-from-a-file-string-or-stream.md)。

3. 在建立來源 XML 檔的程式碼之後，新增下列程式碼以從物件取出所有專案 \<Book> ，並將它們轉換成 HTML 檔案。 專案清單 \<Book> 是使用 LINQ 查詢所建立的，它會傳回 <xref:System.Xml.Linq.XElement> 包含已轉換之 HTML 的物件集合。 您可以使用內嵌的運算式，將來源文件中的值放入新的 XML 格式。

     產生的 HTML 檔案會使用方法寫入檔案 <xref:System.Xml.Linq.XElement.Save%2A> 。

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

4. 在 `Sub Main` 之後 `Module1` ，請加入新的方法（ `Sub` ），以將節點轉換為 \<Description> 指定的 HTML 格式。 這個方法是由上一個步驟中的程式碼所呼叫，用來保留元素的格式 \<Description> 。

     這個方法會以 HTML 取代元素的子項目 \<Description> 。 `ReplaceWith`方法是用來保留子項目的位置。 元素的已轉換內容 \<Description> 包含在 HTML 段落（ \<p> ）元素中。 <xref:System.Xml.Linq.XContainer.Nodes%2A>屬性是用來抓取元素的已轉換內容 \<Description> 。 這可確保子項目會包含在已轉換的內容中。

     在之後新增下列程式 `Sub Main` 代碼 `Module1` 。

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

5. 儲存您的變更。

6. 按 F5 執行程式碼。 所產生的儲存檔會如下所示：

    ```html
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

- [XML 常值](../../../language-reference/xml-literals/index.md)
- [在 Visual Basic 中管理 XML](manipulating-xml.md)
- [XML](index.md)
- [如何：從檔案、字串或資料流載入 XML](how-to-load-xml-from-a-file-string-or-stream.md)
- [LINQ](../linq/index.md)
- [Visual Basic 中的 LINQ 簡介](../linq/introduction-to-linq.md)
