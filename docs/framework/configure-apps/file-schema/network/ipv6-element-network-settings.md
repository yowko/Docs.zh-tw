---
title: <ipv6> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: bf04b16682c2c1bc677fecbd6dc966090c77e1da
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698124"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="d1bd8-102">\<ipv6> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="d1bd8-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="d1bd8-103">從 <xref:System.Net.Dns> 類別的過時成員啟用網際網路通訊協定第6版（IPv6）回應。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
[<span data-ttu-id="d1bd8-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="d1bd8-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="d1bd8-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d1bd8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="d1bd8-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="d1bd8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="d1bd8-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<ipv6 >**</span><span class="sxs-lookup"><span data-stu-id="d1bd8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1bd8-108">語法</span><span class="sxs-lookup"><span data-stu-id="d1bd8-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1bd8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1bd8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d1bd8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1bd8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d1bd8-111">Attributes</span></span>  
  
|<span data-ttu-id="d1bd8-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d1bd8-112">**Attribute**</span></span>|<span data-ttu-id="d1bd8-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="d1bd8-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="d1bd8-114">指定 @no__t 0 類別的成員是否傳回網際網路通訊協定第6版（IPv6）位址。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="d1bd8-115">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1bd8-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d1bd8-116">Child Elements</span></span>  
 <span data-ttu-id="d1bd8-117">無。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1bd8-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d1bd8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d1bd8-119">**目**</span><span class="sxs-lookup"><span data-stu-id="d1bd8-119">**Element**</span></span>|<span data-ttu-id="d1bd8-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="d1bd8-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d1bd8-121">設置</span><span class="sxs-lookup"><span data-stu-id="d1bd8-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="d1bd8-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1bd8-123">備註</span><span class="sxs-lookup"><span data-stu-id="d1bd8-123">Remarks</span></span>  
 <span data-ttu-id="d1bd8-124">此設定可讓 <xref:System.Net.Dns> 類別的過時成員支援 IPv6： <xref:System.Net.Dns.BeginGetHostByName%2A>、<xref:System.Net.Dns.BeginResolve%2A>、<xref:System.Net.Dns.EndGetHostByName%2A>、<xref:System.Net.Dns.EndResolve%2A>、<xref:System.Net.Dns.GetHostByAddress%2A>、<xref:System.Net.Dns.GetHostByName%2A> 和 <xref:System.Net.Dns.Resolve%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="d1bd8-125">若為 <xref:System.Net?displayProperty=nameWithType> 命名空間的其他成員，則在作業系統中啟用 IPv6 時，可能會傳回 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d1bd8-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="d1bd8-126">Configuration Files</span></span>  
 <span data-ttu-id="d1bd8-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1bd8-128">範例</span><span class="sxs-lookup"><span data-stu-id="d1bd8-128">Example</span></span>  
 <span data-ttu-id="d1bd8-129">下列範例顯示如何啟用 <xref:System.Net.Dns> 類別的 IPv6 支援。</span><span class="sxs-lookup"><span data-stu-id="d1bd8-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1bd8-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1bd8-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d1bd8-131">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d1bd8-131">Network Settings Schema</span></span>](index.md)
