---
title: HOW TO：將 XML 轉換使用 LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
ms.openlocfilehash: c34d3988c89e0ce07676e9181200fc039010b50a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028430"
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="b7047-102">HOW TO：將 XML 轉換使用 LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7047-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="b7047-103">[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)輕鬆地從一個來源讀取 XML 並將其轉換為新的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="b7047-103">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="b7047-104">您可以利用 LINQ 查詢來擷取要轉換的內容，或將現有的文件中的內容變更為新的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="b7047-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>  
  
 <span data-ttu-id="b7047-105">本主題中的範例轉換為 HTML 在瀏覽器中檢視從 XML 來源文件內容。</span><span class="sxs-lookup"><span data-stu-id="b7047-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a><span data-ttu-id="b7047-106">要轉換的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="b7047-106">To transform an XML document</span></span>  
  
1. <span data-ttu-id="b7047-107">在 Visual Studio 中建立新的 Visual Basic 專案中**主控台應用程式**專案範本。</span><span class="sxs-lookup"><span data-stu-id="b7047-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>  
  
2. <span data-ttu-id="b7047-108">按兩下 Module1.vb 檔案來修改 Visual Basic 程式碼專案中建立。</span><span class="sxs-lookup"><span data-stu-id="b7047-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="b7047-109">將下列程式碼加入`Sub Main`的`Module1`模組。</span><span class="sxs-lookup"><span data-stu-id="b7047-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="b7047-110">此程式碼會建立來源 XML 文件<xref:System.Xml.Linq.XDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="b7047-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
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
  
     <span data-ttu-id="b7047-111">[如何：從檔案、 字串或 Stream 載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)。</span><span class="sxs-lookup"><span data-stu-id="b7047-111">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span></span>  
  
3. <span data-ttu-id="b7047-112">若要建立來源 XML 文件的程式碼之後, 新增下列程式碼來擷取所有\<書籍 > 物件項目並將它們轉換成 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="b7047-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="b7047-113">清單\<書籍 > 項目由使用 LINQ 查詢所傳回的集合<xref:System.Xml.Linq.XElement>物件，包含已轉換的 HTML。</span><span class="sxs-lookup"><span data-stu-id="b7047-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="b7047-114">您可以使用內嵌的運算式將值放在新的 XML 格式將來源文件。</span><span class="sxs-lookup"><span data-stu-id="b7047-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>  
  
     <span data-ttu-id="b7047-115">產生的 HTML 文件就會寫入檔案中，使用<xref:System.Xml.Linq.XElement.Save%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b7047-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>  
  
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
  
4. <span data-ttu-id="b7047-116">在後`Sub Main`的`Module1`，新增新方法 (`Sub`) 來轉換\<描述 > 節點插入指定的 HTML 格式。</span><span class="sxs-lookup"><span data-stu-id="b7047-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="b7047-117">這個方法稱為由上一個步驟中的程式碼和用來保留格式\<描述 > 項目。</span><span class="sxs-lookup"><span data-stu-id="b7047-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>  
  
     <span data-ttu-id="b7047-118">這個方法會取代的子元素\<描述 > 具有 HTML 項目。</span><span class="sxs-lookup"><span data-stu-id="b7047-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="b7047-119">`ReplaceWith`方法用來保留子元素的位置。</span><span class="sxs-lookup"><span data-stu-id="b7047-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="b7047-120">轉換後的內容\<描述 > 項目包含在 HTML 段落 (\<p >) 項目。</span><span class="sxs-lookup"><span data-stu-id="b7047-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="b7047-121"><xref:System.Xml.Linq.XContainer.Nodes%2A>屬性用來擷取已轉換的內容\<描述 > 項目。</span><span class="sxs-lookup"><span data-stu-id="b7047-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="b7047-122">這可確保在轉換後的內容中，包含子元素。</span><span class="sxs-lookup"><span data-stu-id="b7047-122">This ensures that sub-elements are included in the transformed content.</span></span>  
  
     <span data-ttu-id="b7047-123">新增下列程式碼後的`Sub Main`的`Module1`。</span><span class="sxs-lookup"><span data-stu-id="b7047-123">Add the following code after `Sub Main` of `Module1`.</span></span>  
  
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
  
5. <span data-ttu-id="b7047-124">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="b7047-124">Save your changes.</span></span>  
  
6. <span data-ttu-id="b7047-125">按 f5 鍵執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="b7047-125">Press F5 to run the code.</span></span> <span data-ttu-id="b7047-126">最後儲存的文件將會如下所示：</span><span class="sxs-lookup"><span data-stu-id="b7047-126">The resulting saved document will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7047-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7047-127">See also</span></span>

- [<span data-ttu-id="b7047-128">XML 常值</span><span class="sxs-lookup"><span data-stu-id="b7047-128">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="b7047-129">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="b7047-129">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
- [<span data-ttu-id="b7047-130">XML</span><span class="sxs-lookup"><span data-stu-id="b7047-130">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="b7047-131">如何：從檔案、 字串或 Stream 載入 XML</span><span class="sxs-lookup"><span data-stu-id="b7047-131">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)
- [<span data-ttu-id="b7047-132">LINQ</span><span class="sxs-lookup"><span data-stu-id="b7047-132">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="b7047-133">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="b7047-133">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
