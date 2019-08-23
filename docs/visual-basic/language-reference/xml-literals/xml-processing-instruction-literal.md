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
ms.openlocfilehash: c589d3f4ac6bbb9aa9b2b8f2535888bddbf9c934
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958473"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="73b07-102">XML 處理指示常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73b07-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="73b07-103">代表<xref:System.Xml.Linq.XProcessingInstruction>物件的常值。</span><span class="sxs-lookup"><span data-stu-id="73b07-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b07-104">語法</span><span class="sxs-lookup"><span data-stu-id="73b07-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="73b07-105">組件</span><span class="sxs-lookup"><span data-stu-id="73b07-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="73b07-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="73b07-106">Required.</span></span> <span data-ttu-id="73b07-107">表示 XML 處理指示常值的開頭。</span><span class="sxs-lookup"><span data-stu-id="73b07-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="73b07-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="73b07-108">Required.</span></span> <span data-ttu-id="73b07-109">指出處理指示以哪個應用程式為目標的名稱。</span><span class="sxs-lookup"><span data-stu-id="73b07-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="73b07-110">不能以 "xml" 或 "XML" 開頭。</span><span class="sxs-lookup"><span data-stu-id="73b07-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="73b07-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="73b07-111">Optional.</span></span> <span data-ttu-id="73b07-112">字串, 指出以`piName`為目標的應用程式應該如何處理 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="73b07-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="73b07-113">必要項。</span><span class="sxs-lookup"><span data-stu-id="73b07-113">Required.</span></span> <span data-ttu-id="73b07-114">表示處理指示的結尾。</span><span class="sxs-lookup"><span data-stu-id="73b07-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73b07-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="73b07-115">Return Value</span></span>  
 <span data-ttu-id="73b07-116"><xref:System.Xml.Linq.XProcessingInstruction> 物件。</span><span class="sxs-lookup"><span data-stu-id="73b07-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73b07-117">備註</span><span class="sxs-lookup"><span data-stu-id="73b07-117">Remarks</span></span>  
 <span data-ttu-id="73b07-118">XML 處理指示常值指出應用程式應該如何處理 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="73b07-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="73b07-119">當應用程式載入 XML 檔時, 應用程式可以檢查 XML 處理指示, 以決定如何處理檔。</span><span class="sxs-lookup"><span data-stu-id="73b07-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="73b07-120">應用程式會解讀`piName`和`piData`的意義。</span><span class="sxs-lookup"><span data-stu-id="73b07-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="73b07-121">XML 檔常值會使用類似于 XML 處理指示的語法。</span><span class="sxs-lookup"><span data-stu-id="73b07-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="73b07-122">如需詳細資訊, 請參閱[XML 檔常](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)值。</span><span class="sxs-lookup"><span data-stu-id="73b07-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73b07-123">`piName`元素的開頭不能是 "xml" 或 "xml" 字串, 因為 xml 1.0 規格會保留這些識別碼。</span><span class="sxs-lookup"><span data-stu-id="73b07-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="73b07-124">您可以將 XML 處理指示常值指派給變數, 或將它包含在 XML 檔常值中。</span><span class="sxs-lookup"><span data-stu-id="73b07-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73b07-125">XML 常值可以跨越多行, 而不需要行接續字元。</span><span class="sxs-lookup"><span data-stu-id="73b07-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="73b07-126">這可讓您從 XML 檔案複製內容, 並將它直接貼到 Visual Basic 程式中。</span><span class="sxs-lookup"><span data-stu-id="73b07-126">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="73b07-127">Visual Basic 編譯器會將 XML 處理指示常值轉換為對此<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>函式呼叫的呼叫。</span><span class="sxs-lookup"><span data-stu-id="73b07-127">The Visual Basic compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73b07-128">範例</span><span class="sxs-lookup"><span data-stu-id="73b07-128">Example</span></span>  
 <span data-ttu-id="73b07-129">下列範例會建立一個處理指示, 以識別 XML 檔的樣式表單。</span><span class="sxs-lookup"><span data-stu-id="73b07-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="73b07-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73b07-130">See also</span></span>

- <xref:System.Xml.Linq.XProcessingInstruction>
- [<span data-ttu-id="73b07-131">XML 文件常值</span><span class="sxs-lookup"><span data-stu-id="73b07-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [<span data-ttu-id="73b07-132">XML 常值</span><span class="sxs-lookup"><span data-stu-id="73b07-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="73b07-133">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="73b07-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
