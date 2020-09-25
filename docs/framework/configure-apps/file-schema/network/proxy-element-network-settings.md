---
title: <proxy> 項目 (網路設定)
description: <proxy>網路設定元素會定義 .NET Framework 中的 proxy 伺服器選項。 本文包含範例。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 54b324dcd27d5827159bc2d773365e388a367d26
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190211"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="2699d-104">\<proxy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="2699d-104">\<proxy> Element (Network Settings)</span></span>

<span data-ttu-id="2699d-105">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2699d-105">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="2699d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2699d-106">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2699d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2699d-107">Attributes and Elements</span></span>  

 <span data-ttu-id="2699d-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2699d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2699d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="2699d-109">Attributes</span></span>  
  
|<span data-ttu-id="2699d-110">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="2699d-110">**Attribute**</span></span>|<span data-ttu-id="2699d-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="2699d-111">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="2699d-112">指定是否自動偵測 Proxy。</span><span class="sxs-lookup"><span data-stu-id="2699d-112">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="2699d-113">預設值是 `Unspecified`。</span><span class="sxs-lookup"><span data-stu-id="2699d-113">The default value is `Unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="2699d-114">指定是否略過本機資源的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="2699d-114">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="2699d-115">本機資源包含本機伺服器 (`http://localhost` 、 `http://loopback` 或) ， `http://127.0.0.1` 以及不含句號 () 的 URI `http://webserver` 。</span><span class="sxs-lookup"><span data-stu-id="2699d-115">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="2699d-116">預設值是 `Unspecified`。</span><span class="sxs-lookup"><span data-stu-id="2699d-116">The default value is `Unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="2699d-117">指定要使用的 proxy URI。</span><span class="sxs-lookup"><span data-stu-id="2699d-117">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="2699d-118">指定設定腳本的位置。</span><span class="sxs-lookup"><span data-stu-id="2699d-118">Specifies the location of the configuration script.</span></span> <span data-ttu-id="2699d-119">請勿將 `bypassonlocal` 屬性與此屬性搭配使用。</span><span class="sxs-lookup"><span data-stu-id="2699d-119">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="2699d-120">指定是否要使用 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="2699d-120">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="2699d-121">如果設定為 `True` ，後續的屬性將會覆寫 Internet Explorer proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="2699d-121">If set to `True`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="2699d-122">預設值是 `Unspecified`。</span><span class="sxs-lookup"><span data-stu-id="2699d-122">The default value is `Unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2699d-123">子元素</span><span class="sxs-lookup"><span data-stu-id="2699d-123">Child Elements</span></span>  

 <span data-ttu-id="2699d-124">無。</span><span class="sxs-lookup"><span data-stu-id="2699d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2699d-125">父項目</span><span class="sxs-lookup"><span data-stu-id="2699d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2699d-126">**Element**</span><span class="sxs-lookup"><span data-stu-id="2699d-126">**Element**</span></span>|<span data-ttu-id="2699d-127">**說明**</span><span class="sxs-lookup"><span data-stu-id="2699d-127">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2699d-128">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="2699d-128">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="2699d-129">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2699d-129">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="2699d-130">文字值</span><span class="sxs-lookup"><span data-stu-id="2699d-130">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2699d-131">備註</span><span class="sxs-lookup"><span data-stu-id="2699d-131">Remarks</span></span>  

 <span data-ttu-id="2699d-132">`proxy`元素會定義應用程式的 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2699d-132">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="2699d-133">如果設定檔中遺漏此元素，.NET Framework 將會使用 Internet Explorer 中的 proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="2699d-133">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="2699d-134">屬性的值應該是格式正確的 `proxyaddress` 統一資源指標 (URI) 。</span><span class="sxs-lookup"><span data-stu-id="2699d-134">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="2699d-135">`scriptLocation`屬性是指自動偵測 proxy 設定腳本。</span><span class="sxs-lookup"><span data-stu-id="2699d-135">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="2699d-136"><xref:System.Net.WebProxy>當您在 Internet Explorer 中選取 [**使用自動設定腳本**] 選項時，類別會嘗試找出設定腳本 (通常名為 Wpad) 。</span><span class="sxs-lookup"><span data-stu-id="2699d-136">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="2699d-137">如果 `bypassonlocal` 設定為任何值， `scriptLocation` 則會忽略。</span><span class="sxs-lookup"><span data-stu-id="2699d-137">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="2699d-138">針對要 `usesystemdefault` 遷移至2.0 版的 .NET Framework 版本1.1 應用程式，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="2699d-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="2699d-139">如果 `proxyaddress` 屬性指定的預設 proxy 無效，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2699d-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="2699d-140">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2699d-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2699d-141">組態檔</span><span class="sxs-lookup"><span data-stu-id="2699d-141">Configuration Files</span></span>  

 <span data-ttu-id="2699d-142">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="2699d-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2699d-143">範例</span><span class="sxs-lookup"><span data-stu-id="2699d-143">Example</span></span>  

 <span data-ttu-id="2699d-144">下列範例會使用 Internet Explorer proxy 的預設值、指定 proxy 位址，以及略過 proxy 以進行本機存取。</span><span class="sxs-lookup"><span data-stu-id="2699d-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2699d-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2699d-145">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="2699d-146">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2699d-146">Network Settings Schema</span></span>](index.md)
