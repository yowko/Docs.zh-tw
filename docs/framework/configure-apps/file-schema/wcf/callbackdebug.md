---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: a1190eb1c015ba07488ff5a5952f2f5f1b10974c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704514"
---
# <a name="callbackdebug"></a><span data-ttu-id="a1fcf-101">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="a1fcf-101">\<callbackDebug></span></span>
<span data-ttu-id="a1fcf-102">指定 Windows Communication Foundation (WCF) 回呼物件的偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="a1fcf-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
 <span data-ttu-id="a1fcf-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a1fcf-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a1fcf-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="a1fcf-104">\<behaviors></span></span>  
<span data-ttu-id="a1fcf-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a1fcf-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="a1fcf-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a1fcf-106">\<behavior></span></span>  
<span data-ttu-id="a1fcf-107">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="a1fcf-107">\<callbackDebug></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1fcf-108">語法</span><span class="sxs-lookup"><span data-stu-id="a1fcf-108">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="a1fcf-109">類型</span><span class="sxs-lookup"><span data-stu-id="a1fcf-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1fcf-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a1fcf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a1fcf-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a1fcf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1fcf-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a1fcf-112">Attributes</span></span>  
  
|<span data-ttu-id="a1fcf-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a1fcf-113">Attribute</span></span>|<span data-ttu-id="a1fcf-114">描述</span><span class="sxs-lookup"><span data-stu-id="a1fcf-114">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="a1fcf-115">這個值會指定用戶端回呼物件是否將 SOAP 錯誤中的 Managed 例外狀況資訊傳回給服務。</span><span class="sxs-lookup"><span data-stu-id="a1fcf-115">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="a1fcf-116">如果您以程式設計方式將這個屬性設定為 `true`，您可以讓用戶端回呼物件中的 Managed 例外狀況資訊的流動回到服務，以達偵錯的目的。</span><span class="sxs-lookup"><span data-stu-id="a1fcf-116">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="a1fcf-117">**注意：** 將 Managed 例外狀況資訊傳回用戶端時，可能會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="a1fcf-117">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="a1fcf-118">這是因為例外狀況細節會公開內部服務實作 (Implementation) 的相關資訊，可能會被未經授權的用戶端加以利用。</span><span class="sxs-lookup"><span data-stu-id="a1fcf-118">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1fcf-119">子元素</span><span class="sxs-lookup"><span data-stu-id="a1fcf-119">Child Elements</span></span>  
 <span data-ttu-id="a1fcf-120">無。</span><span class="sxs-lookup"><span data-stu-id="a1fcf-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1fcf-121">父項目</span><span class="sxs-lookup"><span data-stu-id="a1fcf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a1fcf-122">項目</span><span class="sxs-lookup"><span data-stu-id="a1fcf-122">Element</span></span>|<span data-ttu-id="a1fcf-123">描述</span><span class="sxs-lookup"><span data-stu-id="a1fcf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1fcf-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a1fcf-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a1fcf-125">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="a1fcf-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1fcf-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1fcf-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
