---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 9b7092878c604142c29dcd8d27e3c458d203f9fa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399523"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="27f2d-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="27f2d-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="27f2d-102">表示以 SSL 資料流支援通道安全性的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="27f2d-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="27f2d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27f2d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="27f2d-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="27f2d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="27f2d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="27f2d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="27f2d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="27f2d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="27f2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="27f2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="27f2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sslStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="27f2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f2d-109">語法</span><span class="sxs-lookup"><span data-stu-id="27f2d-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27f2d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="27f2d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="27f2d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="27f2d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27f2d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="27f2d-112">Attributes</span></span>  
  
|<span data-ttu-id="27f2d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="27f2d-113">Attribute</span></span>|<span data-ttu-id="27f2d-114">描述</span><span class="sxs-lookup"><span data-stu-id="27f2d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27f2d-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="27f2d-115">requireClientCertificate</span></span>|<span data-ttu-id="27f2d-116">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="27f2d-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="27f2d-117">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="27f2d-117">The default is `false`.</span></span>|  
|<span data-ttu-id="27f2d-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="27f2d-118">sslProtocols</span></span>|<span data-ttu-id="27f2d-119">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="27f2d-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="27f2d-120">預設值為 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="27f2d-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27f2d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="27f2d-121">Child Elements</span></span>  
 <span data-ttu-id="27f2d-122">無。</span><span class="sxs-lookup"><span data-stu-id="27f2d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27f2d-123">父項目</span><span class="sxs-lookup"><span data-stu-id="27f2d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="27f2d-124">項目</span><span class="sxs-lookup"><span data-stu-id="27f2d-124">Element</span></span>|<span data-ttu-id="27f2d-125">描述</span><span class="sxs-lookup"><span data-stu-id="27f2d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27f2d-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="27f2d-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="27f2d-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="27f2d-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27f2d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27f2d-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="27f2d-129">繫結</span><span class="sxs-lookup"><span data-stu-id="27f2d-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="27f2d-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="27f2d-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="27f2d-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="27f2d-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="27f2d-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="27f2d-132">\<customBinding></span></span>](custombinding.md)
