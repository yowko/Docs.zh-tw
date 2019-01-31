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
ms.openlocfilehash: a6c6d85d8ec1b79f6b3ddf53af0a4b289289dd6a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256859"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="dba6e-102">\<proxy > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="dba6e-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="dba6e-103">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="dba6e-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="dba6e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dba6e-104">\<configuration></span></span>  
<span data-ttu-id="dba6e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="dba6e-105">\<system.net></span></span>  
<span data-ttu-id="dba6e-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="dba6e-106">\<defaultProxy></span></span>  
<span data-ttu-id="dba6e-107">\<proxy></span><span class="sxs-lookup"><span data-stu-id="dba6e-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba6e-108">語法</span><span class="sxs-lookup"><span data-stu-id="dba6e-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dba6e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dba6e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dba6e-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dba6e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dba6e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dba6e-111">Attributes</span></span>  
  
|<span data-ttu-id="dba6e-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="dba6e-112">**Attribute**</span></span>|<span data-ttu-id="dba6e-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="dba6e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="dba6e-114">指定是否自動偵測 proxy。</span><span class="sxs-lookup"><span data-stu-id="dba6e-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="dba6e-115">預設值為 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="dba6e-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="dba6e-116">指定是否略過本機資源的 proxy。</span><span class="sxs-lookup"><span data-stu-id="dba6e-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="dba6e-117">本機資源包含在本機伺服器 (`http://localhost`， `http://loopback`，或`http://127.0.0.1`) 和不含點的 URI (`http://webserver`)。</span><span class="sxs-lookup"><span data-stu-id="dba6e-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="dba6e-118">預設值為 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="dba6e-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="dba6e-119">指定 proxy 使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="dba6e-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="dba6e-120">指定的組態指令碼的位置。</span><span class="sxs-lookup"><span data-stu-id="dba6e-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="dba6e-121">請勿使用`bypassonlocal`具有此屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="dba6e-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="dba6e-122">指定是否要使用 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="dba6e-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="dba6e-123">如果設定為`true`，後續的屬性會覆寫 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="dba6e-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="dba6e-124">預設值為 `unspecified`。</span><span class="sxs-lookup"><span data-stu-id="dba6e-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dba6e-125">子元素</span><span class="sxs-lookup"><span data-stu-id="dba6e-125">Child Elements</span></span>  
 <span data-ttu-id="dba6e-126">無。</span><span class="sxs-lookup"><span data-stu-id="dba6e-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dba6e-127">父項目</span><span class="sxs-lookup"><span data-stu-id="dba6e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="dba6e-128">**目**</span><span class="sxs-lookup"><span data-stu-id="dba6e-128">**Element**</span></span>|<span data-ttu-id="dba6e-129">**描述**</span><span class="sxs-lookup"><span data-stu-id="dba6e-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dba6e-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="dba6e-130">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="dba6e-131">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="dba6e-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="dba6e-132">文字值</span><span class="sxs-lookup"><span data-stu-id="dba6e-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dba6e-133">備註</span><span class="sxs-lookup"><span data-stu-id="dba6e-133">Remarks</span></span>  
 <span data-ttu-id="dba6e-134">`proxy`項目會定義應用程式 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="dba6e-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="dba6e-135">如果組態檔中沒有這個項目，.NET Framework 會在 Internet Explorer 中使用的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="dba6e-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="dba6e-136">值`proxyaddress`屬性應該是語式正確的 Uniform Resource Indicator (URI)。</span><span class="sxs-lookup"><span data-stu-id="dba6e-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="dba6e-137">`scriptLocation`屬性會自動偵測 proxy 設定指令碼的參考。</span><span class="sxs-lookup"><span data-stu-id="dba6e-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="dba6e-138"><xref:System.Net.WebProxy>類別會嘗試找出組態指令碼 (通常是具名 Wpad.dat) 時，當**使用自動設定指令碼**Internet Explorer 中選取選項。</span><span class="sxs-lookup"><span data-stu-id="dba6e-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="dba6e-139">如果`bypassonlocal`設定為任何值，`scriptLocation`會被忽略。</span><span class="sxs-lookup"><span data-stu-id="dba6e-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="dba6e-140">使用`usesystemdefault`要移轉至 2.0 版的.NET Framework 1.1 版應用程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="dba6e-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="dba6e-141">如果將會擲回例外狀況`proxyaddress`屬性會指定無效的預設 proxy。</span><span class="sxs-lookup"><span data-stu-id="dba6e-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="dba6e-142">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="dba6e-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dba6e-143">組態檔</span><span class="sxs-lookup"><span data-stu-id="dba6e-143">Configuration Files</span></span>  
 <span data-ttu-id="dba6e-144">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="dba6e-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dba6e-145">範例</span><span class="sxs-lookup"><span data-stu-id="dba6e-145">Example</span></span>  
 <span data-ttu-id="dba6e-146">下列範例會使用來自 Internet Explorer proxy 的預設值，指定 proxy 位址，並會略過本機存取的 proxy。</span><span class="sxs-lookup"><span data-stu-id="dba6e-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dba6e-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba6e-147">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="dba6e-148">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="dba6e-148">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
