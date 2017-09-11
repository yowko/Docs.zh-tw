---
title: "在 Visual Basic 中存取 XML |Microsoft 文件"
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
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
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
ms.openlocfilehash: fe096d3686adc2386235944b59b51fb7442dd096
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="af80c-102">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="af80c-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="af80c-103">XML 軸屬性提供用於存取和瀏覽[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]結構。</span><span class="sxs-lookup"><span data-stu-id="af80c-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] structures.</span></span> <span data-ttu-id="af80c-104">這些屬性會使用特殊語法，可讓您指定的 XML 名稱來存取項目和屬性。</span><span class="sxs-lookup"><span data-stu-id="af80c-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="af80c-105">下表列出的語言功能，可讓您存取中 XML 元素和屬性[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="af80c-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="af80c-106">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="af80c-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="af80c-107">屬性描述</span><span class="sxs-lookup"><span data-stu-id="af80c-107">Property description</span></span>|<span data-ttu-id="af80c-108">範例</span><span class="sxs-lookup"><span data-stu-id="af80c-108">Example</span></span>|<span data-ttu-id="af80c-109">描述</span><span class="sxs-lookup"><span data-stu-id="af80c-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="af80c-110">*子軸*</span><span class="sxs-lookup"><span data-stu-id="af80c-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="af80c-111">取得所有`phone`子項目的項目`contact`項目。</span><span class="sxs-lookup"><span data-stu-id="af80c-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="af80c-112">*屬性軸*</span><span class="sxs-lookup"><span data-stu-id="af80c-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="af80c-113">取得所有`type`屬性`phone`項目。</span><span class="sxs-lookup"><span data-stu-id="af80c-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="af80c-114">*descendant 軸*</span><span class="sxs-lookup"><span data-stu-id="af80c-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="af80c-115">取得所有`name`的項目`contacts`項目，不論它們發生在階層中深度。</span><span class="sxs-lookup"><span data-stu-id="af80c-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="af80c-116">*擴充索引子*</span><span class="sxs-lookup"><span data-stu-id="af80c-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="af80c-117">取得第一個`name`序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="af80c-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="af80c-118">*value*</span><span class="sxs-lookup"><span data-stu-id="af80c-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="af80c-119">取得第一個物件的字串表示的序列中，或`Nothing`如果序列是空的。</span><span class="sxs-lookup"><span data-stu-id="af80c-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="af80c-120">本章節內容</span><span class="sxs-lookup"><span data-stu-id="af80c-120">In This Section</span></span>  
 [<span data-ttu-id="af80c-121">如何：存取 XML 子系項目</span><span class="sxs-lookup"><span data-stu-id="af80c-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="af80c-122">示範如何使用子代軸屬性來存取所有的 XML 項目具有指定的名稱，而且包含在指定的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="af80c-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="af80c-123">如何：存取 XML 子項目</span><span class="sxs-lookup"><span data-stu-id="af80c-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="af80c-124">示範如何使用子項 axis 屬性來存取 XML 項目中具有指定的名稱的所有 XML 子項目。</span><span class="sxs-lookup"><span data-stu-id="af80c-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="af80c-125">如何：存取 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="af80c-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="af80c-126">示範如何使用屬性軸屬性來存取 XML 項目中具有指定的名稱的所有 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="af80c-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="af80c-127">如何：宣告和使用 XML 命名空間前置詞</span><span class="sxs-lookup"><span data-stu-id="af80c-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="af80c-128">示範如何宣告 XML 命名空間前置詞，並使用它來建立及存取 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="af80c-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="af80c-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="af80c-129">Related Sections</span></span>  
 [<span data-ttu-id="af80c-130">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="af80c-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="af80c-131">提供各節描述各種 XML 存取內容的連結。</span><span class="sxs-lookup"><span data-stu-id="af80c-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="af80c-132">LINQ to XML 在 Visual Basic 中的概觀</span><span class="sxs-lookup"><span data-stu-id="af80c-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="af80c-133">介紹使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="af80c-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="af80c-134">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="af80c-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="af80c-135">介紹 Visual Basic 中使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="af80c-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="af80c-136">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="af80c-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="af80c-137">提供有關載入和修改在 Visual Basic 中的 XML 的章節連結。</span><span class="sxs-lookup"><span data-stu-id="af80c-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="af80c-138">XML</span><span class="sxs-lookup"><span data-stu-id="af80c-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="af80c-139">提供描述如何使用連結[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="af80c-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] in Visual Basic.</span></span>
