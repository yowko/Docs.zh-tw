---
title: <remove> WebRequestModules （網路設定） 的項目
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
ms.openlocfilehash: c57e2849d608b1706c41beca91ff8026ebd9ca45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085391"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="76c8d-102">\<移除 > webRequestModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="76c8d-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="76c8d-103">移除應用程式自訂的 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="76c8d-103">Removes a custom Web request module from the application.</span></span>  
  
 <span data-ttu-id="76c8d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="76c8d-104">\<configuration></span></span>  
<span data-ttu-id="76c8d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="76c8d-105">\<system.net></span></span>  
<span data-ttu-id="76c8d-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="76c8d-106">\<webRequestModules></span></span>  
<span data-ttu-id="76c8d-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="76c8d-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76c8d-108">語法</span><span class="sxs-lookup"><span data-stu-id="76c8d-108">Syntax</span></span>  
  
```xml  
<remove   
  prefix="URI prefix"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76c8d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="76c8d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="76c8d-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="76c8d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76c8d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="76c8d-111">Attributes</span></span>  
  
|**<span data-ttu-id="76c8d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="76c8d-112">Attribute</span></span>**|**<span data-ttu-id="76c8d-113">描述</span><span class="sxs-lookup"><span data-stu-id="76c8d-113">Description</span></span>**|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="76c8d-114">此 Web 要求模組所處理的要求 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="76c8d-114">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76c8d-115">子元素</span><span class="sxs-lookup"><span data-stu-id="76c8d-115">Child Elements</span></span>  
 <span data-ttu-id="76c8d-116">無。</span><span class="sxs-lookup"><span data-stu-id="76c8d-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76c8d-117">父項目</span><span class="sxs-lookup"><span data-stu-id="76c8d-117">Parent Elements</span></span>  
  
|**<span data-ttu-id="76c8d-118">項目</span><span class="sxs-lookup"><span data-stu-id="76c8d-118">Element</span></span>**|**<span data-ttu-id="76c8d-119">描述</span><span class="sxs-lookup"><span data-stu-id="76c8d-119">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="76c8d-120">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="76c8d-120">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="76c8d-121">指定要求資訊從網路主機使用的模組。</span><span class="sxs-lookup"><span data-stu-id="76c8d-121">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76c8d-122">備註</span><span class="sxs-lookup"><span data-stu-id="76c8d-122">Remarks</span></span>  
 <span data-ttu-id="76c8d-123">`remove`項目會移除已註冊的 Web 要求模組指定的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="76c8d-123">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="76c8d-124">值`prefix`屬性應為有效的 URI-前置字元，例如"`http`"，或 「`http://www.contoso.com`"。</span><span class="sxs-lookup"><span data-stu-id="76c8d-124">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="76c8d-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="76c8d-125">Configuration Files</span></span>  
 <span data-ttu-id="76c8d-126">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="76c8d-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76c8d-127">範例</span><span class="sxs-lookup"><span data-stu-id="76c8d-127">Example</span></span>  

<span data-ttu-id="76c8d-128">下列範例會移除現有的 Web 要求模組的 HTTP，然後註冊新的自訂 Web 要求模組的 HTTP 要求`www.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="76c8d-128">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="76c8d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76c8d-129">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="76c8d-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="76c8d-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
