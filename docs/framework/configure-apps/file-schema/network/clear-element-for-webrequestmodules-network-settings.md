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
ms.openlocfilehash: 5dea238629b282776cb45f7b388e655fa557d084
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674593"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="36174-102">\<清除 > webRequestModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="36174-102">\<clear> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="36174-103">移除應用程式中的所有已註冊的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="36174-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="36174-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="36174-104">\<configuration></span></span>  
<span data-ttu-id="36174-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="36174-105">\<system.net></span></span>  
<span data-ttu-id="36174-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="36174-106">\<webRequestModules></span></span>  
<span data-ttu-id="36174-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="36174-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36174-108">語法</span><span class="sxs-lookup"><span data-stu-id="36174-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36174-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="36174-109">Attributes and Elements</span></span>  
 <span data-ttu-id="36174-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="36174-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36174-111">屬性</span><span class="sxs-lookup"><span data-stu-id="36174-111">Attributes</span></span>  
 <span data-ttu-id="36174-112">無。</span><span class="sxs-lookup"><span data-stu-id="36174-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="36174-113">子元素</span><span class="sxs-lookup"><span data-stu-id="36174-113">Child Elements</span></span>  
 <span data-ttu-id="36174-114">無。</span><span class="sxs-lookup"><span data-stu-id="36174-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36174-115">父項目</span><span class="sxs-lookup"><span data-stu-id="36174-115">Parent Elements</span></span>  
  
|<span data-ttu-id="36174-116">**目**</span><span class="sxs-lookup"><span data-stu-id="36174-116">**Element**</span></span>|<span data-ttu-id="36174-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="36174-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="36174-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="36174-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="36174-119">指定要求資訊從網路主機使用的模組。</span><span class="sxs-lookup"><span data-stu-id="36174-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36174-120">備註</span><span class="sxs-lookup"><span data-stu-id="36174-120">Remarks</span></span>  
 <span data-ttu-id="36174-121">`clear`項目會移除所有已註冊的 Web 要求模組組態檔中或在組態階層架構中較高層級稍早定義。</span><span class="sxs-lookup"><span data-stu-id="36174-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="36174-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="36174-122">Configuration Files</span></span>  
 <span data-ttu-id="36174-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="36174-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36174-124">範例</span><span class="sxs-lookup"><span data-stu-id="36174-124">Example</span></span>  
 <span data-ttu-id="36174-125">下列範例會清除所有的 Web 要求模組，並再註冊 HTTP Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="36174-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36174-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36174-126">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="36174-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="36174-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
