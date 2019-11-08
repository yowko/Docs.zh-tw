---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738600"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="6e0a5-101">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="6e0a5-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="6e0a5-102">表示以 SSL 資料流支援通道安全性的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="6e0a5-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="6e0a5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e0a5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6e0a5-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6e0a5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6e0a5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="6e0a5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6e0a5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="6e0a5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="6e0a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="6e0a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6e0a5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sslStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="6e0a5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e0a5-109">語法</span><span class="sxs-lookup"><span data-stu-id="6e0a5-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e0a5-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6e0a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e0a5-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6e0a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e0a5-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6e0a5-112">Attributes</span></span>  
  
|<span data-ttu-id="6e0a5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6e0a5-113">Attribute</span></span>|<span data-ttu-id="6e0a5-114">描述</span><span class="sxs-lookup"><span data-stu-id="6e0a5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e0a5-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="6e0a5-115">requireClientCertificate</span></span>|<span data-ttu-id="6e0a5-116">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="6e0a5-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="6e0a5-117">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6e0a5-117">The default is `false`.</span></span>|  
|<span data-ttu-id="6e0a5-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="6e0a5-118">sslProtocols</span></span>|<span data-ttu-id="6e0a5-119">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="6e0a5-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="6e0a5-120">預設值為 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="6e0a5-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e0a5-121">子項目</span><span class="sxs-lookup"><span data-stu-id="6e0a5-121">Child Elements</span></span>  
 <span data-ttu-id="6e0a5-122">無。</span><span class="sxs-lookup"><span data-stu-id="6e0a5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e0a5-123">父項目</span><span class="sxs-lookup"><span data-stu-id="6e0a5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e0a5-124">項目</span><span class="sxs-lookup"><span data-stu-id="6e0a5-124">Element</span></span>|<span data-ttu-id="6e0a5-125">描述</span><span class="sxs-lookup"><span data-stu-id="6e0a5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e0a5-126">\<binding ></span><span class="sxs-lookup"><span data-stu-id="6e0a5-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="6e0a5-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="6e0a5-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e0a5-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e0a5-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="6e0a5-129">繫結</span><span class="sxs-lookup"><span data-stu-id="6e0a5-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6e0a5-130">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="6e0a5-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6e0a5-131">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="6e0a5-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="6e0a5-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6e0a5-132">\<customBinding></span></span>](custombinding.md)
