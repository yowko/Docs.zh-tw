---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a86e1aae7ddd5389f098e532ae2c2cc67f4085e3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752399"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="6bc97-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="6bc97-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="6bc97-103">代表使用 SSL 資料流支援通道安全性的自訂繫結元素。</span><span class="sxs-lookup"><span data-stu-id="6bc97-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="6bc97-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6bc97-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6bc97-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="6bc97-105">\<bindings></span></span>  
<span data-ttu-id="6bc97-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6bc97-106">\<customBinding></span></span>  
<span data-ttu-id="6bc97-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="6bc97-107">\<binding></span></span>  
<span data-ttu-id="6bc97-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="6bc97-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc97-109">語法</span><span class="sxs-lookup"><span data-stu-id="6bc97-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bc97-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6bc97-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6bc97-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6bc97-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bc97-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6bc97-112">Attributes</span></span>  
  
|<span data-ttu-id="6bc97-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6bc97-113">Attribute</span></span>|<span data-ttu-id="6bc97-114">描述</span><span class="sxs-lookup"><span data-stu-id="6bc97-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6bc97-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="6bc97-115">requireClientCertificate</span></span>|<span data-ttu-id="6bc97-116">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="6bc97-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="6bc97-117">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6bc97-117">The default is `false`.</span></span>|  
|<span data-ttu-id="6bc97-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="6bc97-118">sslProtocols</span></span>|<span data-ttu-id="6bc97-119">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="6bc97-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="6bc97-120">預設值是 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="6bc97-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6bc97-121">子項目</span><span class="sxs-lookup"><span data-stu-id="6bc97-121">Child Elements</span></span>  
 <span data-ttu-id="6bc97-122">無。</span><span class="sxs-lookup"><span data-stu-id="6bc97-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6bc97-123">父項目</span><span class="sxs-lookup"><span data-stu-id="6bc97-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6bc97-124">項目</span><span class="sxs-lookup"><span data-stu-id="6bc97-124">Element</span></span>|<span data-ttu-id="6bc97-125">描述</span><span class="sxs-lookup"><span data-stu-id="6bc97-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bc97-126">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="6bc97-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6bc97-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="6bc97-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bc97-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bc97-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="6bc97-129">繫結</span><span class="sxs-lookup"><span data-stu-id="6bc97-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6bc97-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="6bc97-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="6bc97-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="6bc97-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="6bc97-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6bc97-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
