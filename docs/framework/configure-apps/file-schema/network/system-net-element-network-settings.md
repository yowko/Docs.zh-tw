---
title: '&lt;system.Net&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 82e022e28d3559791be3236fb80081807426a456
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192534"
---
# <a name="ltsystemnetgt-element-network-settings"></a><span data-ttu-id="a0d71-102">&lt;system.Net&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="a0d71-102">&lt;system.Net&gt; Element (Network Settings)</span></span>
<span data-ttu-id="a0d71-103">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="a0d71-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="a0d71-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a0d71-104">\<configuration></span></span>  
<span data-ttu-id="a0d71-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a0d71-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d71-106">語法</span><span class="sxs-lookup"><span data-stu-id="a0d71-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0d71-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a0d71-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a0d71-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a0d71-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0d71-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a0d71-109">Attributes</span></span>  
 <span data-ttu-id="a0d71-110">無。</span><span class="sxs-lookup"><span data-stu-id="a0d71-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0d71-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a0d71-111">Child Elements</span></span>  
  
|<span data-ttu-id="a0d71-112">**目**</span><span class="sxs-lookup"><span data-stu-id="a0d71-112">**Element**</span></span>|<span data-ttu-id="a0d71-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="a0d71-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a0d71-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="a0d71-114">authenticationModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="a0d71-115">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="a0d71-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="a0d71-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="a0d71-116">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="a0d71-117">指定連線到網際網路主機的最大數目。</span><span class="sxs-lookup"><span data-stu-id="a0d71-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="a0d71-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="a0d71-118">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="a0d71-119">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a0d71-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="a0d71-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="a0d71-120">mailSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="a0d71-121">設定 Simple Mail Transport Protocol (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="a0d71-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="a0d71-122">Requestcaching></span><span class="sxs-lookup"><span data-stu-id="a0d71-122">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="a0d71-123">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="a0d71-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="a0d71-124">設定</span><span class="sxs-lookup"><span data-stu-id="a0d71-124">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="a0d71-125">會設定基本的網路中的類別選項<xref:System.Net>和相關的子命名空間。</span><span class="sxs-lookup"><span data-stu-id="a0d71-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="a0d71-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="a0d71-126">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="a0d71-127">指定用於來自網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="a0d71-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0d71-128">父項目</span><span class="sxs-lookup"><span data-stu-id="a0d71-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a0d71-129">**目**</span><span class="sxs-lookup"><span data-stu-id="a0d71-129">**Element**</span></span>|<span data-ttu-id="a0d71-130">**描述**</span><span class="sxs-lookup"><span data-stu-id="a0d71-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a0d71-131">組態</span><span class="sxs-lookup"><span data-stu-id="a0d71-131">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a0d71-132">包含的所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="a0d71-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d71-133">備註</span><span class="sxs-lookup"><span data-stu-id="a0d71-133">Remarks</span></span>  
 <span data-ttu-id="a0d71-134">[ \<System.net >](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)項目包含設定中的類別<xref:System.Net>和相關的子命名空間。</span><span class="sxs-lookup"><span data-stu-id="a0d71-134">The [\<system.net>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="a0d71-135">這些設定會設定驗證模組、 連線的管理、 郵件設定、 proxy 伺服器和接收來自網際網路主機的資訊適用於網際網路要求模組。</span><span class="sxs-lookup"><span data-stu-id="a0d71-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0d71-136">範例</span><span class="sxs-lookup"><span data-stu-id="a0d71-136">Example</span></span>  
 <span data-ttu-id="a0d71-137">下列範例顯示所使用的一般組態<xref:System.Net>類別。</span><span class="sxs-lookup"><span data-stu-id="a0d71-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a0d71-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0d71-138">See Also</span></span>  
- [<span data-ttu-id="a0d71-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a0d71-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
