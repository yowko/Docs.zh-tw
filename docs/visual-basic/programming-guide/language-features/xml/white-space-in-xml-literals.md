---
title: XML 常值中的空白字元 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: ef371a984d03485ccaf1ee5d61aa3cf39d80ef32
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979056"
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="0dd18-102">XML 常值中的空白字元 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dd18-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="0dd18-103">Visual Basic 編譯器會在建立時，包含只有顯著泛空白字元字元從 XML 常值[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="0dd18-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="0dd18-104">不會納入不顯著泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="0dd18-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="0dd18-105">顯著與不顯著泛空白字元</span><span class="sxs-lookup"><span data-stu-id="0dd18-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="0dd18-106">XML 常值中的空白字元很重要的只有三個方面：</span><span class="sxs-lookup"><span data-stu-id="0dd18-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="0dd18-107">當它們位於屬性值。</span><span class="sxs-lookup"><span data-stu-id="0dd18-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="0dd18-108">當它們是項目的文字內容的一部分，文字也包含其他字元。</span><span class="sxs-lookup"><span data-stu-id="0dd18-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="0dd18-109">當它們位於項目的文字內容的內嵌運算式。</span><span class="sxs-lookup"><span data-stu-id="0dd18-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="0dd18-110">否則，編譯器泛空白字元視為無意義，而且不包含然後中[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]的常值的物件。</span><span class="sxs-lookup"><span data-stu-id="0dd18-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="0dd18-111">若要在 XML 常值包含不顯著泛空白字元，使用內嵌的運算式，其中包含泛空白字元常值的字串。</span><span class="sxs-lookup"><span data-stu-id="0dd18-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0dd18-112">如果`xml:space`屬性會出現在 XML 元素常值、 Visual Basic 編譯器包含中的屬性<xref:System.Xml.Linq.XElement>物件，但新增這個屬性不會變更編譯器如何處理泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="0dd18-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0dd18-113">範例</span><span class="sxs-lookup"><span data-stu-id="0dd18-113">Examples</span></span>  
 <span data-ttu-id="0dd18-114">下列範例包含兩個外部和內部的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="0dd18-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="0dd18-115">這兩個項目會包含其文字內容中的泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="0dd18-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="0dd18-116">外部的項目中的泛空白字元不重要，因為它只包含泛空白字元和 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="0dd18-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="0dd18-117">內部項目中的泛空白字元是顯著，因為它包含泛空白字元和文字。</span><span class="sxs-lookup"><span data-stu-id="0dd18-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 <span data-ttu-id="0dd18-118">當執行時，此程式碼就會顯示下列文字。</span><span class="sxs-lookup"><span data-stu-id="0dd18-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dd18-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dd18-119">See also</span></span>
- [<span data-ttu-id="0dd18-120">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="0dd18-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
