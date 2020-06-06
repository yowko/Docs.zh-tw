---
title: 網路設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698156"
---
# <a name="network-settings-schema"></a><span data-ttu-id="bb54c-102">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bb54c-102">Network Settings Schema</span></span>
<span data-ttu-id="bb54c-103">網路設定會指定 .NET Framework 如何連接至網際網路。</span><span class="sxs-lookup"><span data-stu-id="bb54c-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="bb54c-104">這些 \<system.net> 設定會指定 .NET Framework 如何連接到網路。</span><span class="sxs-lookup"><span data-stu-id="bb54c-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="bb54c-105">下表描述[ \<system.Net> 元素（網路設定）](system-net-element-network-settings.md)底下每個子 configuration 專案的功能。</span><span class="sxs-lookup"><span data-stu-id="bb54c-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="bb54c-106">元素</span><span class="sxs-lookup"><span data-stu-id="bb54c-106">Element</span></span>|<span data-ttu-id="bb54c-107">描述</span><span class="sxs-lookup"><span data-stu-id="bb54c-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb54c-108">\<authenticationModules>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="bb54c-109">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="bb54c-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="bb54c-110">\<connectionManagement>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="bb54c-111">指定連線到網際網路主機的最大連線數目。</span><span class="sxs-lookup"><span data-stu-id="bb54c-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="bb54c-112">\<defaultProxy>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="bb54c-113">指定用於網際網路之 HTTP 要求的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bb54c-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="bb54c-114">\<mailSettings>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="bb54c-115">包含郵件傳送選項的設定。</span><span class="sxs-lookup"><span data-stu-id="bb54c-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="bb54c-116">\<requestCaching>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="bb54c-117">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="bb54c-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="bb54c-118">\<webRequestModules>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="bb54c-119">指定用來向網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="bb54c-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="bb54c-120">這些 \<uri> 設定會指定 .NET Framework 如何處理使用統一資源識別項（uri）所表示的 web 位址。</span><span class="sxs-lookup"><span data-stu-id="bb54c-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="bb54c-121">下表描述專案[ \<uri> （Uri 設定）](uri-element-uri-settings.md)底下每個子設定元素的功能。</span><span class="sxs-lookup"><span data-stu-id="bb54c-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="bb54c-122">元素</span><span class="sxs-lookup"><span data-stu-id="bb54c-122">Element</span></span>|<span data-ttu-id="bb54c-123">描述</span><span class="sxs-lookup"><span data-stu-id="bb54c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb54c-124">\<idn>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="bb54c-125">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="bb54c-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="bb54c-126">\<iriParsing>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="bb54c-127">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="bb54c-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="bb54c-128">\<schemeSettings>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="bb54c-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="bb54c-129">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="bb54c-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb54c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb54c-130">See also</span></span>

- [<span data-ttu-id="bb54c-131">設定網際網路應用程式</span><span class="sxs-lookup"><span data-stu-id="bb54c-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="bb54c-132">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="bb54c-132">Configuration File Schema</span></span>](../index.md)
