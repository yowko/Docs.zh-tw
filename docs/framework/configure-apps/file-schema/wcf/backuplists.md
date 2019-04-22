---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 6e44dbe3c0966c6d243db343b9f9b0dec2480cb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134442"
---
# <a name="backuplists"></a><span data-ttu-id="a3194-101">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="a3194-101">\<backupLists></span></span>
<span data-ttu-id="a3194-102">代表組態區段，用於定義錯誤處理中使用的一組備份服務。</span><span class="sxs-lookup"><span data-stu-id="a3194-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="a3194-103">每個子項目是備份清單會列舉一組您希望路由服務在無法找到主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="a3194-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="a3194-104">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="a3194-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="a3194-105">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="a3194-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="a3194-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a3194-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a3194-107">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="a3194-107">\<routing></span></span>  
<span data-ttu-id="a3194-108">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="a3194-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3194-109">語法</span><span class="sxs-lookup"><span data-stu-id="a3194-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3194-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a3194-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a3194-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a3194-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3194-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a3194-112">Attributes</span></span>  
 <span data-ttu-id="a3194-113">無。</span><span class="sxs-lookup"><span data-stu-id="a3194-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a3194-114">子元素</span><span class="sxs-lookup"><span data-stu-id="a3194-114">Child Elements</span></span>  
  
|<span data-ttu-id="a3194-115">項目</span><span class="sxs-lookup"><span data-stu-id="a3194-115">Element</span></span>|<span data-ttu-id="a3194-116">描述</span><span class="sxs-lookup"><span data-stu-id="a3194-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3194-117">\<filter></span><span class="sxs-lookup"><span data-stu-id="a3194-117">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="a3194-118">包含一份您希望路由服務在無法找到主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="a3194-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="a3194-119">。</span><span class="sxs-lookup"><span data-stu-id="a3194-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a3194-120">父項目</span><span class="sxs-lookup"><span data-stu-id="a3194-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a3194-121">項目</span><span class="sxs-lookup"><span data-stu-id="a3194-121">Element</span></span>|<span data-ttu-id="a3194-122">描述</span><span class="sxs-lookup"><span data-stu-id="a3194-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3194-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="a3194-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="a3194-124">代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>評估內送訊息，以及路由資料表定義目標端點時要使用將訊息傳送至篩選條件的比對。</span><span class="sxs-lookup"><span data-stu-id="a3194-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3194-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3194-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
