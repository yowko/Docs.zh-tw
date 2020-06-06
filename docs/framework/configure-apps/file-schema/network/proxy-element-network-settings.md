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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154786"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="e0265-102">\<proxy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="e0265-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="e0265-103">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e0265-103">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="e0265-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0265-104">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0265-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e0265-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e0265-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e0265-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0265-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e0265-107">Attributes</span></span>  
  
|<span data-ttu-id="e0265-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e0265-108">**Attribute**</span></span>|<span data-ttu-id="e0265-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="e0265-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="e0265-110">指定是否自動偵測 Proxy。</span><span class="sxs-lookup"><span data-stu-id="e0265-110">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="e0265-111">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="e0265-111">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="e0265-112">指定是否略過本機資源的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="e0265-112">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="e0265-113">本機資源包括本機伺服器（ `http://localhost` 、 `http://loopback` 或 `http://127.0.0.1` ），以及沒有句號（）的 URI `http://webserver` 。</span><span class="sxs-lookup"><span data-stu-id="e0265-113">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="e0265-114">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="e0265-114">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="e0265-115">指定要使用的 proxy URI。</span><span class="sxs-lookup"><span data-stu-id="e0265-115">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="e0265-116">指定設定腳本的位置。</span><span class="sxs-lookup"><span data-stu-id="e0265-116">Specifies the location of the configuration script.</span></span> <span data-ttu-id="e0265-117">請勿使用屬性搭配 `bypassonlocal` 這個屬性。</span><span class="sxs-lookup"><span data-stu-id="e0265-117">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="e0265-118">指定是否要使用 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="e0265-118">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="e0265-119">如果設定為 `true` ，後續的屬性會覆寫 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="e0265-119">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="e0265-120">預設值是 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="e0265-120">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0265-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e0265-121">Child Elements</span></span>  
 <span data-ttu-id="e0265-122">無。</span><span class="sxs-lookup"><span data-stu-id="e0265-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0265-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e0265-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e0265-124">**元素**</span><span class="sxs-lookup"><span data-stu-id="e0265-124">**Element**</span></span>|<span data-ttu-id="e0265-125">**說明**</span><span class="sxs-lookup"><span data-stu-id="e0265-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e0265-126">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="e0265-126">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e0265-127">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e0265-127">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="e0265-128">文字值</span><span class="sxs-lookup"><span data-stu-id="e0265-128">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0265-129">備註</span><span class="sxs-lookup"><span data-stu-id="e0265-129">Remarks</span></span>  
 <span data-ttu-id="e0265-130">`proxy`元素會定義應用程式的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e0265-130">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="e0265-131">如果設定檔中缺少此元素，則 .NET Framework 會使用 Internet Explorer 中的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="e0265-131">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="e0265-132">屬性的值應該是格式正確的 `proxyaddress` 統一資源指標（URI）。</span><span class="sxs-lookup"><span data-stu-id="e0265-132">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="e0265-133">`scriptLocation`屬性會參考 proxy 設定腳本的自動偵測。</span><span class="sxs-lookup"><span data-stu-id="e0265-133">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="e0265-134"><xref:System.Net.WebProxy>當 Internet Explorer 中選取了 [**使用自動設定腳本**] 選項時，類別會嘗試尋找設定腳本（通常是名為 Wpad. dat）。</span><span class="sxs-lookup"><span data-stu-id="e0265-134">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="e0265-135">如果 `bypassonlocal` 設定為任何值， `scriptLocation` 則會忽略。</span><span class="sxs-lookup"><span data-stu-id="e0265-135">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="e0265-136">針對要 `usesystemdefault` 遷移至2.0 版的 .NET Framework 版本1.1 應用程式，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="e0265-136">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="e0265-137">如果 `proxyaddress` 屬性指定了不正確預設 proxy，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e0265-137">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="e0265-138">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e0265-138">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e0265-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="e0265-139">Configuration Files</span></span>  
 <span data-ttu-id="e0265-140">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="e0265-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0265-141">範例</span><span class="sxs-lookup"><span data-stu-id="e0265-141">Example</span></span>  
 <span data-ttu-id="e0265-142">下列範例會使用 Internet Explorer proxy 的預設值、指定 proxy 位址，並略過 proxy 以進行本機存取。</span><span class="sxs-lookup"><span data-stu-id="e0265-142">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0265-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0265-143">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e0265-144">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e0265-144">Network Settings Schema</span></span>](index.md)
