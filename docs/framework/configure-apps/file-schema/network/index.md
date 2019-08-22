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
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664112"
---
# <a name="network-settings-schema"></a><span data-ttu-id="64a76-102">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="64a76-102">Network Settings Schema</span></span>
<span data-ttu-id="64a76-103">網路設定會指定 .NET Framework 如何連接至網際網路。</span><span class="sxs-lookup"><span data-stu-id="64a76-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="64a76-104">下表描述 [\<system.Net> 項目 (網路設定)](system-net-element-network-settings.md) 下每個子組態項目的功能。</span><span class="sxs-lookup"><span data-stu-id="64a76-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="64a76-105">項目</span><span class="sxs-lookup"><span data-stu-id="64a76-105">Element</span></span>|<span data-ttu-id="64a76-106">說明</span><span class="sxs-lookup"><span data-stu-id="64a76-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64a76-107">\<authenticationModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-107">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="64a76-108">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="64a76-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="64a76-109">\<connectionManagement> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-109">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="64a76-110">指定連線到網際網路主機的最大連線數目。</span><span class="sxs-lookup"><span data-stu-id="64a76-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="64a76-111">\<defaultProxy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-111">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="64a76-112">指定用於網際網路之 HTTP 要求的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="64a76-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="64a76-113">\<mailSettings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-113">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="64a76-114">包含郵件傳送選項的設定。</span><span class="sxs-lookup"><span data-stu-id="64a76-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="64a76-115">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-115">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="64a76-116">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="64a76-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="64a76-117">\<webRequestModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-117">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="64a76-118">指定用來向網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="64a76-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="64a76-119">URI 設定會指定 .NET Framework 如何處理使用統一資源識別元 (URI) 表示的網站位址。</span><span class="sxs-lookup"><span data-stu-id="64a76-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="64a76-120">下表描述 [\<URI> 項目 (URI 設定)](uri-element-uri-settings.md) 下每個子組態項目的功能。</span><span class="sxs-lookup"><span data-stu-id="64a76-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="64a76-121">項目</span><span class="sxs-lookup"><span data-stu-id="64a76-121">Element</span></span>|<span data-ttu-id="64a76-122">描述</span><span class="sxs-lookup"><span data-stu-id="64a76-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64a76-123">\<idn> 項目 (URI設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-123">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="64a76-124">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="64a76-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="64a76-125">\<iriParsing> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-125">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="64a76-126">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="64a76-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="64a76-127">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="64a76-127">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="64a76-128">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="64a76-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64a76-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64a76-129">See also</span></span>

- [<span data-ttu-id="64a76-130">設定網際網路應用程式</span><span class="sxs-lookup"><span data-stu-id="64a76-130">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="64a76-131">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="64a76-131">Configuration File Schema</span></span>](../index.md)
