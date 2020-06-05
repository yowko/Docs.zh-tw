---
title: 如何：存取 XML 子項目
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392814"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="e7183-102">如何：存取 XML 子項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7183-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="e7183-103">這個範例示範如何使用子軸屬性來存取 XML 元素中具有指定名稱的所有 XML 子專案。</span><span class="sxs-lookup"><span data-stu-id="e7183-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="e7183-104">特別是，它會使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來取得子 axis 屬性傳回之集合中第一個元素的值 `name` 。</span><span class="sxs-lookup"><span data-stu-id="e7183-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="e7183-105">[ `name` 子軸] 屬性會取得物件中名為的所有子項目 `phone` `contact` 。</span><span class="sxs-lookup"><span data-stu-id="e7183-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="e7183-106">這個範例也會使用 [ `phone` 子軸] 屬性來存取 `phone` 包含在物件中名為的所有子項目 `contact` 。</span><span class="sxs-lookup"><span data-stu-id="e7183-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7183-107">範例</span><span class="sxs-lookup"><span data-stu-id="e7183-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="e7183-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e7183-108">Compile the code</span></span>  
 <span data-ttu-id="e7183-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e7183-109">This example requires:</span></span>  
  
- <span data-ttu-id="e7183-110"><xref:System.Xml.Linq> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="e7183-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7183-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7183-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e7183-112">XML Child Axis Property</span><span class="sxs-lookup"><span data-stu-id="e7183-112">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="e7183-113">XML 值屬性</span><span class="sxs-lookup"><span data-stu-id="e7183-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="e7183-114">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="e7183-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="e7183-115">XML</span><span class="sxs-lookup"><span data-stu-id="e7183-115">XML</span></span>](index.md)
