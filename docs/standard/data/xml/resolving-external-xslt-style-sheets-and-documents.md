---
title: "解析外部的 XSLT 樣式表和文件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5e84935f9fff1f993a677d408287cd775269f03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a><span data-ttu-id="3a4f0-102">解析外部的 XSLT 樣式表和文件</span><span class="sxs-lookup"><span data-stu-id="3a4f0-102">Resolving External XSLT Style Sheets and Documents</span></span>
<span data-ttu-id="3a4f0-103">在轉換期間，您可能需要進行數次外部資源解析。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-103">There are several times during a transformation when you may need to resolve external resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a4f0-104"><xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="3a4f0-105">您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 <span data-ttu-id="3a4f0-106">在轉換期間，您可能需要進行數次外部資源解析：</span><span class="sxs-lookup"><span data-stu-id="3a4f0-106">There are several times during a transformation when you may need to resolve external resources:</span></span>  
  
-   <span data-ttu-id="3a4f0-107">在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間用來尋找外部樣式表。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-107">During the <xref:System.Xml.Xsl.XslTransform.Load%2A> to locate an external style sheet.</span></span>  
  
-   <span data-ttu-id="3a4f0-108">在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間，用來解析樣式表中找到的任何 `<xsl:include>` 或 `<xsl:import>` 項目。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-108">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to resolve any `<xsl:include>` or `<xsl:import>` elements found in the style sheet.</span></span>  
  
-   <span data-ttu-id="3a4f0-109">在 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 期間，用來解析任何 `document()` 函式。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-109">During <xref:System.Xml.Xsl.XslTransform.Transform%2A> to resolve any `document()` functions.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="3a4f0-110">使用 XmlResolver 類別</span><span class="sxs-lookup"><span data-stu-id="3a4f0-110">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="3a4f0-111">如果存取網路資源需要驗證，請使用具有可傳遞 <xref:System.Xml.Xsl.XslTransform.Load%2A> 物件之 <xref:System.Xml.XmlResolver> 參數的 <xref:System.Xml.XmlResolver> 方法，該物件具有必要的認證屬性集。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-111">If authentication is required to access a network resource, use the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that have an <xref:System.Xml.XmlResolver> parameter to pass the <xref:System.Xml.XmlResolver> object, which has the necessary credential properties set.</span></span>  
  
 <span data-ttu-id="3a4f0-112">若要使用自訂的 <xref:System.Xml.XmlResolver>，或需要指定不同的認證，可參考下表根據外部資源何時需進行解析所列出之必要的工作。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-112">If you have a custom <xref:System.Xml.XmlResolver> that you want to use, or if you need to specify different credentials, the following table lists the task required, depending on when the external resource needs resolution.</span></span>  
  
