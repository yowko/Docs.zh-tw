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
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154552"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="92003-102">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="92003-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="92003-103">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="92003-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="92003-104">語法</span><span class="sxs-lookup"><span data-stu-id="92003-104">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92003-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="92003-105">Attributes and Elements</span></span>  
 <span data-ttu-id="92003-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="92003-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92003-107">屬性</span><span class="sxs-lookup"><span data-stu-id="92003-107">Attributes</span></span>  
 <span data-ttu-id="92003-108">無。</span><span class="sxs-lookup"><span data-stu-id="92003-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="92003-109">子元素</span><span class="sxs-lookup"><span data-stu-id="92003-109">Child Elements</span></span>  
  
|<span data-ttu-id="92003-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="92003-110">**Element**</span></span>|<span data-ttu-id="92003-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="92003-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="92003-112">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="92003-112">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="92003-113">指定用來驗證網際網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="92003-113">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="92003-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="92003-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="92003-115">指定網際網路主機的最大連接數目。</span><span class="sxs-lookup"><span data-stu-id="92003-115">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="92003-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="92003-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="92003-117">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="92003-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="92003-118">mailSettings</span><span class="sxs-lookup"><span data-stu-id="92003-118">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="92003-119">設定簡單郵件傳輸通訊協定（SMTP）郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="92003-119">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="92003-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="92003-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="92003-121">控制網路要求的快取機制。</span><span class="sxs-lookup"><span data-stu-id="92003-121">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="92003-122">設定</span><span class="sxs-lookup"><span data-stu-id="92003-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="92003-123">為 <xref:System.Net> 和相關的子命名空間中的類別設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="92003-123">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="92003-124">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="92003-124">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="92003-125">指定要用來從網際網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="92003-125">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92003-126">父項目</span><span class="sxs-lookup"><span data-stu-id="92003-126">Parent Elements</span></span>  
  
|<span data-ttu-id="92003-127">**元素**</span><span class="sxs-lookup"><span data-stu-id="92003-127">**Element**</span></span>|<span data-ttu-id="92003-128">**說明**</span><span class="sxs-lookup"><span data-stu-id="92003-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="92003-129">設定</span><span class="sxs-lookup"><span data-stu-id="92003-129">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="92003-130">包含所有命名空間的設定。</span><span class="sxs-lookup"><span data-stu-id="92003-130">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92003-131">備註</span><span class="sxs-lookup"><span data-stu-id="92003-131">Remarks</span></span>  
 <span data-ttu-id="92003-132">[\<system.net>](system-net-element-network-settings.md)元素包含 <xref:System.Net> 和相關子命名空間中的類別設定。</span><span class="sxs-lookup"><span data-stu-id="92003-132">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="92003-133">設定可設定驗證模組、連線管理、郵件設定、proxy 伺服器，以及從網際網路主機接收資訊的網際網路要求模組。</span><span class="sxs-lookup"><span data-stu-id="92003-133">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92003-134">範例</span><span class="sxs-lookup"><span data-stu-id="92003-134">Example</span></span>  
 <span data-ttu-id="92003-135">下列範例顯示類別所使用的一般設定 <xref:System.Net> 。</span><span class="sxs-lookup"><span data-stu-id="92003-135">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92003-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92003-136">See also</span></span>

- [<span data-ttu-id="92003-137">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="92003-137">Network Settings Schema</span></span>](index.md)
