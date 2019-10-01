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
ms.openlocfilehash: f8209ea89ac8cd214389feddee8c475e10bc939a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697810"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="625d0-102">適用于 Webrequestmodules 專案的 @no__t 0remove > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="625d0-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="625d0-103">從應用程式中移除自訂 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="625d0-103">Removes a custom Web request module from the application.</span></span>  
  
[<span data-ttu-id="625d0-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="625d0-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="625d0-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="625d0-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="625d0-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="625d0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="625d0-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="625d0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="625d0-108">語法</span><span class="sxs-lookup"><span data-stu-id="625d0-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="625d0-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="625d0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="625d0-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="625d0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="625d0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="625d0-111">Attributes</span></span>  
  
|<span data-ttu-id="625d0-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="625d0-112">**Attribute**</span></span>|<span data-ttu-id="625d0-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="625d0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="625d0-114">此 Web 要求模組所處理之要求的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="625d0-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="625d0-115">子元素</span><span class="sxs-lookup"><span data-stu-id="625d0-115">Child Elements</span></span>  
 <span data-ttu-id="625d0-116">無。</span><span class="sxs-lookup"><span data-stu-id="625d0-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="625d0-117">父項目</span><span class="sxs-lookup"><span data-stu-id="625d0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="625d0-118">**目**</span><span class="sxs-lookup"><span data-stu-id="625d0-118">**Element**</span></span>|<span data-ttu-id="625d0-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="625d0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="625d0-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="625d0-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="625d0-121">指定要用來要求網路主機資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="625d0-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="625d0-122">備註</span><span class="sxs-lookup"><span data-stu-id="625d0-122">Remarks</span></span>  
 <span data-ttu-id="625d0-123">@No__t-0 元素會移除所指定 URI 前置詞的已註冊 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="625d0-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="625d0-124">@No__t-0 屬性的值應該是有效 URI 的前置字元，例如 "`http`" 或 "`http://www.contoso.com`"。</span><span class="sxs-lookup"><span data-stu-id="625d0-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="625d0-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="625d0-125">Configuration Files</span></span>  
 <span data-ttu-id="625d0-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="625d0-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="625d0-127">範例</span><span class="sxs-lookup"><span data-stu-id="625d0-127">Example</span></span>  

<span data-ttu-id="625d0-128">下列範例會移除 HTTP 的現有 Web 要求模組，然後為 HTTP 要求註冊新的自訂 Web 要求模組，以 `www.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="625d0-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="625d0-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="625d0-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="625d0-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="625d0-130">Network Settings Schema</span></span>](index.md)
