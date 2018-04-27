---
title: XML 處理指示常值 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d2df93a46d426358988b3ad7f3161c7ae0c7b9e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="7f9df-102">XML 處理指示常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f9df-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="7f9df-103">常值代表<xref:System.Xml.Linq.XProcessingInstruction>物件。</span><span class="sxs-lookup"><span data-stu-id="7f9df-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9df-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f9df-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="7f9df-105">組件</span><span class="sxs-lookup"><span data-stu-id="7f9df-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="7f9df-106">必要。</span><span class="sxs-lookup"><span data-stu-id="7f9df-106">Required.</span></span> <span data-ttu-id="7f9df-107">代表 XML 處理指示常值的開始。</span><span class="sxs-lookup"><span data-stu-id="7f9df-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="7f9df-108">必要。</span><span class="sxs-lookup"><span data-stu-id="7f9df-108">Required.</span></span> <span data-ttu-id="7f9df-109">名稱指出哪個應用程式處理指示目標。</span><span class="sxs-lookup"><span data-stu-id="7f9df-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="7f9df-110">無法以"xml"或"XML"開頭。</span><span class="sxs-lookup"><span data-stu-id="7f9df-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="7f9df-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7f9df-111">Optional.</span></span> <span data-ttu-id="7f9df-112">字串，表示如何在應用程式做為目標`piName`應該處理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="7f9df-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="7f9df-113">必要。</span><span class="sxs-lookup"><span data-stu-id="7f9df-113">Required.</span></span> <span data-ttu-id="7f9df-114">代表處理指示的結尾。</span><span class="sxs-lookup"><span data-stu-id="7f9df-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f9df-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="7f9df-115">Return Value</span></span>  
 <span data-ttu-id="7f9df-116"><xref:System.Xml.Linq.XProcessingInstruction> 物件。</span><span class="sxs-lookup"><span data-stu-id="7f9df-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f9df-117">備註</span><span class="sxs-lookup"><span data-stu-id="7f9df-117">Remarks</span></span>  
 <span data-ttu-id="7f9df-118">XML 處理指示常值會指出應用程式應該如何處理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="7f9df-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="7f9df-119">當應用程式載入的 XML 文件時，應用程式可以檢查以決定如何處理文件的 XML 處理指示。</span><span class="sxs-lookup"><span data-stu-id="7f9df-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="7f9df-120">應用程式會將解譯的意義`piName`和`piData`。</span><span class="sxs-lookup"><span data-stu-id="7f9df-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="7f9df-121">XML 文件常值會使用類似的 XML 處理指示的語法。</span><span class="sxs-lookup"><span data-stu-id="7f9df-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="7f9df-122">如需詳細資訊，請參閱[XML 文件常值](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="7f9df-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f9df-123">`piName`與字串"xml"或"XML"，無法開始項目，因為 XML 1.0 規格會保留這些識別項。</span><span class="sxs-lookup"><span data-stu-id="7f9df-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="7f9df-124">您可以指派給變數的 XML 處理指示常值，或將它包含在 XML 文件常值。</span><span class="sxs-lookup"><span data-stu-id="7f9df-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f9df-125">XML 常值可以跨越多行，而不需行接續字元。</span><span class="sxs-lookup"><span data-stu-id="7f9df-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="7f9df-126">這可讓您從 XML 文件內容複製並貼上直接在 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="7f9df-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="7f9df-127">Visual Basic 編譯器會將 XML 處理指示常值轉換成呼叫<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="7f9df-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f9df-128">範例</span><span class="sxs-lookup"><span data-stu-id="7f9df-128">Example</span></span>  
 <span data-ttu-id="7f9df-129">下列範例會建立用來識別 XML 文件樣式表處理指示。</span><span class="sxs-lookup"><span data-stu-id="7f9df-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7f9df-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f9df-130">See Also</span></span>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [<span data-ttu-id="7f9df-131">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="7f9df-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="7f9df-132">XML 常值</span><span class="sxs-lookup"><span data-stu-id="7f9df-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="7f9df-133">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="7f9df-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
