---
title: HOW TO：存取 XML 子項目 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: cd1b0db5305c7879d89cfdfff6cd458d6dea14f4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836814"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="c35f6-102">HOW TO：存取 XML 子項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c35f6-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="c35f6-103">此範例會示範如何使用子系軸屬性，來存取所有的 XML 子項目中的 XML 項目具有指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="c35f6-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="c35f6-104">特別是，它會使用<xref:System.Xml.Linq.XElement.Value%2A>屬性的第一個項目值取得集合中`name`子軸屬性傳回。</span><span class="sxs-lookup"><span data-stu-id="c35f6-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="c35f6-105">`name`子軸屬性會取得所有子項目`phone`在`contact`物件。</span><span class="sxs-lookup"><span data-stu-id="c35f6-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="c35f6-106">此範例也會使用`phone`子軸屬性，來存取所有的子項目，名為`phone`包含在`contact`物件。</span><span class="sxs-lookup"><span data-stu-id="c35f6-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c35f6-107">範例</span><span class="sxs-lookup"><span data-stu-id="c35f6-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c35f6-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c35f6-108">Compiling the Code</span></span>  
 <span data-ttu-id="c35f6-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="c35f6-109">This example requires:</span></span>  
  
-   <span data-ttu-id="c35f6-110"><xref:System.Xml.Linq> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="c35f6-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c35f6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c35f6-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c35f6-112">XML 子代軸屬性</span><span class="sxs-lookup"><span data-stu-id="c35f6-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="c35f6-113">XML Value 屬性</span><span class="sxs-lookup"><span data-stu-id="c35f6-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="c35f6-114">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="c35f6-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="c35f6-115">XML</span><span class="sxs-lookup"><span data-stu-id="c35f6-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
