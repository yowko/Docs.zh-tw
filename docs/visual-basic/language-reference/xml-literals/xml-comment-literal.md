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
ms.openlocfilehash: 60c354215c627683fd6c69d9ca66fc115c26ccda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603934"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="0a27c-102">XML 註解常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a27c-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="0a27c-103">常值代表<xref:System.Xml.Linq.XComment>物件。</span><span class="sxs-lookup"><span data-stu-id="0a27c-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a27c-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a27c-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="0a27c-105">組件</span><span class="sxs-lookup"><span data-stu-id="0a27c-105">Parts</span></span>  
  
|<span data-ttu-id="0a27c-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="0a27c-106">Term</span></span>|<span data-ttu-id="0a27c-107">定義</span><span class="sxs-lookup"><span data-stu-id="0a27c-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="0a27c-108">必要。</span><span class="sxs-lookup"><span data-stu-id="0a27c-108">Required.</span></span> <span data-ttu-id="0a27c-109">代表 XML 註解的開始。</span><span class="sxs-lookup"><span data-stu-id="0a27c-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="0a27c-110">必要。</span><span class="sxs-lookup"><span data-stu-id="0a27c-110">Required.</span></span> <span data-ttu-id="0a27c-111">要出現在 XML 註解的文字。</span><span class="sxs-lookup"><span data-stu-id="0a27c-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="0a27c-112">不能包含一系列的兩個連字號 （-） 或連字號相鄰結尾標記的結尾。</span><span class="sxs-lookup"><span data-stu-id="0a27c-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="0a27c-113">必要。</span><span class="sxs-lookup"><span data-stu-id="0a27c-113">Required.</span></span> <span data-ttu-id="0a27c-114">代表 XML 註解的結尾。</span><span class="sxs-lookup"><span data-stu-id="0a27c-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="0a27c-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="0a27c-115">Return Value</span></span>  
 <span data-ttu-id="0a27c-116"><xref:System.Xml.Linq.XComment> 物件。</span><span class="sxs-lookup"><span data-stu-id="0a27c-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a27c-117">備註</span><span class="sxs-lookup"><span data-stu-id="0a27c-117">Remarks</span></span>  
 <span data-ttu-id="0a27c-118">XML 註解常值不包含文件內容。其中包含文件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0a27c-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="0a27c-119">XML 註解區段以序列"-->"結尾。</span><span class="sxs-lookup"><span data-stu-id="0a27c-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="0a27c-120">這表示下列各點：</span><span class="sxs-lookup"><span data-stu-id="0a27c-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="0a27c-121">因為內嵌的運算式分隔符號是有效的 XML 註解內容，您無法在 XML 註解常值中使用內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="0a27c-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="0a27c-122">XML 註解區段不可為巢狀，因為`content`不能用來包含"-->"的值。</span><span class="sxs-lookup"><span data-stu-id="0a27c-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="0a27c-123">您可以將 XML 註解常值指派給變數，或您可以包含在 XML 元素常值。</span><span class="sxs-lookup"><span data-stu-id="0a27c-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a27c-124">XML 常值可以跨越多行，而不使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="0a27c-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="0a27c-125">這項功能可讓您從 XML 文件內容複製並貼上直接在 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="0a27c-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="0a27c-126">Visual Basic 編譯器會將 XML 註解常值轉換成呼叫<xref:System.Xml.Linq.XComment.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="0a27c-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a27c-127">範例</span><span class="sxs-lookup"><span data-stu-id="0a27c-127">Example</span></span>  
 <span data-ttu-id="0a27c-128">下列範例會建立包含文字的 XML 註解"This is 註解"。</span><span class="sxs-lookup"><span data-stu-id="0a27c-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0a27c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a27c-129">See Also</span></span>  
 <xref:System.Xml.Linq.XComment>  
 [<span data-ttu-id="0a27c-130">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="0a27c-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="0a27c-131">XML 常值</span><span class="sxs-lookup"><span data-stu-id="0a27c-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="0a27c-132">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="0a27c-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
