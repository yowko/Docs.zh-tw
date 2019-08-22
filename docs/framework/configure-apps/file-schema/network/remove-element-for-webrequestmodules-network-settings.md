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
ms.openlocfilehash: 20a586e945a889d1fd8a8d4c5c09c8b790c56fc3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664022"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="ccd61-102">\<移除 Webrequestmodules 專案的 > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="ccd61-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="ccd61-103">從應用程式中移除自訂 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="ccd61-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="ccd61-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ccd61-104">\<configuration></span></span>  
<span data-ttu-id="ccd61-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ccd61-105">\<system.net></span></span>  
<span data-ttu-id="ccd61-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="ccd61-106">\<webRequestModules></span></span>  
<span data-ttu-id="ccd61-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="ccd61-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd61-108">語法</span><span class="sxs-lookup"><span data-stu-id="ccd61-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccd61-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ccd61-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ccd61-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ccd61-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccd61-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ccd61-111">Attributes</span></span>  
  
|<span data-ttu-id="ccd61-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="ccd61-112">**Attribute**</span></span>|<span data-ttu-id="ccd61-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="ccd61-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="ccd61-114">此 Web 要求模組所處理之要求的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="ccd61-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccd61-115">子元素</span><span class="sxs-lookup"><span data-stu-id="ccd61-115">Child Elements</span></span>  
 <span data-ttu-id="ccd61-116">無。</span><span class="sxs-lookup"><span data-stu-id="ccd61-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccd61-117">父項目</span><span class="sxs-lookup"><span data-stu-id="ccd61-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ccd61-118">**目**</span><span class="sxs-lookup"><span data-stu-id="ccd61-118">**Element**</span></span>|<span data-ttu-id="ccd61-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="ccd61-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ccd61-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="ccd61-120">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="ccd61-121">指定要用來要求網路主機資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="ccd61-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccd61-122">備註</span><span class="sxs-lookup"><span data-stu-id="ccd61-122">Remarks</span></span>  
 <span data-ttu-id="ccd61-123">`remove`元素會移除所指定 URI 前置詞的已註冊 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="ccd61-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="ccd61-124">`prefix`屬性的值應該是有效 URI 的前置字元, 例如 "`http`" 或 "`http://www.contoso.com`"。</span><span class="sxs-lookup"><span data-stu-id="ccd61-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ccd61-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="ccd61-125">Configuration Files</span></span>  
 <span data-ttu-id="ccd61-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="ccd61-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccd61-127">範例</span><span class="sxs-lookup"><span data-stu-id="ccd61-127">Example</span></span>  

<span data-ttu-id="ccd61-128">下列範例會移除 HTTP 的現有 Web 要求模組, 然後針對 HTTP 要求`www.contoso.com`註冊新的自訂 web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="ccd61-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="ccd61-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccd61-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="ccd61-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ccd61-130">Network Settings Schema</span></span>](index.md)
