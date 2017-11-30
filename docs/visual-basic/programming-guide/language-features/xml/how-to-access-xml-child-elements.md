---
title: "如何：存取 XML 子項目 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d3a708b787ad38f08d4673d4003db839f6cf6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="5fdae-102">如何：存取 XML 子項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fdae-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="5fdae-103">這個範例會示範如何使用子軸屬性，來存取所有的 XML 項目具有指定的名稱的 XML 子項目。</span><span class="sxs-lookup"><span data-stu-id="5fdae-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="5fdae-104">特別是，它會使用<xref:System.Xml.Linq.XElement.Value%2A>屬性集合中取得的第一個項目值`name`子軸屬性傳回。</span><span class="sxs-lookup"><span data-stu-id="5fdae-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="5fdae-105">`name`子軸屬性會取得名為的所有子項目`phone`中`contact`物件。</span><span class="sxs-lookup"><span data-stu-id="5fdae-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="5fdae-106">此範例也會使用`phone`子軸屬性，來存取具名的所有子項目`phone`包含在`contact`物件。</span><span class="sxs-lookup"><span data-stu-id="5fdae-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fdae-107">範例</span><span class="sxs-lookup"><span data-stu-id="5fdae-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5fdae-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5fdae-108">Compiling the Code</span></span>  
 <span data-ttu-id="5fdae-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="5fdae-109">This example requires:</span></span>  
  
-   <span data-ttu-id="5fdae-110"><xref:System.Xml.Linq> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="5fdae-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdae-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fdae-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5fdae-112">XML 子代軸屬性</span><span class="sxs-lookup"><span data-stu-id="5fdae-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="5fdae-113">XML Value 屬性</span><span class="sxs-lookup"><span data-stu-id="5fdae-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="5fdae-114">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="5fdae-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="5fdae-115">XML</span><span class="sxs-lookup"><span data-stu-id="5fdae-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
