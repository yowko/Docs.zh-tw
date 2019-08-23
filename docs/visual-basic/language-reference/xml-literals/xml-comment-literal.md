---
title: XML 註解常值 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 91369392f33f2a86a7a4cb5ffb3faa668c113348
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965404"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="16e23-102">XML 註解常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16e23-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="16e23-103">代表<xref:System.Xml.Linq.XComment>物件的常值。</span><span class="sxs-lookup"><span data-stu-id="16e23-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e23-104">語法</span><span class="sxs-lookup"><span data-stu-id="16e23-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="16e23-105">組件</span><span class="sxs-lookup"><span data-stu-id="16e23-105">Parts</span></span>  
  
|<span data-ttu-id="16e23-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="16e23-106">Term</span></span>|<span data-ttu-id="16e23-107">定義</span><span class="sxs-lookup"><span data-stu-id="16e23-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="16e23-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="16e23-108">Required.</span></span> <span data-ttu-id="16e23-109">表示 XML 批註的開頭。</span><span class="sxs-lookup"><span data-stu-id="16e23-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="16e23-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="16e23-110">Required.</span></span> <span data-ttu-id="16e23-111">要出現在 XML 批註中的文字。</span><span class="sxs-lookup"><span data-stu-id="16e23-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="16e23-112">不能包含一系列的兩個連字號 (--), 也不能以連字號連續的結束記號結束。</span><span class="sxs-lookup"><span data-stu-id="16e23-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="16e23-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="16e23-113">Required.</span></span> <span data-ttu-id="16e23-114">表示 XML 批註的結尾。</span><span class="sxs-lookup"><span data-stu-id="16e23-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="16e23-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="16e23-115">Return Value</span></span>  
 <span data-ttu-id="16e23-116"><xref:System.Xml.Linq.XComment> 物件。</span><span class="sxs-lookup"><span data-stu-id="16e23-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16e23-117">備註</span><span class="sxs-lookup"><span data-stu-id="16e23-117">Remarks</span></span>  
 <span data-ttu-id="16e23-118">XML 批註常值不包含檔內容;其中包含檔的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="16e23-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="16e23-119">XML 批註區段的結尾是「-->」序列。</span><span class="sxs-lookup"><span data-stu-id="16e23-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="16e23-120">這表示下列幾點:</span><span class="sxs-lookup"><span data-stu-id="16e23-120">This implies the following points:</span></span>  
  
- <span data-ttu-id="16e23-121">您不能在 XML 批註常值中使用內嵌運算式, 因為內嵌的運算式分隔符號是有效的 XML 批註內容。</span><span class="sxs-lookup"><span data-stu-id="16e23-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
- <span data-ttu-id="16e23-122">XML 批註區段無法嵌套, 因為`content`不能包含值 "-->"。</span><span class="sxs-lookup"><span data-stu-id="16e23-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="16e23-123">您可以將 XML 批註常值指派給變數, 也可以將它包含在 XML 元素常值中。</span><span class="sxs-lookup"><span data-stu-id="16e23-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16e23-124">XML 常值可以跨越多行, 而不需要使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="16e23-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="16e23-125">這項功能可讓您從 XML 檔案複製內容, 並將它直接貼到 Visual Basic 程式中。</span><span class="sxs-lookup"><span data-stu-id="16e23-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="16e23-126">Visual Basic 編譯器會將 XML 批註常值轉換為對此<xref:System.Xml.Linq.XComment.%23ctor%2A>函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="16e23-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16e23-127">範例</span><span class="sxs-lookup"><span data-stu-id="16e23-127">Example</span></span>  
 <span data-ttu-id="16e23-128">下列範例會建立包含文字 "This is a comment" 的 XML 批註。</span><span class="sxs-lookup"><span data-stu-id="16e23-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="16e23-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16e23-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="16e23-130">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="16e23-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="16e23-131">XML 常值</span><span class="sxs-lookup"><span data-stu-id="16e23-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="16e23-132">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="16e23-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
