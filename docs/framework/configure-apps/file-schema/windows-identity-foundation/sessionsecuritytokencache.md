---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: e949b16f76f20191b84bbbbb6e8b019d913316f0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251836"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="c3fda-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="c3fda-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="c3fda-102">向服務或安全性權杖處理常式集合註冊會話權杖的快取。</span><span class="sxs-lookup"><span data-stu-id="c3fda-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="c3fda-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c3fda-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c3fda-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c3fda-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c3fda-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c3fda-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c3fda-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<快取 >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="c3fda-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="c3fda-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Sessionsecuritytokencache> >**</span><span class="sxs-lookup"><span data-stu-id="c3fda-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3fda-108">語法</span><span class="sxs-lookup"><span data-stu-id="c3fda-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3fda-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c3fda-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c3fda-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c3fda-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3fda-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c3fda-111">Attributes</span></span>  
  
|<span data-ttu-id="c3fda-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c3fda-112">Attribute</span></span>|<span data-ttu-id="c3fda-113">描述</span><span class="sxs-lookup"><span data-stu-id="c3fda-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3fda-114">型別</span><span class="sxs-lookup"><span data-stu-id="c3fda-114">type</span></span>|<span data-ttu-id="c3fda-115">衍生自<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別的類型。</span><span class="sxs-lookup"><span data-stu-id="c3fda-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3fda-116">子元素</span><span class="sxs-lookup"><span data-stu-id="c3fda-116">Child Elements</span></span>  
 <span data-ttu-id="c3fda-117">無</span><span class="sxs-lookup"><span data-stu-id="c3fda-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3fda-118">父項目</span><span class="sxs-lookup"><span data-stu-id="c3fda-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c3fda-119">項目</span><span class="sxs-lookup"><span data-stu-id="c3fda-119">Element</span></span>|<span data-ttu-id="c3fda-120">描述</span><span class="sxs-lookup"><span data-stu-id="c3fda-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3fda-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="c3fda-121">\<caches></span></span>](caches.md)|<span data-ttu-id="c3fda-122">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="c3fda-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c3fda-123">範例</span><span class="sxs-lookup"><span data-stu-id="c3fda-123">Example</span></span>  
 <span data-ttu-id="c3fda-124">下列 XML 顯示用來保存會話安全性權杖（<xref:System.IdentityModel.Tokens.SessionSecurityToken>）的自訂快取設定。</span><span class="sxs-lookup"><span data-stu-id="c3fda-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="c3fda-125">此設定取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="c3fda-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="c3fda-126">如需此範例的詳細資訊，請參閱[WIF 程式碼範例索引](../../../security/wif-code-sample-index.md)。</span><span class="sxs-lookup"><span data-stu-id="c3fda-126">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3fda-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3fda-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
