---
title: "XSLT 安全性考量"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fea695be-617c-4977-9567-140e820436fc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 560a0866a526caf4c8fe129209d0077374306a9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-security-considerations"></a><span data-ttu-id="58ed0-102">XSLT 安全性考量</span><span class="sxs-lookup"><span data-stu-id="58ed0-102">XSLT Security Considerations</span></span>
<span data-ttu-id="58ed0-103">XSLT 語言具有一組豐富的功能，可讓您擁有強大的能力與彈性。</span><span class="sxs-lookup"><span data-stu-id="58ed0-103">The XSLT language has a rich set of features that give you a great deal of power and flexibility.</span></span> <span data-ttu-id="58ed0-104">它還包含許多可由外部來源利用的功能 (若有幫助)。</span><span class="sxs-lookup"><span data-stu-id="58ed0-104">It includes many features that, while useful, could also be exploited by outside sources.</span></span> <span data-ttu-id="58ed0-105">若要安全使用 XSLT，您必須瞭解使用 XSLT 時會出現的各種安全性問題，以及為了減緩這些危險可使用的基本策略。</span><span class="sxs-lookup"><span data-stu-id="58ed0-105">In order to use XSLT safely, you must understand the types of security issues that arise when using XSLT, and the basic strategies that you can employ to mitigate these risks.</span></span>  
  
## <a name="xslt-extensions"></a><span data-ttu-id="58ed0-106">XSLT 擴充</span><span class="sxs-lookup"><span data-stu-id="58ed0-106">XSLT Extensions</span></span>  
 <span data-ttu-id="58ed0-107">兩個普遍使用的 XSLT 擴充為樣式表指令碼及擴充物件。</span><span class="sxs-lookup"><span data-stu-id="58ed0-107">Two popular XSLT extensions are style sheet scripting and extension objects.</span></span> <span data-ttu-id="58ed0-108">這些擴充允許 XSLT 處理器執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="58ed0-108">These extensions allow the XSLT processor to execute code.</span></span>  
  
-   <span data-ttu-id="58ed0-109">擴充物件會將程式設計功能加入至 XSL 轉換。</span><span class="sxs-lookup"><span data-stu-id="58ed0-109">Extension objects add programming capabilities to XSL transformations.</span></span>  
  
-   <span data-ttu-id="58ed0-110">指令碼可透過 `msxsl:script` 擴充項目內嵌在樣式表中。</span><span class="sxs-lookup"><span data-stu-id="58ed0-110">Scripts can be embedded in the style sheet using the `msxsl:script` extension element.</span></span>  
  
### <a name="extension-objects"></a><span data-ttu-id="58ed0-111">擴充物件</span><span class="sxs-lookup"><span data-stu-id="58ed0-111">Extension Objects</span></span>  
 <span data-ttu-id="58ed0-112">擴充物件可透過 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法加入。</span><span class="sxs-lookup"><span data-stu-id="58ed0-112">Extension objects are added using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="58ed0-113">FullTrust 使用權限集合必須支援擴充物件。</span><span class="sxs-lookup"><span data-stu-id="58ed0-113">The FullTrust permission set is required to support extension objects.</span></span> <span data-ttu-id="58ed0-114">這會確保在執行擴充物件程式碼時不會提高使用權限。</span><span class="sxs-lookup"><span data-stu-id="58ed0-114">This ensures that elevation of permissions does not happen when extension object code is executed.</span></span> <span data-ttu-id="58ed0-115">嘗試呼叫沒有 FullTrust 使用權限的 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法，會導致擲回安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="58ed0-115">Attempting to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method without FullTrust permissions results in a security exception being thrown.</span></span>  
  
### <a name="style-sheet-scripts"></a><span data-ttu-id="58ed0-116">樣式表指令碼</span><span class="sxs-lookup"><span data-stu-id="58ed0-116">Style Sheet Scripts</span></span>  
 <span data-ttu-id="58ed0-117">指令碼可透過 `msxsl:script` 擴充項目內嵌在樣式表中。</span><span class="sxs-lookup"><span data-stu-id="58ed0-117">Scripts can be embedded in a style sheet using the `msxsl:script` extension element.</span></span> <span data-ttu-id="58ed0-118">指令碼支援是 <xref:System.Xml.Xsl.XslCompiledTransform> 類別上的選擇性功能 (預設為停用)。</span><span class="sxs-lookup"><span data-stu-id="58ed0-118">Script support is an optional feature on the <xref:System.Xml.Xsl.XslCompiledTransform> class that is disabled by default.</span></span> <span data-ttu-id="58ed0-119">可透過將 <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> 屬性設為 `true`，並將 <xref:System.Xml.Xsl.XsltSettings> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法，即可啟用指令碼。</span><span class="sxs-lookup"><span data-stu-id="58ed0-119">Scripting can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="58ed0-120">方針</span><span class="sxs-lookup"><span data-stu-id="58ed0-120">Guidelines</span></span>  
 <span data-ttu-id="58ed0-121">僅在樣式表來自受信任來源時啟用指令碼。</span><span class="sxs-lookup"><span data-stu-id="58ed0-121">Enable scripting only when the style sheet comes from a trusted source.</span></span> <span data-ttu-id="58ed0-122">如果無法驗證樣式表的來源，或樣式表不是來自受信任來源，請傳入 `null` 做為 XSLT 設定引數。</span><span class="sxs-lookup"><span data-stu-id="58ed0-122">If you cannot verify the source of the style sheet, or if the style sheet does not come from a trusted source, pass in `null` for the XSLT settings argument.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="58ed0-123">外部資源</span><span class="sxs-lookup"><span data-stu-id="58ed0-123">External Resources</span></span>  
 <span data-ttu-id="58ed0-124">對於 XSLT 語言的某些功能 (如 `xsl:import`、`xsl:include` 或 `document()` 函式)，處理器需要解析 URI 參考。</span><span class="sxs-lookup"><span data-stu-id="58ed0-124">The XSLT language has features such as `xsl:import`, `xsl:include`, or the `document()` function, where the processor needs to resolve URI references.</span></span> <span data-ttu-id="58ed0-125"><xref:System.Xml.XmlResolver> 類別可用於解析外部資源。</span><span class="sxs-lookup"><span data-stu-id="58ed0-125">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="58ed0-126">在下列兩種情況下，可能需要解析外部資源：</span><span class="sxs-lookup"><span data-stu-id="58ed0-126">External resources may need to be resolved in the following two cases:</span></span>  
  
