---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 5ed87adfb3963513602844fc69afce8f7994fa8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932428"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="96cdc-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="96cdc-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="96cdc-102">表示以 SSL 資料流支援通道安全性的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="96cdc-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="96cdc-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96cdc-103">\<system.serviceModel></span></span>  
<span data-ttu-id="96cdc-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="96cdc-104">\<bindings></span></span>  
<span data-ttu-id="96cdc-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="96cdc-105">\<customBinding></span></span>  
<span data-ttu-id="96cdc-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="96cdc-106">\<binding></span></span>  
<span data-ttu-id="96cdc-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="96cdc-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96cdc-108">語法</span><span class="sxs-lookup"><span data-stu-id="96cdc-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96cdc-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="96cdc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="96cdc-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="96cdc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96cdc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="96cdc-111">Attributes</span></span>  
  
|<span data-ttu-id="96cdc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="96cdc-112">Attribute</span></span>|<span data-ttu-id="96cdc-113">說明</span><span class="sxs-lookup"><span data-stu-id="96cdc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96cdc-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="96cdc-114">requireClientCertificate</span></span>|<span data-ttu-id="96cdc-115">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="96cdc-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="96cdc-116">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="96cdc-116">The default is `false`.</span></span>|  
|<span data-ttu-id="96cdc-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="96cdc-117">sslProtocols</span></span>|<span data-ttu-id="96cdc-118">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="96cdc-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="96cdc-119">預設值為 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="96cdc-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96cdc-120">子元素</span><span class="sxs-lookup"><span data-stu-id="96cdc-120">Child Elements</span></span>  
 <span data-ttu-id="96cdc-121">無。</span><span class="sxs-lookup"><span data-stu-id="96cdc-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96cdc-122">父項目</span><span class="sxs-lookup"><span data-stu-id="96cdc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="96cdc-123">項目</span><span class="sxs-lookup"><span data-stu-id="96cdc-123">Element</span></span>|<span data-ttu-id="96cdc-124">描述</span><span class="sxs-lookup"><span data-stu-id="96cdc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96cdc-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="96cdc-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="96cdc-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="96cdc-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96cdc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96cdc-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="96cdc-128">繫結</span><span class="sxs-lookup"><span data-stu-id="96cdc-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="96cdc-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="96cdc-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="96cdc-130">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="96cdc-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="96cdc-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="96cdc-131">\<customBinding></span></span>](custombinding.md)
