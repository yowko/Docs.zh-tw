---
title: 網路設定結構描述
description: 深入瞭解網路設定的架構，這些設定會指定 .NET Framework 如何連接到網際網路並處理 Uri。
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
ms.openlocfilehash: 8071fcfcdb16b6e71d8d7af05a704d8842b3e963
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158912"
---
# <a name="network-settings-schema"></a><span data-ttu-id="0f449-103">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0f449-103">Network Settings Schema</span></span>

<span data-ttu-id="0f449-104">網路設定會指定 .NET Framework 如何連接至網際網路。</span><span class="sxs-lookup"><span data-stu-id="0f449-104">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="0f449-105">這些 \<system.net> 設定會指定 .NET Framework 如何連接到網路。</span><span class="sxs-lookup"><span data-stu-id="0f449-105">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="0f449-106">下表描述專案底下的每個子[ \<system.Net> 設定專案 (網路設定) ](system-net-element-network-settings.md)的功能。</span><span class="sxs-lookup"><span data-stu-id="0f449-106">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="0f449-107">項目</span><span class="sxs-lookup"><span data-stu-id="0f449-107">Element</span></span>|<span data-ttu-id="0f449-108">描述</span><span class="sxs-lookup"><span data-stu-id="0f449-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f449-109">\<authenticationModules> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-109">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="0f449-110">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="0f449-110">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="0f449-111">\<connectionManagement> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-111">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="0f449-112">指定連線到網際網路主機的最大連線數目。</span><span class="sxs-lookup"><span data-stu-id="0f449-112">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="0f449-113">\<defaultProxy> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-113">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="0f449-114">指定用於網際網路之 HTTP 要求的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="0f449-114">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="0f449-115">\<mailSettings> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-115">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="0f449-116">包含郵件傳送選項的設定。</span><span class="sxs-lookup"><span data-stu-id="0f449-116">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="0f449-117">\<requestCaching> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-117">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="0f449-118">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="0f449-118">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="0f449-119">\<webRequestModules> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-119">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="0f449-120">指定用來向網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="0f449-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="0f449-121">這些 \<uri> 設定會指定 .NET Framework 如何使用 (uri) 的統一資源識別項來處理 web 位址。</span><span class="sxs-lookup"><span data-stu-id="0f449-121">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="0f449-122">下表描述專案底下的每個子設定元素的函式[ \<uri> (Uri 設定) ](uri-element-uri-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="0f449-122">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="0f449-123">項目</span><span class="sxs-lookup"><span data-stu-id="0f449-123">Element</span></span>|<span data-ttu-id="0f449-124">描述</span><span class="sxs-lookup"><span data-stu-id="0f449-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f449-125">\<idn> (Uri 設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-125">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="0f449-126">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="0f449-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="0f449-127">\<iriParsing> (Uri 設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-127">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="0f449-128">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="0f449-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="0f449-129">\<schemeSettings> (Uri 設定的元素) </span><span class="sxs-lookup"><span data-stu-id="0f449-129">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="0f449-130">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="0f449-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f449-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f449-131">See also</span></span>

- [<span data-ttu-id="0f449-132">設定網際網路應用程式</span><span class="sxs-lookup"><span data-stu-id="0f449-132">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="0f449-133">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="0f449-133">Configuration File Schema</span></span>](../index.md)
