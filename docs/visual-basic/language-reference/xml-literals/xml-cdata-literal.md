---
title: XML CDATA 常值 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8dfc091409e060e20970b0b6d6bc19b4fc2aeea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="9188a-102">XML CDATA 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9188a-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="9188a-103">常值代表<xref:System.Xml.Linq.XCData>物件。</span><span class="sxs-lookup"><span data-stu-id="9188a-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9188a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9188a-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="9188a-105">組件</span><span class="sxs-lookup"><span data-stu-id="9188a-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="9188a-106">必要。</span><span class="sxs-lookup"><span data-stu-id="9188a-106">Required.</span></span> <span data-ttu-id="9188a-107">代表 XML CDATA 區段的開頭。</span><span class="sxs-lookup"><span data-stu-id="9188a-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="9188a-108">必要。</span><span class="sxs-lookup"><span data-stu-id="9188a-108">Required.</span></span> <span data-ttu-id="9188a-109">在 XML CDATA 區段中顯示的文字內容。</span><span class="sxs-lookup"><span data-stu-id="9188a-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="9188a-110">必要。</span><span class="sxs-lookup"><span data-stu-id="9188a-110">Required.</span></span> <span data-ttu-id="9188a-111">表示區段的結尾。</span><span class="sxs-lookup"><span data-stu-id="9188a-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9188a-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="9188a-112">Return Value</span></span>  
 <span data-ttu-id="9188a-113"><xref:System.Xml.Linq.XCData> 物件。</span><span class="sxs-lookup"><span data-stu-id="9188a-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9188a-114">備註</span><span class="sxs-lookup"><span data-stu-id="9188a-114">Remarks</span></span>  
 <span data-ttu-id="9188a-115">XML CDATA 區段包含應該包括但不是剖析 xml 包含它的原始文字。</span><span class="sxs-lookup"><span data-stu-id="9188a-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="9188a-116">XML CDATA 區段都可以包含任何文字。</span><span class="sxs-lookup"><span data-stu-id="9188a-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="9188a-117">這包括保留的 XML 字元。</span><span class="sxs-lookup"><span data-stu-id="9188a-117">This includes reserved XML characters.</span></span> <span data-ttu-id="9188a-118">XML CDATA 區段結尾序列"]] > 」。</span><span class="sxs-lookup"><span data-stu-id="9188a-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="9188a-119">這表示下列各點：</span><span class="sxs-lookup"><span data-stu-id="9188a-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="9188a-120">您無法在 XML CDATA 常值中使用內嵌的運算式，因為內嵌的運算式分隔符號是有效的 XML 註解內容。</span><span class="sxs-lookup"><span data-stu-id="9188a-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="9188a-121">XML CDATA 區段不可為巢狀，因為`content`不能包含值 「]] > 」。</span><span class="sxs-lookup"><span data-stu-id="9188a-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="9188a-122">您可以將 XML CDATA 常值指派給變數，或將它包含在 XML 元素常值。</span><span class="sxs-lookup"><span data-stu-id="9188a-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9188a-123">XML 常值可以跨越多行，但不會使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="9188a-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="9188a-124">這可讓您從 XML 文件內容複製並貼上直接在 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="9188a-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="9188a-125">Visual Basic 編譯器會將 XML CDATA 常值轉換成呼叫<xref:System.Xml.Linq.XCData.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="9188a-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9188a-126">範例</span><span class="sxs-lookup"><span data-stu-id="9188a-126">Example</span></span>  
 <span data-ttu-id="9188a-127">下列範例會建立包含文字的 CDATA 區段 」 可以包含常值\<XML > 標記 」。</span><span class="sxs-lookup"><span data-stu-id="9188a-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9188a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9188a-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="9188a-129">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="9188a-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="9188a-130">XML 常值</span><span class="sxs-lookup"><span data-stu-id="9188a-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="9188a-131">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="9188a-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
