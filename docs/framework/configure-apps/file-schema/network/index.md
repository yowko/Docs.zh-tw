---
title: "網路設定結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca4a0000d85c8fbac9a723beeda51f9c7886ed8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="network-settings-schema"></a><span data-ttu-id="07e94-102">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="07e94-102">Network Settings Schema</span></span>
<span data-ttu-id="07e94-103">網路設定會指定 .NET Framework 如何連接至網際網路。</span><span class="sxs-lookup"><span data-stu-id="07e94-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="07e94-104">下表描述 [\<system.Net> 項目 (網路設定)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 下每個子組態項目的功能。</span><span class="sxs-lookup"><span data-stu-id="07e94-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="07e94-105">項目</span><span class="sxs-lookup"><span data-stu-id="07e94-105">Element</span></span>|<span data-ttu-id="07e94-106">說明</span><span class="sxs-lookup"><span data-stu-id="07e94-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07e94-107">\<authenticationModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-107">\<authenticationModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="07e94-108">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="07e94-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="07e94-109">\<connectionManagement> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-109">\<connectionManagement> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="07e94-110">指定連線到網際網路主機的最大連線數目。</span><span class="sxs-lookup"><span data-stu-id="07e94-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="07e94-111">\<defaultProxy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-111">\<defaultProxy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="07e94-112">指定用於網際網路之 HTTP 要求的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="07e94-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="07e94-113">\<mailSettings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-113">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="07e94-114">包含郵件傳送選項的設定。</span><span class="sxs-lookup"><span data-stu-id="07e94-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="07e94-115">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-115">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="07e94-116">指定用來向網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="07e94-116">Specifies the modules used to request information from Internet hosts.</span></span>|  
|[<span data-ttu-id="07e94-117">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-117">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="07e94-118">為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="07e94-118">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>|  
|[<span data-ttu-id="07e94-119">\<webRequestModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-119">\<webRequestModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="07e94-120">指定用來向網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="07e94-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="07e94-121">URI 設定會指定 .NET Framework 如何處理使用統一資源識別元 (URI) 表示的網站位址。</span><span class="sxs-lookup"><span data-stu-id="07e94-121">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="07e94-122">下表描述 [\<URI> 項目 (URI 設定)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md) 下每個子組態項目的功能。</span><span class="sxs-lookup"><span data-stu-id="07e94-122">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="07e94-123">項目</span><span class="sxs-lookup"><span data-stu-id="07e94-123">Element</span></span>|<span data-ttu-id="07e94-124">說明</span><span class="sxs-lookup"><span data-stu-id="07e94-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07e94-125">\<idn> 項目 (URI設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-125">\<idn> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="07e94-126">指定是否要對網域名稱套用國際化網域名稱 (IDN) 剖析。</span><span class="sxs-lookup"><span data-stu-id="07e94-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="07e94-127">\<iriParsing> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-127">\<iriParsing> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="07e94-128">指定是否要將國際資源識別項 (IRI) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。</span><span class="sxs-lookup"><span data-stu-id="07e94-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="07e94-129">\<schemeSettings> 項目 (URI 設定)</span><span class="sxs-lookup"><span data-stu-id="07e94-129">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="07e94-130">指定如何針對特定配置剖析 <xref:System.Uri>。</span><span class="sxs-lookup"><span data-stu-id="07e94-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07e94-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07e94-131">See Also</span></span>  
 [<span data-ttu-id="07e94-132">設定網際網路應用程式</span><span class="sxs-lookup"><span data-stu-id="07e94-132">Configuring Internet Applications</span></span>](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [<span data-ttu-id="07e94-133">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="07e94-133">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
