---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 2e2159a73ca79fc362a8138eea95dbd173dafb11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944289"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="75559-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="75559-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="75559-102">啟用權杖重新執行偵測, 並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="75559-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="75559-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="75559-103">\<system.identityModel></span></span>  
<span data-ttu-id="75559-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="75559-104">\<identityConfiguration></span></span>  
<span data-ttu-id="75559-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="75559-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75559-106">語法</span><span class="sxs-lookup"><span data-stu-id="75559-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="75559-107">類型</span><span class="sxs-lookup"><span data-stu-id="75559-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75559-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="75559-108">Attributes and Elements</span></span>  
 <span data-ttu-id="75559-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="75559-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75559-110">屬性</span><span class="sxs-lookup"><span data-stu-id="75559-110">Attributes</span></span>  
  
|<span data-ttu-id="75559-111">屬性</span><span class="sxs-lookup"><span data-stu-id="75559-111">Attribute</span></span>|<span data-ttu-id="75559-112">說明</span><span class="sxs-lookup"><span data-stu-id="75559-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75559-113">enabled</span><span class="sxs-lookup"><span data-stu-id="75559-113">enabled</span></span>|<span data-ttu-id="75559-114">值, 指定是否啟用權杖重新執行偵測;"true" 表示啟用權杖重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="75559-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="75559-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="75559-115">expirationPeriod</span></span>|<span data-ttu-id="75559-116"><xref:System.TimeSpan> , 指定將專案視為過期並從快取中移除之前的最大時間量。</span><span class="sxs-lookup"><span data-stu-id="75559-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="75559-117">如需如何指定<xref:System.TimeSpan>值的詳細資訊, 請參閱[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="75559-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75559-118">子元素</span><span class="sxs-lookup"><span data-stu-id="75559-118">Child Elements</span></span>  
 <span data-ttu-id="75559-119">None</span><span class="sxs-lookup"><span data-stu-id="75559-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75559-120">父項目</span><span class="sxs-lookup"><span data-stu-id="75559-120">Parent Elements</span></span>  
  
|<span data-ttu-id="75559-121">項目</span><span class="sxs-lookup"><span data-stu-id="75559-121">Element</span></span>|<span data-ttu-id="75559-122">說明</span><span class="sxs-lookup"><span data-stu-id="75559-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75559-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="75559-123">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="75559-124">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="75559-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="75559-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="75559-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="75559-126">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="75559-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75559-127">備註</span><span class="sxs-lookup"><span data-stu-id="75559-127">Remarks</span></span>  
 <span data-ttu-id="75559-128">元素可以在專案`<identityConfiguration>`下的服務層級或專案底下的安全性權杖`<securityTokenHandlerConfiguration>`處理常式集合層級指定。 `<tokenReplayDetection>`</span><span class="sxs-lookup"><span data-stu-id="75559-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="75559-129">權杖處理常式集合上的設定會覆寫在服務上指定的值。</span><span class="sxs-lookup"><span data-stu-id="75559-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="75559-130">權杖重新執行快取的類型是由[ \<tokenReplayCache >](tokenreplaycache.md)元素所指定。</span><span class="sxs-lookup"><span data-stu-id="75559-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
