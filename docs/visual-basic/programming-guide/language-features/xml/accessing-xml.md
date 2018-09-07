---
title: 在 Visual Basic 中存取 XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 0540c52cf3e4cd7594f051c10832ea99cf58a34e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078891"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="866a1-102">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="866a1-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="866a1-103">Visual Basic 提供的 XML 軸屬性，用於存取和瀏覽[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]結構。</span><span class="sxs-lookup"><span data-stu-id="866a1-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="866a1-104">這些屬性會使用特殊的語法，可讓您指定的 XML 名稱來存取元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="866a1-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="866a1-105">下表列出的語言功能可讓您存取 XML 項目和 Visual Basic 中的屬性。</span><span class="sxs-lookup"><span data-stu-id="866a1-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="866a1-106">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="866a1-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="866a1-107">屬性描述</span><span class="sxs-lookup"><span data-stu-id="866a1-107">Property description</span></span>|<span data-ttu-id="866a1-108">範例</span><span class="sxs-lookup"><span data-stu-id="866a1-108">Example</span></span>|<span data-ttu-id="866a1-109">描述</span><span class="sxs-lookup"><span data-stu-id="866a1-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="866a1-110">*子軸*</span><span class="sxs-lookup"><span data-stu-id="866a1-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="866a1-111">取得所有`phone`子項目的項目`contact`項目。</span><span class="sxs-lookup"><span data-stu-id="866a1-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="866a1-112">*屬性軸*</span><span class="sxs-lookup"><span data-stu-id="866a1-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="866a1-113">取得所有`type`屬性的`phone`項目。</span><span class="sxs-lookup"><span data-stu-id="866a1-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="866a1-114">*descendant 軸*</span><span class="sxs-lookup"><span data-stu-id="866a1-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="866a1-115">取得所有`name`的項目`contacts`項目，不論發生的階層中深度。</span><span class="sxs-lookup"><span data-stu-id="866a1-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="866a1-116">*擴充索引子*</span><span class="sxs-lookup"><span data-stu-id="866a1-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="866a1-117">取得第一個`name`序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="866a1-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="866a1-118">*值*</span><span class="sxs-lookup"><span data-stu-id="866a1-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="866a1-119">取得第一個物件的字串表示，在順序中，或`Nothing`如果序列是空的。</span><span class="sxs-lookup"><span data-stu-id="866a1-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="866a1-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="866a1-120">In This Section</span></span>  
 [<span data-ttu-id="866a1-121">如何：存取 XML 子系項目</span><span class="sxs-lookup"><span data-stu-id="866a1-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="866a1-122">示範如何使用 descendant 軸屬性來存取所有的 XML 項目中具有指定的名稱，以及包含在指定的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="866a1-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="866a1-123">如何：存取 XML 子項目</span><span class="sxs-lookup"><span data-stu-id="866a1-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="866a1-124">示範如何使用子系軸屬性，來存取所有的 XML 子項目中的 XML 項目具有指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="866a1-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="866a1-125">如何：存取 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="866a1-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="866a1-126">示範如何使用屬性軸屬性，存取所有的 XML 屬性中的 XML 項目具有指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="866a1-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="866a1-127">如何：宣告和使用 XML 命名空間前置詞</span><span class="sxs-lookup"><span data-stu-id="866a1-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="866a1-128">示範如何宣告 XML 命名空間前置詞，並使用它來建立及存取 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="866a1-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="866a1-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="866a1-129">Related Sections</span></span>  
 [<span data-ttu-id="866a1-130">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="866a1-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="866a1-131">提供各節描述各種不同的 XML 存取內容的連結。</span><span class="sxs-lookup"><span data-stu-id="866a1-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="866a1-132">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="866a1-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="866a1-133">簡介如何使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="866a1-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="866a1-134">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="866a1-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="866a1-135">提供在 Visual Basic 中使用 XML 常值的簡介。</span><span class="sxs-lookup"><span data-stu-id="866a1-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="866a1-136">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="866a1-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="866a1-137">提供載入及修改 XML，在 Visual Basic 中的相關章節的連結。</span><span class="sxs-lookup"><span data-stu-id="866a1-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="866a1-138">XML</span><span class="sxs-lookup"><span data-stu-id="866a1-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="866a1-139">提供描述如何使用章節的連結[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="866a1-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
