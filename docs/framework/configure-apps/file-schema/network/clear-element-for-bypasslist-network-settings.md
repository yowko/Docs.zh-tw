---
title: bypasslist 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: c25477c2c99be66b34b07e1f7e50115bfa8d14e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154929"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="ffee4-102">bypasslist 的 \<clear> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="ffee4-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="ffee4-103">清除 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="ffee4-103">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="ffee4-104">語法</span><span class="sxs-lookup"><span data-stu-id="ffee4-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffee4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ffee4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ffee4-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ffee4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffee4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ffee4-107">Attributes</span></span>  
 <span data-ttu-id="ffee4-108">無。</span><span class="sxs-lookup"><span data-stu-id="ffee4-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ffee4-109">子元素</span><span class="sxs-lookup"><span data-stu-id="ffee4-109">Child Elements</span></span>  
 <span data-ttu-id="ffee4-110">無。</span><span class="sxs-lookup"><span data-stu-id="ffee4-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffee4-111">父項目</span><span class="sxs-lookup"><span data-stu-id="ffee4-111">Parent Elements</span></span>  
  
|<span data-ttu-id="ffee4-112">**元素**</span><span class="sxs-lookup"><span data-stu-id="ffee4-112">**Element**</span></span>|<span data-ttu-id="ffee4-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="ffee4-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ffee4-114">bypasslist</span><span class="sxs-lookup"><span data-stu-id="ffee4-114">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="ffee4-115">提供一組正則運算式，描述不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="ffee4-115">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffee4-116">備註</span><span class="sxs-lookup"><span data-stu-id="ffee4-116">Remarks</span></span>  
 <span data-ttu-id="ffee4-117">`clear`元素會清除略過清單中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="ffee4-117">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ffee4-118">組態檔</span><span class="sxs-lookup"><span data-stu-id="ffee4-118">Configuration Files</span></span>  
 <span data-ttu-id="ffee4-119">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="ffee4-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffee4-120">範例</span><span class="sxs-lookup"><span data-stu-id="ffee4-120">Example</span></span>  
 <span data-ttu-id="ffee4-121">下列範例會清除略過清單，然後將兩個位址新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="ffee4-121">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="ffee4-122">第一個會略過 contoso.com 網域中所有伺服器的 proxy;第二個會略過其 IP 位址開頭為192.168 的所有伺服器的 proxy。</span><span class="sxs-lookup"><span data-stu-id="ffee4-122">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="ffee4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffee4-123">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="ffee4-124">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ffee4-124">Network Settings Schema</span></span>](index.md)
