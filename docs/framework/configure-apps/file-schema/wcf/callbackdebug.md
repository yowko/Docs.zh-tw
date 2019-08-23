---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 91e7bd63bf496f2c38776d88173ed2ac12a3b888
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926313"
---
# <a name="callbackdebug"></a><span data-ttu-id="41a79-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="41a79-101">\<callbackDebug></span></span>
<span data-ttu-id="41a79-102">指定 Windows Communication Foundation (WCF) 回呼物件的服務偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="41a79-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="41a79-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="41a79-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="41a79-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="41a79-104">\<behaviors></span></span>  
<span data-ttu-id="41a79-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="41a79-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="41a79-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="41a79-106">\<behavior></span></span>  
<span data-ttu-id="41a79-107">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="41a79-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a79-108">語法</span><span class="sxs-lookup"><span data-stu-id="41a79-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="41a79-109">類型</span><span class="sxs-lookup"><span data-stu-id="41a79-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41a79-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="41a79-110">Attributes and Elements</span></span>  
 <span data-ttu-id="41a79-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="41a79-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41a79-112">屬性</span><span class="sxs-lookup"><span data-stu-id="41a79-112">Attributes</span></span>  
  
|<span data-ttu-id="41a79-113">屬性</span><span class="sxs-lookup"><span data-stu-id="41a79-113">Attribute</span></span>|<span data-ttu-id="41a79-114">說明</span><span class="sxs-lookup"><span data-stu-id="41a79-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="41a79-115">這個值會指定用戶端回呼物件是否將 SOAP 錯誤中的 Managed 例外狀況資訊傳回給服務。</span><span class="sxs-lookup"><span data-stu-id="41a79-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="41a79-116">如果您以程式設計方式將這個屬性設定為 `true`，您可以讓用戶端回呼物件中的 Managed 例外狀況資訊的流動回到服務，以達偵錯的目的。</span><span class="sxs-lookup"><span data-stu-id="41a79-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="41a79-117">**注意**：將 Managed 例外狀況資訊傳回用戶端時，可能會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="41a79-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="41a79-118">這是因為例外狀況細節會公開內部服務實作 (Implementation) 的相關資訊，可能會被未經授權的用戶端加以利用。</span><span class="sxs-lookup"><span data-stu-id="41a79-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41a79-119">子元素</span><span class="sxs-lookup"><span data-stu-id="41a79-119">Child Elements</span></span>  
 <span data-ttu-id="41a79-120">無。</span><span class="sxs-lookup"><span data-stu-id="41a79-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41a79-121">父項目</span><span class="sxs-lookup"><span data-stu-id="41a79-121">Parent Elements</span></span>  
  
|<span data-ttu-id="41a79-122">項目</span><span class="sxs-lookup"><span data-stu-id="41a79-122">Element</span></span>|<span data-ttu-id="41a79-123">描述</span><span class="sxs-lookup"><span data-stu-id="41a79-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41a79-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="41a79-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="41a79-125">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="41a79-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41a79-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41a79-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
