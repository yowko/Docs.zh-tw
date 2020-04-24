---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646072"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="e5b50-101">\<工作階段安全權杖快取></span><span class="sxs-lookup"><span data-stu-id="e5b50-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="e5b50-102">使用服務或安全權杖處理程式集合註冊會話令牌的緩存。</span><span class="sxs-lookup"><span data-stu-id="e5b50-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="e5b50-103">[**\<設定>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5b50-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e5b50-104">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="e5b50-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="e5b50-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份設定>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e5b50-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="e5b50-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<快取>**](caches.md)</span><span class="sxs-lookup"><span data-stu-id="e5b50-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="e5b50-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<工作階段安全權杖快取>**</span><span class="sxs-lookup"><span data-stu-id="e5b50-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b50-108">語法</span><span class="sxs-lookup"><span data-stu-id="e5b50-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5b50-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5b50-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e5b50-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5b50-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5b50-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e5b50-111">Attributes</span></span>  
  
|<span data-ttu-id="e5b50-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e5b50-112">Attribute</span></span>|<span data-ttu-id="e5b50-113">描述</span><span class="sxs-lookup"><span data-stu-id="e5b50-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5b50-114">type</span><span class="sxs-lookup"><span data-stu-id="e5b50-114">type</span></span>|<span data-ttu-id="e5b50-115">派生自<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類的類型。</span><span class="sxs-lookup"><span data-stu-id="e5b50-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5b50-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e5b50-116">Child Elements</span></span>  
 <span data-ttu-id="e5b50-117">None</span><span class="sxs-lookup"><span data-stu-id="e5b50-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5b50-118">父項目</span><span class="sxs-lookup"><span data-stu-id="e5b50-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e5b50-119">元素</span><span class="sxs-lookup"><span data-stu-id="e5b50-119">Element</span></span>|<span data-ttu-id="e5b50-120">描述</span><span class="sxs-lookup"><span data-stu-id="e5b50-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5b50-121">\<快取></span><span class="sxs-lookup"><span data-stu-id="e5b50-121">\<caches></span></span>](caches.md)|<span data-ttu-id="e5b50-122">註冊服務或安全權杖處理程式集合使用的快取。</span><span class="sxs-lookup"><span data-stu-id="e5b50-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5b50-123">範例</span><span class="sxs-lookup"><span data-stu-id="e5b50-123">Example</span></span>  
 <span data-ttu-id="e5b50-124">以下 XML 顯示了用於儲存工作階段安全權杖的自訂快取的<xref:System.IdentityModel.Tokens.SessionSecurityToken>設定 。</span><span class="sxs-lookup"><span data-stu-id="e5b50-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="e5b50-125">配置取自`ClaimsAwareWebFarm`示例。</span><span class="sxs-lookup"><span data-stu-id="e5b50-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="e5b50-126">有關此範例的詳細資訊,請參閱[WIF 代碼範例索引](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index)。</span><span class="sxs-lookup"><span data-stu-id="e5b50-126">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5b50-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5b50-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
