---
title: <system.Net> 項目 (網路設定)
description: <system.Net> network settings 元素包含的設定，可指定 .NET Framework 如何連接到 .NET Framework 中的網路選項。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 9f18c7a3586948c03391d609f437e216a91bc27f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504481"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="9dfc7-103">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="9dfc7-103">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="9dfc7-104">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-104">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="9dfc7-105">語法</span><span class="sxs-lookup"><span data-stu-id="9dfc7-105">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9dfc7-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9dfc7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9dfc7-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9dfc7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9dfc7-108">Attributes</span></span>  
 <span data-ttu-id="9dfc7-109">無。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9dfc7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9dfc7-110">Child Elements</span></span>  
  
|<span data-ttu-id="9dfc7-111">**元素**</span><span class="sxs-lookup"><span data-stu-id="9dfc7-111">**Element**</span></span>|<span data-ttu-id="9dfc7-112">**描述**</span><span class="sxs-lookup"><span data-stu-id="9dfc7-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9dfc7-113">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="9dfc7-113">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="9dfc7-114">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-114">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="9dfc7-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="9dfc7-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="9dfc7-116">指定網際網路主機的最大連接數目。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-116">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="9dfc7-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="9dfc7-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="9dfc7-118">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="9dfc7-119">mailSettings</span><span class="sxs-lookup"><span data-stu-id="9dfc7-119">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="9dfc7-120">設定簡單郵件傳輸通訊協定（SMTP）郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-120">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="9dfc7-121">requestCaching</span><span class="sxs-lookup"><span data-stu-id="9dfc7-121">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="9dfc7-122">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-122">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="9dfc7-123">設定</span><span class="sxs-lookup"><span data-stu-id="9dfc7-123">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="9dfc7-124">為 <xref:System.Net> 和相關的子命名空間中的類別設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-124">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="9dfc7-125">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="9dfc7-125">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="9dfc7-126">指定要用來從網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-126">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9dfc7-127">父項目</span><span class="sxs-lookup"><span data-stu-id="9dfc7-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9dfc7-128">**元素**</span><span class="sxs-lookup"><span data-stu-id="9dfc7-128">**Element**</span></span>|<span data-ttu-id="9dfc7-129">**描述**</span><span class="sxs-lookup"><span data-stu-id="9dfc7-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9dfc7-130">設定</span><span class="sxs-lookup"><span data-stu-id="9dfc7-130">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="9dfc7-131">包含所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-131">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dfc7-132">備註</span><span class="sxs-lookup"><span data-stu-id="9dfc7-132">Remarks</span></span>  
 <span data-ttu-id="9dfc7-133">[\<system.net>](system-net-element-network-settings.md)元素包含 <xref:System.Net> 和相關子命名空間中的類別設定。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-133">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="9dfc7-134">設定可設定驗證模組、連線管理、郵件設定、proxy 伺服器，以及從網際網路主機接收資訊的網際網路要求模組。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-134">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dfc7-135">範例</span><span class="sxs-lookup"><span data-stu-id="9dfc7-135">Example</span></span>  
 <span data-ttu-id="9dfc7-136">下列範例顯示類別所使用的一般設定 <xref:System.Net> 。</span><span class="sxs-lookup"><span data-stu-id="9dfc7-136">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9dfc7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dfc7-137">See also</span></span>

- [<span data-ttu-id="9dfc7-138">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="9dfc7-138">Network Settings Schema</span></span>](index.md)
