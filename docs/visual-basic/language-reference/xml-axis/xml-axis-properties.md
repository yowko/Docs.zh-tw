---
title: "XML 軸屬性 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML axis properties [Visual Basic]
- Visual Basic code, XML
- XML axis [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 7e400e20-5d1e-4d22-a65c-9df79d5c1621
caps.latest.revision: 9
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
ms.openlocfilehash: 4dd15670eed316552f2f02e4536122a6a110542d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xml-axis-properties-visual-basic"></a><span data-ttu-id="fc17c-102">XML 軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc17c-102">XML Axis Properties (Visual Basic)</span></span>
<span data-ttu-id="fc17c-103">本節主題文件中的 XML 軸屬性的語法[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fc17c-103">The topics in this section document the syntax of XML axis properties in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="fc17c-104">XML 軸屬性讓您輕鬆地直接在您的程式碼中存取 XML。</span><span class="sxs-lookup"><span data-stu-id="fc17c-104">The XML axis properties make it easy to access XML directly in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc17c-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="fc17c-105">In This Section</span></span>  
  
|<span data-ttu-id="fc17c-106">主題</span><span class="sxs-lookup"><span data-stu-id="fc17c-106">Topic</span></span>|<span data-ttu-id="fc17c-107">描述</span><span class="sxs-lookup"><span data-stu-id="fc17c-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="fc17c-108">XML 屬性 (Attribute) 軸屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="fc17c-108">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="fc17c-109">說明如何存取的屬性<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="fc17c-109">Describes how to access the attributes of an <xref:System.Xml.Linq.XElement> object.</span></span>|  
|[<span data-ttu-id="fc17c-110">XML 子代軸屬性</span><span class="sxs-lookup"><span data-stu-id="fc17c-110">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="fc17c-111">說明如何存取的子系<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="fc17c-111">Describes how to access the children of an <xref:System.Xml.Linq.XElement> object.</span></span>|  
|[<span data-ttu-id="fc17c-112">XML 子系軸屬性</span><span class="sxs-lookup"><span data-stu-id="fc17c-112">XML Descendant Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="fc17c-113">說明如何存取的下階<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="fc17c-113">Describes how to access the descendants of an <xref:System.Xml.Linq.XElement> object.</span></span>|  
|[<span data-ttu-id="fc17c-114">擴充索引子屬性</span><span class="sxs-lookup"><span data-stu-id="fc17c-114">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="fc17c-115">說明如何存取集合中的個別項目<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="fc17c-115">Describes how to access individual elements in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects.</span></span>|  
|[<span data-ttu-id="fc17c-116">XML Value 屬性</span><span class="sxs-lookup"><span data-stu-id="fc17c-116">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)|<span data-ttu-id="fc17c-117">描述如何存取一系列的第一個元素的值<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="fc17c-117">Describes how to access the value of the first element of a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc17c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc17c-118">See Also</span></span>  
 [<span data-ttu-id="fc17c-119">XML</span><span class="sxs-lookup"><span data-stu-id="fc17c-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
