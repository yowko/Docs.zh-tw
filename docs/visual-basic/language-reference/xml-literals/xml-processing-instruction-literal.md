---
title: XML 處理指示常值 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3fbb16a4d47801b671d37566573215d3a57afff1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820148"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="1010d-102">XML 處理指示常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1010d-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="1010d-103">常值代表<xref:System.Xml.Linq.XProcessingInstruction>物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1010d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1010d-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="1010d-105">組件</span><span class="sxs-lookup"><span data-stu-id="1010d-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="1010d-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="1010d-106">Required.</span></span> <span data-ttu-id="1010d-107">代表 XML 處理指示常值的開頭。</span><span class="sxs-lookup"><span data-stu-id="1010d-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="1010d-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="1010d-108">Required.</span></span> <span data-ttu-id="1010d-109">名稱指出哪個應用程式的處理指示目標。</span><span class="sxs-lookup"><span data-stu-id="1010d-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="1010d-110">無法以"xml"或"XML"開頭。</span><span class="sxs-lookup"><span data-stu-id="1010d-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="1010d-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1010d-111">Optional.</span></span> <span data-ttu-id="1010d-112">字串，表示應用程式設為目標的`piName`應該處理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1010d-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="1010d-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="1010d-113">Required.</span></span> <span data-ttu-id="1010d-114">代表處理指示的結尾。</span><span class="sxs-lookup"><span data-stu-id="1010d-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1010d-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="1010d-115">Return Value</span></span>  
 <span data-ttu-id="1010d-116"><xref:System.Xml.Linq.XProcessingInstruction> 物件。</span><span class="sxs-lookup"><span data-stu-id="1010d-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1010d-117">備註</span><span class="sxs-lookup"><span data-stu-id="1010d-117">Remarks</span></span>  
 <span data-ttu-id="1010d-118">XML 處理指示常值會指出應用程式應該如何處理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1010d-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="1010d-119">當應用程式載入 XML 文件時，應用程式可以檢查以判斷如何處理文件的 XML 處理指示。</span><span class="sxs-lookup"><span data-stu-id="1010d-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="1010d-120">應用程式會將解譯的意義`piName`和`piData`。</span><span class="sxs-lookup"><span data-stu-id="1010d-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="1010d-121">XML 文件常值會使用類似的 XML 處理指示的語法。</span><span class="sxs-lookup"><span data-stu-id="1010d-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="1010d-122">如需詳細資訊，請參閱 < [XML 文件常值](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="1010d-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1010d-123">`piName`與字串"xml"或"XML"，無法開始項目，因為 XML 1.0 規格會保留這些識別項。</span><span class="sxs-lookup"><span data-stu-id="1010d-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="1010d-124">您可以指派給變數的 XML 處理指示常值，或將它包含在 XML 文件常值。</span><span class="sxs-lookup"><span data-stu-id="1010d-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1010d-125">XML 常值可以跨越多行，而不需要行接續字元。</span><span class="sxs-lookup"><span data-stu-id="1010d-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="1010d-126">這可讓您從 XML 文件複製內容，並將它貼到 Visual Basic 程式直接。</span><span class="sxs-lookup"><span data-stu-id="1010d-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="1010d-127">Visual Basic 編譯器會將 XML 處理指示常值轉換成呼叫<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="1010d-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1010d-128">範例</span><span class="sxs-lookup"><span data-stu-id="1010d-128">Example</span></span>  
 <span data-ttu-id="1010d-129">下列範例會建立用來識別 XML 文件樣式表處理指示。</span><span class="sxs-lookup"><span data-stu-id="1010d-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="1010d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1010d-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="1010d-131">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="1010d-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="1010d-132">XML 常值</span><span class="sxs-lookup"><span data-stu-id="1010d-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="1010d-133">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="1010d-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
