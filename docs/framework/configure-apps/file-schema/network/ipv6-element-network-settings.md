---
title: '&lt;ipv6&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4b73e5d781829292513e809c39ac9de9dfc6d0e8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742480"
---
# <a name="ltipv6gt-element-network-settings"></a><span data-ttu-id="4d616-102">&lt;ipv6&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="4d616-102">&lt;ipv6&gt; Element (Network Settings)</span></span>
<span data-ttu-id="4d616-103">可讓網際網路通訊協定第 6 版 (IPv6) 的過時成員的回應<xref:System.Net.Dns>類別。</span><span class="sxs-lookup"><span data-stu-id="4d616-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="4d616-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4d616-104">\<configuration></span></span>  
<span data-ttu-id="4d616-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4d616-105">\<system.net></span></span>  
<span data-ttu-id="4d616-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="4d616-106">\<settings></span></span>  
<span data-ttu-id="4d616-107">\<ipv6 ></span><span class="sxs-lookup"><span data-stu-id="4d616-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d616-108">語法</span><span class="sxs-lookup"><span data-stu-id="4d616-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d616-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4d616-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4d616-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4d616-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d616-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4d616-111">Attributes</span></span>  
  
|<span data-ttu-id="4d616-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="4d616-112">**Attribute**</span></span>|<span data-ttu-id="4d616-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="4d616-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="4d616-114">指定是否屬於<xref:System.Net.Dns>類別傳回 Internet Protocol version 6 (IPv6) 位址。</span><span class="sxs-lookup"><span data-stu-id="4d616-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="4d616-115">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="4d616-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d616-116">子項目</span><span class="sxs-lookup"><span data-stu-id="4d616-116">Child Elements</span></span>  
 <span data-ttu-id="4d616-117">無。</span><span class="sxs-lookup"><span data-stu-id="4d616-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d616-118">父項目</span><span class="sxs-lookup"><span data-stu-id="4d616-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4d616-119">**目**</span><span class="sxs-lookup"><span data-stu-id="4d616-119">**Element**</span></span>|<span data-ttu-id="4d616-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="4d616-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4d616-121">設定</span><span class="sxs-lookup"><span data-stu-id="4d616-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="4d616-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="4d616-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d616-123">備註</span><span class="sxs-lookup"><span data-stu-id="4d616-123">Remarks</span></span>  
 <span data-ttu-id="4d616-124">此設定會啟用 IPv6 支援過時成員<xref:System.Net.Dns>類別： <xref:System.Net.Dns.BeginGetHostByName%2A>， <xref:System.Net.Dns.BeginResolve%2A>， <xref:System.Net.Dns.EndGetHostByName%2A>， <xref:System.Net.Dns.EndResolve%2A>， <xref:System.Net.Dns.GetHostByAddress%2A>， <xref:System.Net.Dns.GetHostByName%2A>，和<xref:System.Net.Dns.Resolve%2A>。</span><span class="sxs-lookup"><span data-stu-id="4d616-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="4d616-125">其他成員的<xref:System.Net?displayProperty=nameWithType>命名空間，IPv6 位址可能會傳回如果 IPv6 已啟用作業系統中。</span><span class="sxs-lookup"><span data-stu-id="4d616-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4d616-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="4d616-126">Configuration Files</span></span>  
 <span data-ttu-id="4d616-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="4d616-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d616-128">範例</span><span class="sxs-lookup"><span data-stu-id="4d616-128">Example</span></span>  
 <span data-ttu-id="4d616-129">下列範例示範如何啟用 IPv6 的支援<xref:System.Net.Dns>類別。</span><span class="sxs-lookup"><span data-stu-id="4d616-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d616-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d616-130">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Dns?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="4d616-131">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="4d616-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
