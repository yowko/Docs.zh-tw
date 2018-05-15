---
title: XML CDATA 常值 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 999531d8146748fe491255663f0d2d17d056bcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="4caa5-102">XML CDATA 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4caa5-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="4caa5-103">常值代表<xref:System.Xml.Linq.XCData>物件。</span><span class="sxs-lookup"><span data-stu-id="4caa5-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4caa5-104">語法</span><span class="sxs-lookup"><span data-stu-id="4caa5-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="4caa5-105">組件</span><span class="sxs-lookup"><span data-stu-id="4caa5-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="4caa5-106">必要。</span><span class="sxs-lookup"><span data-stu-id="4caa5-106">Required.</span></span> <span data-ttu-id="4caa5-107">代表 XML CDATA 區段的開頭。</span><span class="sxs-lookup"><span data-stu-id="4caa5-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="4caa5-108">必要。</span><span class="sxs-lookup"><span data-stu-id="4caa5-108">Required.</span></span> <span data-ttu-id="4caa5-109">在 XML CDATA 區段中顯示的文字內容。</span><span class="sxs-lookup"><span data-stu-id="4caa5-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="4caa5-110">必要。</span><span class="sxs-lookup"><span data-stu-id="4caa5-110">Required.</span></span> <span data-ttu-id="4caa5-111">表示區段的結尾。</span><span class="sxs-lookup"><span data-stu-id="4caa5-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4caa5-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="4caa5-112">Return Value</span></span>  
 <span data-ttu-id="4caa5-113"><xref:System.Xml.Linq.XCData> 物件。</span><span class="sxs-lookup"><span data-stu-id="4caa5-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4caa5-114">備註</span><span class="sxs-lookup"><span data-stu-id="4caa5-114">Remarks</span></span>  
 <span data-ttu-id="4caa5-115">XML CDATA 區段包含應該包括但不是剖析 xml 包含它的原始文字。</span><span class="sxs-lookup"><span data-stu-id="4caa5-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="4caa5-116">XML CDATA 區段都可以包含任何文字。</span><span class="sxs-lookup"><span data-stu-id="4caa5-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="4caa5-117">這包括保留的 XML 字元。</span><span class="sxs-lookup"><span data-stu-id="4caa5-117">This includes reserved XML characters.</span></span> <span data-ttu-id="4caa5-118">XML CDATA 區段結尾序列"]] > 」。</span><span class="sxs-lookup"><span data-stu-id="4caa5-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="4caa5-119">這表示下列各點：</span><span class="sxs-lookup"><span data-stu-id="4caa5-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="4caa5-120">您無法在 XML CDATA 常值中使用內嵌的運算式，因為內嵌的運算式分隔符號是有效的 XML 註解內容。</span><span class="sxs-lookup"><span data-stu-id="4caa5-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="4caa5-121">XML CDATA 區段不可為巢狀，因為`content`不能包含值 「]] > 」。</span><span class="sxs-lookup"><span data-stu-id="4caa5-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="4caa5-122">您可以將 XML CDATA 常值指派給變數，或將它包含在 XML 元素常值。</span><span class="sxs-lookup"><span data-stu-id="4caa5-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4caa5-123">XML 常值可以跨越多行，但不會使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="4caa5-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="4caa5-124">這可讓您從 XML 文件內容複製並貼上直接在 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="4caa5-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="4caa5-125">Visual Basic 編譯器會將 XML CDATA 常值轉換成呼叫<xref:System.Xml.Linq.XCData.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="4caa5-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4caa5-126">範例</span><span class="sxs-lookup"><span data-stu-id="4caa5-126">Example</span></span>  
 <span data-ttu-id="4caa5-127">下列範例會建立包含文字的 CDATA 區段 」 可以包含常值\<XML > 標記 」。</span><span class="sxs-lookup"><span data-stu-id="4caa5-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4caa5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4caa5-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="4caa5-129">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="4caa5-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="4caa5-130">XML 常值</span><span class="sxs-lookup"><span data-stu-id="4caa5-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="4caa5-131">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="4caa5-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
