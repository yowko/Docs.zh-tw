---
title: <system.Net> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154552"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="72c75-102">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="72c75-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="72c75-103">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="72c75-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="72c75-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="72c75-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="72c75-105">&nbsp;&nbsp;**\<system.net>**</span><span class="sxs-lookup"><span data-stu-id="72c75-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72c75-106">語法</span><span class="sxs-lookup"><span data-stu-id="72c75-106">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72c75-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="72c75-107">Attributes and Elements</span></span>  
 <span data-ttu-id="72c75-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="72c75-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72c75-109">屬性</span><span class="sxs-lookup"><span data-stu-id="72c75-109">Attributes</span></span>  
 <span data-ttu-id="72c75-110">無。</span><span class="sxs-lookup"><span data-stu-id="72c75-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="72c75-111">子元素</span><span class="sxs-lookup"><span data-stu-id="72c75-111">Child Elements</span></span>  
  
|<span data-ttu-id="72c75-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="72c75-112">**Element**</span></span>|<span data-ttu-id="72c75-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="72c75-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="72c75-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="72c75-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="72c75-115">指定用於驗證 Internet 請求的模組。</span><span class="sxs-lookup"><span data-stu-id="72c75-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="72c75-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="72c75-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="72c75-117">指定與 Internet 主機的最大連接數。</span><span class="sxs-lookup"><span data-stu-id="72c75-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="72c75-118">預設代理</span><span class="sxs-lookup"><span data-stu-id="72c75-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="72c75-119">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="72c75-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="72c75-120">郵件設置</span><span class="sxs-lookup"><span data-stu-id="72c75-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="72c75-121">配置簡單的郵件傳輸協議 （SMTP） 郵件發送選項。</span><span class="sxs-lookup"><span data-stu-id="72c75-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="72c75-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="72c75-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="72c75-123">控制網路請求的緩存機制。</span><span class="sxs-lookup"><span data-stu-id="72c75-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="72c75-124">設定</span><span class="sxs-lookup"><span data-stu-id="72c75-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="72c75-125">為 和相關子命名空間中的<xref:System.Net>類配置基本網路選項。</span><span class="sxs-lookup"><span data-stu-id="72c75-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="72c75-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="72c75-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="72c75-127">指定用於從 Internet 主機請求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="72c75-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="72c75-128">父項目</span><span class="sxs-lookup"><span data-stu-id="72c75-128">Parent Elements</span></span>  
  
|<span data-ttu-id="72c75-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="72c75-129">**Element**</span></span>|<span data-ttu-id="72c75-130">**描述**</span><span class="sxs-lookup"><span data-stu-id="72c75-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="72c75-131">設定</span><span class="sxs-lookup"><span data-stu-id="72c75-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="72c75-132">包含所有命名空間的設置。</span><span class="sxs-lookup"><span data-stu-id="72c75-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72c75-133">備註</span><span class="sxs-lookup"><span data-stu-id="72c75-133">Remarks</span></span>  
 <span data-ttu-id="72c75-134">[ \<system.net>](system-net-element-network-settings.md)元素包含 和相關<xref:System.Net>子命名空間中的類的設置。</span><span class="sxs-lookup"><span data-stu-id="72c75-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="72c75-135">這些設置配置身份驗證模組、連接管理、郵件設置、代理伺服器和 Internet 請求模組，以便從 Internet 主機接收資訊。</span><span class="sxs-lookup"><span data-stu-id="72c75-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72c75-136">範例</span><span class="sxs-lookup"><span data-stu-id="72c75-136">Example</span></span>  
 <span data-ttu-id="72c75-137">下面的示例顯示了<xref:System.Net>類使用的典型配置。</span><span class="sxs-lookup"><span data-stu-id="72c75-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="72c75-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72c75-138">See also</span></span>

- [<span data-ttu-id="72c75-139">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="72c75-139">Network Settings Schema</span></span>](index.md)
