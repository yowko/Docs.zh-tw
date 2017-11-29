---
title: "&lt;proxy&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7178527f369c698b0ab53aa41cb28dd0126436b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="70b9a-102">&lt;proxy&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="70b9a-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="70b9a-103">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="70b9a-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="70b9a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="70b9a-104">\<configuration></span></span>  
<span data-ttu-id="70b9a-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="70b9a-105">\<system.net></span></span>  
<span data-ttu-id="70b9a-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="70b9a-106">\<defaultProxy></span></span>  
<span data-ttu-id="70b9a-107">\<proxy ></span><span class="sxs-lookup"><span data-stu-id="70b9a-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70b9a-108">語法</span><span class="sxs-lookup"><span data-stu-id="70b9a-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70b9a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="70b9a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="70b9a-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="70b9a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70b9a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="70b9a-111">Attributes</span></span>  
  
|<span data-ttu-id="70b9a-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="70b9a-112">**Attribute**</span></span>|<span data-ttu-id="70b9a-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="70b9a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="70b9a-114">指定是否自動偵測 proxy。</span><span class="sxs-lookup"><span data-stu-id="70b9a-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="70b9a-115">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="70b9a-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="70b9a-116">指定是否略過本機資源的 proxy。</span><span class="sxs-lookup"><span data-stu-id="70b9a-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="70b9a-117">本機資源包括本機伺服器 （http://localhost、 http://loopback 或 http://127.0.0.1） 及沒有句號 (http://webserver) URI。</span><span class="sxs-lookup"><span data-stu-id="70b9a-117">Local resources include the local server (http://localhost, http://loopback, or http://127.0.0.1) and a URI without a period (http://webserver).</span></span> <span data-ttu-id="70b9a-118">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="70b9a-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="70b9a-119">指定 proxy 使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="70b9a-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="70b9a-120">指定組態指令碼的位置。</span><span class="sxs-lookup"><span data-stu-id="70b9a-120">Specifies the location of the configuration script.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="70b9a-121">指定是否要使用 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="70b9a-121">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="70b9a-122">如果設定為`true`，後續的屬性會覆寫 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="70b9a-122">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="70b9a-123">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="70b9a-123">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70b9a-124">子元素</span><span class="sxs-lookup"><span data-stu-id="70b9a-124">Child Elements</span></span>  
 <span data-ttu-id="70b9a-125">無。</span><span class="sxs-lookup"><span data-stu-id="70b9a-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70b9a-126">父項目</span><span class="sxs-lookup"><span data-stu-id="70b9a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="70b9a-127">**目**</span><span class="sxs-lookup"><span data-stu-id="70b9a-127">**Element**</span></span>|<span data-ttu-id="70b9a-128">**說明**</span><span class="sxs-lookup"><span data-stu-id="70b9a-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="70b9a-129">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="70b9a-129">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="70b9a-130">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="70b9a-130">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="70b9a-131">文字值</span><span class="sxs-lookup"><span data-stu-id="70b9a-131">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70b9a-132">備註</span><span class="sxs-lookup"><span data-stu-id="70b9a-132">Remarks</span></span>  
 <span data-ttu-id="70b9a-133">`proxy`項目會定義應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="70b9a-133">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="70b9a-134">如果組態檔中沒有這個項目，.NET Framework 會在 Internet Explorer 中使用的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="70b9a-134">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="70b9a-135">值`proxyaddress`屬性應該是語式正確的 Uniform Resource Indicator (URI)。</span><span class="sxs-lookup"><span data-stu-id="70b9a-135">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="70b9a-136">`scriptLocation`屬性會自動偵測 proxy 設定指令碼的參考。</span><span class="sxs-lookup"><span data-stu-id="70b9a-136">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="70b9a-137"><xref:System.Net.WebProxy>類別會嘗試找出在設定指令碼 (通常是具名 Wpad.dat) 時，當**使用自動設定指令碼**Internet Explorer 中選取選項。</span><span class="sxs-lookup"><span data-stu-id="70b9a-137">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span>  
  
 <span data-ttu-id="70b9a-138">使用`usesystemdefault`要移轉至 2.0 版的.NET Framework 1.1 版應用程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="70b9a-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="70b9a-139">如果擲回例外狀況`proxyaddress`屬性會指定無效的預設 proxy。</span><span class="sxs-lookup"><span data-stu-id="70b9a-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="70b9a-140">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="70b9a-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="70b9a-141">組態檔</span><span class="sxs-lookup"><span data-stu-id="70b9a-141">Configuration Files</span></span>  
 <span data-ttu-id="70b9a-142">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="70b9a-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70b9a-143">範例</span><span class="sxs-lookup"><span data-stu-id="70b9a-143">Example</span></span>  
 <span data-ttu-id="70b9a-144">下列範例會使用來自 Internet Explorer proxy 的預設值，指定 proxy 位址，並略過本機存取的 proxy。</span><span class="sxs-lookup"><span data-stu-id="70b9a-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="70b9a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70b9a-145">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="70b9a-146">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="70b9a-146">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
