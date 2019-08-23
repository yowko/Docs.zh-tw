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
ms.openlocfilehash: 248f3cf31f686de3af2ea06012aa4a6d4f3f29fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942911"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="0c87d-102">XML CDATA 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c87d-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="0c87d-103">代表<xref:System.Xml.Linq.XCData>物件的常值。</span><span class="sxs-lookup"><span data-stu-id="0c87d-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c87d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c87d-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="0c87d-105">組件</span><span class="sxs-lookup"><span data-stu-id="0c87d-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="0c87d-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="0c87d-106">Required.</span></span> <span data-ttu-id="0c87d-107">表示 XML CDATA 區段的開頭。</span><span class="sxs-lookup"><span data-stu-id="0c87d-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="0c87d-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="0c87d-108">Required.</span></span> <span data-ttu-id="0c87d-109">要出現在 XML CDATA 區段中的文字內容。</span><span class="sxs-lookup"><span data-stu-id="0c87d-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="0c87d-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="0c87d-110">Required.</span></span> <span data-ttu-id="0c87d-111">表示區段的結尾。</span><span class="sxs-lookup"><span data-stu-id="0c87d-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c87d-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="0c87d-112">Return Value</span></span>  
 <span data-ttu-id="0c87d-113"><xref:System.Xml.Linq.XCData> 物件。</span><span class="sxs-lookup"><span data-stu-id="0c87d-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c87d-114">備註</span><span class="sxs-lookup"><span data-stu-id="0c87d-114">Remarks</span></span>  
 <span data-ttu-id="0c87d-115">XML CDATA 區段包含應包含但未剖析的原始文字, 以及包含它的 XML。</span><span class="sxs-lookup"><span data-stu-id="0c87d-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="0c87d-116">XML CDATA 區段可以包含任何文字。</span><span class="sxs-lookup"><span data-stu-id="0c87d-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="0c87d-117">這包括保留的 XML 字元。</span><span class="sxs-lookup"><span data-stu-id="0c87d-117">This includes reserved XML characters.</span></span> <span data-ttu-id="0c87d-118">XML CDATA 區段的結尾是序列 "]] >"。</span><span class="sxs-lookup"><span data-stu-id="0c87d-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="0c87d-119">這表示下列幾點:</span><span class="sxs-lookup"><span data-stu-id="0c87d-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="0c87d-120">您不能在 XML CDATA 常值中使用內嵌運算式, 因為內嵌的運算式分隔符號是有效的 XML CDATA 內容。</span><span class="sxs-lookup"><span data-stu-id="0c87d-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="0c87d-121">XML CDATA 區段無法嵌套, 因為`content`不能包含值 "]] >"。</span><span class="sxs-lookup"><span data-stu-id="0c87d-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="0c87d-122">您可以將 XML CDATA 常值指派給變數, 或將它包含在 XML 元素常值中。</span><span class="sxs-lookup"><span data-stu-id="0c87d-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c87d-123">XML 常值可以跨越多行, 但不會使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="0c87d-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="0c87d-124">這可讓您從 XML 檔案複製內容, 並將它直接貼到 Visual Basic 程式中。</span><span class="sxs-lookup"><span data-stu-id="0c87d-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="0c87d-125">Visual Basic 編譯器會將 XML CDATA 常值轉換為對此<xref:System.Xml.Linq.XCData.%23ctor%2A>函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0c87d-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c87d-126">範例</span><span class="sxs-lookup"><span data-stu-id="0c87d-126">Example</span></span>  
 <span data-ttu-id="0c87d-127">下列範例會建立一個 CDATA 區段, 其中包含「可以包含常\<值 XML > 標記」文字。</span><span class="sxs-lookup"><span data-stu-id="0c87d-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="0c87d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c87d-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="0c87d-129">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="0c87d-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="0c87d-130">XML 常值</span><span class="sxs-lookup"><span data-stu-id="0c87d-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="0c87d-131">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="0c87d-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
