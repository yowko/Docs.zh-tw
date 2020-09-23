---
title: LINQ to XML 概觀
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 4ec1c96bdca96a6e9b68b240c147b70536514d85
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91099186"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="547d9-102">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="547d9-102">Overview of LINQ to XML in Visual Basic</span></span>

<span data-ttu-id="547d9-103">Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 透過 xml 常值和 xml 軸屬性提供支援。</span><span class="sxs-lookup"><span data-stu-id="547d9-103">Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="547d9-104">這可讓您使用熟悉且方便的語法，在 Visual Basic 程式碼中使用 XML。</span><span class="sxs-lookup"><span data-stu-id="547d9-104">This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code.</span></span> <span data-ttu-id="547d9-105">*Xml 常* 值可讓您直接在程式碼中包含 xml。</span><span class="sxs-lookup"><span data-stu-id="547d9-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="547d9-106">*Xml 軸屬性* 可讓您存取子節點、子系節點，以及 xml 常值的屬性。</span><span class="sxs-lookup"><span data-stu-id="547d9-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="547d9-107">如需詳細資訊，請參閱 [Xml 常值總覽](xml-literals-overview.md) 和 [存取 VISUAL BASIC 中的 xml](accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="547d9-107">For more information, see [XML Literals Overview](xml-literals-overview.md) and [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="547d9-108">是記憶體中的 XML 程式設計 API，專為利用 (LINQ) 的語言整合式查詢所設計。</span><span class="sxs-lookup"><span data-stu-id="547d9-108">is an in-memory XML programming API designed specifically to take advantage of Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="547d9-109">雖然您可以直接呼叫 LINQ Api，但只有 Visual Basic 可讓您宣告 XML 常值，並直接存取 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="547d9-109">Although you can call the LINQ APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="547d9-110">ASP.NET 網頁中的宣告式程式碼不支援 XML 常值和 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="547d9-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="547d9-111">若要使用 Visual Basic XML 功能，請將您的程式碼放在 ASP.NET 應用程式的程式碼後置頁面中。</span><span class="sxs-lookup"><span data-stu-id="547d9-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="547d9-112">[[播放] 按鈕](./media/overview-of-linq-to-xml/play-video-icon-example.gif)如需相關的影片示範，請參閱[如何使用 LINQ to XML 開始？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)以及[如何使用 LINQ to XML 建立 Excel 試算表？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)。</span><span class="sxs-lookup"><span data-stu-id="547d9-112">[Play button](./media/overview-of-linq-to-xml/play-video-icon-example.gif) For related video demonstrations, see [How Do I Get Started with LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) and [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span></span>
  
## <a name="creating-xml"></a><span data-ttu-id="547d9-113">建立 XML</span><span class="sxs-lookup"><span data-stu-id="547d9-113">Creating XML</span></span>  

 <span data-ttu-id="547d9-114">有兩種方式可以在 Visual Basic 中建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="547d9-114">There are two ways to create XML trees in Visual Basic.</span></span> <span data-ttu-id="547d9-115">您可以直接在程式碼中宣告 XML 常值，也可以使用 LINQ Api 來建立樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="547d9-115">You can declare an XML literal directly in code, or you can use the LINQ APIs to create the tree.</span></span> <span data-ttu-id="547d9-116">這兩個進程都可讓程式碼反映 XML 樹狀結構的最終結構。</span><span class="sxs-lookup"><span data-stu-id="547d9-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="547d9-117">例如，下列程式碼範例會建立 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="547d9-117">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 <span data-ttu-id="547d9-118">如需詳細資訊，請參閱 [在 Visual Basic 中建立 XML](creating-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="547d9-118">For more information, see [Creating XML in Visual Basic](creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="547d9-119">存取和流覽 XML</span><span class="sxs-lookup"><span data-stu-id="547d9-119">Accessing and Navigating XML</span></span>  

 <span data-ttu-id="547d9-120">Visual Basic 提供 XML 軸屬性來存取和流覽 XML 結構。</span><span class="sxs-lookup"><span data-stu-id="547d9-120">Visual Basic provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="547d9-121">這些屬性可讓您藉由指定 XML 子項目名稱，來存取 XML 專案和屬性。</span><span class="sxs-lookup"><span data-stu-id="547d9-121">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="547d9-122">或者，您也可以明確地呼叫 LINQ 方法，以流覽和尋找元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="547d9-122">Alternatively, you can explicitly call the LINQ methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="547d9-123">例如，下列程式碼範例會使用 XML 軸屬性來參考 XML 專案的屬性和子項目。</span><span class="sxs-lookup"><span data-stu-id="547d9-123">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="547d9-124">程式碼範例會使用 LINQ 查詢來取出子專案，並將它們輸出為 XML 專案，以有效地執行轉換。</span><span class="sxs-lookup"><span data-stu-id="547d9-124">The code example uses a LINQ query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 <span data-ttu-id="547d9-125">如需詳細資訊，請參閱 [存取 Visual Basic 中的 XML](accessing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="547d9-125">For more information, see [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="547d9-126">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="547d9-126">XML Namespaces</span></span>  

 <span data-ttu-id="547d9-127">Visual Basic 可讓您使用語句來指定全域 XML 命名空間的別名 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="547d9-127">Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="547d9-128">下列範例顯示如何使用 `Imports` 語句匯入 XML 命名空間：</span><span class="sxs-lookup"><span data-stu-id="547d9-128">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 <span data-ttu-id="547d9-129">當您存取 XML 軸屬性，並宣告 xml 檔和元素的 XML 常值時，您可以使用 XML 命名空間別名。</span><span class="sxs-lookup"><span data-stu-id="547d9-129">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="547d9-130">您可以 <xref:System.Xml.Linq.XNamespace> 使用 [GetXmlNamespace 運算子](../../../language-reference/operators/getxmlnamespace-operator.md)，來取得特定命名空間前置詞的物件。</span><span class="sxs-lookup"><span data-stu-id="547d9-130">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="547d9-131">如需詳細資訊，請參閱 [ (XML 命名空間) 的 Imports 語句 ](../../../language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="547d9-131">For more information, see [Imports Statement (XML Namespace)](../../../language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="547d9-132">使用 xml 常值中的 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="547d9-132">Using XML Namespaces in XML Literals</span></span>  

 <span data-ttu-id="547d9-133">下列範例顯示如何建立 <xref:System.Xml.Linq.XElement> 使用全域命名空間的物件 `ns` ：</span><span class="sxs-lookup"><span data-stu-id="547d9-133">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 <span data-ttu-id="547d9-134">Visual Basic 編譯器會將包含 XML 命名空間別名的 XML 常值轉譯為對等的程式碼，該程式碼使用 xml 標記法搭配屬性來使用 xml 命名空間 `xmlns` 。</span><span class="sxs-lookup"><span data-stu-id="547d9-134">The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="547d9-135">編譯時，上一節範例中的程式碼基本上會產生與下列範例相同的可執行程式碼：</span><span class="sxs-lookup"><span data-stu-id="547d9-135">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="547d9-136">在 XML 軸屬性中使用 XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="547d9-136">Using XML Namespaces in XML Axis Properties</span></span>  

 <span data-ttu-id="547d9-137">Xml 常值中宣告的 XML 命名空間不能用於 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="547d9-137">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="547d9-138">不過，全域命名空間可以與 XML 軸屬性搭配使用。</span><span class="sxs-lookup"><span data-stu-id="547d9-138">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="547d9-139">使用冒號來分隔 XML 命名空間前置詞與本機專案名稱。</span><span class="sxs-lookup"><span data-stu-id="547d9-139">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="547d9-140">以下是範例：</span><span class="sxs-lookup"><span data-stu-id="547d9-140">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="547d9-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="547d9-141">See also</span></span>

- [<span data-ttu-id="547d9-142">XML</span><span class="sxs-lookup"><span data-stu-id="547d9-142">XML</span></span>](index.md)
- [<span data-ttu-id="547d9-143">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="547d9-143">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="547d9-144">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="547d9-144">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="547d9-145">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="547d9-145">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
