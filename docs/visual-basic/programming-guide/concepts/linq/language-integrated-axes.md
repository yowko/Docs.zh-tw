---
title: Visual Basic 中已整合語言的軸心方法 (LINQ to XML)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d450a556-a134-4261-b011-44e399660894
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8360281d1d8de0cad243297cd78e97958530bae4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="39aaf-102">Visual Basic 中已整合語言的軸心方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="39aaf-102">Language-Integrated Axes in Visual Basic (LINQ to XML)</span></span>
<span data-ttu-id="39aaf-103">本節描述直接內建讓您輕鬆存取 XML Visual Basic 語言的功能。</span><span class="sxs-lookup"><span data-stu-id="39aaf-103">This section describes features built directly into the Visual Basic language to make it easy to access XML.</span></span> <span data-ttu-id="39aaf-104">許多 LINQ to XML 文件的範例都使用這些整合式的 Visual Basic 軸。</span><span class="sxs-lookup"><span data-stu-id="39aaf-104">Many of the examples in the LINQ to XML documentation use these integrated Visual Basic axes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="39aaf-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="39aaf-105">In This Section</span></span>  
  
|<span data-ttu-id="39aaf-106">主題</span><span class="sxs-lookup"><span data-stu-id="39aaf-106">Topic</span></span>|<span data-ttu-id="39aaf-107">描述</span><span class="sxs-lookup"><span data-stu-id="39aaf-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="39aaf-108">XML 子代軸屬性</span><span class="sxs-lookup"><span data-stu-id="39aaf-108">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="39aaf-109">提供下列任一項目之子系的存取：<xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件的集合，或是 <xref:System.Xml.Linq.XDocument> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="39aaf-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="39aaf-110">這個座標軸等同於 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="39aaf-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|  
|[<span data-ttu-id="39aaf-111">XML 子系軸屬性</span><span class="sxs-lookup"><span data-stu-id="39aaf-111">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="39aaf-112">提供下列任一項目之子系的存取：<xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="39aaf-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="39aaf-113">這個座標軸等同於 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="39aaf-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="39aaf-114">XML 屬性 (Attribute) 軸屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="39aaf-114">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="39aaf-115">提供 <xref:System.Xml.Linq.XElement> 物件之屬性的存取。</span><span class="sxs-lookup"><span data-stu-id="39aaf-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="39aaf-116">這個座標軸大致等同於 <xref:System.Xml.Linq.XElement.Attribute%2A> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="39aaf-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="39aaf-117">這個座標軸與 <xref:System.Xml.Linq.XElement.Attribute%2A> 座標軸不同之處在於，前者會傳回屬性的值，而非 <xref:System.Xml.Linq.XAttribute> 物件的值。</span><span class="sxs-lookup"><span data-stu-id="39aaf-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|  
|[<span data-ttu-id="39aaf-118">擴充索引子屬性</span><span class="sxs-lookup"><span data-stu-id="39aaf-118">Extension Indexer Property</span></span>](../../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="39aaf-119">提供集合中個別項目的存取。</span><span class="sxs-lookup"><span data-stu-id="39aaf-119">Provides access to individual elements in a collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39aaf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39aaf-120">See Also</span></span>  
 [<span data-ttu-id="39aaf-121">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39aaf-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
