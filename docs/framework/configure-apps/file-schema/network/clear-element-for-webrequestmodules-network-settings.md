---
title: webRequestModules 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: 5832d120824df75d374fc94cb0aa4e08189cb965
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088492"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="86025-102">webRequestModules 的 \<clear> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="86025-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="86025-103">從應用程式中移除所有已註冊的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="86025-103">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="86025-104">語法</span><span class="sxs-lookup"><span data-stu-id="86025-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86025-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="86025-105">Attributes and Elements</span></span>  
 <span data-ttu-id="86025-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="86025-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86025-107">屬性</span><span class="sxs-lookup"><span data-stu-id="86025-107">Attributes</span></span>  
 <span data-ttu-id="86025-108">無。</span><span class="sxs-lookup"><span data-stu-id="86025-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="86025-109">子元素</span><span class="sxs-lookup"><span data-stu-id="86025-109">Child Elements</span></span>  
 <span data-ttu-id="86025-110">無。</span><span class="sxs-lookup"><span data-stu-id="86025-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86025-111">父項目</span><span class="sxs-lookup"><span data-stu-id="86025-111">Parent Elements</span></span>  
  
|<span data-ttu-id="86025-112">**元素**</span><span class="sxs-lookup"><span data-stu-id="86025-112">**Element**</span></span>|<span data-ttu-id="86025-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="86025-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="86025-114">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="86025-114">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="86025-115">指定要用來要求網路主機資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="86025-115">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86025-116">備註</span><span class="sxs-lookup"><span data-stu-id="86025-116">Remarks</span></span>  
 <span data-ttu-id="86025-117">`clear`元素會移除先前在設定檔或設定階層中較高層級定義的所有已註冊 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="86025-117">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="86025-118">組態檔</span><span class="sxs-lookup"><span data-stu-id="86025-118">Configuration Files</span></span>  
 <span data-ttu-id="86025-119">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="86025-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86025-120">範例</span><span class="sxs-lookup"><span data-stu-id="86025-120">Example</span></span>  
 <span data-ttu-id="86025-121">下列範例會清除所有的 Web 要求模組，然後註冊 HTTP 的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="86025-121">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86025-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86025-122">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="86025-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="86025-123">Network Settings Schema</span></span>](index.md)
