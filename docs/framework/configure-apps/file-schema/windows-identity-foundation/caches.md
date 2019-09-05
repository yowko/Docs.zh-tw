---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252153"
---
# <a name="caches"></a><span data-ttu-id="660d0-101">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="660d0-101">\<caches></span></span>
<span data-ttu-id="660d0-102">註冊用於會話權杖和權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="660d0-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
<span data-ttu-id="660d0-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="660d0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="660d0-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="660d0-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="660d0-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="660d0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="660d0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<快取 >**</span><span class="sxs-lookup"><span data-stu-id="660d0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="660d0-107">語法</span><span class="sxs-lookup"><span data-stu-id="660d0-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="660d0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="660d0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="660d0-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="660d0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="660d0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="660d0-110">Attributes</span></span>  
 <span data-ttu-id="660d0-111">None</span><span class="sxs-lookup"><span data-stu-id="660d0-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="660d0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="660d0-112">Child Elements</span></span>  
  
|<span data-ttu-id="660d0-113">項目</span><span class="sxs-lookup"><span data-stu-id="660d0-113">Element</span></span>|<span data-ttu-id="660d0-114">說明</span><span class="sxs-lookup"><span data-stu-id="660d0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="660d0-115">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="660d0-115">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="660d0-116">向服務或安全性權杖處理常式集合註冊會話權杖的快取。</span><span class="sxs-lookup"><span data-stu-id="660d0-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="660d0-117">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="660d0-117">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="660d0-118">向服務或安全性權杖處理常式集合註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="660d0-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="660d0-119">父項目</span><span class="sxs-lookup"><span data-stu-id="660d0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="660d0-120">項目</span><span class="sxs-lookup"><span data-stu-id="660d0-120">Element</span></span>|<span data-ttu-id="660d0-121">描述</span><span class="sxs-lookup"><span data-stu-id="660d0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="660d0-122">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="660d0-122">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="660d0-123">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="660d0-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="660d0-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="660d0-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="660d0-125">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="660d0-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="660d0-126">備註</span><span class="sxs-lookup"><span data-stu-id="660d0-126">Remarks</span></span>  
 <span data-ttu-id="660d0-127">元素可以在專案`<identityConfiguration>`下的服務層級或專案底下的安全性權杖`<securityTokenHandlerConfiguration>`處理常式集合層級指定。 `<caches>`</span><span class="sxs-lookup"><span data-stu-id="660d0-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="660d0-128">權杖處理常式集合上的設定會覆寫在服務上指定的值。</span><span class="sxs-lookup"><span data-stu-id="660d0-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="660d0-129">`<caches>`元素是<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="660d0-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="660d0-130">設定的快取是由<xref:System.IdentityModel.Configuration.IdentityModelCaches>類別表示。</span><span class="sxs-lookup"><span data-stu-id="660d0-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="660d0-131">範例</span><span class="sxs-lookup"><span data-stu-id="660d0-131">Example</span></span>  
 <span data-ttu-id="660d0-132">下列 XML 顯示用來保存會話安全性權杖 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>) 的自訂快取設定。</span><span class="sxs-lookup"><span data-stu-id="660d0-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="660d0-133">此設定取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="660d0-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
