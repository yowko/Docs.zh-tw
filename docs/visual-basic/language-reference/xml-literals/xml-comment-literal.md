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
ms.openlocfilehash: 149bbac6d301a9c2f166d05698e3780171126cb3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827272"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="07493-102">XML 註解常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07493-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="07493-103">常值代表<xref:System.Xml.Linq.XComment>物件。</span><span class="sxs-lookup"><span data-stu-id="07493-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07493-104">語法</span><span class="sxs-lookup"><span data-stu-id="07493-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="07493-105">組件</span><span class="sxs-lookup"><span data-stu-id="07493-105">Parts</span></span>  
  
|<span data-ttu-id="07493-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="07493-106">Term</span></span>|<span data-ttu-id="07493-107">定義</span><span class="sxs-lookup"><span data-stu-id="07493-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="07493-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="07493-108">Required.</span></span> <span data-ttu-id="07493-109">代表 XML 註解的開始。</span><span class="sxs-lookup"><span data-stu-id="07493-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="07493-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="07493-110">Required.</span></span> <span data-ttu-id="07493-111">XML 註解中所顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="07493-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="07493-112">不能包含一系列的兩個連字號 （-） 或連字號結尾標記相鄰的結尾。</span><span class="sxs-lookup"><span data-stu-id="07493-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="07493-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="07493-113">Required.</span></span> <span data-ttu-id="07493-114">代表 XML 註解的結尾。</span><span class="sxs-lookup"><span data-stu-id="07493-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="07493-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="07493-115">Return Value</span></span>  
 <span data-ttu-id="07493-116"><xref:System.Xml.Linq.XComment> 物件。</span><span class="sxs-lookup"><span data-stu-id="07493-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07493-117">備註</span><span class="sxs-lookup"><span data-stu-id="07493-117">Remarks</span></span>  
 <span data-ttu-id="07493-118">XML 註解常值不包含文件內容;它們包含文件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="07493-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="07493-119">XML 註解區段結尾序列 」-->"。</span><span class="sxs-lookup"><span data-stu-id="07493-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="07493-120">這表示下列各點：</span><span class="sxs-lookup"><span data-stu-id="07493-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="07493-121">因為內嵌的運算式分隔符號是有效的 XML 註解內容，您無法在 XML 註解常值中使用內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="07493-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="07493-122">XML 註解區段不可為巢狀，因為`content`不能包含值"-->"。</span><span class="sxs-lookup"><span data-stu-id="07493-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="07493-123">您可以將 XML 註解常值指派給變數，或將它包含在 XML 元素常值。</span><span class="sxs-lookup"><span data-stu-id="07493-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07493-124">XML 常值可以跨越多行，而不使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="07493-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="07493-125">這項功能可讓您從 XML 文件複製內容，並將它貼到 Visual Basic 程式直接。</span><span class="sxs-lookup"><span data-stu-id="07493-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="07493-126">Visual Basic 編譯器會將 XML 註解常值轉換成呼叫<xref:System.Xml.Linq.XComment.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="07493-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07493-127">範例</span><span class="sxs-lookup"><span data-stu-id="07493-127">Example</span></span>  
 <span data-ttu-id="07493-128">下列範例會建立 XML 註解包含文字 「 這是註解 」。</span><span class="sxs-lookup"><span data-stu-id="07493-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="07493-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07493-129">See also</span></span>

- <xref:System.Xml.Linq.XComment>
- [<span data-ttu-id="07493-130">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="07493-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="07493-131">XML 常值</span><span class="sxs-lookup"><span data-stu-id="07493-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="07493-132">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="07493-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
