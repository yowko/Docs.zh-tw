---
title: "XML 處理指示常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
dev_langs:
- VB
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
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
ms.openlocfilehash: 2ae976530ed3028677a1fef39db92265591df530
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="6a8b3-102">XML 處理指示常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a8b3-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="6a8b3-103">常值代表<xref:System.Xml.Linq.XProcessingInstruction>物件。</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="6a8b3-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a8b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a8b3-104">Syntax</span></span>  
  
```  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="6a8b3-105">組件</span><span class="sxs-lookup"><span data-stu-id="6a8b3-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="6a8b3-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-106">Required.</span></span> <span data-ttu-id="6a8b3-107">代表 XML 處理指示常值開始。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="6a8b3-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-108">Required.</span></span> <span data-ttu-id="6a8b3-109">名稱指出哪個應用程式處理指示目標。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="6a8b3-110">不能以"xml"或"XML"開頭。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="6a8b3-111">選擇項。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-111">Optional.</span></span> <span data-ttu-id="6a8b3-112">字串，表示應用程式的目標的方式`piName`應該處理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="6a8b3-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-113">Required.</span></span> <span data-ttu-id="6a8b3-114">代表處理指示的結尾。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a8b3-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="6a8b3-115">Return Value</span></span>  
 <span data-ttu-id="6a8b3-116"><xref:System.Xml.Linq.XProcessingInstruction>物件。</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="6a8b3-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a8b3-117">備註</span><span class="sxs-lookup"><span data-stu-id="6a8b3-117">Remarks</span></span>  
 <span data-ttu-id="6a8b3-118">XML 處理指示常值會指出應用程式應該如何處理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="6a8b3-119">當應用程式載入 XML 文件時，應用程式可以檢查以決定如何處理文件的 XML 處理指示。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="6a8b3-120">應用程式會將解譯的意義`piName`和`piData`。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="6a8b3-121">XML 文件常值會使用類似的 XML 處理指示的語法。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="6a8b3-122">如需詳細資訊，請參閱[XML 文件常值](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a8b3-123">`piName`項目開頭的字串"xml"或"XML"，因為 XML 1.0 規格會保留這些識別項。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="6a8b3-124">您可以指派給變數的 XML 處理指示常值或將它包含在 XML 文件常值。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a8b3-125">XML 常值可以跨越多行程式碼，而不需要行接續字元。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="6a8b3-126">這可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-126">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="6a8b3-127">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 處理指示常值轉換成呼叫<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="6a8b3-127">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a8b3-128">範例</span><span class="sxs-lookup"><span data-stu-id="6a8b3-128">Example</span></span>  
 <span data-ttu-id="6a8b3-129">下列範例會建立用來識別 XML 文件樣式表處理指示。</span><span class="sxs-lookup"><span data-stu-id="6a8b3-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 <span data-ttu-id="6a8b3-130">[!code-vb[VbXMLSamples #&28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6a8b3-130">[!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8b3-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a8b3-131">See Also</span></span>  
 <span data-ttu-id="6a8b3-132"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="6a8b3-132"><xref:System.Xml.Linq.XProcessingInstruction></span></span>   
<span data-ttu-id="6a8b3-133"> [XML 文件常值](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span><span class="sxs-lookup"><span data-stu-id="6a8b3-133"> [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span></span>  
<span data-ttu-id="6a8b3-134"> [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="6a8b3-134"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="6a8b3-135"> [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="6a8b3-135"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
