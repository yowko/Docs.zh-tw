---
title: "XML 常值中的空白字元 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8587abb98fe33ab2c5a0cef6cea76049a00909e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="90179-102">XML 常值中的空白字元 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90179-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="90179-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會在建立時，編譯器會併入只有顯著泛空白字元字元從 XML 常值[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="90179-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="90179-104">不會納入無意義的空格字元。</span><span class="sxs-lookup"><span data-stu-id="90179-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="90179-105">顯著和不顯著泛空白字元</span><span class="sxs-lookup"><span data-stu-id="90179-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="90179-106">XML 常值中的空白字元就很重要的只有三個方面：</span><span class="sxs-lookup"><span data-stu-id="90179-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="90179-107">當它們位於屬性值。</span><span class="sxs-lookup"><span data-stu-id="90179-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="90179-108">當它們是項目的文字內容的一部分，而且文字也包含其他字元。</span><span class="sxs-lookup"><span data-stu-id="90179-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="90179-109">當仍在內嵌運算式的項目文字內容。</span><span class="sxs-lookup"><span data-stu-id="90179-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="90179-110">否則，編譯器會將空格字元視為無意義，而且不包含然後中[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]常值的物件。</span><span class="sxs-lookup"><span data-stu-id="90179-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="90179-111">若要在 XML 常值包含有效的空白字元，使用內嵌的運算式，其中包含字串常值空白字元。</span><span class="sxs-lookup"><span data-stu-id="90179-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90179-112">如果`xml:space`屬性會出現在 XML 元素常值，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器包含中的屬性<xref:System.Xml.Linq.XElement>物件，但加入此屬性不會變更編譯器如何處理空白字元。</span><span class="sxs-lookup"><span data-stu-id="90179-112">If the `xml:space` attribute appears in an XML element literal, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="90179-113">範例</span><span class="sxs-lookup"><span data-stu-id="90179-113">Examples</span></span>  
 <span data-ttu-id="90179-114">下列範例包含兩個外部和內部的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="90179-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="90179-115">這兩個元素包含文字內容中的空白字元。</span><span class="sxs-lookup"><span data-stu-id="90179-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="90179-116">外部的項目中的泛空白字元是無意義的因為它只包含空白字元和 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="90179-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="90179-117">內部項目中的空白字元很重要的因為它包含泛空白字元和文字。</span><span class="sxs-lookup"><span data-stu-id="90179-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="90179-118">當執行時，此程式碼會顯示下列文字。</span><span class="sxs-lookup"><span data-stu-id="90179-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90179-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90179-119">See Also</span></span>  
 [<span data-ttu-id="90179-120">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="90179-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
