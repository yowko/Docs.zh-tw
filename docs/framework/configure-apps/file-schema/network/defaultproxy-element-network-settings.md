---
title: <defaultProxy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 9d9e96296cb764d3fbb3cdcd561e036f9ad6aa2b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257209"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="f33b5-102">\<defaultProxy > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="f33b5-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="f33b5-103">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f33b5-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="f33b5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f33b5-104">\<configuration></span></span>  
<span data-ttu-id="f33b5-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f33b5-105">\<system.net></span></span>  
<span data-ttu-id="f33b5-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="f33b5-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f33b5-107">語法</span><span class="sxs-lookup"><span data-stu-id="f33b5-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f33b5-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f33b5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f33b5-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f33b5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f33b5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f33b5-110">Attributes</span></span>  
  
|<span data-ttu-id="f33b5-111">**目**</span><span class="sxs-lookup"><span data-stu-id="f33b5-111">**Element**</span></span>|<span data-ttu-id="f33b5-112">**描述**</span><span class="sxs-lookup"><span data-stu-id="f33b5-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="f33b5-113">指定是否使用 Web Proxy。</span><span class="sxs-lookup"><span data-stu-id="f33b5-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="f33b5-114">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f33b5-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="f33b5-115">指定此主機的預設認證是否用來存取 Web Proxy。</span><span class="sxs-lookup"><span data-stu-id="f33b5-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="f33b5-116">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="f33b5-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f33b5-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f33b5-117">Child Elements</span></span>  
  
|<span data-ttu-id="f33b5-118">**目**</span><span class="sxs-lookup"><span data-stu-id="f33b5-118">**Element**</span></span>|<span data-ttu-id="f33b5-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="f33b5-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f33b5-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="f33b5-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="f33b5-121">提供一組位址的規則運算式，說明不使用 Proxy。</span><span class="sxs-lookup"><span data-stu-id="f33b5-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="f33b5-122">module</span><span class="sxs-lookup"><span data-stu-id="f33b5-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="f33b5-123">將新的 Proxy 模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="f33b5-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="f33b5-124">proxy</span><span class="sxs-lookup"><span data-stu-id="f33b5-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="f33b5-125">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f33b5-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f33b5-126">父項目</span><span class="sxs-lookup"><span data-stu-id="f33b5-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f33b5-127">**目**</span><span class="sxs-lookup"><span data-stu-id="f33b5-127">**Element**</span></span>|<span data-ttu-id="f33b5-128">**描述**</span><span class="sxs-lookup"><span data-stu-id="f33b5-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f33b5-129">system.net</span><span class="sxs-lookup"><span data-stu-id="f33b5-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="f33b5-130">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="f33b5-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f33b5-131">備註</span><span class="sxs-lookup"><span data-stu-id="f33b5-131">Remarks</span></span>  
 <span data-ttu-id="f33b5-132">如果 defaultProxy 項目是空的，則會使用來自 Internet Explorer 的 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="f33b5-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="f33b5-133">這個行為與 .NET Framework 1.1 版的不同。</span><span class="sxs-lookup"><span data-stu-id="f33b5-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f33b5-134">如果將會擲回例外狀況[模組](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)項目會指定非公用型別、 型別並非衍生自<xref:System.Net.IWebProxy>類別，這個物件的預設建構函式的例外狀況發生，或發生例外狀況時正在擷取系統指定的預設 proxy。</span><span class="sxs-lookup"><span data-stu-id="f33b5-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="f33b5-135">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f33b5-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f33b5-136">組態檔</span><span class="sxs-lookup"><span data-stu-id="f33b5-136">Configuration Files</span></span>  
 <span data-ttu-id="f33b5-137">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="f33b5-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f33b5-138">範例</span><span class="sxs-lookup"><span data-stu-id="f33b5-138">Example</span></span>  
 <span data-ttu-id="f33b5-139">下列範例會使用來自 Internet Explorer proxy 的預設值，指定 proxy 位址，並會略過本機存取及 contoso.com 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="f33b5-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f33b5-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f33b5-140">See also</span></span>
- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f33b5-141">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f33b5-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
