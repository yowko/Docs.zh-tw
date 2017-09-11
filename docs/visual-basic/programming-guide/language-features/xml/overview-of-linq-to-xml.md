---
title: "LINQ to XML 在 Visual Basic 中的概觀 |Microsoft 文件"
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
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cab0c219fe62064c62af4bd93e445107d73974db
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="52eb1-102">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="52eb1-102">Overview of LINQ to XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="52eb1-103">提供支援[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]透過 XML 常值和 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="52eb1-103"> provides support for [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="52eb1-104">這可讓您使用熟悉且方便的語法中的 XML 所使用的程式[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼。</span><span class="sxs-lookup"><span data-stu-id="52eb1-104">This enables you to use a familiar, convenient syntax for working with XML in your [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span> <span data-ttu-id="52eb1-105">*XML 常值*可讓您直接在您的程式碼中包含 XML。</span><span class="sxs-lookup"><span data-stu-id="52eb1-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="52eb1-106">*XML 軸屬性*讓您存取子節點、 子代節點和 XML 常值的屬性。</span><span class="sxs-lookup"><span data-stu-id="52eb1-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="52eb1-107">如需詳細資訊，請參閱[XML 常值概觀](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)和[存取 Visual Basic 中的 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="52eb1-107">For more information, see [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) and [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="52eb1-108">為記憶體中 XML 程式設計 API，專門設計來利用[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="52eb1-108"> is an in-memory XML programming API designed specifically to take advantage of [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)].</span></span> <span data-ttu-id="52eb1-109">雖然您可以呼叫[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]Api 直接，只[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可讓您宣告 XML 常值，並直接存取 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="52eb1-109">Although you can call the [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] APIs directly, only [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52eb1-110">在 ASP.NET 網頁中的宣告式程式碼中不支援 XML 常值和 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="52eb1-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="52eb1-111">若要使用 Visual Basic XML 功能，將程式碼放入 ASP.NET 應用程式中的程式碼後置頁面。</span><span class="sxs-lookup"><span data-stu-id="52eb1-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="52eb1-112">![視訊連結](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")相關的影片示範，請參閱[如何開始使用 LINQ to XML？](http://go.microsoft.com/fwlink/?LinkId=143034)和[如何建立 Excel 試算表使用 LINQ to XML？](http://go.microsoft.com/fwlink/?LinkId=143536)。</span><span class="sxs-lookup"><span data-stu-id="52eb1-112">![link to video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") For related video demonstrations, see [How Do I Get Started with LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143034) and [How Do I Create Excel Spreadsheets using LINQ to XML?](http://go.microsoft.com/fwlink/?LinkId=143536).</span></span>  
  
## <a name="creating-xml"></a><span data-ttu-id="52eb1-113">建立 XML</span><span class="sxs-lookup"><span data-stu-id="52eb1-113">Creating XML</span></span>  
 <span data-ttu-id="52eb1-114">有兩種方式建立 XML 樹狀結構中的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="52eb1-114">There are two ways to create XML trees in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="52eb1-115">您可以宣告 XML 常值直接在程式碼，或者您可以使用[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]Api 來建立樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="52eb1-115">You can declare an XML literal directly in code, or you can use the [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] APIs to create the tree.</span></span> <span data-ttu-id="52eb1-116">這兩個程序允許程式碼以反映最終結構的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="52eb1-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="52eb1-117">例如，下列程式碼範例會建立 XML 項目︰</span><span class="sxs-lookup"><span data-stu-id="52eb1-117">For example, the following code example creates an XML element:</span></span>  
  
 <span data-ttu-id="52eb1-118">[!code-vb[VbXmlSamples #&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="52eb1-118">[!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]</span></span>  
  
 <span data-ttu-id="52eb1-119">如需詳細資訊，請參閱[建立 Visual Basic 中的 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="52eb1-119">For more information, see [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="52eb1-120">存取和巡覽 XML</span><span class="sxs-lookup"><span data-stu-id="52eb1-120">Accessing and Navigating XML</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="52eb1-121">提供 XML 軸屬性存取及巡覽 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="52eb1-121"> provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="52eb1-122">這些屬性可讓您指定的 XML 子元素名稱來存取 XML 項目和屬性。</span><span class="sxs-lookup"><span data-stu-id="52eb1-122">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="52eb1-123">或者，您可以明確呼叫[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]瀏覽和尋找項目和屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="52eb1-123">Alternatively, you can explicitly call the [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="52eb1-124">例如，下列程式碼範例使用 XML 軸屬性來參考屬性和子項目的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="52eb1-124">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="52eb1-125">此程式碼範例會使用[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢來擷取子項目和其輸出為 XML 項目，有效地執行轉換。</span><span class="sxs-lookup"><span data-stu-id="52eb1-125">The code example uses a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 <span data-ttu-id="52eb1-126">[!code-vb[VbXmlSamples #&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="52eb1-126">[!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]</span></span>  
  
 <span data-ttu-id="52eb1-127">如需詳細資訊，請參閱[存取 Visual Basic 中的 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="52eb1-127">For more information, see [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="52eb1-128">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="52eb1-128">XML Namespaces</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="52eb1-129">可讓您藉由指定為全域的 XML 命名空間別名`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="52eb1-129"> enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="52eb1-130">下列範例示範如何使用`Imports`陳述式來匯入 XML 命名空間︰</span><span class="sxs-lookup"><span data-stu-id="52eb1-130">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 <span data-ttu-id="52eb1-131">[!code-vb[VbXMLSamples #&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="52eb1-131">[!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]</span></span>  
  
 <span data-ttu-id="52eb1-132">當您存取 XML 軸屬性，並宣告 XML 常值的 XML 文件和項目時，您可以使用 XML 命名空間別名。</span><span class="sxs-lookup"><span data-stu-id="52eb1-132">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="52eb1-133">您可以擷取<xref:System.Xml.Linq.XNamespace>物件使用的特定命名空間前置詞[GetXmlNamespace 運算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)。</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="52eb1-133">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="52eb1-134">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="52eb1-134">For more information, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="52eb1-135">使用 XML 常值中的 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="52eb1-135">Using XML Namespaces in XML Literals</span></span>  
 <span data-ttu-id="52eb1-136">下列範例示範如何建立<xref:System.Xml.Linq.XElement>物件，使用全域命名空間`ns`:</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="52eb1-136">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 <span data-ttu-id="52eb1-137">[!code-vb[VbXMLSamples #&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="52eb1-137">[!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]</span></span>  
  
 <span data-ttu-id="52eb1-138">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將轉譯的對等的程式碼中使用 XML 命名空間中，使用 XML 表示法中包含 XML 命名空間別名的 XML 常值`xmlns`屬性。</span><span class="sxs-lookup"><span data-stu-id="52eb1-138">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="52eb1-139">編譯時前, 一節的範例程式碼會產生基本上相同可執行的程式碼如下列範例︰</span><span class="sxs-lookup"><span data-stu-id="52eb1-139">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 <span data-ttu-id="52eb1-140">[!code-vb[VbXMLSamples #&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="52eb1-140">[!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]</span></span>  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="52eb1-141">XML 軸屬性中使用 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="52eb1-141">Using XML Namespaces in XML Axis Properties</span></span>  
 <span data-ttu-id="52eb1-142">宣告 XML 常值中的 XML 命名空間不適用於 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="52eb1-142">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="52eb1-143">不過，全域命名空間可以搭配 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="52eb1-143">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="52eb1-144">您可以使用冒號分隔開來的本機項目名稱的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="52eb1-144">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="52eb1-145">以下是一個範例：</span><span class="sxs-lookup"><span data-stu-id="52eb1-145">Following is an example:</span></span>  
  
 <span data-ttu-id="52eb1-146">[!code-vb[VbXMLSamples #&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="52eb1-146">[!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52eb1-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52eb1-147">See Also</span></span>  
 <span data-ttu-id="52eb1-148">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="52eb1-148">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="52eb1-149"> [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="52eb1-149"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="52eb1-150"> [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md) </span><span class="sxs-lookup"><span data-stu-id="52eb1-150"> [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md) </span></span>  
<span data-ttu-id="52eb1-151"> [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="52eb1-151"> [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)</span></span>
