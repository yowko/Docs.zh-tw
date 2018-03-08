---
title: "使用 XslCompiledTransform 類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a00ae5a2f54aee3d6ac16d0870f9171fe42ca289
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="291b1-102">使用 XslCompiledTransform 類別</span><span class="sxs-lookup"><span data-stu-id="291b1-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="291b1-103"><xref:System.Xml.Xsl.XslCompiledTransform> 類別為 Microsoft .NET Framework XSLT 處理器。</span><span class="sxs-lookup"><span data-stu-id="291b1-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="291b1-104">此類別用於編譯樣式表，並執行 XSLT 轉換。</span><span class="sxs-lookup"><span data-stu-id="291b1-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="291b1-105">雖然 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的整體效能優於 <xref:System.Xml.Xsl.XslTransform> 類別，但是在轉換時第一次呼叫 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 類別的 <xref:System.Xml.Xsl.XslCompiledTransform> 方法之執行速度可能會比 <xref:System.Xml.Xsl.XslTransform.Load%2A> 類別的 <xref:System.Xml.Xsl.XslTransform> 方法慢許多。</span><span class="sxs-lookup"><span data-stu-id="291b1-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="291b1-106">這是因為在載入之前必須先編譯 XSLT 檔案。</span><span class="sxs-lookup"><span data-stu-id="291b1-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="291b1-107">如需詳細資訊，請參閱下列部落格文章：[XslCompiledTransform 比 XslTransform 還慢嗎？](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/) (英文)</span><span class="sxs-lookup"><span data-stu-id="291b1-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="291b1-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="291b1-108">In This Section</span></span>  
 [<span data-ttu-id="291b1-109">XslCompiledTransform 類別的輸入</span><span class="sxs-lookup"><span data-stu-id="291b1-109">Inputs to the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="291b1-110">說明可用的 XSLT 輸入選項。</span><span class="sxs-lookup"><span data-stu-id="291b1-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="291b1-111">XslCompiledTransform 類別的輸出選項</span><span class="sxs-lookup"><span data-stu-id="291b1-111">Output Options on the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="291b1-112">說明可用的 XSLT 輸出選項。</span><span class="sxs-lookup"><span data-stu-id="291b1-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="291b1-113">XSLT 處理期間解析外部資源</span><span class="sxs-lookup"><span data-stu-id="291b1-113">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="291b1-114">討論如何使用 <xref:System.Xml.XmlResolver> 類別解析外部資源。</span><span class="sxs-lookup"><span data-stu-id="291b1-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="291b1-115">延伸 XSLT 樣式表</span><span class="sxs-lookup"><span data-stu-id="291b1-115">Extending XSLT Style Sheets</span></span>](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 <span data-ttu-id="291b1-116">討論如何支援 XSLT 擴充。</span><span class="sxs-lookup"><span data-stu-id="291b1-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="291b1-117">可復原的 XSLT 錯誤</span><span class="sxs-lookup"><span data-stu-id="291b1-117">Recoverable XSLT Errors</span></span>](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|<span data-ttu-id="291b1-118">列出全球資訊網協會 (W3C) XSLT 1.0 版建議事項所允許的判別行為，以及說明 <xref:System.Xml.Xsl.XslCompiledTransform> 類別如何處理這些行為。</span><span class="sxs-lookup"><span data-stu-id="291b1-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="291b1-119">如何：轉換節點片段</span><span class="sxs-lookup"><span data-stu-id="291b1-119">How to: Transform a Node Fragment</span></span>](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|<span data-ttu-id="291b1-120">描述如何轉換節點片段。</span><span class="sxs-lookup"><span data-stu-id="291b1-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="291b1-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="291b1-121">Related Sections</span></span>  
 [<span data-ttu-id="291b1-122">從 XslTransform 類別移轉</span><span class="sxs-lookup"><span data-stu-id="291b1-122">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="291b1-123">討論如何從 <xref:System.Xml.Xsl.XslTransform> 類別移轉程式碼</span><span class="sxs-lookup"><span data-stu-id="291b1-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291b1-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="291b1-124">See Also</span></span>  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
