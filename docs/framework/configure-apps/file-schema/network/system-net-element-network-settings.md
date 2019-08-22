---
title: <system.Net> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 449146612938700f59f5e2ec761526d1dc66a3fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663949"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="fe2e3-102">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="fe2e3-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="fe2e3-103">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
 <span data-ttu-id="fe2e3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fe2e3-104">\<configuration></span></span>  
<span data-ttu-id="fe2e3-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fe2e3-105">\<system.net></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe2e3-106">語法</span><span class="sxs-lookup"><span data-stu-id="fe2e3-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe2e3-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fe2e3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="fe2e3-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe2e3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="fe2e3-109">Attributes</span></span>  
 <span data-ttu-id="fe2e3-110">無。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe2e3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="fe2e3-111">Child Elements</span></span>  
  
|<span data-ttu-id="fe2e3-112">**目**</span><span class="sxs-lookup"><span data-stu-id="fe2e3-112">**Element**</span></span>|<span data-ttu-id="fe2e3-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="fe2e3-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fe2e3-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="fe2e3-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="fe2e3-115">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="fe2e3-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="fe2e3-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="fe2e3-117">指定網際網路主機的最大連接數目。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="fe2e3-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="fe2e3-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="fe2e3-119">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="fe2e3-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="fe2e3-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="fe2e3-121">設定簡單郵件傳輸通訊協定 (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="fe2e3-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="fe2e3-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="fe2e3-123">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="fe2e3-124">設置</span><span class="sxs-lookup"><span data-stu-id="fe2e3-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="fe2e3-125">為和相關的<xref:System.Net>子命名空間中的類別設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="fe2e3-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="fe2e3-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="fe2e3-127">指定要用來從網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe2e3-128">父項目</span><span class="sxs-lookup"><span data-stu-id="fe2e3-128">Parent Elements</span></span>  
  
|<span data-ttu-id="fe2e3-129">**目**</span><span class="sxs-lookup"><span data-stu-id="fe2e3-129">**Element**</span></span>|<span data-ttu-id="fe2e3-130">**描述**</span><span class="sxs-lookup"><span data-stu-id="fe2e3-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fe2e3-131">configuration</span><span class="sxs-lookup"><span data-stu-id="fe2e3-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="fe2e3-132">包含所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe2e3-133">備註</span><span class="sxs-lookup"><span data-stu-id="fe2e3-133">Remarks</span></span>  
 <span data-ttu-id="fe2e3-134">System.web > 元素包含<xref:System.Net>和相關子命名空間中的類別設定。 [ \< ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fe2e3-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="fe2e3-135">設定可設定驗證模組、連線管理、郵件設定、proxy 伺服器, 以及從網際網路主機接收資訊的網際網路要求模組。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe2e3-136">範例</span><span class="sxs-lookup"><span data-stu-id="fe2e3-136">Example</span></span>  
 <span data-ttu-id="fe2e3-137">下列範例顯示<xref:System.Net>類別所使用的一般設定。</span><span class="sxs-lookup"><span data-stu-id="fe2e3-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe2e3-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe2e3-138">See also</span></span>

- [<span data-ttu-id="fe2e3-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="fe2e3-139">Network Settings Schema</span></span>](index.md)
