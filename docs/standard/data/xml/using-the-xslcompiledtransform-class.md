---
title: 使用 XslCompiledTransform 類別
ms.date: 03/30/2017
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: cdcbb803fee8eba2b05c7ca12208dbf9c5ad0f7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675603"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="6e581-102">使用 XslCompiledTransform 類別</span><span class="sxs-lookup"><span data-stu-id="6e581-102">Using the XslCompiledTransform Class</span></span>

<span data-ttu-id="6e581-103"><xref:System.Xml.Xsl.XslCompiledTransform> 類別為 Microsoft .NET Framework XSLT 處理器。</span><span class="sxs-lookup"><span data-stu-id="6e581-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="6e581-104">此類別用於編譯樣式表，並執行 XSLT 轉換。</span><span class="sxs-lookup"><span data-stu-id="6e581-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e581-105">雖然 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的整體效能優於 <xref:System.Xml.Xsl.XslTransform> 類別，但是在轉換時第一次呼叫 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 類別的 <xref:System.Xml.Xsl.XslCompiledTransform> 方法之執行速度可能會比 <xref:System.Xml.Xsl.XslTransform.Load%2A> 類別的 <xref:System.Xml.Xsl.XslTransform> 方法慢許多。</span><span class="sxs-lookup"><span data-stu-id="6e581-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="6e581-106">這是因為在載入之前必須先編譯 XSLT 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e581-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="6e581-107">如需詳細資訊，請參閱下列部落格文章：[XslCompiledTransform 比 XslTransform 還慢嗎？](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform) (英文)</span><span class="sxs-lookup"><span data-stu-id="6e581-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e581-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="6e581-108">In This Section</span></span>  

 [<span data-ttu-id="6e581-109">XslCompiledTransform 類別的輸入</span><span class="sxs-lookup"><span data-stu-id="6e581-109">Inputs to the XslCompiledTransform Class</span></span>](inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="6e581-110">說明可用的 XSLT 輸入選項。</span><span class="sxs-lookup"><span data-stu-id="6e581-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="6e581-111">XslCompiledTransform 類別的輸出選項</span><span class="sxs-lookup"><span data-stu-id="6e581-111">Output Options on the XslCompiledTransform Class</span></span>](output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="6e581-112">說明可用的 XSLT 輸出選項。</span><span class="sxs-lookup"><span data-stu-id="6e581-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="6e581-113">XSLT 處理期間解析外部資源</span><span class="sxs-lookup"><span data-stu-id="6e581-113">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="6e581-114">討論如何使用 <xref:System.Xml.XmlResolver> 類別解析外部資源。</span><span class="sxs-lookup"><span data-stu-id="6e581-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="6e581-115">延伸 XSLT 樣式表</span><span class="sxs-lookup"><span data-stu-id="6e581-115">Extending XSLT Style Sheets</span></span>](extending-xslt-style-sheets.md)  
 <span data-ttu-id="6e581-116">討論如何支援 XSLT 擴充。</span><span class="sxs-lookup"><span data-stu-id="6e581-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="6e581-117">可復原的 XSLT 錯誤</span><span class="sxs-lookup"><span data-stu-id="6e581-117">Recoverable XSLT Errors</span></span>](recoverable-xslt-errors.md)|<span data-ttu-id="6e581-118">列出全球資訊網協會 (W3C) XSLT 1.0 版建議事項所允許的判別行為，以及說明 <xref:System.Xml.Xsl.XslCompiledTransform> 類別如何處理這些行為。</span><span class="sxs-lookup"><span data-stu-id="6e581-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="6e581-119">作法：轉換節點片段</span><span class="sxs-lookup"><span data-stu-id="6e581-119">How to: Transform a Node Fragment</span></span>](how-to-transform-a-node-fragment.md)|<span data-ttu-id="6e581-120">描述如何轉換節點片段。</span><span class="sxs-lookup"><span data-stu-id="6e581-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="6e581-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="6e581-121">Related Sections</span></span>  

 [<span data-ttu-id="6e581-122">從 XslTransform 類別移轉</span><span class="sxs-lookup"><span data-stu-id="6e581-122">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="6e581-123">討論如何從 <xref:System.Xml.Xsl.XslTransform> 類別移轉程式碼</span><span class="sxs-lookup"><span data-stu-id="6e581-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e581-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e581-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
