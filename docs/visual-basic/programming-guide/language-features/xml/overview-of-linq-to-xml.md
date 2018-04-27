---
title: Visual Basic 中的 LINQ to XML 概觀
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be9038fb194c0e4890593b4b80751a477def20a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="04d13-102">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="04d13-102">Overview of LINQ to XML in Visual Basic</span></span>
<span data-ttu-id="04d13-103">Visual Basic 提供的支援[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]透過 XML 常值和 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="04d13-103">Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="04d13-104">這可讓您使用熟悉且方便的語法，在 Visual Basic 程式碼中使用的 XML。</span><span class="sxs-lookup"><span data-stu-id="04d13-104">This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code.</span></span> <span data-ttu-id="04d13-105">*XML 常值*可讓您直接在您的程式碼中包含 XML。</span><span class="sxs-lookup"><span data-stu-id="04d13-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="04d13-106">*XML 軸屬性*讓您存取子節點、 子代節點和 XML 常值的屬性。</span><span class="sxs-lookup"><span data-stu-id="04d13-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="04d13-107">如需詳細資訊，請參閱[XML 常值概觀](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)和[存取 Visual Basic 中的 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="04d13-107">For more information, see [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) and [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="04d13-108"> 為記憶體中 XML 程式設計 API 專門設計為利用[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="04d13-108"> is an in-memory XML programming API designed specifically to take advantage of [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="04d13-109">雖然您可以呼叫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]直接 Api，但只有 Visual Basic 可讓您宣告 XML 常值及直接存取 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="04d13-109">Although you can call the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04d13-110">ASP.NET 網頁中的宣告式程式碼中不支援 XML 常值和 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="04d13-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="04d13-111">若要使用 Visual Basic XML 功能，將程式碼放在 ASP.NET 應用程式中的程式碼後置頁面。</span><span class="sxs-lookup"><span data-stu-id="04d13-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="04d13-112">![影片連結](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")相關的影片示範，請參閱[如何開始使用 LINQ to XML？](http://go.microsoft.com/fwlink/?LinkId=143034)和[如何建立 Excel 試算表使用 LINQ to XML？](http://go.microsoft.com/fwlink/?LinkId=143536)。</span><span class="sxs-lookup"><span data-stu-id="04d13-112">![link to video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") For related video demonstrations, see [How Do I Get Started with LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143034) and [How Do I Create Excel Spreadsheets using LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143536).</span></span>  
  
## <a name="creating-xml"></a><span data-ttu-id="04d13-113">建立 XML</span><span class="sxs-lookup"><span data-stu-id="04d13-113">Creating XML</span></span>  
 <span data-ttu-id="04d13-114">有兩種方式可以在 Visual Basic 中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="04d13-114">There are two ways to create XML trees in Visual Basic.</span></span> <span data-ttu-id="04d13-115">您可以宣告 XML 常值，直接在程式碼中，或者您可以使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Api 來建立樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="04d13-115">You can declare an XML literal directly in code, or you can use the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] APIs to create the tree.</span></span> <span data-ttu-id="04d13-116">這兩個程序允許以反映最終的 XML 樹狀結構的程式碼。</span><span class="sxs-lookup"><span data-stu-id="04d13-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="04d13-117">例如，下列程式碼範例會建立 XML 項目：</span><span class="sxs-lookup"><span data-stu-id="04d13-117">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 <span data-ttu-id="04d13-118">如需詳細資訊，請參閱[在 Visual Basic 中建立的 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="04d13-118">For more information, see [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="04d13-119">存取和巡覽 XML</span><span class="sxs-lookup"><span data-stu-id="04d13-119">Accessing and Navigating XML</span></span>  
 <span data-ttu-id="04d13-120">Visual Basic 提供 XML 軸屬性，可存取及巡覽 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="04d13-120">Visual Basic provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="04d13-121">這些屬性可讓您指定的 XML 子元素名稱來存取 XML 元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="04d13-121">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="04d13-122">或者，您可以明確地呼叫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]巡覽及尋找項目和屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="04d13-122">Alternatively, you can explicitly call the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="04d13-123">例如，下列的程式碼範例會使用 XML 軸屬性來參考的屬性和子項目的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="04d13-123">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="04d13-124">此程式碼範例會使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢來擷取子項目和其輸出為 XML 項目，有效地執行轉換。</span><span class="sxs-lookup"><span data-stu-id="04d13-124">The code example uses a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 <span data-ttu-id="04d13-125">如需詳細資訊，請參閱[存取 Visual Basic 中的 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="04d13-125">For more information, see [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="04d13-126">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="04d13-126">XML Namespaces</span></span>  
 <span data-ttu-id="04d13-127">Visual Basic 可讓您使用指定的全域 XML 命名空間別名`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="04d13-127">Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="04d13-128">下列範例示範如何使用`Imports`陳述式匯入的 XML 命名空間：</span><span class="sxs-lookup"><span data-stu-id="04d13-128">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 <span data-ttu-id="04d13-129">當您存取 XML 軸屬性，並宣告 XML 常值的 XML 文件和項目時，您可以使用 XML 命名空間別名。</span><span class="sxs-lookup"><span data-stu-id="04d13-129">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="04d13-130">您可以擷取<xref:System.Xml.Linq.XNamespace>物件使用的特定命名空間前置詞[GetXmlNamespace 運算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="04d13-130">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="04d13-131">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="04d13-131">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="04d13-132">使用 XML 常值中的 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="04d13-132">Using XML Namespaces in XML Literals</span></span>  
 <span data-ttu-id="04d13-133">下列範例示範如何建立<xref:System.Xml.Linq.XElement>使用全域命名空間的物件`ns`:</span><span class="sxs-lookup"><span data-stu-id="04d13-133">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 <span data-ttu-id="04d13-134">Visual Basic 編譯器將轉譯 XML 常值到對等程式碼中使用的 XML 表示法搭配使用 XML 命名空間，包含 XML 命名空間別名`xmlns`屬性。</span><span class="sxs-lookup"><span data-stu-id="04d13-134">The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="04d13-135">編譯時，在上一節的範例程式碼會產生基本上相同可執行程式碼，如下列範例：</span><span class="sxs-lookup"><span data-stu-id="04d13-135">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="04d13-136">XML 軸屬性中使用 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="04d13-136">Using XML Namespaces in XML Axis Properties</span></span>  
 <span data-ttu-id="04d13-137">在 XML 常值中宣告的 XML 命名空間不適用於 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="04d13-137">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="04d13-138">不過，全域命名空間可以搭配 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="04d13-138">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="04d13-139">您可以使用冒號來分開的本機項目名稱的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="04d13-139">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="04d13-140">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="04d13-140">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="04d13-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04d13-141">See Also</span></span>  
 [<span data-ttu-id="04d13-142">XML</span><span class="sxs-lookup"><span data-stu-id="04d13-142">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="04d13-143">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="04d13-143">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="04d13-144">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="04d13-144">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="04d13-145">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="04d13-145">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
