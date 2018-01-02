---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccb48efcdd1924ade27220a685e146a7f5eeef76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcallbackdebuggt"></a><span data-ttu-id="e32a9-102">&lt;callbackDebug&gt;</span><span class="sxs-lookup"><span data-stu-id="e32a9-102">&lt;callbackDebug&gt;</span></span>
<span data-ttu-id="e32a9-103">指定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 回呼物件的服務偵錯。</span><span class="sxs-lookup"><span data-stu-id="e32a9-103">Specifies service debugging for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] callback object.</span></span>  
  
 <span data-ttu-id="e32a9-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e32a9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e32a9-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e32a9-105">\<behaviors></span></span>  
<span data-ttu-id="e32a9-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e32a9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e32a9-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e32a9-107">\<behavior></span></span>  
<span data-ttu-id="e32a9-108">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="e32a9-108">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e32a9-109">語法</span><span class="sxs-lookup"><span data-stu-id="e32a9-109">Syntax</span></span>  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a><span data-ttu-id="e32a9-110">類型</span><span class="sxs-lookup"><span data-stu-id="e32a9-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e32a9-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e32a9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e32a9-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e32a9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e32a9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e32a9-113">Attributes</span></span>  
  
|<span data-ttu-id="e32a9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="e32a9-114">Attribute</span></span>|<span data-ttu-id="e32a9-115">描述</span><span class="sxs-lookup"><span data-stu-id="e32a9-115">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="e32a9-116">這個值會指定用戶端回呼物件是否將 SOAP 錯誤中的 Managed 例外狀況資訊傳回給服務。</span><span class="sxs-lookup"><span data-stu-id="e32a9-116">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="e32a9-117">如果您以程式設計方式將這個屬性設定為 `true`，您可以讓用戶端回呼物件中的 Managed 例外狀況資訊的流動回到服務，以達偵錯的目的。</span><span class="sxs-lookup"><span data-stu-id="e32a9-117">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="e32a9-118">**注意：**傳回 managed 例外狀況資訊傳回用戶端可能會有的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="e32a9-118">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="e32a9-119">這是因為例外狀況細節會公開內部服務實作 (Implementation) 的相關資訊，可能會被未經授權的用戶端加以利用。</span><span class="sxs-lookup"><span data-stu-id="e32a9-119">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e32a9-120">子元素</span><span class="sxs-lookup"><span data-stu-id="e32a9-120">Child Elements</span></span>  
 <span data-ttu-id="e32a9-121">無。</span><span class="sxs-lookup"><span data-stu-id="e32a9-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e32a9-122">父項目</span><span class="sxs-lookup"><span data-stu-id="e32a9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e32a9-123">項目</span><span class="sxs-lookup"><span data-stu-id="e32a9-123">Element</span></span>|<span data-ttu-id="e32a9-124">描述</span><span class="sxs-lookup"><span data-stu-id="e32a9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e32a9-125">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e32a9-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e32a9-126">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="e32a9-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e32a9-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="e32a9-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
