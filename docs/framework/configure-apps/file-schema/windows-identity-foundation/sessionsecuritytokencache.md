---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646072"
---
# \<sessionSecurityTokenCache>
<span data-ttu-id="01c9f-101">向服務或安全性權杖處理常式集合註冊會話權杖的快取。</span><span class="sxs-lookup"><span data-stu-id="01c9f-101">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="01c9f-102">語法</span><span class="sxs-lookup"><span data-stu-id="01c9f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01c9f-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="01c9f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="01c9f-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="01c9f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01c9f-105">屬性</span><span class="sxs-lookup"><span data-stu-id="01c9f-105">Attributes</span></span>  
  
|<span data-ttu-id="01c9f-106">屬性</span><span class="sxs-lookup"><span data-stu-id="01c9f-106">Attribute</span></span>|<span data-ttu-id="01c9f-107">描述</span><span class="sxs-lookup"><span data-stu-id="01c9f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01c9f-108">type</span><span class="sxs-lookup"><span data-stu-id="01c9f-108">type</span></span>|<span data-ttu-id="01c9f-109">衍生自類別的類型 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> 。</span><span class="sxs-lookup"><span data-stu-id="01c9f-109">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01c9f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="01c9f-110">Child Elements</span></span>  
 <span data-ttu-id="01c9f-111">無</span><span class="sxs-lookup"><span data-stu-id="01c9f-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01c9f-112">父項目</span><span class="sxs-lookup"><span data-stu-id="01c9f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="01c9f-113">元素</span><span class="sxs-lookup"><span data-stu-id="01c9f-113">Element</span></span>|<span data-ttu-id="01c9f-114">描述</span><span class="sxs-lookup"><span data-stu-id="01c9f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="01c9f-115">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="01c9f-115">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="01c9f-116">範例</span><span class="sxs-lookup"><span data-stu-id="01c9f-116">Example</span></span>  
 <span data-ttu-id="01c9f-117">下列 XML 顯示用來保存會話安全性權杖（）的自訂快取設定 <xref:System.IdentityModel.Tokens.SessionSecurityToken> 。</span><span class="sxs-lookup"><span data-stu-id="01c9f-117">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="01c9f-118">此設定取自 `ClaimsAwareWebFarm` 範例。</span><span class="sxs-lookup"><span data-stu-id="01c9f-118">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="01c9f-119">如需此範例的詳細資訊，請參閱[WIF 程式碼範例索引](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index)。</span><span class="sxs-lookup"><span data-stu-id="01c9f-119">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="01c9f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01c9f-120">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
