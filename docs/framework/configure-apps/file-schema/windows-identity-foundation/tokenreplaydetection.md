---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 4deeb1d84f2621adb7ff1b649a505138b6856ec1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283071"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="a9e61-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="a9e61-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="a9e61-102">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="a9e61-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="a9e61-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a9e61-103">\<system.identityModel></span></span>  
<span data-ttu-id="a9e61-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a9e61-104">\<identityConfiguration></span></span>  
<span data-ttu-id="a9e61-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="a9e61-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9e61-106">語法</span><span class="sxs-lookup"><span data-stu-id="a9e61-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="a9e61-107">類型</span><span class="sxs-lookup"><span data-stu-id="a9e61-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9e61-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a9e61-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a9e61-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a9e61-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9e61-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a9e61-110">Attributes</span></span>  
  
|<span data-ttu-id="a9e61-111">屬性</span><span class="sxs-lookup"><span data-stu-id="a9e61-111">Attribute</span></span>|<span data-ttu-id="a9e61-112">描述</span><span class="sxs-lookup"><span data-stu-id="a9e61-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9e61-113">enabled</span><span class="sxs-lookup"><span data-stu-id="a9e61-113">enabled</span></span>|<span data-ttu-id="a9e61-114">值，指定是否啟用權杖重新執行偵測。"true"來啟用權杖重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="a9e61-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="a9e61-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="a9e61-115">expirationPeriod</span></span>|<span data-ttu-id="a9e61-116">A <xref:System.TimeSpan> ，指定最大項目被視為過期並從快取移除之前的時間量。</span><span class="sxs-lookup"><span data-stu-id="a9e61-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="a9e61-117">如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a9e61-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9e61-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a9e61-118">Child Elements</span></span>  
 <span data-ttu-id="a9e61-119">無</span><span class="sxs-lookup"><span data-stu-id="a9e61-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9e61-120">父項目</span><span class="sxs-lookup"><span data-stu-id="a9e61-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a9e61-121">項目</span><span class="sxs-lookup"><span data-stu-id="a9e61-121">Element</span></span>|<span data-ttu-id="a9e61-122">描述</span><span class="sxs-lookup"><span data-stu-id="a9e61-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9e61-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a9e61-123">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="a9e61-124">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="a9e61-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="a9e61-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="a9e61-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="a9e61-126">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="a9e61-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9e61-127">備註</span><span class="sxs-lookup"><span data-stu-id="a9e61-127">Remarks</span></span>  
 <span data-ttu-id="a9e61-128">A`<tokenReplayDetection>`項目可以指定服務層級底下`<identityConfiguration>`項目或之下的安全性權杖處理常式集合層級`<securityTokenHandlerConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="a9e61-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="a9e61-129">權杖處理常式集合上的設定會覆寫所指定的服務。</span><span class="sxs-lookup"><span data-stu-id="a9e61-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="a9e61-130">權杖重新執行快取的類型由[ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)項目。</span><span class="sxs-lookup"><span data-stu-id="a9e61-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
