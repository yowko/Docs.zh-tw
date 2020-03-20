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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154929"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="a3fc3-102">\<清除>元素以進行繞過清單（網路設置）</span><span class="sxs-lookup"><span data-stu-id="a3fc3-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="a3fc3-103">清除代理繞過清單。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-103">Clears the proxy bypass list.</span></span>  
  
<span data-ttu-id="a3fc3-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3fc3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a3fc3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a3fc3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="a3fc3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<預設代理>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a3fc3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="a3fc3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<繞過清單>**](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a3fc3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>\
<span data-ttu-id="a3fc3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<明確>**</span><span class="sxs-lookup"><span data-stu-id="a3fc3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a3fc3-109">語法</span><span class="sxs-lookup"><span data-stu-id="a3fc3-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3fc3-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a3fc3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a3fc3-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3fc3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a3fc3-112">Attributes</span></span>  
 <span data-ttu-id="a3fc3-113">無。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3fc3-114">子元素</span><span class="sxs-lookup"><span data-stu-id="a3fc3-114">Child Elements</span></span>  
 <span data-ttu-id="a3fc3-115">無。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3fc3-116">父項目</span><span class="sxs-lookup"><span data-stu-id="a3fc3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a3fc3-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="a3fc3-117">**Element**</span></span>|<span data-ttu-id="a3fc3-118">**描述**</span><span class="sxs-lookup"><span data-stu-id="a3fc3-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a3fc3-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="a3fc3-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="a3fc3-120">提供一組常規運算式，用於描述不使用代理的位址。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3fc3-121">備註</span><span class="sxs-lookup"><span data-stu-id="a3fc3-121">Remarks</span></span>  
 <span data-ttu-id="a3fc3-122">該`clear`元素清除旁路清單中的所有條目。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a3fc3-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="a3fc3-123">Configuration Files</span></span>  
 <span data-ttu-id="a3fc3-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3fc3-125">範例</span><span class="sxs-lookup"><span data-stu-id="a3fc3-125">Example</span></span>  
 <span data-ttu-id="a3fc3-126">下面的示例清除旁路清單，然後將兩個位址添加到旁路清單中。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="a3fc3-127">第一個繞過contoso.com域中所有伺服器的代理;第二個伺服器繞過其 IP 位址以 192.168 開頭的所有伺服器的代理。</span><span class="sxs-lookup"><span data-stu-id="a3fc3-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a3fc3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3fc3-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a3fc3-129">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="a3fc3-129">Network Settings Schema</span></span>](index.md)
