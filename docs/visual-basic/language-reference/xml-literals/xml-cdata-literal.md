---
title: XML CDATA 常值
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: b9cc830d27625f192d8f5e059bd3783d05d8ba3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400224"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="e387e-102">XML CDATA 常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e387e-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="e387e-103">代表物件的常值 <xref:System.Xml.Linq.XCData> 。</span><span class="sxs-lookup"><span data-stu-id="e387e-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e387e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e387e-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="e387e-105">組件</span><span class="sxs-lookup"><span data-stu-id="e387e-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="e387e-106">必要。</span><span class="sxs-lookup"><span data-stu-id="e387e-106">Required.</span></span> <span data-ttu-id="e387e-107">表示 XML CDATA 區段的開頭。</span><span class="sxs-lookup"><span data-stu-id="e387e-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="e387e-108">必要。</span><span class="sxs-lookup"><span data-stu-id="e387e-108">Required.</span></span> <span data-ttu-id="e387e-109">要出現在 XML CDATA 區段中的文字內容。</span><span class="sxs-lookup"><span data-stu-id="e387e-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="e387e-110">必要。</span><span class="sxs-lookup"><span data-stu-id="e387e-110">Required.</span></span> <span data-ttu-id="e387e-111">表示區段的結尾。</span><span class="sxs-lookup"><span data-stu-id="e387e-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e387e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="e387e-112">Return Value</span></span>  
 <span data-ttu-id="e387e-113"><xref:System.Xml.Linq.XCData> 物件。</span><span class="sxs-lookup"><span data-stu-id="e387e-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e387e-114">備註</span><span class="sxs-lookup"><span data-stu-id="e387e-114">Remarks</span></span>  
 <span data-ttu-id="e387e-115">XML CDATA 區段包含應包含但未剖析的原始文字，以及包含它的 XML。</span><span class="sxs-lookup"><span data-stu-id="e387e-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="e387e-116">XML CDATA 區段可以包含任何文字。</span><span class="sxs-lookup"><span data-stu-id="e387e-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="e387e-117">這包括保留的 XML 字元。</span><span class="sxs-lookup"><span data-stu-id="e387e-117">This includes reserved XML characters.</span></span> <span data-ttu-id="e387e-118">XML CDATA 區段的結尾是序列 "]] >"。</span><span class="sxs-lookup"><span data-stu-id="e387e-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="e387e-119">這表示下列幾點：</span><span class="sxs-lookup"><span data-stu-id="e387e-119">This implies the following points:</span></span>  
  
- <span data-ttu-id="e387e-120">您不能在 XML CDATA 常值中使用內嵌運算式，因為內嵌的運算式分隔符號是有效的 XML CDATA 內容。</span><span class="sxs-lookup"><span data-stu-id="e387e-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
- <span data-ttu-id="e387e-121">XML CDATA 區段無法嵌套，因為 `content` 不能包含值 "]] >"。</span><span class="sxs-lookup"><span data-stu-id="e387e-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="e387e-122">您可以將 XML CDATA 常值指派給變數，或將它包含在 XML 元素常值中。</span><span class="sxs-lookup"><span data-stu-id="e387e-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e387e-123">XML 常值可以跨越多行，但不會使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="e387e-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="e387e-124">這可讓您從 XML 檔案複製內容，並將它直接貼到 Visual Basic 程式中。</span><span class="sxs-lookup"><span data-stu-id="e387e-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="e387e-125">Visual Basic 編譯器會將 XML CDATA 常值轉換為對此函式的呼叫 <xref:System.Xml.Linq.XCData.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e387e-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e387e-126">範例</span><span class="sxs-lookup"><span data-stu-id="e387e-126">Example</span></span>  
 <span data-ttu-id="e387e-127">下列範例會建立 CDATA 區段，其中包含「可以包含常值標記」文字 \<XML> 。</span><span class="sxs-lookup"><span data-stu-id="e387e-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e387e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e387e-128">See also</span></span>

- <xref:System.Xml.Linq.XCData>
- [<span data-ttu-id="e387e-129">XML 元素常值</span><span class="sxs-lookup"><span data-stu-id="e387e-129">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="e387e-130">XML 常值</span><span class="sxs-lookup"><span data-stu-id="e387e-130">XML Literals</span></span>](index.md)
- [<span data-ttu-id="e387e-131">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="e387e-131">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
