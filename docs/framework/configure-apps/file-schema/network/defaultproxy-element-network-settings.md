---
title: "&lt;defaultProxy&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5fb58c01f8a8e3135878036454a1265e6b92e939
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaultproxygt-element-network-settings"></a><span data-ttu-id="aa324-102">&lt;defaultProxy&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="aa324-102">&lt;defaultProxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="aa324-103">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="aa324-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="aa324-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aa324-104">\<configuration></span></span>  
<span data-ttu-id="aa324-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="aa324-105">\<system.net></span></span>  
<span data-ttu-id="aa324-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="aa324-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa324-107">語法</span><span class="sxs-lookup"><span data-stu-id="aa324-107">Syntax</span></span>  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa324-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aa324-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aa324-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aa324-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa324-110">屬性</span><span class="sxs-lookup"><span data-stu-id="aa324-110">Attributes</span></span>  
  
|<span data-ttu-id="aa324-111">**目**</span><span class="sxs-lookup"><span data-stu-id="aa324-111">**Element**</span></span>|<span data-ttu-id="aa324-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="aa324-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="aa324-113">指定是否使用 Web Proxy。</span><span class="sxs-lookup"><span data-stu-id="aa324-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="aa324-114">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="aa324-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="aa324-115">指定此主機的預設認證是否用來存取 Web Proxy。</span><span class="sxs-lookup"><span data-stu-id="aa324-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="aa324-116">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="aa324-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa324-117">子元素</span><span class="sxs-lookup"><span data-stu-id="aa324-117">Child Elements</span></span>  
  
|<span data-ttu-id="aa324-118">**目**</span><span class="sxs-lookup"><span data-stu-id="aa324-118">**Element**</span></span>|<span data-ttu-id="aa324-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="aa324-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aa324-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="aa324-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="aa324-121">提供一組位址的規則運算式，說明不使用 Proxy。</span><span class="sxs-lookup"><span data-stu-id="aa324-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="aa324-122">模組</span><span class="sxs-lookup"><span data-stu-id="aa324-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="aa324-123">將新的 Proxy 模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="aa324-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="aa324-124">proxy</span><span class="sxs-lookup"><span data-stu-id="aa324-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="aa324-125">定義 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="aa324-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aa324-126">父項目</span><span class="sxs-lookup"><span data-stu-id="aa324-126">Parent Elements</span></span>  
  
|<span data-ttu-id="aa324-127">**目**</span><span class="sxs-lookup"><span data-stu-id="aa324-127">**Element**</span></span>|<span data-ttu-id="aa324-128">**說明**</span><span class="sxs-lookup"><span data-stu-id="aa324-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aa324-129">system.net</span><span class="sxs-lookup"><span data-stu-id="aa324-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="aa324-130">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="aa324-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa324-131">備註</span><span class="sxs-lookup"><span data-stu-id="aa324-131">Remarks</span></span>  
 <span data-ttu-id="aa324-132">如果 defaultProxy 項目是空的，則會使用來自 Internet Explorer 的 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="aa324-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="aa324-133">這個行為與 .NET Framework 1.1 版的不同。</span><span class="sxs-lookup"><span data-stu-id="aa324-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="aa324-134">如果擲回例外狀況[模組](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)項目會指定非公用型別、 型別並非衍生自<xref:System.Net.IWebProxy>類別，這個物件的預設建構函式發生例外狀況發生，或發生例外狀況時擷取系統指定的預設 proxy。</span><span class="sxs-lookup"><span data-stu-id="aa324-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="aa324-135">例外狀況的 <xref:System.Exception.InnerException%2A> 屬性應該會有此錯誤的根本原因之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="aa324-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="aa324-136">組態檔</span><span class="sxs-lookup"><span data-stu-id="aa324-136">Configuration Files</span></span>  
 <span data-ttu-id="aa324-137">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="aa324-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa324-138">範例</span><span class="sxs-lookup"><span data-stu-id="aa324-138">Example</span></span>  
 <span data-ttu-id="aa324-139">下列範例會使用來自 Internet Explorer proxy 的預設值，指定 proxy 位址，並略過本機存取及 contoso.com 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="aa324-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa324-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa324-140">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="aa324-141">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="aa324-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
