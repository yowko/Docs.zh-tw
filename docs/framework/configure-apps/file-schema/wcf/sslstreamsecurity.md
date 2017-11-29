---
title: '&lt;sslStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5c801562339f02ff983bb5a755fda6718185ba5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="3ec47-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="3ec47-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="3ec47-103">代表使用 SSL 資料流支援通道安全性的自訂繫結元素。</span><span class="sxs-lookup"><span data-stu-id="3ec47-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="3ec47-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3ec47-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3ec47-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="3ec47-105">\<bindings></span></span>  
<span data-ttu-id="3ec47-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3ec47-106">\<customBinding></span></span>  
<span data-ttu-id="3ec47-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="3ec47-107">\<binding></span></span>  
<span data-ttu-id="3ec47-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="3ec47-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec47-109">語法</span><span class="sxs-lookup"><span data-stu-id="3ec47-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ec47-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3ec47-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ec47-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3ec47-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ec47-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3ec47-112">Attributes</span></span>  
  
|<span data-ttu-id="3ec47-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3ec47-113">Attribute</span></span>|<span data-ttu-id="3ec47-114">描述</span><span class="sxs-lookup"><span data-stu-id="3ec47-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ec47-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="3ec47-115">requireClientCertificate</span></span>|<span data-ttu-id="3ec47-116">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="3ec47-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="3ec47-117">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3ec47-117">The default is `false`.</span></span>|  
|<span data-ttu-id="3ec47-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="3ec47-118">sslProtocols</span></span>|<span data-ttu-id="3ec47-119">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="3ec47-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="3ec47-120">預設值是 Ssl3 &#124;Tls &#124;Tls11 &#124; Tls12。</span><span class="sxs-lookup"><span data-stu-id="3ec47-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ec47-121">子元素</span><span class="sxs-lookup"><span data-stu-id="3ec47-121">Child Elements</span></span>  
 <span data-ttu-id="3ec47-122">無。</span><span class="sxs-lookup"><span data-stu-id="3ec47-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ec47-123">父項目</span><span class="sxs-lookup"><span data-stu-id="3ec47-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3ec47-124">項目</span><span class="sxs-lookup"><span data-stu-id="3ec47-124">Element</span></span>|<span data-ttu-id="3ec47-125">說明</span><span class="sxs-lookup"><span data-stu-id="3ec47-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ec47-126">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="3ec47-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3ec47-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="3ec47-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ec47-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ec47-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="3ec47-129">繫結</span><span class="sxs-lookup"><span data-stu-id="3ec47-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3ec47-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="3ec47-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="3ec47-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3ec47-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="3ec47-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="3ec47-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