|<span data-ttu-id="3a4f0-113">需要解析的程序</span><span class="sxs-lookup"><span data-stu-id="3a4f0-113">What process requires resolution</span></span>|<span data-ttu-id="3a4f0-114">必要的工作</span><span class="sxs-lookup"><span data-stu-id="3a4f0-114">Task required</span></span>|  
|--------------------------------------|-------------------|  
|<span data-ttu-id="3a4f0-115">在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間用來尋找樣式表。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-115">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to locate the style sheet.</span></span>|<span data-ttu-id="3a4f0-116">若樣式表位於需要認證的資源上，請指定以 <xref:System.Xml.Xsl.XslTransform.Load%2A> 當做參數的多載 <xref:System.Xml.XmlResolver> 方法。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-116">Specify the overloaded <xref:System.Xml.Xsl.XslTransform.Load%2A> method that takes, as a parameter, an <xref:System.Xml.XmlResolver> if the style sheet is on a resource that requires credentials.</span></span>|  
|<span data-ttu-id="3a4f0-117">在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間用來解析 `<xsl:include>` 或 `<xsl:import>`。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-117">During <xref:System.Xml.Xsl.XslTransform.Load%2A> to resolve `<xsl:include>` or `<xsl:import>`.</span></span>|<span data-ttu-id="3a4f0-118">指定以 <xref:System.Xml.Xsl.XslTransform.Load%2A> 當做參數的多載 <xref:System.Xml.XmlResolver> 方法。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-118">Specify the overloaded <xref:System.Xml.Xsl.XslTransform.Load%2A> method that takes, as a parameter, an <xref:System.Xml.XmlResolver>.</span></span> <span data-ttu-id="3a4f0-119"><xref:System.Xml.XmlResolver> 是用來載入 `import` 或 `include` 陳述式所參考的樣式表。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-119">The <xref:System.Xml.XmlResolver> is used to load the style sheets referenced by the `import` or `include` statements.</span></span> <span data-ttu-id="3a4f0-120">若傳入 `null`，則不會解析外部資源。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-120">If you pass in `null`, the external resources are not resolved.</span></span>|  
|<span data-ttu-id="3a4f0-121">在轉換期間用來解析任何 `document()` 函式。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-121">During a transformation to resolve any `document()` functions.</span></span>|<span data-ttu-id="3a4f0-122">指定<xref:System.Xml.XmlResolver>使用轉換期間<xref:System.Xml.Xsl.XslTransform.Transform%2A>採用方法<xref:System.Xml.XmlResolver>引數。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-122">Specify the <xref:System.Xml.XmlResolver> during the transformation by using the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method that takes an <xref:System.Xml.XmlResolver> argument.</span></span>|  
  
 <span data-ttu-id="3a4f0-123">`document()`函式可擷取其他 XML 資源從樣式表，另外提供輸入資料流的初始 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-123">The `document()` function retrieves other XML resources from a style sheet, in addition to the initial XML data provided by the input stream.</span></span> <span data-ttu-id="3a4f0-124">由於此函式可併入能夠放置於其他位置的 XML 資料，因此您可以將含有 <xref:System.Xml.XmlResolver> 值的 `null` 提供給 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法，以防止 `document()` 函式的執行。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-124">Since this function allows the inclusion of XML data that can be located elsewhere, an <xref:System.Xml.XmlResolver> with a `null` value supplied to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method prevents the `document()` function from executing.</span></span> <span data-ttu-id="3a4f0-125">若要使用 `document()` 函式，除了具有適當的使用權限集合外，請使用以 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 當做參數的 <xref:System.Xml.XmlResolver> 方法。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-125">If you want to use the `document()` function, use the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method that takes an <xref:System.Xml.XmlResolver> as a parameter, in addition to having the appropriate permission set.</span></span>  
  
 <span data-ttu-id="3a4f0-126">如需 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法及其使用 <xref:System.Xml.XmlResolver> 的詳細資訊，請參閱 <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-126">For more information on the <xref:System.Xml.Xsl.XslTransform.Load%2A> method and its use of the <xref:System.Xml.XmlResolver>, see <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="3a4f0-127">呼叫 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法時，即會針對載入期間所提供的辨識項計算使用權限，接著將該使用權限集合指派給整個轉換程序。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-127">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at load time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="3a4f0-128">若 `document()` 函式試圖啟始的動作所需要之使用權限，在使用權限集合中找不到，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3a4f0-128">If the `document()` function attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a4f0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a4f0-129">See Also</span></span>  
 [<span data-ttu-id="3a4f0-130">使用 XslTransform 類別進行 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="3a4f0-130">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="3a4f0-131">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="3a4f0-131">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [<span data-ttu-id="3a4f0-132">XslTransform 的輸出</span><span class="sxs-lookup"><span data-stu-id="3a4f0-132">Outputs from an XslTransform</span></span>](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
 [<span data-ttu-id="3a4f0-133">不同的存放區上的 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="3a4f0-133">XSLT Transformations Over Different Stores</span></span>](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
 [<span data-ttu-id="3a4f0-134">樣式表參數和擴充物件的 XsltArgumentList</span><span class="sxs-lookup"><span data-stu-id="3a4f0-134">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
 [<span data-ttu-id="3a4f0-135">XSLT 樣式表指令碼使用\<msxsl: script ></span><span class="sxs-lookup"><span data-stu-id="3a4f0-135">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
 [<span data-ttu-id="3a4f0-136">支援 msxsl:node-set() 函式</span><span class="sxs-lookup"><span data-stu-id="3a4f0-136">Support for the msxsl:node-set() Function</span></span>](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
 [<span data-ttu-id="3a4f0-137">轉換中的 XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3a4f0-137">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="3a4f0-138">轉換中的 XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="3a4f0-138">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="3a4f0-139">XslTransform 的 XPathDocument 輸入</span><span class="sxs-lookup"><span data-stu-id="3a4f0-139">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="3a4f0-140">XslTransform 的 XmlDataDocument 輸入</span><span class="sxs-lookup"><span data-stu-id="3a4f0-140">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="3a4f0-141">XslTransform 的 XmlDocument 輸入</span><span class="sxs-lookup"><span data-stu-id="3a4f0-141">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
