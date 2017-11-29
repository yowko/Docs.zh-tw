---
title: "&lt;system.Net&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d2eb903b8a84410aa08504c12e78a016d2368923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltsystemnetgt-element-network-settings"></a><span data-ttu-id="f976b-102">&lt;system.Net&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="f976b-102">&lt;system.Net&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f976b-103">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="f976b-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="f976b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f976b-104">\<configuration></span></span>  
<span data-ttu-id="f976b-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="f976b-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f976b-106">語法</span><span class="sxs-lookup"><span data-stu-id="f976b-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f976b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f976b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f976b-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f976b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f976b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f976b-109">Attributes</span></span>  
 <span data-ttu-id="f976b-110">無。</span><span class="sxs-lookup"><span data-stu-id="f976b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f976b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f976b-111">Child Elements</span></span>  
  
|<span data-ttu-id="f976b-112">**目**</span><span class="sxs-lookup"><span data-stu-id="f976b-112">**Element**</span></span>|<span data-ttu-id="f976b-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="f976b-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f976b-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="f976b-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="f976b-115">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="f976b-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="f976b-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="f976b-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="f976b-117">指定連接至網際網路主機的數目上限。</span><span class="sxs-lookup"><span data-stu-id="f976b-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="f976b-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="f976b-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="f976b-119">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f976b-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="f976b-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="f976b-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="f976b-121">設定簡易郵件傳輸通訊協定 (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="f976b-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="f976b-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="f976b-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="f976b-123">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="f976b-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="f976b-124">設定</span><span class="sxs-lookup"><span data-stu-id="f976b-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="f976b-125">設定類別中的基本網路選項<xref:System.Net>和相關的子命名空間。</span><span class="sxs-lookup"><span data-stu-id="f976b-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="f976b-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="f976b-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="f976b-127">指定要求資訊從網際網路主機使用的模組。</span><span class="sxs-lookup"><span data-stu-id="f976b-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f976b-128">父項目</span><span class="sxs-lookup"><span data-stu-id="f976b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f976b-129">**目**</span><span class="sxs-lookup"><span data-stu-id="f976b-129">**Element**</span></span>|<span data-ttu-id="f976b-130">**說明**</span><span class="sxs-lookup"><span data-stu-id="f976b-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f976b-131">組態</span><span class="sxs-lookup"><span data-stu-id="f976b-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f976b-132">包含所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="f976b-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f976b-133">備註</span><span class="sxs-lookup"><span data-stu-id="f976b-133">Remarks</span></span>  
 <span data-ttu-id="f976b-134">[ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)項目包含的類別中設定<xref:System.Net>和相關的子命名空間。</span><span class="sxs-lookup"><span data-stu-id="f976b-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="f976b-135">這些設定會設定驗證模組、 連線管理、 郵件設定、 proxy 伺服器和網際網路主機從接收資訊的網際網路要求模組。</span><span class="sxs-lookup"><span data-stu-id="f976b-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f976b-136">範例</span><span class="sxs-lookup"><span data-stu-id="f976b-136">Example</span></span>  
 <span data-ttu-id="f976b-137">下列範例會顯示所使用的一般組態<xref:System.Net>類別。</span><span class="sxs-lookup"><span data-stu-id="f976b-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f976b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f976b-138">See Also</span></span>  
 [<span data-ttu-id="f976b-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f976b-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
