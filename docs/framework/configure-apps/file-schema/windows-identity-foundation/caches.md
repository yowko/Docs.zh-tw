---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252153"
---
# \<caches>
<span data-ttu-id="917dd-101">註冊用於會話權杖和權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="917dd-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="917dd-102">語法</span><span class="sxs-lookup"><span data-stu-id="917dd-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="917dd-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="917dd-103">Attributes and Elements</span></span>  
 <span data-ttu-id="917dd-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="917dd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="917dd-105">屬性</span><span class="sxs-lookup"><span data-stu-id="917dd-105">Attributes</span></span>  
 <span data-ttu-id="917dd-106">無</span><span class="sxs-lookup"><span data-stu-id="917dd-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="917dd-107">子元素</span><span class="sxs-lookup"><span data-stu-id="917dd-107">Child Elements</span></span>  
  
|<span data-ttu-id="917dd-108">元素</span><span class="sxs-lookup"><span data-stu-id="917dd-108">Element</span></span>|<span data-ttu-id="917dd-109">描述</span><span class="sxs-lookup"><span data-stu-id="917dd-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="917dd-110">向服務或安全性權杖處理常式集合註冊會話權杖的快取。</span><span class="sxs-lookup"><span data-stu-id="917dd-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="917dd-111">向服務或安全性權杖處理常式集合註冊權杖重新執行快取。</span><span class="sxs-lookup"><span data-stu-id="917dd-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="917dd-112">父項目</span><span class="sxs-lookup"><span data-stu-id="917dd-112">Parent Elements</span></span>  
  
|<span data-ttu-id="917dd-113">元素</span><span class="sxs-lookup"><span data-stu-id="917dd-113">Element</span></span>|<span data-ttu-id="917dd-114">描述</span><span class="sxs-lookup"><span data-stu-id="917dd-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="917dd-115">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="917dd-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="917dd-116">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="917dd-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="917dd-117">備註</span><span class="sxs-lookup"><span data-stu-id="917dd-117">Remarks</span></span>  
 <span data-ttu-id="917dd-118">`<caches>`元素可以在專案下的服務層級或專案底下 `<identityConfiguration>` 的安全性權杖處理常式集合層級指定 `<securityTokenHandlerConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="917dd-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="917dd-119">權杖處理常式集合上的設定會覆寫在服務上指定的值。</span><span class="sxs-lookup"><span data-stu-id="917dd-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="917dd-120">`<caches>`元素是由 <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="917dd-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="917dd-121">設定的快取是由 <xref:System.IdentityModel.Configuration.IdentityModelCaches> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="917dd-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="917dd-122">範例</span><span class="sxs-lookup"><span data-stu-id="917dd-122">Example</span></span>  
 <span data-ttu-id="917dd-123">下列 XML 顯示用來保存會話安全性權杖（）的自訂快取設定 <xref:System.IdentityModel.Tokens.SessionSecurityToken> 。</span><span class="sxs-lookup"><span data-stu-id="917dd-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="917dd-124">此設定取自 `ClaimsAwareWebFarm` 範例。</span><span class="sxs-lookup"><span data-stu-id="917dd-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
