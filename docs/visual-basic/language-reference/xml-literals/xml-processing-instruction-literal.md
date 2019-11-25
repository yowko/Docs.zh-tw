---
title: XML 處理指示常值
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347038"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="fe48b-102">XML 處理指示常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe48b-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="fe48b-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span><span class="sxs-lookup"><span data-stu-id="fe48b-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe48b-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe48b-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="fe48b-105">組件</span><span class="sxs-lookup"><span data-stu-id="fe48b-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="fe48b-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="fe48b-106">Required.</span></span> <span data-ttu-id="fe48b-107">Denotes the start of the XML processing instruction literal.</span><span class="sxs-lookup"><span data-stu-id="fe48b-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="fe48b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="fe48b-108">Required.</span></span> <span data-ttu-id="fe48b-109">Name indicating which application the processing instruction targets.</span><span class="sxs-lookup"><span data-stu-id="fe48b-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="fe48b-110">Cannot begin with "xml" or "XML".</span><span class="sxs-lookup"><span data-stu-id="fe48b-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="fe48b-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="fe48b-111">Optional.</span></span> <span data-ttu-id="fe48b-112">String indicating how the application targeted by `piName` should process the XML document.</span><span class="sxs-lookup"><span data-stu-id="fe48b-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="fe48b-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="fe48b-113">Required.</span></span> <span data-ttu-id="fe48b-114">Denotes the end of the processing instruction.</span><span class="sxs-lookup"><span data-stu-id="fe48b-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe48b-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe48b-115">Return Value</span></span>  
 <span data-ttu-id="fe48b-116"><xref:System.Xml.Linq.XProcessingInstruction> 物件。</span><span class="sxs-lookup"><span data-stu-id="fe48b-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe48b-117">備註</span><span class="sxs-lookup"><span data-stu-id="fe48b-117">Remarks</span></span>  
 <span data-ttu-id="fe48b-118">XML processing instruction literals indicate how applications should process an XML document.</span><span class="sxs-lookup"><span data-stu-id="fe48b-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="fe48b-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span><span class="sxs-lookup"><span data-stu-id="fe48b-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="fe48b-120">The application interprets the meaning of `piName` and `piData`.</span><span class="sxs-lookup"><span data-stu-id="fe48b-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="fe48b-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span><span class="sxs-lookup"><span data-stu-id="fe48b-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="fe48b-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="fe48b-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe48b-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span><span class="sxs-lookup"><span data-stu-id="fe48b-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="fe48b-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span><span class="sxs-lookup"><span data-stu-id="fe48b-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe48b-125">An XML literal can span multiple lines without needing line continuation characters.</span><span class="sxs-lookup"><span data-stu-id="fe48b-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="fe48b-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span><span class="sxs-lookup"><span data-stu-id="fe48b-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="fe48b-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span><span class="sxs-lookup"><span data-stu-id="fe48b-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe48b-128">範例</span><span class="sxs-lookup"><span data-stu-id="fe48b-128">Example</span></span>  
 <span data-ttu-id="fe48b-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span><span class="sxs-lookup"><span data-stu-id="fe48b-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="fe48b-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe48b-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="fe48b-131">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="fe48b-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="fe48b-132">XML 常值</span><span class="sxs-lookup"><span data-stu-id="fe48b-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="fe48b-133">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="fe48b-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
