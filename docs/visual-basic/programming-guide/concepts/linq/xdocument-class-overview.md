---
title: "XDocument 類別概觀 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3f51808a64d51fb354159df1a7323ad2fc26eedc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="90ffd-102">XDocument 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90ffd-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="90ffd-103">本主題介紹的<xref:System.Xml.Linq.XDocument>類別。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="90ffd-104">XDocument 類別的概觀</span><span class="sxs-lookup"><span data-stu-id="90ffd-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="90ffd-105"><xref:System.Xml.Linq.XDocument>類別包含有效的 XML 文件所需的資訊。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="90ffd-106">這包括 XML 宣告、處理指示與註解。</span><span class="sxs-lookup"><span data-stu-id="90ffd-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="90ffd-107">請注意您只需要建立<xref:System.Xml.Linq.XDocument>物件，如果您需要特定的功能提供的<xref:System.Xml.Linq.XDocument>類別。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="90ffd-108">在許多情況下，您可直接與<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="90ffd-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="90ffd-109">直接使用<xref:System.Xml.Linq.XElement>是較簡單的程式設計模型。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="90ffd-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="90ffd-110"><xref:System.Xml.Linq.XDocument>衍生自<xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="90ffd-111">因此，它可以包含子節點。</span><span class="sxs-lookup"><span data-stu-id="90ffd-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="90ffd-112">不過，<xref:System.Xml.Linq.XDocument>物件可以有只有一個小孩<xref:System.Xml.Linq.XElement>節點。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="90ffd-113">這會反映 XML 標準，也就是說 XML 文件中只能有一個根項目 (Root Element)。</span><span class="sxs-lookup"><span data-stu-id="90ffd-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="90ffd-114">XDocument 的元件</span><span class="sxs-lookup"><span data-stu-id="90ffd-114">Components of XDocument</span></span>  
 <span data-ttu-id="90ffd-115"><xref:System.Xml.Linq.XDocument>可以包含下列元素︰</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="90ffd-116">一個<xref:System.Xml.Linq.XDeclaration>物件。</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="90ffd-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="90ffd-117"><xref:System.Xml.Linq.XDeclaration>可讓您指定 XML 宣告的關聯部分︰ XML 版本、 編碼方式的文件，以及是否是獨立的 XML 文件。</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="90ffd-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="90ffd-118">一個<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="90ffd-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="90ffd-119">這是 XML 文件的根節點。</span><span class="sxs-lookup"><span data-stu-id="90ffd-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="90ffd-120">任何數目的<xref:System.Xml.Linq.XProcessingInstruction>物件。</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="90ffd-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="90ffd-121">處理指示會將資訊傳達到處理 XML 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="90ffd-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="90ffd-122">任何數目的<xref:System.Xml.Linq.XComment>物件。</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="90ffd-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="90ffd-123">這些註解將是根項目的同層級。</span><span class="sxs-lookup"><span data-stu-id="90ffd-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="90ffd-124"><xref:System.Xml.Linq.XComment>物件不能在清單中，第一個引數，因為不是有效的 XML 文件註解的開頭。</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="90ffd-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="90ffd-125">一個<xref:System.Xml.Linq.XDocumentType>適用於 DTD。</xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="90ffd-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="90ffd-126">當您序列化<xref:System.Xml.Linq.XDocument>，即使`XDocument.Declaration`是`null`，輸出將會有 XML 宣告，如果寫入器已`Writer.Settings.OmitXmlDeclaration`設為`false`（預設值）。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="90ffd-127">根據預設，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 會將版本設定為 "1.0"，並將編碼設定為 "utf-8"。</span><span class="sxs-lookup"><span data-stu-id="90ffd-127">By default, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="90ffd-128">在沒有 XDocument 的情況下使用 XElement</span><span class="sxs-lookup"><span data-stu-id="90ffd-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="90ffd-129">如先前所述，<xref:System.Xml.Linq.XElement>類別是中的主要類別[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]程式設計介面。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="90ffd-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] programming interface.</span></span> <span data-ttu-id="90ffd-130">在許多情況下，您的應用程式將不需要您建立文件。</span><span class="sxs-lookup"><span data-stu-id="90ffd-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="90ffd-131">使用<xref:System.Xml.Linq.XElement>類別中，您可以建立 XML 樹狀結構中，加入其他 XML 樹狀結構、 修改 XML 樹狀結構中，並儲存它。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="90ffd-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="90ffd-132">使用 XDocument</span><span class="sxs-lookup"><span data-stu-id="90ffd-132">Using XDocument</span></span>  
 <span data-ttu-id="90ffd-133">若要建構<xref:System.Xml.Linq.XDocument>，使用功能結構，就像建構<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="90ffd-134">下列程式碼會建立<xref:System.Xml.Linq.XDocument>物件及其相關聯所包含的物件。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="90ffd-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 <span data-ttu-id="90ffd-135">當您檢查 test.xml 檔案時，您會得到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="90ffd-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="90ffd-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90ffd-136">See Also</span></span>  
 [<span data-ttu-id="90ffd-137">LINQ to XML 程式設計概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90ffd-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
