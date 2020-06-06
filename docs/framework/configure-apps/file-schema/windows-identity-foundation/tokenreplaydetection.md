---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251763"
---
# \<tokenReplayDetection>
<span data-ttu-id="5be29-101">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="5be29-101">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="5be29-102">語法</span><span class="sxs-lookup"><span data-stu-id="5be29-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="5be29-103">類型</span><span class="sxs-lookup"><span data-stu-id="5be29-103">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5be29-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5be29-104">Attributes and Elements</span></span>  
 <span data-ttu-id="5be29-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5be29-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5be29-106">屬性</span><span class="sxs-lookup"><span data-stu-id="5be29-106">Attributes</span></span>  
  
|<span data-ttu-id="5be29-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5be29-107">Attribute</span></span>|<span data-ttu-id="5be29-108">描述</span><span class="sxs-lookup"><span data-stu-id="5be29-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5be29-109">已啟用</span><span class="sxs-lookup"><span data-stu-id="5be29-109">enabled</span></span>|<span data-ttu-id="5be29-110">值，指定是否啟用權杖重新執行偵測;"true" 表示啟用權杖重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="5be29-110">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="5be29-111">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="5be29-111">expirationPeriod</span></span>|<span data-ttu-id="5be29-112"><xref:System.TimeSpan>，指定將專案視為過期並從快取中移除之前的最大時間量。</span><span class="sxs-lookup"><span data-stu-id="5be29-112">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="5be29-113">如需如何指定值的詳細資訊 <xref:System.TimeSpan> ，請參閱[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5be29-113">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5be29-114">子元素</span><span class="sxs-lookup"><span data-stu-id="5be29-114">Child Elements</span></span>  
 <span data-ttu-id="5be29-115">無</span><span class="sxs-lookup"><span data-stu-id="5be29-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5be29-116">父項目</span><span class="sxs-lookup"><span data-stu-id="5be29-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5be29-117">元素</span><span class="sxs-lookup"><span data-stu-id="5be29-117">Element</span></span>|<span data-ttu-id="5be29-118">描述</span><span class="sxs-lookup"><span data-stu-id="5be29-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="5be29-119">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="5be29-119">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="5be29-120">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="5be29-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5be29-121">備註</span><span class="sxs-lookup"><span data-stu-id="5be29-121">Remarks</span></span>  
 <span data-ttu-id="5be29-122">`<tokenReplayDetection>`元素可以在專案下的服務層級或專案底下 `<identityConfiguration>` 的安全性權杖處理常式集合層級指定 `<securityTokenHandlerConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="5be29-122">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="5be29-123">權杖處理常式集合上的設定會覆寫在服務上指定的值。</span><span class="sxs-lookup"><span data-stu-id="5be29-123">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="5be29-124">權杖重新執行快取的類型是由元素所指定 [\<tokenReplayCache>](tokenreplaycache.md) 。</span><span class="sxs-lookup"><span data-stu-id="5be29-124">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
