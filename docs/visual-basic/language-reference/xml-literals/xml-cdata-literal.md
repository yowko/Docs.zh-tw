---
title: "XML CDATA 常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
dev_langs:
- VB
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
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
ms.openlocfilehash: 6bf12a5dd5b24b0a915cb15f41cb8947c33e94b0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="b290e-102">XML CDATA 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b290e-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="b290e-103">常值代表<xref:System.Xml.Linq.XCData>物件。</xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="b290e-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b290e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b290e-104">Syntax</span></span>  
  
```  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="b290e-105">組件</span><span class="sxs-lookup"><span data-stu-id="b290e-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="b290e-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="b290e-106">Required.</span></span> <span data-ttu-id="b290e-107">表示 XML CDATA 區段的開頭。</span><span class="sxs-lookup"><span data-stu-id="b290e-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="b290e-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="b290e-108">Required.</span></span> <span data-ttu-id="b290e-109">XML CDATA 區段中顯示的文字內容。</span><span class="sxs-lookup"><span data-stu-id="b290e-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="b290e-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="b290e-110">Required.</span></span> <span data-ttu-id="b290e-111">代表區段的結尾。</span><span class="sxs-lookup"><span data-stu-id="b290e-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b290e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="b290e-112">Return Value</span></span>  
 <span data-ttu-id="b290e-113"><xref:System.Xml.Linq.XCData>物件。</xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="b290e-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b290e-114">備註</span><span class="sxs-lookup"><span data-stu-id="b290e-114">Remarks</span></span>  
 <span data-ttu-id="b290e-115">XML CDATA 區段包含應該包括但不是剖析 xml，其中包含它的原始文字。</span><span class="sxs-lookup"><span data-stu-id="b290e-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="b290e-116">XML CDATA 區段可以包含任何文字。</span><span class="sxs-lookup"><span data-stu-id="b290e-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="b290e-117">這包括保留的 XML 字元。</span><span class="sxs-lookup"><span data-stu-id="b290e-117">This includes reserved XML characters.</span></span> <span data-ttu-id="b290e-118">XML CDATA 區段的結尾是序列"]] > 」。</span><span class="sxs-lookup"><span data-stu-id="b290e-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="b290e-119">這表示下列各點︰</span><span class="sxs-lookup"><span data-stu-id="b290e-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="b290e-120">您無法在 XML CDATA 常值中使用內嵌的運算式，因為內嵌的運算式分隔符號是有效的 XML CDATA 內容。</span><span class="sxs-lookup"><span data-stu-id="b290e-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="b290e-121">XML CDATA 區段不可為巢狀，因為`content`不能包含值"]] > 」。</span><span class="sxs-lookup"><span data-stu-id="b290e-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="b290e-122">您可以將 XML CDATA 常值指派給變數，或將它包含在 XML 項目常值。</span><span class="sxs-lookup"><span data-stu-id="b290e-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b290e-123">XML 常值可以跨越多行，但不會使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="b290e-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="b290e-124">這可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="b290e-124">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="b290e-125">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML CDATA 常值轉換成呼叫<xref:System.Xml.Linq.XCData.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XCData.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="b290e-125">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b290e-126">範例</span><span class="sxs-lookup"><span data-stu-id="b290e-126">Example</span></span>  
 <span data-ttu-id="b290e-127">下列範例會建立包含文字的 CDATA 區段 」 可以包含常值\<XML > 標記 」。</span><span class="sxs-lookup"><span data-stu-id="b290e-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 <span data-ttu-id="b290e-128">[!code-vb[VbXMLSamples #&23;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b290e-128">[!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b290e-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b290e-129">See Also</span></span>  
 <span data-ttu-id="b290e-130"><xref:System.Xml.Linq.XCData></xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="b290e-130"><xref:System.Xml.Linq.XCData></span></span>   
<span data-ttu-id="b290e-131"> [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="b290e-131"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="b290e-132"> [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="b290e-132"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="b290e-133"> [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="b290e-133"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
