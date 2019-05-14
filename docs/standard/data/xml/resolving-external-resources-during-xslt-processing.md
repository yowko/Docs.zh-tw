---
title: XSLT 處理期間解析外部資源
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bcd45a97ab0f0b0ac462d50c18fb68f9d7bd386
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590032"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="e5eff-102">XSLT 處理期間解析外部資源</span><span class="sxs-lookup"><span data-stu-id="e5eff-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="e5eff-103">在 XSLT 轉換期間，您可能需要進行數次外部資源解析。</span><span class="sxs-lookup"><span data-stu-id="e5eff-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="e5eff-104">使用 XmlResolver 類別</span><span class="sxs-lookup"><span data-stu-id="e5eff-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="e5eff-105"><xref:System.Xml.XmlResolver> 類別可用於解析外部資源。</span><span class="sxs-lookup"><span data-stu-id="e5eff-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="e5eff-106">下表說明在 XSLT 處理期間何時會使用 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="e5eff-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="e5eff-107">XSLT 工作</span><span class="sxs-lookup"><span data-stu-id="e5eff-107">XSLT task</span></span>|<span data-ttu-id="e5eff-108">XmlResolver 的用途</span><span class="sxs-lookup"><span data-stu-id="e5eff-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="e5eff-109">編譯樣式表。</span><span class="sxs-lookup"><span data-stu-id="e5eff-109">Compile the style sheet.</span></span>|<span data-ttu-id="e5eff-110">解析樣式表的 URI。</span><span class="sxs-lookup"><span data-stu-id="e5eff-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="e5eff-111">-和-</span><span class="sxs-lookup"><span data-stu-id="e5eff-111">-and-</span></span><br /><br /> <span data-ttu-id="e5eff-112">在任意 `xsl:import` 或 `xsl:include` 項目中解析 URI 參考。</span><span class="sxs-lookup"><span data-stu-id="e5eff-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="e5eff-113">執行樣式表。</span><span class="sxs-lookup"><span data-stu-id="e5eff-113">Execute the style sheet.</span></span>|<span data-ttu-id="e5eff-114">解析內容文件的 URI。</span><span class="sxs-lookup"><span data-stu-id="e5eff-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="e5eff-115">-和-</span><span class="sxs-lookup"><span data-stu-id="e5eff-115">-and-</span></span><br /><br /> <span data-ttu-id="e5eff-116">在任意 XSLT `document()` 函式中解析 URI 參考。</span><span class="sxs-lookup"><span data-stu-id="e5eff-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="e5eff-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 及 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法包括將 <xref:System.Xml.XmlResolver> 物件做為其中一個引數的多載。</span><span class="sxs-lookup"><span data-stu-id="e5eff-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="e5eff-118">如果未指定 <xref:System.Xml.XmlResolver>，則會使用沒有任何認證的預設 <xref:System.Xml.XmlUrlResolver>。</span><span class="sxs-lookup"><span data-stu-id="e5eff-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="e5eff-119">下列清單說明何時您可能想要指定 <xref:System.Xml.XmlResolver> 物件：</span><span class="sxs-lookup"><span data-stu-id="e5eff-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="e5eff-120">如果 XSLT 處理序需要存取需要驗證的網路資源，可使用具有必要認證的 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="e5eff-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="e5eff-121">如果要限制 XSLT 處理序可存取的資源，您可使用具有正確使用權限集合的 <xref:System.Xml.XmlSecureResolver>。</span><span class="sxs-lookup"><span data-stu-id="e5eff-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="e5eff-122">如果您需要開啟不是由您控制或不受信任的資源，請使用 <xref:System.Xml.XmlSecureResolver> 類別。</span><span class="sxs-lookup"><span data-stu-id="e5eff-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="e5eff-123">如果要自訂行為，可實作自己的 <xref:System.Xml.XmlResolver> 類別，然後使用它來解析資源。</span><span class="sxs-lookup"><span data-stu-id="e5eff-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="e5eff-124">如果要確保不存取任何外部資源，您可對 `null` 引數指定 <xref:System.Xml.XmlResolver>。</span><span class="sxs-lookup"><span data-stu-id="e5eff-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5eff-125">範例</span><span class="sxs-lookup"><span data-stu-id="e5eff-125">Example</span></span>  
 <span data-ttu-id="e5eff-126">下列範例編譯了儲存在網路資源上的樣式表。</span><span class="sxs-lookup"><span data-stu-id="e5eff-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="e5eff-127"><xref:System.Xml.XmlUrlResolver> 物件指定存取樣式表所需的認證。</span><span class="sxs-lookup"><span data-stu-id="e5eff-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e5eff-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5eff-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="e5eff-129">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="e5eff-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
