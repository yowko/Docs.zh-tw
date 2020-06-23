---
title: <defaultProxy> 項目 (網路設定)
description: <defaultProxy>Network settings 元素會在 .NET Framework 中設定超文字傳輸通訊協定（HTTP） proxy 伺服器。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 85004d49ce7605b050709a3019592ec696a7bada
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141627"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="97109-103">\<defaultProxy> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="97109-103">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="97109-104">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="97109-104">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="97109-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="97109-105">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="True|False"  
  useDefaultCredentials="True|False">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97109-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="97109-106">Attributes and Elements</span></span>  
 <span data-ttu-id="97109-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="97109-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97109-108">屬性</span><span class="sxs-lookup"><span data-stu-id="97109-108">Attributes</span></span>  
  
|<span data-ttu-id="97109-109">**元素**</span><span class="sxs-lookup"><span data-stu-id="97109-109">**Element**</span></span>|<span data-ttu-id="97109-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="97109-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="97109-111">指定是否使用 Web Proxy。</span><span class="sxs-lookup"><span data-stu-id="97109-111">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="97109-112">預設值是 `True`。</span><span class="sxs-lookup"><span data-stu-id="97109-112">The default value is `True`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="97109-113">指定此主機的預設認證是否用來存取 Web Proxy。</span><span class="sxs-lookup"><span data-stu-id="97109-113">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="97109-114">預設值是 `False`。</span><span class="sxs-lookup"><span data-stu-id="97109-114">The default value is `False`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97109-115">子元素</span><span class="sxs-lookup"><span data-stu-id="97109-115">Child Elements</span></span>  
  
|<span data-ttu-id="97109-116">**元素**</span><span class="sxs-lookup"><span data-stu-id="97109-116">**Element**</span></span>|<span data-ttu-id="97109-117">**說明**</span><span class="sxs-lookup"><span data-stu-id="97109-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="97109-118">bypasslist</span><span class="sxs-lookup"><span data-stu-id="97109-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="97109-119">提供一組位址的規則運算式，說明不使用 Proxy。</span><span class="sxs-lookup"><span data-stu-id="97109-119">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="97109-120">module</span><span class="sxs-lookup"><span data-stu-id="97109-120">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="97109-121">將新的 Proxy 模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="97109-121">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="97109-122">proxy</span><span class="sxs-lookup"><span data-stu-id="97109-122">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="97109-123">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="97109-123">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97109-124">父項目</span><span class="sxs-lookup"><span data-stu-id="97109-124">Parent Elements</span></span>  
  
|<span data-ttu-id="97109-125">**元素**</span><span class="sxs-lookup"><span data-stu-id="97109-125">**Element**</span></span>|<span data-ttu-id="97109-126">**說明**</span><span class="sxs-lookup"><span data-stu-id="97109-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="97109-127">system.net</span><span class="sxs-lookup"><span data-stu-id="97109-127">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="97109-128">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="97109-128">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97109-129">備註</span><span class="sxs-lookup"><span data-stu-id="97109-129">Remarks</span></span>  
 <span data-ttu-id="97109-130">如果 defaultProxy 項目是空的，則會使用來自 Internet Explorer 的 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="97109-130">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="97109-131">這個行為與 .NET Framework 1.1 版的不同。</span><span class="sxs-lookup"><span data-stu-id="97109-131">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="97109-132">如果[module](module-element-network-settings.md)元素指定非公用類型、類型不是衍生自 <xref:System.Net.IWebProxy> 類別、這個物件的無參數的函式發生例外狀況，或在抓取系統指定的預設 proxy 時發生例外狀況，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="97109-132">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="97109-133">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="97109-133">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="97109-134">組態檔</span><span class="sxs-lookup"><span data-stu-id="97109-134">Configuration Files</span></span>  
 <span data-ttu-id="97109-135">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="97109-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97109-136">範例</span><span class="sxs-lookup"><span data-stu-id="97109-136">Example</span></span>  
 <span data-ttu-id="97109-137">下列範例會使用 Internet Explorer proxy 的預設值、指定 proxy 位址，並略過 proxy 以進行本機存取和 contoso.com。</span><span class="sxs-lookup"><span data-stu-id="97109-137">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97109-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97109-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="97109-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="97109-139">Network Settings Schema</span></span>](index.md)
