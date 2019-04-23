---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 5c68fe618f965f364a3716c3bc65de5e165b12ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207795"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="9cdae-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="9cdae-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="9cdae-102">註冊工作階段權杖快取服務或安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="9cdae-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="9cdae-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9cdae-103">\<system.identityModel></span></span>  
<span data-ttu-id="9cdae-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9cdae-104">\<identityConfiguration></span></span>  
<span data-ttu-id="9cdae-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="9cdae-105">\<caches></span></span>  
<span data-ttu-id="9cdae-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="9cdae-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cdae-107">語法</span><span class="sxs-lookup"><span data-stu-id="9cdae-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cdae-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9cdae-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9cdae-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9cdae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cdae-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9cdae-110">Attributes</span></span>  
  
|<span data-ttu-id="9cdae-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9cdae-111">Attribute</span></span>|<span data-ttu-id="9cdae-112">描述</span><span class="sxs-lookup"><span data-stu-id="9cdae-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9cdae-113">類型</span><span class="sxs-lookup"><span data-stu-id="9cdae-113">type</span></span>|<span data-ttu-id="9cdae-114">衍生自類型<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別。</span><span class="sxs-lookup"><span data-stu-id="9cdae-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cdae-115">子元素</span><span class="sxs-lookup"><span data-stu-id="9cdae-115">Child Elements</span></span>  
 <span data-ttu-id="9cdae-116">None</span><span class="sxs-lookup"><span data-stu-id="9cdae-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cdae-117">父項目</span><span class="sxs-lookup"><span data-stu-id="9cdae-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9cdae-118">項目</span><span class="sxs-lookup"><span data-stu-id="9cdae-118">Element</span></span>|<span data-ttu-id="9cdae-119">描述</span><span class="sxs-lookup"><span data-stu-id="9cdae-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cdae-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="9cdae-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="9cdae-121">註冊服務或安全性權杖處理常式集合所使用的快取。</span><span class="sxs-lookup"><span data-stu-id="9cdae-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9cdae-122">範例</span><span class="sxs-lookup"><span data-stu-id="9cdae-122">Example</span></span>  
 <span data-ttu-id="9cdae-123">下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。</span><span class="sxs-lookup"><span data-stu-id="9cdae-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="9cdae-124">組態取自`ClaimsAwareWebFarm`範例。</span><span class="sxs-lookup"><span data-stu-id="9cdae-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="9cdae-125">如需有關此範例的詳細資訊，請參閱 < [WIF 程式碼範例索引](../../../../../docs/framework/security/wif-code-sample-index.md)。</span><span class="sxs-lookup"><span data-stu-id="9cdae-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cdae-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cdae-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
