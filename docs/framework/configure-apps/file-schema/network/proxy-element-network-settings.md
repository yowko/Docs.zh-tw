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
ms.openlocfilehash: a183c4160c4cd55b05c5c23f7a10e3a1d1c74ea4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659283"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="1be34-102">\<proxy > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="1be34-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="1be34-103">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1be34-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="1be34-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1be34-104">\<configuration></span></span>  
<span data-ttu-id="1be34-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1be34-105">\<system.net></span></span>  
<span data-ttu-id="1be34-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="1be34-106">\<defaultProxy></span></span>  
<span data-ttu-id="1be34-107">\<proxy ></span><span class="sxs-lookup"><span data-stu-id="1be34-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be34-108">語法</span><span class="sxs-lookup"><span data-stu-id="1be34-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1be34-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1be34-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1be34-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1be34-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1be34-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1be34-111">Attributes</span></span>  
  
|<span data-ttu-id="1be34-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="1be34-112">**Attribute**</span></span>|<span data-ttu-id="1be34-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="1be34-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="1be34-114">指定是否自動偵測到 proxy。</span><span class="sxs-lookup"><span data-stu-id="1be34-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="1be34-115">預設值為 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="1be34-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="1be34-116">指定是否略過本機資源的 proxy。</span><span class="sxs-lookup"><span data-stu-id="1be34-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="1be34-117">本機資源包括本機伺服器`http://localhost`(、 `http://loopback`或`http://127.0.0.1`), 以及沒有句號 (`http://webserver`) 的 URI。</span><span class="sxs-lookup"><span data-stu-id="1be34-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="1be34-118">預設值為 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="1be34-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="1be34-119">指定要使用的 proxy URI。</span><span class="sxs-lookup"><span data-stu-id="1be34-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="1be34-120">指定設定腳本的位置。</span><span class="sxs-lookup"><span data-stu-id="1be34-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="1be34-121">請勿使用`bypassonlocal`屬性搭配這個屬性。</span><span class="sxs-lookup"><span data-stu-id="1be34-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="1be34-122">指定是否要使用 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="1be34-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="1be34-123">如果設定為`true`, 後續的屬性會覆寫 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="1be34-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="1be34-124">預設值為 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="1be34-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1be34-125">子元素</span><span class="sxs-lookup"><span data-stu-id="1be34-125">Child Elements</span></span>  
 <span data-ttu-id="1be34-126">無。</span><span class="sxs-lookup"><span data-stu-id="1be34-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1be34-127">父項目</span><span class="sxs-lookup"><span data-stu-id="1be34-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1be34-128">**目**</span><span class="sxs-lookup"><span data-stu-id="1be34-128">**Element**</span></span>|<span data-ttu-id="1be34-129">**描述**</span><span class="sxs-lookup"><span data-stu-id="1be34-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1be34-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="1be34-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="1be34-131">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1be34-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="1be34-132">文字值</span><span class="sxs-lookup"><span data-stu-id="1be34-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1be34-133">備註</span><span class="sxs-lookup"><span data-stu-id="1be34-133">Remarks</span></span>  
 <span data-ttu-id="1be34-134">`proxy`元素會定義應用程式的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1be34-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="1be34-135">如果設定檔中缺少此元素, 則 .NET Framework 會使用 Internet Explorer 中的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="1be34-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="1be34-136">`proxyaddress`屬性的值應該是格式正確的統一資源指標 (URI)。</span><span class="sxs-lookup"><span data-stu-id="1be34-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="1be34-137">`scriptLocation`屬性會參考 proxy 設定腳本的自動偵測。</span><span class="sxs-lookup"><span data-stu-id="1be34-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="1be34-138">當<xref:System.Net.WebProxy> Internet Explorer 中選取了 [**使用自動設定腳本**] 選項時, 類別會嘗試尋找設定腳本 (通常是名為 Wpad. dat)。</span><span class="sxs-lookup"><span data-stu-id="1be34-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="1be34-139">如果`bypassonlocal`設定為任何值, `scriptLocation`則會忽略。</span><span class="sxs-lookup"><span data-stu-id="1be34-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="1be34-140">針對要遷移至2.0 版的 .NET Framework 版本1.1 應用程式, 請使用屬性。`usesystemdefault`</span><span class="sxs-lookup"><span data-stu-id="1be34-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="1be34-141">如果`proxyaddress`屬性指定了不正確預設 proxy, 則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1be34-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="1be34-142">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1be34-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1be34-143">組態檔</span><span class="sxs-lookup"><span data-stu-id="1be34-143">Configuration Files</span></span>  
 <span data-ttu-id="1be34-144">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="1be34-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1be34-145">範例</span><span class="sxs-lookup"><span data-stu-id="1be34-145">Example</span></span>  
 <span data-ttu-id="1be34-146">下列範例會使用 Internet Explorer proxy 的預設值、指定 proxy 位址, 並略過 proxy 以進行本機存取。</span><span class="sxs-lookup"><span data-stu-id="1be34-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1be34-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1be34-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="1be34-148">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1be34-148">Network Settings Schema</span></span>](index.md)
