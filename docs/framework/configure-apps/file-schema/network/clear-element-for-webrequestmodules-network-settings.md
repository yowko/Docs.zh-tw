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
ms.openlocfilehash: 95a190dac3a9512b404a054c60c48de9c4574790
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698333"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="67130-102">適用于 Webrequestmodules 專案的 @no__t 0clear > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="67130-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="67130-103">從應用程式中移除所有已註冊的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="67130-103">Removes all registered Web request modules from the application.</span></span>  
  
[<span data-ttu-id="67130-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="67130-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="67130-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="67130-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="67130-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="67130-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="67130-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="67130-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67130-108">語法</span><span class="sxs-lookup"><span data-stu-id="67130-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67130-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="67130-109">Attributes and Elements</span></span>  
 <span data-ttu-id="67130-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="67130-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67130-111">屬性</span><span class="sxs-lookup"><span data-stu-id="67130-111">Attributes</span></span>  
 <span data-ttu-id="67130-112">無。</span><span class="sxs-lookup"><span data-stu-id="67130-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="67130-113">子元素</span><span class="sxs-lookup"><span data-stu-id="67130-113">Child Elements</span></span>  
 <span data-ttu-id="67130-114">無。</span><span class="sxs-lookup"><span data-stu-id="67130-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67130-115">父項目</span><span class="sxs-lookup"><span data-stu-id="67130-115">Parent Elements</span></span>  
  
|<span data-ttu-id="67130-116">**目**</span><span class="sxs-lookup"><span data-stu-id="67130-116">**Element**</span></span>|<span data-ttu-id="67130-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="67130-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="67130-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="67130-118">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="67130-119">指定要用來要求網路主機資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="67130-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67130-120">備註</span><span class="sxs-lookup"><span data-stu-id="67130-120">Remarks</span></span>  
 <span data-ttu-id="67130-121">@No__t-0 元素會移除先前在設定檔或設定階層中較高層級定義的所有已註冊 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="67130-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="67130-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="67130-122">Configuration Files</span></span>  
 <span data-ttu-id="67130-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="67130-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67130-124">範例</span><span class="sxs-lookup"><span data-stu-id="67130-124">Example</span></span>  
 <span data-ttu-id="67130-125">下列範例會清除所有的 Web 要求模組，然後註冊 HTTP 的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="67130-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67130-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67130-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="67130-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="67130-127">Network Settings Schema</span></span>](index.md)
