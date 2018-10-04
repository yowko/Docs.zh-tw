---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: bd2272cb83dc0183d5008cfa178e11783f51ca2d
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261051"
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="97e69-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="97e69-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="97e69-103">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="97e69-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="97e69-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="97e69-104">\<system.identityModel></span></span>  
<span data-ttu-id="97e69-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="97e69-105">\<identityConfiguration></span></span>  
<span data-ttu-id="97e69-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="97e69-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e69-107">語法</span><span class="sxs-lookup"><span data-stu-id="97e69-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="97e69-108">類型</span><span class="sxs-lookup"><span data-stu-id="97e69-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97e69-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="97e69-109">Attributes and Elements</span></span>  
 <span data-ttu-id="97e69-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="97e69-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97e69-111">屬性</span><span class="sxs-lookup"><span data-stu-id="97e69-111">Attributes</span></span>  
  
|<span data-ttu-id="97e69-112">屬性</span><span class="sxs-lookup"><span data-stu-id="97e69-112">Attribute</span></span>|<span data-ttu-id="97e69-113">描述</span><span class="sxs-lookup"><span data-stu-id="97e69-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97e69-114">enabled</span><span class="sxs-lookup"><span data-stu-id="97e69-114">enabled</span></span>|<span data-ttu-id="97e69-115">值，指定是否啟用權杖重新執行偵測。"true"來啟用權杖重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="97e69-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="97e69-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="97e69-116">expirationPeriod</span></span>|<span data-ttu-id="97e69-117">A <xref:System.TimeSpan> ，指定最大項目被視為過期並從快取移除之前的時間量。</span><span class="sxs-lookup"><span data-stu-id="97e69-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="97e69-118">如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="97e69-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97e69-119">子元素</span><span class="sxs-lookup"><span data-stu-id="97e69-119">Child Elements</span></span>  
 <span data-ttu-id="97e69-120">無</span><span class="sxs-lookup"><span data-stu-id="97e69-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97e69-121">父項目</span><span class="sxs-lookup"><span data-stu-id="97e69-121">Parent Elements</span></span>  
  
|<span data-ttu-id="97e69-122">項目</span><span class="sxs-lookup"><span data-stu-id="97e69-122">Element</span></span>|<span data-ttu-id="97e69-123">描述</span><span class="sxs-lookup"><span data-stu-id="97e69-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97e69-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="97e69-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="97e69-125">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="97e69-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="97e69-126">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="97e69-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="97e69-127">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="97e69-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97e69-128">備註</span><span class="sxs-lookup"><span data-stu-id="97e69-128">Remarks</span></span>  
 <span data-ttu-id="97e69-129">A`<tokenReplayDetection>`項目可以指定服務層級底下`<identityConfiguration>`項目或之下的安全性權杖處理常式集合層級`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="97e69-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="97e69-130">權杖處理常式集合上的設定會覆寫所指定的服務。</span><span class="sxs-lookup"><span data-stu-id="97e69-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="97e69-131">權杖重新執行快取的類型由[ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)項目。</span><span class="sxs-lookup"><span data-stu-id="97e69-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
