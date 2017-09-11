---
title: "XML 文件常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
dev_langs:
- VB
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
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
ms.openlocfilehash: 5e173c8bc89f61925c3e6127fb3cac61379aeffa
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="e1e6d-102">XML 文件常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1e6d-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="e1e6d-103">常值代表<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="e1e6d-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e6d-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1e6d-104">Syntax</span></span>  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e1e6d-105">組件</span><span class="sxs-lookup"><span data-stu-id="e1e6d-105">Parts</span></span>  
  
|<span data-ttu-id="e1e6d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="e1e6d-106">Term</span></span>|<span data-ttu-id="e1e6d-107">定義</span><span class="sxs-lookup"><span data-stu-id="e1e6d-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="e1e6d-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-108">Optional.</span></span> <span data-ttu-id="e1e6d-109">使用宣告編碼文件常值文字。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="e1e6d-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-110">Optional.</span></span> <span data-ttu-id="e1e6d-111">常值文字。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-111">Literal text.</span></span> <span data-ttu-id="e1e6d-112">必須是"yes"或"no"。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="e1e6d-113">選擇項。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-113">Optional.</span></span> <span data-ttu-id="e1e6d-114">XML 處理指示和 XML 註解的清單。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="e1e6d-115">採用下列格式︰</span><span class="sxs-lookup"><span data-stu-id="e1e6d-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="e1e6d-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="e1e6d-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="e1e6d-117">每個`piComment`可以是下列其中之一︰</span><span class="sxs-lookup"><span data-stu-id="e1e6d-117">Each `piComment`can be one of the following:</span></span><br /><br /><span data-ttu-id="e1e6d-118"> -   [XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-118"> -   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="e1e6d-119">-   [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="e1e6d-120">必要項。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-120">Required.</span></span> <span data-ttu-id="e1e6d-121">文件的根項目。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-121">Root element of the document.</span></span> <span data-ttu-id="e1e6d-122">格式為下列其中一項︰</span><span class="sxs-lookup"><span data-stu-id="e1e6d-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="e1e6d-123">[XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="e1e6d-124">內嵌運算式格式`<%=` `elementExp` `%>`。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="e1e6d-125">`elementExp`傳回下列其中之一︰</span><span class="sxs-lookup"><span data-stu-id="e1e6d-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="e1e6d-126"><xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="e1e6d-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="e1e6d-127">集合，其中包含一個<xref:System.Xml.Linq.XElement>物件和任意數目的<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>物件。</xref:System.Xml.Linq.XComment> </xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="e1e6d-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="e1e6d-128">如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="e1e6d-129">傳回值</span><span class="sxs-lookup"><span data-stu-id="e1e6d-129">Return Value</span></span>  
 <span data-ttu-id="e1e6d-130"><xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="e1e6d-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1e6d-131">備註</span><span class="sxs-lookup"><span data-stu-id="e1e6d-131">Remarks</span></span>  
 <span data-ttu-id="e1e6d-132">常值開頭的 XML 宣告來識別 XML 文件常值。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="e1e6d-133">雖然每個 XML 文件常值必須有一個根 XML 項目，它可以有任意數目的 XML 處理指示和 XML 註解。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="e1e6d-134">XML 文件常值不能出現在 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1e6d-135">XML 常值可以跨越多行程式碼，而不需使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="e1e6d-136">這可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-136">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="e1e6d-137">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 文件常值轉換成呼叫<xref:System.Xml.Linq.XDocument.%23ctor%2A>和<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XDeclaration.%23ctor%2A> </xref:System.Xml.Linq.XDocument.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="e1e6d-137">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1e6d-138">範例</span><span class="sxs-lookup"><span data-stu-id="e1e6d-138">Example</span></span>  
 <span data-ttu-id="e1e6d-139">下列範例會建立 XML 文件具有 XML 宣告、 處理指示、 註解和包含另一個項目。</span><span class="sxs-lookup"><span data-stu-id="e1e6d-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 <span data-ttu-id="e1e6d-140">[!code-vb[VbXMLSamples #&30;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e1e6d-140">[!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e6d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1e6d-141">See Also</span></span>  
 <span data-ttu-id="e1e6d-142"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="e1e6d-142"><xref:System.Xml.Linq.XElement></span></span>   
 <span data-ttu-id="e1e6d-143"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="e1e6d-143"><xref:System.Xml.Linq.XProcessingInstruction></span></span>   
 <span data-ttu-id="e1e6d-144"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="e1e6d-144"><xref:System.Xml.Linq.XComment></span></span>   
 <span data-ttu-id="e1e6d-145"><xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="e1e6d-145"><xref:System.Xml.Linq.XDocument></span></span>   
<span data-ttu-id="e1e6d-146"> [XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md) </span><span class="sxs-lookup"><span data-stu-id="e1e6d-146"> [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md) </span></span>  
<span data-ttu-id="e1e6d-147"> [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span><span class="sxs-lookup"><span data-stu-id="e1e6d-147"> [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span></span>  
<span data-ttu-id="e1e6d-148"> [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="e1e6d-148"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="e1e6d-149"> [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="e1e6d-149"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="e1e6d-150"> [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="e1e6d-150"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="e1e6d-151"> [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)</span><span class="sxs-lookup"><span data-stu-id="e1e6d-151"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)</span></span>
