---
title: 如何：存取 XML 子代項目
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347162"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="bab16-102">如何：存取 XML 子代項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bab16-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="bab16-103">這個範例示範如何使用子代軸屬性來存取所有具有指定名稱且包含在 XML 專案底下的 XML 專案。</span><span class="sxs-lookup"><span data-stu-id="bab16-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="bab16-104">特別是，它會使用 `Value` 屬性，取得集合中 `name` 下階軸屬性傳回的第一個元素的值。</span><span class="sxs-lookup"><span data-stu-id="bab16-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="bab16-105">[`name` 下階軸] 屬性會取得包含在 `contacts` 物件中名為 `name` 的所有元素。</span><span class="sxs-lookup"><span data-stu-id="bab16-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="bab16-106">這個範例也會使用 `phone` 子代軸屬性來存取包含在 `contacts` 物件中名為 `phone` 的所有子系。</span><span class="sxs-lookup"><span data-stu-id="bab16-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bab16-107">範例</span><span class="sxs-lookup"><span data-stu-id="bab16-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="bab16-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bab16-108">Compile the code</span></span>  
 <span data-ttu-id="bab16-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="bab16-109">This example requires:</span></span>  
  
- <span data-ttu-id="bab16-110"><xref:System.Xml.Linq> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="bab16-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab16-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="bab16-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bab16-112">XML 子系軸屬性</span><span class="sxs-lookup"><span data-stu-id="bab16-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="bab16-113">XML Value 屬性</span><span class="sxs-lookup"><span data-stu-id="bab16-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="bab16-114">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="bab16-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="bab16-115">XML</span><span class="sxs-lookup"><span data-stu-id="bab16-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
