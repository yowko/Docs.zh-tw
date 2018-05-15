---
title: 如何：存取 XML 子代項目 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 6d41844b540631df96740ce56818c125cf85e928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="a62cf-102">如何：存取 XML 子代項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a62cf-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="a62cf-103">這個範例示範如何使用子代 axis 屬性來存取所有的 XML 項目具有指定的名稱的資料，而且包含在 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="a62cf-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="a62cf-104">特別是，它會使用`Value`屬性集合中取得的第一個項目值`name`子代軸屬性傳回。</span><span class="sxs-lookup"><span data-stu-id="a62cf-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="a62cf-105">`name`子代 axis 屬性會取得名為的所有項目`name`包含在`contacts`物件。</span><span class="sxs-lookup"><span data-stu-id="a62cf-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="a62cf-106">此範例也會使用`phone`子代 axis 屬性來存取具名的所有下階`phone`包含在`contacts`物件。</span><span class="sxs-lookup"><span data-stu-id="a62cf-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a62cf-107">範例</span><span class="sxs-lookup"><span data-stu-id="a62cf-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a62cf-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a62cf-108">Compiling the Code</span></span>  
 <span data-ttu-id="a62cf-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="a62cf-109">This example requires:</span></span>  
  
-   <span data-ttu-id="a62cf-110"><xref:System.Xml.Linq> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="a62cf-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62cf-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a62cf-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a62cf-112">XML 子系軸屬性</span><span class="sxs-lookup"><span data-stu-id="a62cf-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [<span data-ttu-id="a62cf-113">XML Value 屬性</span><span class="sxs-lookup"><span data-stu-id="a62cf-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="a62cf-114">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="a62cf-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="a62cf-115">XML</span><span class="sxs-lookup"><span data-stu-id="a62cf-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
