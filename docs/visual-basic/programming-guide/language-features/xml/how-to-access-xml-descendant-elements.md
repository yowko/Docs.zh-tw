---
title: 如何：存取 XML 子代項目
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: dcbaf1f9022d86f40a90ef6a1e0033f627caeef2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058205"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="6e23f-102">如何：存取 XML 子代項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e23f-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>

<span data-ttu-id="6e23f-103">這個範例示範如何使用子代軸屬性來存取所有具有指定名稱的 XML 專案，以及包含在 XML 元素底下的所有專案。</span><span class="sxs-lookup"><span data-stu-id="6e23f-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="6e23f-104">尤其是，它會使用 `Value` 屬性來取得下階軸屬性傳回之集合中第一個元素的值 `name` 。</span><span class="sxs-lookup"><span data-stu-id="6e23f-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="6e23f-105">[下階 `name` 軸] 屬性會取得 `name` 物件中包含的所有名為的元素 `contacts` 。</span><span class="sxs-lookup"><span data-stu-id="6e23f-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="6e23f-106">這個範例也會使用 [下階 `phone` 軸] 屬性來存取物件中所包含的所有子系 `phone` ，並命名為 `contacts` 。</span><span class="sxs-lookup"><span data-stu-id="6e23f-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e23f-107">範例</span><span class="sxs-lookup"><span data-stu-id="6e23f-107">Example</span></span>  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="6e23f-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6e23f-108">Compile the code</span></span>  

 <span data-ttu-id="6e23f-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6e23f-109">This example requires:</span></span>  
  
- <span data-ttu-id="6e23f-110"><xref:System.Xml.Linq> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="6e23f-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e23f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e23f-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6e23f-112">XML Descendant Axis Property</span><span class="sxs-lookup"><span data-stu-id="6e23f-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="6e23f-113">XML 值屬性</span><span class="sxs-lookup"><span data-stu-id="6e23f-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="6e23f-114">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="6e23f-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="6e23f-115">XML</span><span class="sxs-lookup"><span data-stu-id="6e23f-115">XML</span></span>](index.md)
