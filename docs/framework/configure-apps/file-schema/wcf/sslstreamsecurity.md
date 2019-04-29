---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 67ec30b2bf3c322b949700789ce942e4281b77a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757985"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="bcc9a-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="bcc9a-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="bcc9a-102">表示以 SSL 資料流支援通道安全性的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="bcc9a-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="bcc9a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bcc9a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="bcc9a-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bcc9a-104">\<bindings></span></span>  
<span data-ttu-id="bcc9a-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bcc9a-105">\<customBinding></span></span>  
<span data-ttu-id="bcc9a-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="bcc9a-106">\<binding></span></span>  
<span data-ttu-id="bcc9a-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="bcc9a-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcc9a-108">語法</span><span class="sxs-lookup"><span data-stu-id="bcc9a-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcc9a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bcc9a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bcc9a-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bcc9a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcc9a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="bcc9a-111">Attributes</span></span>  
  
|<span data-ttu-id="bcc9a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bcc9a-112">Attribute</span></span>|<span data-ttu-id="bcc9a-113">描述</span><span class="sxs-lookup"><span data-stu-id="bcc9a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bcc9a-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="bcc9a-114">requireClientCertificate</span></span>|<span data-ttu-id="bcc9a-115">布林值，指定這個繫結是否需要用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="bcc9a-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="bcc9a-116">預設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="bcc9a-116">The default is `false`.</span></span>|  
|<span data-ttu-id="bcc9a-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="bcc9a-117">sslProtocols</span></span>|<span data-ttu-id="bcc9a-118">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="bcc9a-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="bcc9a-119">預設值是 Ssl3&#124;Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="bcc9a-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcc9a-120">子元素</span><span class="sxs-lookup"><span data-stu-id="bcc9a-120">Child Elements</span></span>  
 <span data-ttu-id="bcc9a-121">無。</span><span class="sxs-lookup"><span data-stu-id="bcc9a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bcc9a-122">父項目</span><span class="sxs-lookup"><span data-stu-id="bcc9a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bcc9a-123">項目</span><span class="sxs-lookup"><span data-stu-id="bcc9a-123">Element</span></span>|<span data-ttu-id="bcc9a-124">描述</span><span class="sxs-lookup"><span data-stu-id="bcc9a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcc9a-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="bcc9a-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bcc9a-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="bcc9a-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bcc9a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcc9a-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="bcc9a-128">繫結</span><span class="sxs-lookup"><span data-stu-id="bcc9a-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="bcc9a-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="bcc9a-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="bcc9a-130">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="bcc9a-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="bcc9a-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="bcc9a-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
