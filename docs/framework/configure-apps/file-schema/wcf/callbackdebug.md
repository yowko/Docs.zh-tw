---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 2103c32112b6c5554d7b510f486d4cbb1349f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747943"
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="be1d9-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="be1d9-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="be1d9-103">指定 Windows Communication Foundation (WCF) 回呼物件的服務偵錯。</span><span class="sxs-lookup"><span data-stu-id="be1d9-103">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="be1d9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="be1d9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="be1d9-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="be1d9-105">\<behaviors></span></span>  
<span data-ttu-id="be1d9-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="be1d9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="be1d9-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="be1d9-107">\<behavior></span></span>  
<span data-ttu-id="be1d9-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="be1d9-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1d9-109">語法</span><span class="sxs-lookup"><span data-stu-id="be1d9-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="be1d9-110">類型</span><span class="sxs-lookup"><span data-stu-id="be1d9-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be1d9-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="be1d9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="be1d9-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="be1d9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be1d9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="be1d9-113">Attributes</span></span>  
  
|<span data-ttu-id="be1d9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="be1d9-114">Attribute</span></span>|<span data-ttu-id="be1d9-115">描述</span><span class="sxs-lookup"><span data-stu-id="be1d9-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="be1d9-116">這個值會指定用戶端回呼物件是否將 SOAP 錯誤中的 Managed 例外狀況資訊傳回給服務。</span><span class="sxs-lookup"><span data-stu-id="be1d9-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="be1d9-117">如果您以程式設計方式將這個屬性設定為 `true`，您可以讓用戶端回呼物件中的 Managed 例外狀況資訊的流動回到服務，以達偵錯的目的。</span><span class="sxs-lookup"><span data-stu-id="be1d9-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="be1d9-118">**注意：** 傳回 managed 例外狀況資訊傳回用戶端可能會有的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="be1d9-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="be1d9-119">這是因為例外狀況細節會公開內部服務實作 (Implementation) 的相關資訊，可能會被未經授權的用戶端加以利用。</span><span class="sxs-lookup"><span data-stu-id="be1d9-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be1d9-120">子項目</span><span class="sxs-lookup"><span data-stu-id="be1d9-120">Child Elements</span></span>  
 <span data-ttu-id="be1d9-121">無。</span><span class="sxs-lookup"><span data-stu-id="be1d9-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="be1d9-122">父項目</span><span class="sxs-lookup"><span data-stu-id="be1d9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="be1d9-123">項目</span><span class="sxs-lookup"><span data-stu-id="be1d9-123">Element</span></span>|<span data-ttu-id="be1d9-124">描述</span><span class="sxs-lookup"><span data-stu-id="be1d9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be1d9-125">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="be1d9-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="be1d9-126">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="be1d9-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be1d9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be1d9-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
