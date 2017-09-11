---
title: "XML 常值 (Visual Basic) 中的泛空白字元 |Microsoft 文件"
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
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
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
ms.openlocfilehash: 4fc3d30a9c71cbd732597c5e3f32bd01eb489a80
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="77d38-102">XML 常值中的空白字元 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77d38-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="77d38-103">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]建立時，編譯器會併入只有顯著泛空白字元字元從 XML 常值[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="77d38-103">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] object.</span></span> <span data-ttu-id="77d38-104">不會納入不顯著泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="77d38-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="77d38-105">顯著與不顯著泛空白字元</span><span class="sxs-lookup"><span data-stu-id="77d38-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="77d38-106">XML 常值中的空白字元是顯著只有三個方面︰</span><span class="sxs-lookup"><span data-stu-id="77d38-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="77d38-107">當它們位於屬性值。</span><span class="sxs-lookup"><span data-stu-id="77d38-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="77d38-108">當它們是項目的文字內容的一部分，文字也包含其他字元。</span><span class="sxs-lookup"><span data-stu-id="77d38-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="77d38-109">當它們位於內嵌的運算式，表示項目的文字內容。</span><span class="sxs-lookup"><span data-stu-id="77d38-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="77d38-110">否則，編譯器泛空白字元視為無意義，而且不包含然後中[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]的常值的物件。</span><span class="sxs-lookup"><span data-stu-id="77d38-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="77d38-111">若要在 XML 常值中包含不顯著泛空白字元，使用內嵌的運算式，其中包含泛空白字元的常值字串。</span><span class="sxs-lookup"><span data-stu-id="77d38-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77d38-112">如果`xml:space`屬性會出現在 XML 項目常值，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器中的屬性會包含<xref:System.Xml.Linq.XElement>物件，但加入此屬性不會變更編譯器如何處理泛空白字元。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="77d38-112">If the `xml:space` attribute appears in an XML element literal, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="77d38-113">範例</span><span class="sxs-lookup"><span data-stu-id="77d38-113">Examples</span></span>  
 <span data-ttu-id="77d38-114">下列範例包含兩個外部和內部的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="77d38-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="77d38-115">這兩個項目包含文字內容中的泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="77d38-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="77d38-116">外部的項目中的泛空白字元是不重要，因為它只包含泛空白字元和 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="77d38-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="77d38-117">內部項目中的泛空白字元是顯著，因為它包含泛空白字元和文字。</span><span class="sxs-lookup"><span data-stu-id="77d38-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 <span data-ttu-id="77d38-118">[!code-vb[VbXMLSamples #&29;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="77d38-118">[!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]</span></span>  
  
 <span data-ttu-id="77d38-119">當執行時，此程式碼會顯示下列文字。</span><span class="sxs-lookup"><span data-stu-id="77d38-119">When run, this code displays the following text.</span></span>  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="77d38-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77d38-120">See Also</span></span>  
 [<span data-ttu-id="77d38-121">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="77d38-121">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
