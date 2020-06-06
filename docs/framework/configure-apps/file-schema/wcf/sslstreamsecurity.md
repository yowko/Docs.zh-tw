---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738600"
---
# \<sslStreamSecurity>
<span data-ttu-id="f38f1-101">表示以 SSL 資料流支援通道安全性的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="f38f1-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="f38f1-102">語法</span><span class="sxs-lookup"><span data-stu-id="f38f1-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f38f1-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f38f1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f38f1-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f38f1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f38f1-105">屬性</span><span class="sxs-lookup"><span data-stu-id="f38f1-105">Attributes</span></span>  
  
|<span data-ttu-id="f38f1-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f38f1-106">Attribute</span></span>|<span data-ttu-id="f38f1-107">描述</span><span class="sxs-lookup"><span data-stu-id="f38f1-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f38f1-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="f38f1-108">requireClientCertificate</span></span>|<span data-ttu-id="f38f1-109">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="f38f1-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="f38f1-110">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="f38f1-110">The default is `false`.</span></span>|  
|<span data-ttu-id="f38f1-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="f38f1-111">sslProtocols</span></span>|<span data-ttu-id="f38f1-112">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="f38f1-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="f38f1-113">預設值為 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="f38f1-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f38f1-114">子元素</span><span class="sxs-lookup"><span data-stu-id="f38f1-114">Child Elements</span></span>  
 <span data-ttu-id="f38f1-115">無。</span><span class="sxs-lookup"><span data-stu-id="f38f1-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f38f1-116">父項目</span><span class="sxs-lookup"><span data-stu-id="f38f1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f38f1-117">元素</span><span class="sxs-lookup"><span data-stu-id="f38f1-117">Element</span></span>|<span data-ttu-id="f38f1-118">描述</span><span class="sxs-lookup"><span data-stu-id="f38f1-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f38f1-119">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="f38f1-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f38f1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f38f1-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="f38f1-121">繫結</span><span class="sxs-lookup"><span data-stu-id="f38f1-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f38f1-122">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="f38f1-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f38f1-123">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="f38f1-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
