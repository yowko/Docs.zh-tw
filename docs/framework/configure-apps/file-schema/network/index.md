---
title: 網路設定結構描述
description: 瞭解網路設定的架構，其指定 .NET Framework 如何連接至網際網路並處理 Uri。
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
ms.openlocfilehash: 6a22d7f1608db2e8909d0ead11e9110ec8a8a2c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504572"
---
# <a name="network-settings-schema"></a><span data-ttu-id="7e3ed-103">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7e3ed-103">Network Settings Schema</span></span>
<span data-ttu-id="7e3ed-104">網路設定會指定 .NET Framework 如何連接至網際網路。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-104">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="7e3ed-105">這些 \<system.net> 設定會指定 .NET Framework 如何連接到網路。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-105">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="7e3ed-106">下表描述[ \<system.Net> 元素（網路設定）](system-net-element-network-settings.md)底下每個子 configuration 專案的功能。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-106">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="7e3ed-107">元素</span><span class="sxs-lookup"><span data-stu-id="7e3ed-107">Element</span></span>|<span data-ttu-id="7e3ed-108">描述</span><span class="sxs-lookup"><span data-stu-id="7e3ed-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e3ed-109">\<authenticationModules>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-109">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="7e3ed-110">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-110">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="7e3ed-111">\<connectionManagement>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-111">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="7e3ed-112">指定連線到網際網路主機的最大連線數目。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-112">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="7e3ed-113">\<defaultProxy>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-113">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="7e3ed-114">指定用於網際網路之 HTTP 要求的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-114">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="7e3ed-115">\<mailSettings>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-115">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="7e3ed-116">包含郵件傳送選項的設定。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-116">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="7e3ed-117">\<requestCaching>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-117">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="7e3ed-118">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-118">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="7e3ed-119">\<webRequestModules>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-119">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="7e3ed-120">指定用來向網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="7e3ed-121">這些 \<uri> 設定會指定 .NET Framework 如何處理使用統一資源識別項（uri）所表示的 web 位址。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-121">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="7e3ed-122">下表描述專案[ \<uri> （Uri 設定）](uri-element-uri-settings.md)底下每個子設定元素的功能。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-122">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="7e3ed-123">元素</span><span class="sxs-lookup"><span data-stu-id="7e3ed-123">Element</span></span>|<span data-ttu-id="7e3ed-124">描述</span><span class="sxs-lookup"><span data-stu-id="7e3ed-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e3ed-125">\<idn>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-125">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="7e3ed-126">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="7e3ed-127">\<iriParsing>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-127">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="7e3ed-128">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="7e3ed-129">\<schemeSettings>元素（Uri 設定）</span><span class="sxs-lookup"><span data-stu-id="7e3ed-129">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="7e3ed-130">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="7e3ed-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e3ed-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e3ed-131">See also</span></span>

- [<span data-ttu-id="7e3ed-132">設定網際網路應用程式</span><span class="sxs-lookup"><span data-stu-id="7e3ed-132">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="7e3ed-133">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="7e3ed-133">Configuration File Schema</span></span>](../index.md)
