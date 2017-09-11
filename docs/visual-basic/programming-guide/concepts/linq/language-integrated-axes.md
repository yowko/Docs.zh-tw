---
title: "在 Visual Basic (LINQ to XML) 的語言整合式座標軸 |Microsoft 文件"
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
ms.assetid: d450a556-a134-4261-b011-44e399660894
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7ca88aed0772f4fb93ab561af4bd9a1129cbf3c5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="bb10f-102">Visual Basic 中已整合語言的軸心方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bb10f-102">Language-Integrated Axes in Visual Basic (LINQ to XML)</span></span>
<span data-ttu-id="bb10f-103">本節描述直接內建功能[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]以方便存取 XML 語言。</span><span class="sxs-lookup"><span data-stu-id="bb10f-103">This section describes features built directly into the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] language to make it easy to access XML.</span></span> <span data-ttu-id="bb10f-104">LINQ to XML 文件中的許多範例都使用這些整合式 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 座標軸。</span><span class="sxs-lookup"><span data-stu-id="bb10f-104">Many of the examples in the LINQ to XML documentation use these integrated [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] axes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb10f-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="bb10f-105">In This Section</span></span>  
  
|<span data-ttu-id="bb10f-106">主題</span><span class="sxs-lookup"><span data-stu-id="bb10f-106">Topic</span></span>|<span data-ttu-id="bb10f-107">說明</span><span class="sxs-lookup"><span data-stu-id="bb10f-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="bb10f-108">XML 子代軸屬性</span><span class="sxs-lookup"><span data-stu-id="bb10f-108">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="bb10f-109">提供存取的下列其中一項目子系︰<xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或一系列<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="bb10f-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="bb10f-110">這個座標軸等同於<xref:System.Xml.Linq.XContainer.Elements%2A>軸。</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="bb10f-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|  
|[<span data-ttu-id="bb10f-111">XML 子系軸屬性</span><span class="sxs-lookup"><span data-stu-id="bb10f-111">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="bb10f-112">可讓您存取下列的下階︰<xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件或一系列<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="bb10f-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bb10f-113">這個座標軸等同於<xref:System.Xml.Linq.XContainer.Descendants%2A>軸。</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="bb10f-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="bb10f-114">XML 屬性 (Attribute) 軸屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="bb10f-114">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="bb10f-115">提供的屬性存取<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="bb10f-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="bb10f-116">這個座標軸大約會等於<xref:System.Xml.Linq.XElement.Attribute%2A>軸。</xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="bb10f-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="bb10f-117">這個座標軸與<xref:System.Xml.Linq.XElement.Attribute%2A>它不會傳回屬性的值中軸<xref:System.Xml.Linq.XAttribute>物件。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="bb10f-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|  
|[<span data-ttu-id="bb10f-118">擴充索引子屬性</span><span class="sxs-lookup"><span data-stu-id="bb10f-118">Extension Indexer Property</span></span>](../../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="bb10f-119">提供集合中個別項目的存取。</span><span class="sxs-lookup"><span data-stu-id="bb10f-119">Provides access to individual elements in a collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb10f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb10f-120">See Also</span></span>  
 [<span data-ttu-id="bb10f-121">LINQ to XML 軸心方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb10f-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
