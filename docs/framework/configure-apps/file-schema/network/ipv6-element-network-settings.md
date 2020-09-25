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
ms.openlocfilehash: 44ef0b8e1b6dc6ad0efde6b26ad7d4700e06f2c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178329"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="87cdb-102">\<ipv6> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="87cdb-102">\<ipv6> Element (Network Settings)</span></span>

<span data-ttu-id="87cdb-103">從類別的過時成員啟用網際網路通訊協定第6版 (IPv6) 回應 <xref:System.Net.Dns> 。</span><span class="sxs-lookup"><span data-stu-id="87cdb-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="87cdb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="87cdb-104">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87cdb-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87cdb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="87cdb-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="87cdb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87cdb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="87cdb-107">Attributes</span></span>  
  
|<span data-ttu-id="87cdb-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="87cdb-108">**Attribute**</span></span>|<span data-ttu-id="87cdb-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="87cdb-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="87cdb-110">指定類別的成員是否會將 <xref:System.Net.Dns> 網際網路通訊協定第6版 (IPv6) 位址。</span><span class="sxs-lookup"><span data-stu-id="87cdb-110">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="87cdb-111">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="87cdb-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87cdb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="87cdb-112">Child Elements</span></span>  

 <span data-ttu-id="87cdb-113">無。</span><span class="sxs-lookup"><span data-stu-id="87cdb-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87cdb-114">父項目</span><span class="sxs-lookup"><span data-stu-id="87cdb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="87cdb-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="87cdb-115">**Element**</span></span>|<span data-ttu-id="87cdb-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="87cdb-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="87cdb-117">設定</span><span class="sxs-lookup"><span data-stu-id="87cdb-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="87cdb-118">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="87cdb-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87cdb-119">備註</span><span class="sxs-lookup"><span data-stu-id="87cdb-119">Remarks</span></span>  

 <span data-ttu-id="87cdb-120">這項設定會針對類別的過時成員啟用 IPv6 支援 <xref:System.Net.Dns> ： <xref:System.Net.Dns.BeginGetHostByName%2A> 、 <xref:System.Net.Dns.BeginResolve%2A> 、 <xref:System.Net.Dns.EndGetHostByName%2A> 、 <xref:System.Net.Dns.EndResolve%2A> 、 <xref:System.Net.Dns.GetHostByAddress%2A> 、 <xref:System.Net.Dns.GetHostByName%2A> 和 <xref:System.Net.Dns.Resolve%2A> 。</span><span class="sxs-lookup"><span data-stu-id="87cdb-120">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="87cdb-121">對於命名空間的其他成員 <xref:System.Net?displayProperty=nameWithType> ，如果在作業系統中啟用 ipv6，可能會傳回 ipv6 位址。</span><span class="sxs-lookup"><span data-stu-id="87cdb-121">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="87cdb-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="87cdb-122">Configuration Files</span></span>  

 <span data-ttu-id="87cdb-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="87cdb-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87cdb-124">範例</span><span class="sxs-lookup"><span data-stu-id="87cdb-124">Example</span></span>  

 <span data-ttu-id="87cdb-125">下列範例顯示如何啟用類別的 IPv6 支援 <xref:System.Net.Dns> 。</span><span class="sxs-lookup"><span data-stu-id="87cdb-125">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87cdb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87cdb-126">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="87cdb-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="87cdb-127">Network Settings Schema</span></span>](index.md)
