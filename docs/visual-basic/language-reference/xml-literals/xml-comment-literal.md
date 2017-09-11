---
title: "XML 註解常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralComment
dev_langs:
- VB
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
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
ms.openlocfilehash: ab896399b664c658710c24d9799218ff3d81aecc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="73e58-102">XML 註解常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73e58-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="73e58-103">常值代表<xref:System.Xml.Linq.XComment>物件。</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="73e58-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e58-104">語法</span><span class="sxs-lookup"><span data-stu-id="73e58-104">Syntax</span></span>  
  
```  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="73e58-105">組件</span><span class="sxs-lookup"><span data-stu-id="73e58-105">Parts</span></span>  
  
|<span data-ttu-id="73e58-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="73e58-106">Term</span></span>|<span data-ttu-id="73e58-107">定義</span><span class="sxs-lookup"><span data-stu-id="73e58-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="73e58-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="73e58-108">Required.</span></span> <span data-ttu-id="73e58-109">代表 XML 註解的開始。</span><span class="sxs-lookup"><span data-stu-id="73e58-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="73e58-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="73e58-110">Required.</span></span> <span data-ttu-id="73e58-111">出現在 XML 註解中的文字。</span><span class="sxs-lookup"><span data-stu-id="73e58-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="73e58-112">不能包含一系列的兩個連字號 （-） 或連字號相鄰結尾標記的結束。</span><span class="sxs-lookup"><span data-stu-id="73e58-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="73e58-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="73e58-113">Required.</span></span> <span data-ttu-id="73e58-114">代表 XML 註解的結尾。</span><span class="sxs-lookup"><span data-stu-id="73e58-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="73e58-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="73e58-115">Return Value</span></span>  
 <span data-ttu-id="73e58-116"><xref:System.Xml.Linq.XComment>物件。</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="73e58-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73e58-117">備註</span><span class="sxs-lookup"><span data-stu-id="73e58-117">Remarks</span></span>  
 <span data-ttu-id="73e58-118">XML 註解常值不包含文件內容。其中包含文件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="73e58-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="73e58-119">XML 註解區段結尾的 「--> 」 順序。</span><span class="sxs-lookup"><span data-stu-id="73e58-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="73e58-120">這表示下列各點︰</span><span class="sxs-lookup"><span data-stu-id="73e58-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="73e58-121">您無法在 XML 註解常值中使用內嵌的運算式，因為內嵌的運算式分隔符號是有效的 XML 註解內容。</span><span class="sxs-lookup"><span data-stu-id="73e58-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="73e58-122">XML 註解區段不可為巢狀，因為`content`不能包含"-->"的值。</span><span class="sxs-lookup"><span data-stu-id="73e58-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="73e58-123">您可以將 XML 註解常值指派給變數，或將它包含在 XML 項目常值。</span><span class="sxs-lookup"><span data-stu-id="73e58-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73e58-124">XML 常值可以跨越多行程式碼，而不需使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="73e58-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="73e58-125">這項功能可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="73e58-125">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="73e58-126">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 註解常值轉換成呼叫<xref:System.Xml.Linq.XComment.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XComment.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="73e58-126">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73e58-127">範例</span><span class="sxs-lookup"><span data-stu-id="73e58-127">Example</span></span>  
 <span data-ttu-id="73e58-128">下列範例會建立包含文字的 XML 註解 「 這是註解 」。</span><span class="sxs-lookup"><span data-stu-id="73e58-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 <span data-ttu-id="73e58-129">[!code-vb[VbXMLSamples #&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="73e58-129">[!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e58-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73e58-130">See Also</span></span>  
 <span data-ttu-id="73e58-131"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="73e58-131"><xref:System.Xml.Linq.XComment></span></span>   
<span data-ttu-id="73e58-132"> [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="73e58-132"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="73e58-133"> [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="73e58-133"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="73e58-134"> [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="73e58-134"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