-   <span data-ttu-id="58ed0-127">編譯樣式表時，會使用 <xref:System.Xml.XmlResolver> 進行 `xsl:import` 及 `xsl:include` 解析。</span><span class="sxs-lookup"><span data-stu-id="58ed0-127">When compiling a style sheet, the <xref:System.Xml.XmlResolver> is used for `xsl:import` and `xsl:include` resolution.</span></span>  
  
-   <span data-ttu-id="58ed0-128">執行轉換時，會使用 <xref:System.Xml.XmlResolver> 解析 `document()` 函式。</span><span class="sxs-lookup"><span data-stu-id="58ed0-128">When executing the transformation, the <xref:System.Xml.XmlResolver> is used to resolve the `document()` function.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="58ed0-129">`document()` 函式在 <xref:System.Xml.Xsl.XslCompiledTransform> 類別上預設為停用。</span><span class="sxs-lookup"><span data-stu-id="58ed0-129">The `document()` function is disabled by default on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="58ed0-130">可透過將 <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> 屬性設為 `true`，並將 <xref:System.Xml.Xsl.XsltSettings> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法，即可啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="58ed0-130">This feature can be enabled by setting the <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> property to `true` and passing the <xref:System.Xml.Xsl.XsltSettings> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
 <span data-ttu-id="58ed0-131"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 及 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法都包含多載，可接受 <xref:System.Xml.XmlResolver> 做為其中一個引數。</span><span class="sxs-lookup"><span data-stu-id="58ed0-131">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods each include overloads that accept an <xref:System.Xml.XmlResolver> as one of its arguments.</span></span> <span data-ttu-id="58ed0-132">如果未指定 <xref:System.Xml.XmlResolver>，則會使用沒有任何認證的預設 <xref:System.Xml.XmlUrlResolver>。</span><span class="sxs-lookup"><span data-stu-id="58ed0-132">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
#### <a name="guidelines"></a><span data-ttu-id="58ed0-133">方針</span><span class="sxs-lookup"><span data-stu-id="58ed0-133">Guidelines</span></span>  
 <span data-ttu-id="58ed0-134">僅在樣式表來自受信任來源時啟用 `document()` 函式。</span><span class="sxs-lookup"><span data-stu-id="58ed0-134">Enable the `document()` function only when the style sheet comes from a trusted source.</span></span>  
  
 <span data-ttu-id="58ed0-135">下列清單說明何時您可能想要指定 <xref:System.Xml.XmlResolver> 物件：</span><span class="sxs-lookup"><span data-stu-id="58ed0-135">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
-   <span data-ttu-id="58ed0-136">如果 XSLT 處理序需要存取需要驗證的網路資源，可使用具有必要認證的 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="58ed0-136">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
-   <span data-ttu-id="58ed0-137">如果要限制 XSLT 處理序可存取的資源，您可使用具有正確使用權限集合的 <xref:System.Xml.XmlSecureResolver>。</span><span class="sxs-lookup"><span data-stu-id="58ed0-137">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="58ed0-138">如果您需要開啟不是由您控制或不受信任的資源，請使用 <xref:System.Xml.XmlSecureResolver> 類別。</span><span class="sxs-lookup"><span data-stu-id="58ed0-138">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
-   <span data-ttu-id="58ed0-139">如果要自訂行為，可實作自己的 <xref:System.Xml.XmlResolver> 類別，然後使用它來解析資源。</span><span class="sxs-lookup"><span data-stu-id="58ed0-139">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
-   <span data-ttu-id="58ed0-140">如果要確保不存取任何外部資源，您可對 `null` 引數指定 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="58ed0-140">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ed0-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58ed0-141">See Also</span></span>  
 [<span data-ttu-id="58ed0-142">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="58ed0-142">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="58ed0-143">在 XSLT 處理期間解析外部資源</span><span class="sxs-lookup"><span data-stu-id="58ed0-143">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 [<span data-ttu-id="58ed0-144">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="58ed0-144">Code Access Security</span></span>](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)
