---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: aa6bc7f5a94afc8a190d3d9d2d71ea8b38d8c25b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153569"
---
# \<sslStreamSecurity>

<span data-ttu-id="5d6ee-101">表示以 SSL 資料流支援通道安全性的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="5d6ee-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="5d6ee-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="5d6ee-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d6ee-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5d6ee-103">Attributes and Elements</span></span>  

 <span data-ttu-id="5d6ee-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5d6ee-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d6ee-105">屬性</span><span class="sxs-lookup"><span data-stu-id="5d6ee-105">Attributes</span></span>  
  
|<span data-ttu-id="5d6ee-106">屬性</span><span class="sxs-lookup"><span data-stu-id="5d6ee-106">Attribute</span></span>|<span data-ttu-id="5d6ee-107">描述</span><span class="sxs-lookup"><span data-stu-id="5d6ee-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d6ee-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="5d6ee-108">requireClientCertificate</span></span>|<span data-ttu-id="5d6ee-109">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="5d6ee-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="5d6ee-110">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5d6ee-110">The default is `false`.</span></span>|  
|<span data-ttu-id="5d6ee-111">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="5d6ee-111">sslProtocols</span></span>|<span data-ttu-id="5d6ee-112">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="5d6ee-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="5d6ee-113">預設值為 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="5d6ee-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d6ee-114">子元素</span><span class="sxs-lookup"><span data-stu-id="5d6ee-114">Child Elements</span></span>  

 <span data-ttu-id="5d6ee-115">無。</span><span class="sxs-lookup"><span data-stu-id="5d6ee-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d6ee-116">父項目</span><span class="sxs-lookup"><span data-stu-id="5d6ee-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5d6ee-117">項目</span><span class="sxs-lookup"><span data-stu-id="5d6ee-117">Element</span></span>|<span data-ttu-id="5d6ee-118">描述</span><span class="sxs-lookup"><span data-stu-id="5d6ee-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="5d6ee-119">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="5d6ee-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d6ee-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d6ee-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="5d6ee-121">繫結</span><span class="sxs-lookup"><span data-stu-id="5d6ee-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5d6ee-122">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="5d6ee-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5d6ee-123">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="5d6ee-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
