---
title: 如何：存取 XML 子代項目
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 03c403aa3c187b0b9d2006104eccaa1f9cd8aec5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392632"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="76830-102">如何：存取 XML 子代項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76830-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="76830-103">這個範例示範如何使用子代軸屬性來存取所有具有指定名稱且包含在 XML 專案底下的 XML 專案。</span><span class="sxs-lookup"><span data-stu-id="76830-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="76830-104">特別是，它會使用 `Value` 屬性來取得子代 axis 屬性傳回之集合中第一個元素的值 `name` 。</span><span class="sxs-lookup"><span data-stu-id="76830-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="76830-105">[下階 `name` 軸] 屬性會取得 `name` 包含在物件中名為的所有元素 `contacts` 。</span><span class="sxs-lookup"><span data-stu-id="76830-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="76830-106">這個範例也會使用 [下階 `phone` 軸] 屬性來存取 `phone` 包含在物件中名為的所有子系 `contacts` 。</span><span class="sxs-lookup"><span data-stu-id="76830-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76830-107">範例</span><span class="sxs-lookup"><span data-stu-id="76830-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="76830-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="76830-108">Compile the code</span></span>  
 <span data-ttu-id="76830-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="76830-109">This example requires:</span></span>  
  
- <span data-ttu-id="76830-110"><xref:System.Xml.Linq> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="76830-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76830-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76830-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="76830-112">XML Descendant Axis Property</span><span class="sxs-lookup"><span data-stu-id="76830-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="76830-113">XML 值屬性</span><span class="sxs-lookup"><span data-stu-id="76830-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="76830-114">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="76830-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="76830-115">XML</span><span class="sxs-lookup"><span data-stu-id="76830-115">XML</span></span>](index.md)
