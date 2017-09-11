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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 12b5bfd059d219a5cb0087e763688d01a75b0533
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="826e2-102">如何：使用 LINQ 轉換 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="826e2-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="826e2-103">[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)更容易讀取的 XML 從一個來源，並將其轉換為新的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="826e2-103">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="826e2-104">您可以利用 LINQ 查詢以擷取要轉換的內容，或將現有的文件中的內容變更為新的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="826e2-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>  
  
 <span data-ttu-id="826e2-105">本主題中的範例轉換從 XML 來源文件將在瀏覽器中檢視的 HTML 內容。</span><span class="sxs-lookup"><span data-stu-id="826e2-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a><span data-ttu-id="826e2-106">轉換 XML 文件</span><span class="sxs-lookup"><span data-stu-id="826e2-106">To transform an XML document</span></span>  
  
1.  <span data-ttu-id="826e2-107">在 Visual Studio 中建立新的 Visual Basic 專案中**主控台應用程式**專案範本。</span><span class="sxs-lookup"><span data-stu-id="826e2-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>  
  
2.  <span data-ttu-id="826e2-108">按兩下要修改 Visual Basic 程式碼專案中建立的 Module1.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="826e2-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="826e2-109">加入下列程式碼以`Sub Main`的`Module1`模組。</span><span class="sxs-lookup"><span data-stu-id="826e2-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="826e2-110">此程式碼會建立來源 XML 文件當成<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="826e2-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
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
  
     <span data-ttu-id="826e2-111">[如何︰ 從檔案、 字串或資料流載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)。</span><span class="sxs-lookup"><span data-stu-id="826e2-111">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span></span>  
  
3.  <span data-ttu-id="826e2-112">若要建立來源 XML 文件的程式碼，後面加入下列程式碼來擷取所有\<通訊錄 > 物件項目並將它們轉換成 HTML 文件。</span><span class="sxs-lookup"><span data-stu-id="826e2-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="826e2-113">清單\<通訊錄 > 項目所使用的 LINQ 查詢，傳回的集合<xref:System.Xml.Linq.XElement>物件包含已轉換的 HTML。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="826e2-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="826e2-114">您可以使用內嵌的運算式值放在新的 XML 格式將來源文件。</span><span class="sxs-lookup"><span data-stu-id="826e2-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>  
  
     <span data-ttu-id="826e2-115">產生的 HTML 文件寫入至檔案，需使用<xref:System.Xml.Linq.XElement.Save%2A>方法。</xref:System.Xml.Linq.XElement.Save%2A></span><span class="sxs-lookup"><span data-stu-id="826e2-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>  
  
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
  
4.  <span data-ttu-id="826e2-116">之後`Sub Main`的`Module1`，新增新方法 (`Sub`) 來轉換\<描述 > 節點插入指定的 HTML 格式。</span><span class="sxs-lookup"><span data-stu-id="826e2-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="826e2-117">這個方法稱為由上一個步驟中的程式碼和用來保留的格式\<描述 > 項目。</span><span class="sxs-lookup"><span data-stu-id="826e2-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>  
  
     <span data-ttu-id="826e2-118">這個方法會取代的子元素\<描述 > 具有 HTML 項目。</span><span class="sxs-lookup"><span data-stu-id="826e2-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="826e2-119">`ReplaceWith`方法用來保留子元素的位置。</span><span class="sxs-lookup"><span data-stu-id="826e2-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="826e2-120">轉換後的內容\<描述 > 項目包含在 HTML 段落 (\<p >) 項目。</span><span class="sxs-lookup"><span data-stu-id="826e2-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="826e2-121"><xref:System.Xml.Linq.XContainer.Nodes%2A>屬性用來擷取轉換後的內容\<描述 > 項目。</xref:System.Xml.Linq.XContainer.Nodes%2A></span><span class="sxs-lookup"><span data-stu-id="826e2-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="826e2-122">這可確保子元素，包含在轉換後的內容。</span><span class="sxs-lookup"><span data-stu-id="826e2-122">This ensures that sub-elements are included in the transformed content.</span></span>  
  
     <span data-ttu-id="826e2-123">加入下列程式碼之後`Sub Main`的`Module1`。</span><span class="sxs-lookup"><span data-stu-id="826e2-123">Add the following code after `Sub Main` of `Module1`.</span></span>  
  
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
  
5.  <span data-ttu-id="826e2-124">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="826e2-124">Save your changes.</span></span>  
  
6.  <span data-ttu-id="826e2-125">按 f5 鍵執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="826e2-125">Press F5 to run the code.</span></span> <span data-ttu-id="826e2-126">最後儲存的文件將會如下所示︰</span><span class="sxs-lookup"><span data-stu-id="826e2-126">The resulting saved document will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="826e2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="826e2-127">See Also</span></span>  
 <span data-ttu-id="826e2-128">[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="826e2-128">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="826e2-129"> [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="826e2-129"> [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span></span>  
<span data-ttu-id="826e2-130"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="826e2-130"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="826e2-131"> [如何︰ 從檔案、 字串或資料流載入 XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span><span class="sxs-lookup"><span data-stu-id="826e2-131"> [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span></span>  
<span data-ttu-id="826e2-132"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="826e2-132"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="826e2-133"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="826e2-133"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>

