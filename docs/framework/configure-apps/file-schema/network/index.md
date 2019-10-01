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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698156"
---
# <a name="network-settings-schema"></a><span data-ttu-id="5d561-102">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5d561-102">Network Settings Schema</span></span>
<span data-ttu-id="5d561-103">網路設定會指定 .NET Framework 如何連接至網際網路。</span><span class="sxs-lookup"><span data-stu-id="5d561-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="5d561-104">@No__t 的-0system > 設定會指定 .NET Framework 連接到網路的方式。</span><span class="sxs-lookup"><span data-stu-id="5d561-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="5d561-105">下表描述 [\<system.Net> 項目 (網路設定)](system-net-element-network-settings.md) 下每個子組態項目的功能。</span><span class="sxs-lookup"><span data-stu-id="5d561-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="5d561-106">元素</span><span class="sxs-lookup"><span data-stu-id="5d561-106">Element</span></span>|<span data-ttu-id="5d561-107">描述</span><span class="sxs-lookup"><span data-stu-id="5d561-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d561-108">\<authenticationModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="5d561-109">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="5d561-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="5d561-110">\<connectionManagement> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="5d561-111">指定連線到網際網路主機的最大連線數目。</span><span class="sxs-lookup"><span data-stu-id="5d561-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="5d561-112">\<defaultProxy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="5d561-113">指定用於網際網路之 HTTP 要求的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="5d561-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="5d561-114">\<mailSettings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="5d561-115">包含郵件傳送選項的設定。</span><span class="sxs-lookup"><span data-stu-id="5d561-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="5d561-116">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="5d561-117">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="5d561-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="5d561-118">\<webRequestModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="5d561-119">指定用來向網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="5d561-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="5d561-120">@No__t 0uri > 設定會指定 .NET Framework 如何處理使用統一資源識別項（Uri）所表示的 web 位址。</span><span class="sxs-lookup"><span data-stu-id="5d561-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="5d561-121">下表描述[\<uri > 元素（Uri 設定）](uri-element-uri-settings.md)下每個子設定元素的功能。</span><span class="sxs-lookup"><span data-stu-id="5d561-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="5d561-122">元素</span><span class="sxs-lookup"><span data-stu-id="5d561-122">Element</span></span>|<span data-ttu-id="5d561-123">描述</span><span class="sxs-lookup"><span data-stu-id="5d561-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d561-124">\<idn> 項目 (URI設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="5d561-125">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="5d561-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="5d561-126">\<iriParsing> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="5d561-127">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="5d561-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="5d561-128">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="5d561-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="5d561-129">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="5d561-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d561-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d561-130">See also</span></span>

- [<span data-ttu-id="5d561-131">設定網際網路應用程式</span><span class="sxs-lookup"><span data-stu-id="5d561-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="5d561-132">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5d561-132">Configuration File Schema</span></span>](../index.md)
