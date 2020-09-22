---
title: XML 文件常值
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: bd1b2f43fce563af431d67b3817b05c7c1048314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866023"
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="40a36-102">XML 文件常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40a36-102">XML Document Literal (Visual Basic)</span></span>

<span data-ttu-id="40a36-103">代表物件的常值 <xref:System.Xml.Linq.XDocument> 。</span><span class="sxs-lookup"><span data-stu-id="40a36-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a36-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="40a36-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="40a36-105">組件</span><span class="sxs-lookup"><span data-stu-id="40a36-105">Parts</span></span>  
  
|<span data-ttu-id="40a36-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="40a36-106">Term</span></span>|<span data-ttu-id="40a36-107">定義</span><span class="sxs-lookup"><span data-stu-id="40a36-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="40a36-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="40a36-108">Optional.</span></span> <span data-ttu-id="40a36-109">常值文字，宣告檔所使用的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="40a36-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="40a36-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="40a36-110">Optional.</span></span> <span data-ttu-id="40a36-111">常值文字。</span><span class="sxs-lookup"><span data-stu-id="40a36-111">Literal text.</span></span> <span data-ttu-id="40a36-112">必須是 "yes" 或 "no"。</span><span class="sxs-lookup"><span data-stu-id="40a36-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="40a36-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="40a36-113">Optional.</span></span> <span data-ttu-id="40a36-114">XML 處理指示和 XML 批註的清單。</span><span class="sxs-lookup"><span data-stu-id="40a36-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="40a36-115">採用下列格式：</span><span class="sxs-lookup"><span data-stu-id="40a36-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="40a36-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="40a36-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="40a36-117">每個都 `piComment` 可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="40a36-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="40a36-118">-   [XML 處理指示常](xml-processing-instruction-literal.md)值。</span><span class="sxs-lookup"><span data-stu-id="40a36-118">-   [XML Processing Instruction Literal](xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="40a36-119">-   [XML 批註常](xml-comment-literal.md)值。</span><span class="sxs-lookup"><span data-stu-id="40a36-119">-   [XML Comment Literal](xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="40a36-120">必要。</span><span class="sxs-lookup"><span data-stu-id="40a36-120">Required.</span></span> <span data-ttu-id="40a36-121">檔的根項目。</span><span class="sxs-lookup"><span data-stu-id="40a36-121">Root element of the document.</span></span> <span data-ttu-id="40a36-122">格式為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="40a36-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="40a36-123">[XML 元素常](xml-element-literal.md)值。</span><span class="sxs-lookup"><span data-stu-id="40a36-123">[XML Element Literal](xml-element-literal.md).</span></span></li><li><span data-ttu-id="40a36-124">表單的內嵌運算式 `<%=` `elementExp` `%>` 。</span><span class="sxs-lookup"><span data-stu-id="40a36-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="40a36-125">會傳回 `elementExp` 下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="40a36-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="40a36-126"><xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="40a36-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="40a36-127">集合，其中包含一個 <xref:System.Xml.Linq.XElement> 物件和任何數目的 <xref:System.Xml.Linq.XProcessingInstruction> 和 <xref:System.Xml.Linq.XComment> 物件。</span><span class="sxs-lookup"><span data-stu-id="40a36-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="40a36-128">如需詳細資訊，請參閱 [XML 中的內嵌運算式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="40a36-128">For more information, see [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="40a36-129">傳回值</span><span class="sxs-lookup"><span data-stu-id="40a36-129">Return Value</span></span>  

 <span data-ttu-id="40a36-130"><xref:System.Xml.Linq.XDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="40a36-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40a36-131">備註</span><span class="sxs-lookup"><span data-stu-id="40a36-131">Remarks</span></span>  

 <span data-ttu-id="40a36-132">XML 檔常值是由常值開頭的 XML 宣告所識別。</span><span class="sxs-lookup"><span data-stu-id="40a36-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="40a36-133">雖然每個 XML 檔常值都必須只有一個根 XML 元素，但它可以有任意數目的 XML 處理指示和 XML 批註。</span><span class="sxs-lookup"><span data-stu-id="40a36-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="40a36-134">Xml 檔常值不能出現在 XML 元素中。</span><span class="sxs-lookup"><span data-stu-id="40a36-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40a36-135">XML 常值可以跨多行，而不使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="40a36-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="40a36-136">這可讓您從 XML 檔案複製內容，並將它直接貼到 Visual Basic 程式中。</span><span class="sxs-lookup"><span data-stu-id="40a36-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="40a36-137">Visual Basic 編譯器會將 XML 檔常值轉換為和函式的呼叫 <xref:System.Xml.Linq.XDocument.%23ctor%2A> <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="40a36-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a36-138">範例</span><span class="sxs-lookup"><span data-stu-id="40a36-138">Example</span></span>  

 <span data-ttu-id="40a36-139">下列範例會建立 XML 檔，其中包含 XML 宣告、處理指示、批註，以及包含其他元素的元素。</span><span class="sxs-lookup"><span data-stu-id="40a36-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="40a36-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40a36-140">See also</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [<span data-ttu-id="40a36-141">XML 處理指示常值</span><span class="sxs-lookup"><span data-stu-id="40a36-141">XML Processing Instruction Literal</span></span>](xml-processing-instruction-literal.md)
- [<span data-ttu-id="40a36-142">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="40a36-142">XML Comment Literal</span></span>](xml-comment-literal.md)
- [<span data-ttu-id="40a36-143">XML 元素常值</span><span class="sxs-lookup"><span data-stu-id="40a36-143">XML Element Literal</span></span>](xml-element-literal.md)
- [<span data-ttu-id="40a36-144">XML 常值</span><span class="sxs-lookup"><span data-stu-id="40a36-144">XML Literals</span></span>](index.md)
- [<span data-ttu-id="40a36-145">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="40a36-145">Creating XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="40a36-146">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="40a36-146">Embedded Expressions in XML</span></span>](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
