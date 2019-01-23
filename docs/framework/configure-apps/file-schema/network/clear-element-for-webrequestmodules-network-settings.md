---
title: '&lt;清除&gt;webRequestModules （網路設定） 的項目'
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
ms.openlocfilehash: ccb9a19d4e6d79a84123014746b659a7168b2158
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607000"
---
# <a name="ltcleargt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="03b9a-102">&lt;清除&gt;webRequestModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="03b9a-102">&lt;clear&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="03b9a-103">移除應用程式中的所有已註冊的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="03b9a-103">Removes all registered Web request modules from the application.</span></span>  
  
 <span data-ttu-id="03b9a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="03b9a-104">\<configuration></span></span>  
<span data-ttu-id="03b9a-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="03b9a-105">\<system.net></span></span>  
<span data-ttu-id="03b9a-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="03b9a-106">\<webRequestModules></span></span>  
<span data-ttu-id="03b9a-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="03b9a-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03b9a-108">語法</span><span class="sxs-lookup"><span data-stu-id="03b9a-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03b9a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="03b9a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="03b9a-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="03b9a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03b9a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="03b9a-111">Attributes</span></span>  
 <span data-ttu-id="03b9a-112">無。</span><span class="sxs-lookup"><span data-stu-id="03b9a-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03b9a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="03b9a-113">Child Elements</span></span>  
 <span data-ttu-id="03b9a-114">無。</span><span class="sxs-lookup"><span data-stu-id="03b9a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03b9a-115">父項目</span><span class="sxs-lookup"><span data-stu-id="03b9a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="03b9a-116">**目**</span><span class="sxs-lookup"><span data-stu-id="03b9a-116">**Element**</span></span>|<span data-ttu-id="03b9a-117">**描述**</span><span class="sxs-lookup"><span data-stu-id="03b9a-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="03b9a-118">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="03b9a-118">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="03b9a-119">指定要求資訊從網路主機使用的模組。</span><span class="sxs-lookup"><span data-stu-id="03b9a-119">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03b9a-120">備註</span><span class="sxs-lookup"><span data-stu-id="03b9a-120">Remarks</span></span>  
 <span data-ttu-id="03b9a-121">`clear`項目會移除所有已註冊的 Web 要求模組組態檔中或在組態階層架構中較高層級稍早定義。</span><span class="sxs-lookup"><span data-stu-id="03b9a-121">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="03b9a-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="03b9a-122">Configuration Files</span></span>  
 <span data-ttu-id="03b9a-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="03b9a-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03b9a-124">範例</span><span class="sxs-lookup"><span data-stu-id="03b9a-124">Example</span></span>  
 <span data-ttu-id="03b9a-125">下列範例會清除所有的 Web 要求模組，並再註冊 HTTP Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="03b9a-125">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="03b9a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03b9a-126">See also</span></span>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="03b9a-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="03b9a-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
