---
title: "在 Visual Basic 中存取 XML"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79c7b8a94731e151a803a041d91dd1e240ddeb97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="7a436-102">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="7a436-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="7a436-103">XML 軸屬性提供用於存取和導覽[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]結構。</span><span class="sxs-lookup"><span data-stu-id="7a436-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="7a436-104">這些屬性會使用特殊的語法，可讓您指定的 XML 名稱來存取項目和屬性。</span><span class="sxs-lookup"><span data-stu-id="7a436-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="7a436-105">下表列出可讓您存取 XML 元素和屬性中的語言功能[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7a436-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="7a436-106">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="7a436-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="7a436-107">屬性描述</span><span class="sxs-lookup"><span data-stu-id="7a436-107">Property description</span></span>|<span data-ttu-id="7a436-108">範例</span><span class="sxs-lookup"><span data-stu-id="7a436-108">Example</span></span>|<span data-ttu-id="7a436-109">說明</span><span class="sxs-lookup"><span data-stu-id="7a436-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="7a436-110">*子軸*</span><span class="sxs-lookup"><span data-stu-id="7a436-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="7a436-111">取得所有`phone`子項目數的項目`contact`項目。</span><span class="sxs-lookup"><span data-stu-id="7a436-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="7a436-112">*屬性軸*</span><span class="sxs-lookup"><span data-stu-id="7a436-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="7a436-113">取得所有`type`屬性`phone`項目。</span><span class="sxs-lookup"><span data-stu-id="7a436-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="7a436-114">*descendant 軸*</span><span class="sxs-lookup"><span data-stu-id="7a436-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="7a436-115">取得所有`name`的項目`contacts`項目，不論它們出現在階層中深度。</span><span class="sxs-lookup"><span data-stu-id="7a436-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="7a436-116">*擴充索引子*</span><span class="sxs-lookup"><span data-stu-id="7a436-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="7a436-117">取得第一個`name`序列中的項目。</span><span class="sxs-lookup"><span data-stu-id="7a436-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="7a436-118">*value*</span><span class="sxs-lookup"><span data-stu-id="7a436-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="7a436-119">取得第一個物件的字串表示，依序或`Nothing`如果序列是空的。</span><span class="sxs-lookup"><span data-stu-id="7a436-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="7a436-120">本章節內容</span><span class="sxs-lookup"><span data-stu-id="7a436-120">In This Section</span></span>  
 [<span data-ttu-id="7a436-121">如何：存取 XML 子系項目</span><span class="sxs-lookup"><span data-stu-id="7a436-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="7a436-122">示範如何使用子代 axis 屬性來存取所有的 XML 項目具有指定的名稱的資料，而且包含在指定的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="7a436-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="7a436-123">如何：存取 XML 子項目</span><span class="sxs-lookup"><span data-stu-id="7a436-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="7a436-124">示範如何使用子軸屬性，來存取所有的 XML 項目具有指定的名稱的 XML 子項目。</span><span class="sxs-lookup"><span data-stu-id="7a436-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="7a436-125">如何：存取 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="7a436-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="7a436-126">示範如何使用屬性軸屬性，存取所有的 XML 項目具有指定的名稱的 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="7a436-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="7a436-127">如何：宣告和使用 XML 命名空間前置詞</span><span class="sxs-lookup"><span data-stu-id="7a436-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="7a436-128">示範如何宣告 XML 命名空間前置詞，並用來建立及存取 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="7a436-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7a436-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="7a436-129">Related Sections</span></span>  
 [<span data-ttu-id="7a436-130">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="7a436-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="7a436-131">提供描述各種 XML 存取屬性章節的連結。</span><span class="sxs-lookup"><span data-stu-id="7a436-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="7a436-132">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="7a436-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="7a436-133">提供簡介使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="7a436-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="7a436-134">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="7a436-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="7a436-135">提供 Visual Basic 中使用 XML 常值的簡介。</span><span class="sxs-lookup"><span data-stu-id="7a436-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="7a436-136">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="7a436-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="7a436-137">提供有關載入及修改 XML，在 Visual Basic 中的章節連結。</span><span class="sxs-lookup"><span data-stu-id="7a436-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="7a436-138">XML</span><span class="sxs-lookup"><span data-stu-id="7a436-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="7a436-139">提供描述如何使用連結[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="7a436-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
