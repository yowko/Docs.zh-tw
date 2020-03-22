---
title: LINQ to XML 概觀
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 0481a140541a7f45c682c5150bc1c3d647de90bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266894"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="13e49-102">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="13e49-102">Overview of LINQ to XML in Visual Basic</span></span>
<span data-ttu-id="13e49-103">Visual Basic[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]通過 XML 文本和 XML 軸屬性提供支援。</span><span class="sxs-lookup"><span data-stu-id="13e49-103">Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="13e49-104">這使您能夠使用熟悉、方便的語法在 Visual Basic 代碼中使用 XML。</span><span class="sxs-lookup"><span data-stu-id="13e49-104">This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code.</span></span> <span data-ttu-id="13e49-105">*XML 文本*使您能夠直接在代碼中包括 XML。</span><span class="sxs-lookup"><span data-stu-id="13e49-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="13e49-106">*XML 軸屬性*使您能夠訪問 XML 文本的子節點、子節點和屬性。</span><span class="sxs-lookup"><span data-stu-id="13e49-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="13e49-107">有關詳細資訊，請參閱視覺化基礎 中的[XML 文本概述](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)和[訪問 XML。](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)</span><span class="sxs-lookup"><span data-stu-id="13e49-107">For more information, see [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) and [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="13e49-108">是一個記憶體中的XML程式設計API，專門用於利用語言集成查詢 （LINQ）。</span><span class="sxs-lookup"><span data-stu-id="13e49-108">is an in-memory XML programming API designed specifically to take advantage of Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="13e49-109">儘管可以直接調用 LINQ API，但只有 Visual Basic 才能聲明 XML 文本並直接存取 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="13e49-109">Although you can call the LINQ APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13e49-110">ASP.NET頁中的聲明性代碼不支援 XML 文本和 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="13e49-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="13e49-111">要使用 Visual Basic XML 功能，請將代碼放在ASP.NET應用程式中的代碼背後頁中。</span><span class="sxs-lookup"><span data-stu-id="13e49-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="13e49-112">[播放按鈕](./media/overview-of-linq-to-xml/play-video-icon-example.gif)有關相關的視頻演示，請參閱[如何開始使用 LINQ 到 XML？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)以及如何[使用 LINQ 創建 Excel 試算表？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)</span><span class="sxs-lookup"><span data-stu-id="13e49-112">[Play button](./media/overview-of-linq-to-xml/play-video-icon-example.gif) For related video demonstrations, see [How Do I Get Started with LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) and [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span></span>
  
## <a name="creating-xml"></a><span data-ttu-id="13e49-113">建立 XML</span><span class="sxs-lookup"><span data-stu-id="13e49-113">Creating XML</span></span>  
 <span data-ttu-id="13e49-114">在 Visual Basic 中創建 XML 樹有兩種方法。</span><span class="sxs-lookup"><span data-stu-id="13e49-114">There are two ways to create XML trees in Visual Basic.</span></span> <span data-ttu-id="13e49-115">可以直接在代碼中聲明 XML 文本，也可以使用 LINQ API 創建樹。</span><span class="sxs-lookup"><span data-stu-id="13e49-115">You can declare an XML literal directly in code, or you can use the LINQ APIs to create the tree.</span></span> <span data-ttu-id="13e49-116">這兩個進程使代碼能夠反映 XML 樹的最終結構。</span><span class="sxs-lookup"><span data-stu-id="13e49-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="13e49-117">例如，以下代碼示例創建一個 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="13e49-117">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 <span data-ttu-id="13e49-118">有關詳細資訊，請參閱[在視覺化基本 中創建 XML。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="13e49-118">For more information, see [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="13e49-119">訪問和導航 XML</span><span class="sxs-lookup"><span data-stu-id="13e49-119">Accessing and Navigating XML</span></span>  
 <span data-ttu-id="13e49-120">Visual Basic 提供了用於訪問和導航 XML 結構的 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="13e49-120">Visual Basic provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="13e49-121">這些屬性使您能夠通過指定 XML 子項目名稱來訪問 XML 元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="13e49-121">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="13e49-122">或者，您可以顯式調用 LINQ 方法來導航和定位元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="13e49-122">Alternatively, you can explicitly call the LINQ methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="13e49-123">例如，以下代碼示例使用 XML 軸屬性來引用 XML 元素的屬性和子項目。</span><span class="sxs-lookup"><span data-stu-id="13e49-123">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="13e49-124">代碼示例使用 LINQ 查詢檢索子項目並將其輸出為 XML 元素，從而有效地執行轉換。</span><span class="sxs-lookup"><span data-stu-id="13e49-124">The code example uses a LINQ query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 <span data-ttu-id="13e49-125">有關詳細資訊，請參閱[在視覺化基本 中訪問 XML。](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)</span><span class="sxs-lookup"><span data-stu-id="13e49-125">For more information, see [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="13e49-126">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="13e49-126">XML Namespaces</span></span>  
 <span data-ttu-id="13e49-127">Visual Basic 使您能夠通過使用`Imports`語句將別名指定為全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="13e49-127">Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="13e49-128">下面的示例演示如何使用 語句`Imports`導入 XML 命名空間：</span><span class="sxs-lookup"><span data-stu-id="13e49-128">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 <span data-ttu-id="13e49-129">訪問 XML 軸屬性並為 XML 文檔和元素聲明 XML 文本時，可以使用 XML 命名空間別名。</span><span class="sxs-lookup"><span data-stu-id="13e49-129">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="13e49-130">可以使用<xref:System.Xml.Linq.XNamespace>[GetXml 命名空間運算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)檢索特定命名空間首碼的物件。</span><span class="sxs-lookup"><span data-stu-id="13e49-130">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="13e49-131">有關詳細資訊，請參閱[導入語句 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="13e49-131">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="13e49-132">在 XML 文本中使用 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="13e49-132">Using XML Namespaces in XML Literals</span></span>  
 <span data-ttu-id="13e49-133">下面的示例演示如何創建<xref:System.Xml.Linq.XElement>使用全域命名空間`ns`的物件：</span><span class="sxs-lookup"><span data-stu-id="13e49-133">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 <span data-ttu-id="13e49-134">Visual Basic 編譯器將包含 XML 命名空間別名的 XML 文本轉換為等效代碼，這些代碼使用 XML 標記法使用 XML`xmlns`命名空間，以及屬性。</span><span class="sxs-lookup"><span data-stu-id="13e49-134">The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="13e49-135">編譯後，上一節示例中的代碼生成與以下示例基本相同的可執行代碼：</span><span class="sxs-lookup"><span data-stu-id="13e49-135">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="13e49-136">在 XML 軸屬性中使用 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="13e49-136">Using XML Namespaces in XML Axis Properties</span></span>  
 <span data-ttu-id="13e49-137">在 XML 文本中聲明的 XML 命名空間不適用於 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="13e49-137">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="13e49-138">但是，全域命名空間可以與 XML 軸屬性一起使用。</span><span class="sxs-lookup"><span data-stu-id="13e49-138">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="13e49-139">使用冒號將 XML 命名空間首碼與本地元素名稱分開。</span><span class="sxs-lookup"><span data-stu-id="13e49-139">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="13e49-140">以下是範例：</span><span class="sxs-lookup"><span data-stu-id="13e49-140">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="13e49-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13e49-141">See also</span></span>

- [<span data-ttu-id="13e49-142">Xml</span><span class="sxs-lookup"><span data-stu-id="13e49-142">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="13e49-143">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="13e49-143">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="13e49-144">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="13e49-144">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="13e49-145">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="13e49-145">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
