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
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="83b77-102">如何：使用 LINQ 轉換 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83b77-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>

<span data-ttu-id="83b77-103">[Xml 常](../../../language-reference/xml-literals/index.md)值可讓您輕鬆地從一個來源讀取 xml，並將它轉換成新的 xml 格式。</span><span class="sxs-lookup"><span data-stu-id="83b77-103">[XML Literals](../../../language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="83b77-104">您可以利用 LINQ 查詢來抓取要轉換的內容，或將現有檔中的內容變更為新的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="83b77-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>

<span data-ttu-id="83b77-105">本主題中的範例會將 XML 來源文件中的內容轉換成 HTML，以便在瀏覽器中查看。</span><span class="sxs-lookup"><span data-stu-id="83b77-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-transform-an-xml-document"></a><span data-ttu-id="83b77-106">轉換 XML 檔</span><span class="sxs-lookup"><span data-stu-id="83b77-106">To transform an XML document</span></span>

1. <span data-ttu-id="83b77-107">在 Visual Studio 中，于 [**主控台應用程式**] 專案範本中建立新的 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="83b77-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>

2. <span data-ttu-id="83b77-108">按兩下專案中建立的 [Module1] 檔案，以修改 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="83b77-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="83b77-109">將下列程式碼新增至 `Sub Main` 模組的 `Module1` 。</span><span class="sxs-lookup"><span data-stu-id="83b77-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="83b77-110">此程式碼會建立來源 XML 檔做為 <xref:System.Xml.Linq.XDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="83b77-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>

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

     <span data-ttu-id="83b77-111">[如何：從檔案、字串或資料流程載入 XML](how-to-load-xml-from-a-file-string-or-stream.md)。</span><span class="sxs-lookup"><span data-stu-id="83b77-111">[How to: Load XML from a File, String, or Stream](how-to-load-xml-from-a-file-string-or-stream.md).</span></span>

3. <span data-ttu-id="83b77-112">在建立來源 XML 檔的程式碼之後，新增下列程式碼以從物件取出所有專案 \<Book> ，並將它們轉換成 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="83b77-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="83b77-113">專案清單 \<Book> 是使用 LINQ 查詢所建立的，它會傳回 <xref:System.Xml.Linq.XElement> 包含已轉換之 HTML 的物件集合。</span><span class="sxs-lookup"><span data-stu-id="83b77-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="83b77-114">您可以使用內嵌的運算式，將來源文件中的值放入新的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="83b77-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>

     <span data-ttu-id="83b77-115">產生的 HTML 檔案會使用方法寫入檔案 <xref:System.Xml.Linq.XElement.Save%2A> 。</span><span class="sxs-lookup"><span data-stu-id="83b77-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>

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

4. <span data-ttu-id="83b77-116">在 `Sub Main` 之後 `Module1` ，請加入新的方法（ `Sub` ），以將節點轉換為 \<Description> 指定的 HTML 格式。</span><span class="sxs-lookup"><span data-stu-id="83b77-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="83b77-117">這個方法是由上一個步驟中的程式碼所呼叫，用來保留元素的格式 \<Description> 。</span><span class="sxs-lookup"><span data-stu-id="83b77-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>

     <span data-ttu-id="83b77-118">這個方法會以 HTML 取代元素的子項目 \<Description> 。</span><span class="sxs-lookup"><span data-stu-id="83b77-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="83b77-119">`ReplaceWith`方法是用來保留子項目的位置。</span><span class="sxs-lookup"><span data-stu-id="83b77-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="83b77-120">元素的已轉換內容 \<Description> 包含在 HTML 段落（ \<p> ）元素中。</span><span class="sxs-lookup"><span data-stu-id="83b77-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="83b77-121"><xref:System.Xml.Linq.XContainer.Nodes%2A>屬性是用來抓取元素的已轉換內容 \<Description> 。</span><span class="sxs-lookup"><span data-stu-id="83b77-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="83b77-122">這可確保子項目會包含在已轉換的內容中。</span><span class="sxs-lookup"><span data-stu-id="83b77-122">This ensures that sub-elements are included in the transformed content.</span></span>

     <span data-ttu-id="83b77-123">在之後新增下列程式 `Sub Main` 代碼 `Module1` 。</span><span class="sxs-lookup"><span data-stu-id="83b77-123">Add the following code after `Sub Main` of `Module1`.</span></span>

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

5. <span data-ttu-id="83b77-124">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="83b77-124">Save your changes.</span></span>

6. <span data-ttu-id="83b77-125">按 F5 執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="83b77-125">Press F5 to run the code.</span></span> <span data-ttu-id="83b77-126">所產生的儲存檔會如下所示：</span><span class="sxs-lookup"><span data-stu-id="83b77-126">The resulting saved document will resemble the following:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="83b77-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83b77-127">See also</span></span>

- [<span data-ttu-id="83b77-128">XML 常值</span><span class="sxs-lookup"><span data-stu-id="83b77-128">XML Literals</span></span>](../../../language-reference/xml-literals/index.md)
- [<span data-ttu-id="83b77-129">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="83b77-129">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
- [<span data-ttu-id="83b77-130">XML</span><span class="sxs-lookup"><span data-stu-id="83b77-130">XML</span></span>](index.md)
- [<span data-ttu-id="83b77-131">如何：從檔案、字串或資料流載入 XML</span><span class="sxs-lookup"><span data-stu-id="83b77-131">How to: Load XML from a File, String, or Stream</span></span>](how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="83b77-132">LINQ</span><span class="sxs-lookup"><span data-stu-id="83b77-132">LINQ</span></span>](../linq/index.md)
- [<span data-ttu-id="83b77-133">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="83b77-133">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
