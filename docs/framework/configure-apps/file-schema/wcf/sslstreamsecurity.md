---
title: '&lt;Custombinding>&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: ecc67c2b3972ccb5bc8a1fe9ae9b400292642d53
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184487"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="2abec-102">&lt;Custombinding>&gt;</span><span class="sxs-lookup"><span data-stu-id="2abec-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="2abec-103">代表使用 SSL 資料流支援通道安全性的自訂繫結元素。</span><span class="sxs-lookup"><span data-stu-id="2abec-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="2abec-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2abec-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2abec-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2abec-105">\<bindings></span></span>  
<span data-ttu-id="2abec-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2abec-106">\<customBinding></span></span>  
<span data-ttu-id="2abec-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2abec-107">\<binding></span></span>  
<span data-ttu-id="2abec-108">\<Custombinding> ></span><span class="sxs-lookup"><span data-stu-id="2abec-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2abec-109">語法</span><span class="sxs-lookup"><span data-stu-id="2abec-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2abec-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2abec-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2abec-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2abec-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2abec-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2abec-112">Attributes</span></span>  
  
|<span data-ttu-id="2abec-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2abec-113">Attribute</span></span>|<span data-ttu-id="2abec-114">描述</span><span class="sxs-lookup"><span data-stu-id="2abec-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2abec-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="2abec-115">requireClientCertificate</span></span>|<span data-ttu-id="2abec-116">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="2abec-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="2abec-117">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2abec-117">The default is `false`.</span></span>|  
|<span data-ttu-id="2abec-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="2abec-118">sslProtocols</span></span>|<span data-ttu-id="2abec-119">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="2abec-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="2abec-120">預設值是 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="2abec-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2abec-121">子元素</span><span class="sxs-lookup"><span data-stu-id="2abec-121">Child Elements</span></span>  
 <span data-ttu-id="2abec-122">無。</span><span class="sxs-lookup"><span data-stu-id="2abec-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2abec-123">父項目</span><span class="sxs-lookup"><span data-stu-id="2abec-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2abec-124">項目</span><span class="sxs-lookup"><span data-stu-id="2abec-124">Element</span></span>|<span data-ttu-id="2abec-125">描述</span><span class="sxs-lookup"><span data-stu-id="2abec-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2abec-126">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2abec-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2abec-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="2abec-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2abec-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2abec-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="2abec-129">繫結</span><span class="sxs-lookup"><span data-stu-id="2abec-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2abec-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="2abec-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2abec-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="2abec-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2abec-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2abec-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
