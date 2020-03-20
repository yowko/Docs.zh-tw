---
title: webRequestModules 的 <remove> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154721"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="e8f73-102">\<刪除 web 請求模組>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="e8f73-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="e8f73-103">從應用程式中刪除自訂 Web 請求模組。</span><span class="sxs-lookup"><span data-stu-id="e8f73-103">Removes a custom Web request module from the application.</span></span>  
  
<span data-ttu-id="e8f73-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e8f73-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e8f73-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e8f73-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e8f73-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<web 請求模組>**](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e8f73-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="e8f73-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<刪除>**</span><span class="sxs-lookup"><span data-stu-id="e8f73-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e8f73-108">語法</span><span class="sxs-lookup"><span data-stu-id="e8f73-108">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8f73-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e8f73-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8f73-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e8f73-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8f73-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e8f73-111">Attributes</span></span>  
  
|<span data-ttu-id="e8f73-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e8f73-112">**Attribute**</span></span>|<span data-ttu-id="e8f73-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="e8f73-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="e8f73-114">此 Web 請求模組處理的請求的 URI 首碼。</span><span class="sxs-lookup"><span data-stu-id="e8f73-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8f73-115">子元素</span><span class="sxs-lookup"><span data-stu-id="e8f73-115">Child Elements</span></span>  
 <span data-ttu-id="e8f73-116">無。</span><span class="sxs-lookup"><span data-stu-id="e8f73-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8f73-117">父項目</span><span class="sxs-lookup"><span data-stu-id="e8f73-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e8f73-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="e8f73-118">**Element**</span></span>|<span data-ttu-id="e8f73-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="e8f73-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e8f73-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="e8f73-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="e8f73-121">指定用於從網路主機請求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="e8f73-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8f73-122">備註</span><span class="sxs-lookup"><span data-stu-id="e8f73-122">Remarks</span></span>  
 <span data-ttu-id="e8f73-123">該`remove`元素將刪除指定 URI 首碼的已註冊的 Web 請求模組。</span><span class="sxs-lookup"><span data-stu-id="e8f73-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="e8f73-124">`prefix`屬性的值應為有效 URI 的前導字元 ， 例如，"`http`或""。`http://www.contoso.com`</span><span class="sxs-lookup"><span data-stu-id="e8f73-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e8f73-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="e8f73-125">Configuration Files</span></span>  
 <span data-ttu-id="e8f73-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="e8f73-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f73-127">範例</span><span class="sxs-lookup"><span data-stu-id="e8f73-127">Example</span></span>  

<span data-ttu-id="e8f73-128">下面的示例刪除現有的 WEB 請求模組 HTTP，然後註冊新的自訂 Web 請求模組，用於 HTTP`www.contoso.com`請求。</span><span class="sxs-lookup"><span data-stu-id="e8f73-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8f73-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8f73-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="e8f73-130">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="e8f73-130">Network Settings Schema</span></span>](index.md)
