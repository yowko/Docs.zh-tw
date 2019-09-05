---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251763"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="8bc97-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="8bc97-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="8bc97-102">啟用權杖重新執行偵測, 並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="8bc97-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
<span data-ttu-id="8bc97-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8bc97-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8bc97-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="8bc97-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="8bc97-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8bc97-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="8bc97-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayDetection >**</span><span class="sxs-lookup"><span data-stu-id="8bc97-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc97-107">語法</span><span class="sxs-lookup"><span data-stu-id="8bc97-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="8bc97-108">類型</span><span class="sxs-lookup"><span data-stu-id="8bc97-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bc97-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8bc97-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8bc97-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8bc97-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bc97-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8bc97-111">Attributes</span></span>  
  
|<span data-ttu-id="8bc97-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8bc97-112">Attribute</span></span>|<span data-ttu-id="8bc97-113">描述</span><span class="sxs-lookup"><span data-stu-id="8bc97-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8bc97-114">enabled</span><span class="sxs-lookup"><span data-stu-id="8bc97-114">enabled</span></span>|<span data-ttu-id="8bc97-115">值, 指定是否啟用權杖重新執行偵測;"true" 表示啟用權杖重新執行偵測。</span><span class="sxs-lookup"><span data-stu-id="8bc97-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="8bc97-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="8bc97-116">expirationPeriod</span></span>|<span data-ttu-id="8bc97-117"><xref:System.TimeSpan> , 指定將專案視為過期並從快取中移除之前的最大時間量。</span><span class="sxs-lookup"><span data-stu-id="8bc97-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="8bc97-118">如需如何指定<xref:System.TimeSpan>值的詳細資訊, 請參閱[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8bc97-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bc97-119">子元素</span><span class="sxs-lookup"><span data-stu-id="8bc97-119">Child Elements</span></span>  
 <span data-ttu-id="8bc97-120">無</span><span class="sxs-lookup"><span data-stu-id="8bc97-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8bc97-121">父項目</span><span class="sxs-lookup"><span data-stu-id="8bc97-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8bc97-122">項目</span><span class="sxs-lookup"><span data-stu-id="8bc97-122">Element</span></span>|<span data-ttu-id="8bc97-123">說明</span><span class="sxs-lookup"><span data-stu-id="8bc97-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bc97-124">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8bc97-124">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="8bc97-125">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="8bc97-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="8bc97-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8bc97-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="8bc97-127">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="8bc97-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bc97-128">備註</span><span class="sxs-lookup"><span data-stu-id="8bc97-128">Remarks</span></span>  
 <span data-ttu-id="8bc97-129">元素可以在專案`<identityConfiguration>`下的服務層級或專案底下的安全性權杖`<securityTokenHandlerConfiguration>`處理常式集合層級指定。 `<tokenReplayDetection>`</span><span class="sxs-lookup"><span data-stu-id="8bc97-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="8bc97-130">權杖處理常式集合上的設定會覆寫在服務上指定的值。</span><span class="sxs-lookup"><span data-stu-id="8bc97-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="8bc97-131">權杖重新執行快取的類型是由[ \<tokenReplayCache >](tokenreplaycache.md)元素所指定。</span><span class="sxs-lookup"><span data-stu-id="8bc97-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
