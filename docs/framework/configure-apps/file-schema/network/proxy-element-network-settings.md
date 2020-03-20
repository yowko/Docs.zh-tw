---
title: <proxy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154786"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="89bc7-102">\<代理>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="89bc7-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="89bc7-103">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="89bc7-103">Defines a proxy server.</span></span>  

<span data-ttu-id="89bc7-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="89bc7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="89bc7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="89bc7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="89bc7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<預設代理>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="89bc7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="89bc7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<代理>**</span><span class="sxs-lookup"><span data-stu-id="89bc7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="89bc7-108">語法</span><span class="sxs-lookup"><span data-stu-id="89bc7-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89bc7-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="89bc7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="89bc7-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="89bc7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89bc7-111">屬性</span><span class="sxs-lookup"><span data-stu-id="89bc7-111">Attributes</span></span>  
  
|<span data-ttu-id="89bc7-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="89bc7-112">**Attribute**</span></span>|<span data-ttu-id="89bc7-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="89bc7-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="89bc7-114">指定是否自動偵測 Proxy。</span><span class="sxs-lookup"><span data-stu-id="89bc7-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="89bc7-115">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="89bc7-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="89bc7-116">指定是否略過本機資源的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="89bc7-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="89bc7-117">本地資源包括本機伺服器`http://localhost`（、`http://loopback`或`http://127.0.0.1`） 和沒有句點`http://webserver`（ 的 URI ）</span><span class="sxs-lookup"><span data-stu-id="89bc7-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="89bc7-118">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="89bc7-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="89bc7-119">指定要使用的代理 URI。</span><span class="sxs-lookup"><span data-stu-id="89bc7-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="89bc7-120">指定配置腳本的位置。</span><span class="sxs-lookup"><span data-stu-id="89bc7-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="89bc7-121">不要將`bypassonlocal`屬性與此屬性一起使用。</span><span class="sxs-lookup"><span data-stu-id="89bc7-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="89bc7-122">指定是否使用 Internet 資源管理器代理設置。</span><span class="sxs-lookup"><span data-stu-id="89bc7-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="89bc7-123">如果設置為`true`，後續屬性將覆蓋 Internet 資源管理器代理設置。</span><span class="sxs-lookup"><span data-stu-id="89bc7-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="89bc7-124">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="89bc7-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89bc7-125">子元素</span><span class="sxs-lookup"><span data-stu-id="89bc7-125">Child Elements</span></span>  
 <span data-ttu-id="89bc7-126">無。</span><span class="sxs-lookup"><span data-stu-id="89bc7-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89bc7-127">父項目</span><span class="sxs-lookup"><span data-stu-id="89bc7-127">Parent Elements</span></span>  
  
|<span data-ttu-id="89bc7-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="89bc7-128">**Element**</span></span>|<span data-ttu-id="89bc7-129">**描述**</span><span class="sxs-lookup"><span data-stu-id="89bc7-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="89bc7-130">預設代理</span><span class="sxs-lookup"><span data-stu-id="89bc7-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="89bc7-131">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="89bc7-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="89bc7-132">文字值</span><span class="sxs-lookup"><span data-stu-id="89bc7-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89bc7-133">備註</span><span class="sxs-lookup"><span data-stu-id="89bc7-133">Remarks</span></span>  
 <span data-ttu-id="89bc7-134">該`proxy`元素為應用程式定義代理伺服器。</span><span class="sxs-lookup"><span data-stu-id="89bc7-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="89bc7-135">如果設定檔中缺少此元素，則 .NET 框架將使用 Internet 資源管理器中的代理設置。</span><span class="sxs-lookup"><span data-stu-id="89bc7-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="89bc7-136">`proxyaddress`屬性的值應為格式良好的統一資源指示器 （URI）。</span><span class="sxs-lookup"><span data-stu-id="89bc7-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="89bc7-137">該`scriptLocation`屬性是指代理配置腳本的自動檢測。</span><span class="sxs-lookup"><span data-stu-id="89bc7-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="89bc7-138">在<xref:System.Net.WebProxy>Internet 資源管理器中選擇 **"使用自動設定腳本"** 選項時，該類將嘗試查找配置腳本（通常稱為 Wpad.dat）。</span><span class="sxs-lookup"><span data-stu-id="89bc7-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="89bc7-139">如果`bypassonlocal`設置為任何值，`scriptLocation`則忽略。</span><span class="sxs-lookup"><span data-stu-id="89bc7-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="89bc7-140">對`usesystemdefault`正在遷移到版本 2.0 的 .NET 框架版本 1.1 應用程式使用該屬性。</span><span class="sxs-lookup"><span data-stu-id="89bc7-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="89bc7-141">如果屬性指定不正確預設`proxyaddress`代理，則引發異常。</span><span class="sxs-lookup"><span data-stu-id="89bc7-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="89bc7-142">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="89bc7-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="89bc7-143">組態檔</span><span class="sxs-lookup"><span data-stu-id="89bc7-143">Configuration Files</span></span>  
 <span data-ttu-id="89bc7-144">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="89bc7-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89bc7-145">範例</span><span class="sxs-lookup"><span data-stu-id="89bc7-145">Example</span></span>  
 <span data-ttu-id="89bc7-146">下面的示例使用 Internet Explorer 代理的預設值，指定代理位址，並繞過代理進行本地訪問。</span><span class="sxs-lookup"><span data-stu-id="89bc7-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89bc7-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89bc7-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="89bc7-148">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="89bc7-148">Network Settings Schema</span></span>](index.md)
