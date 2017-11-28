---
title: '&lt;tokenReplayDetection&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f95d200f74621a40d2987acf68bc554df8d17ab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="eaf61-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="eaf61-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="eaf61-103">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="eaf61-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="eaf61-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="eaf61-104">\<system.identityModel></span></span>  
<span data-ttu-id="eaf61-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="eaf61-105">\<identityConfiguration></span></span>  
<span data-ttu-id="eaf61-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="eaf61-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf61-107">語法</span><span class="sxs-lookup"><span data-stu-id="eaf61-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="eaf61-108">類型</span><span class="sxs-lookup"><span data-stu-id="eaf61-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eaf61-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eaf61-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eaf61-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="eaf61-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eaf61-111">屬性</span><span class="sxs-lookup"><span data-stu-id="eaf61-111">Attributes</span></span>  
  
|<span data-ttu-id="eaf61-112">屬性</span><span class="sxs-lookup"><span data-stu-id="eaf61-112">Attribute</span></span>|<span data-ttu-id="eaf61-113">描述</span><span class="sxs-lookup"><span data-stu-id="eaf61-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eaf61-114">enabled</span><span class="sxs-lookup"><span data-stu-id="eaf61-114">enabled</span></span>|<span data-ttu-id="eaf61-115">值，指定是否啟用權杖重新執行偵測。"true"以啟用權杖重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="eaf61-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="eaf61-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="eaf61-116">expirationPeriod</span></span>|<span data-ttu-id="eaf61-117">A<xref:System.TimeSpan>指定的最大項目會被視為已過期，且從快取中移除之前的時間量。</span><span class="sxs-lookup"><span data-stu-id="eaf61-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="eaf61-118">如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="eaf61-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eaf61-119">子元素</span><span class="sxs-lookup"><span data-stu-id="eaf61-119">Child Elements</span></span>  
 <span data-ttu-id="eaf61-120">無</span><span class="sxs-lookup"><span data-stu-id="eaf61-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eaf61-121">父項目</span><span class="sxs-lookup"><span data-stu-id="eaf61-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eaf61-122">項目</span><span class="sxs-lookup"><span data-stu-id="eaf61-122">Element</span></span>|<span data-ttu-id="eaf61-123">說明</span><span class="sxs-lookup"><span data-stu-id="eaf61-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eaf61-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="eaf61-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="eaf61-125">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="eaf61-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="eaf61-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="eaf61-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="eaf61-127">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="eaf61-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaf61-128">備註</span><span class="sxs-lookup"><span data-stu-id="eaf61-128">Remarks</span></span>  
 <span data-ttu-id="eaf61-129">A`<tokenReplayDetection>`元素可以指定在服務層級下`<identityConfiguration>`項目或安全性權杖處理常式集合層級下`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="eaf61-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="eaf61-130">權杖處理常式集合上的設定會覆寫在服務上指定。</span><span class="sxs-lookup"><span data-stu-id="eaf61-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="eaf61-131">權杖重新執行快取的類型，由指定[ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)項目。</span><span class="sxs-lookup"><span data-stu-id="eaf61-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
