---
title: 存取 XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 282b7d91ec7cfe2f587c67bc9a982f0da22ad925
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410305"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="2d8c8-102">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="2d8c8-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="2d8c8-103">Visual Basic 提供用於存取和流覽結構的 XML 軸屬性 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="2d8c8-104">這些屬性會使用特殊語法，讓您藉由指定 XML 名稱來存取元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="2d8c8-105">下表列出的語言功能可讓您存取 Visual Basic 中的 XML 元素和屬性。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="2d8c8-106">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="2d8c8-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="2d8c8-107">屬性描述</span><span class="sxs-lookup"><span data-stu-id="2d8c8-107">Property description</span></span>|<span data-ttu-id="2d8c8-108">範例</span><span class="sxs-lookup"><span data-stu-id="2d8c8-108">Example</span></span>|<span data-ttu-id="2d8c8-109">描述</span><span class="sxs-lookup"><span data-stu-id="2d8c8-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="2d8c8-110">*子軸*</span><span class="sxs-lookup"><span data-stu-id="2d8c8-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="2d8c8-111">取得專案 `phone` 之子專案的所有元素 `contact` 。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="2d8c8-112">*attribute 軸*</span><span class="sxs-lookup"><span data-stu-id="2d8c8-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="2d8c8-113">取得元素的所有 `type` 屬性 `phone` 。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="2d8c8-114">*下階座標軸*</span><span class="sxs-lookup"><span data-stu-id="2d8c8-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="2d8c8-115">取得專案 `name` 的所有專案 `contacts` ，不論其出現在階層中的深度為何。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="2d8c8-116">*延伸模組索引子*</span><span class="sxs-lookup"><span data-stu-id="2d8c8-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="2d8c8-117">取得序列中的第一個 `name` 元素。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="2d8c8-118">*值*</span><span class="sxs-lookup"><span data-stu-id="2d8c8-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="2d8c8-119">取得序列中第一個物件的字串表示， `Nothing` 如果序列是空的，則為。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="2d8c8-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="2d8c8-120">In This Section</span></span>  
 [<span data-ttu-id="2d8c8-121">如何：存取 XML 子系項目</span><span class="sxs-lookup"><span data-stu-id="2d8c8-121">How to: Access XML Descendant Elements</span></span>](how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="2d8c8-122">示範如何使用子代軸屬性來存取所有具有指定名稱且包含在指定之 XML 專案底下的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="2d8c8-123">如何：存取 XML 子項目</span><span class="sxs-lookup"><span data-stu-id="2d8c8-123">How to: Access XML Child Elements</span></span>](how-to-access-xml-child-elements.md)  
 <span data-ttu-id="2d8c8-124">示範如何使用子軸屬性來存取 XML 元素中所有具有指定名稱的 XML 子專案。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="2d8c8-125">如何：存取 XML 屬性</span><span class="sxs-lookup"><span data-stu-id="2d8c8-125">How to: Access XML Attributes</span></span>](how-to-access-xml-attributes.md)  
 <span data-ttu-id="2d8c8-126">示範如何使用屬性軸屬性來存取 XML 元素中所有具有指定名稱的 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="2d8c8-127">如何：宣告和使用 XML 命名空間前置字元</span><span class="sxs-lookup"><span data-stu-id="2d8c8-127">How to: Declare and Use XML Namespace Prefixes</span></span>](how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="2d8c8-128">示範如何宣告 XML 命名空間前置詞，並使用它來建立和存取 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2d8c8-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="2d8c8-129">Related Sections</span></span>  
 [<span data-ttu-id="2d8c8-130">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="2d8c8-130">XML Axis Properties</span></span>](../../../language-reference/xml-axis/index.md)  
 <span data-ttu-id="2d8c8-131">提供描述各種 XML 存取屬性之區段的連結。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="2d8c8-132">Visual Basic 中的 LINQ to XML 概觀</span><span class="sxs-lookup"><span data-stu-id="2d8c8-132">Overview of LINQ to XML in Visual Basic</span></span>](overview-of-linq-to-xml.md)  
 <span data-ttu-id="2d8c8-133">提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 在 Visual Basic 中使用的簡介。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="2d8c8-134">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="2d8c8-134">Creating XML in Visual Basic</span></span>](creating-xml.md)  
 <span data-ttu-id="2d8c8-135">提供在 Visual Basic 中使用 XML 常值的簡介。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="2d8c8-136">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="2d8c8-136">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)  
 <span data-ttu-id="2d8c8-137">提供有關在 Visual Basic 中載入和修改 XML 的章節連結。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="2d8c8-138">XML</span><span class="sxs-lookup"><span data-stu-id="2d8c8-138">XML</span></span>](index.md)  
 <span data-ttu-id="2d8c8-139">提供章節的連結，說明如何 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 在 Visual Basic 中使用。</span><span class="sxs-lookup"><span data-stu-id="2d8c8-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
