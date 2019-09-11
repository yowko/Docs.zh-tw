---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850265"
---
# <a name="backuplists"></a><span data-ttu-id="6b3a7-101">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="6b3a7-101">\<backupLists></span></span>
<span data-ttu-id="6b3a7-102">代表組態區段，用於定義錯誤處理中使用的一組備份服務。</span><span class="sxs-lookup"><span data-stu-id="6b3a7-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="6b3a7-103">每個子專案都是一個備份清單，它會列舉一組您希望路由服務在無法連上主要端點時使用的端點。</span><span class="sxs-lookup"><span data-stu-id="6b3a7-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="6b3a7-104">如果清單中的第一個端點關閉，路由服務將自動容錯移轉至清單中的下一個端點。</span><span class="sxs-lookup"><span data-stu-id="6b3a7-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="6b3a7-105">如此可提供您快速提升應用程式可靠性的方式，而不需教導用戶端應用程式如何處理複雜的模式以及部署所有服務的位置。</span><span class="sxs-lookup"><span data-stu-id="6b3a7-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="6b3a7-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b3a7-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b3a7-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6b3a7-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6b3a7-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<路由 >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="6b3a7-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="6b3a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupLists >**</span><span class="sxs-lookup"><span data-stu-id="6b3a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b3a7-110">語法</span><span class="sxs-lookup"><span data-stu-id="6b3a7-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b3a7-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6b3a7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6b3a7-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6b3a7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b3a7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6b3a7-113">Attributes</span></span>  
 <span data-ttu-id="6b3a7-114">無。</span><span class="sxs-lookup"><span data-stu-id="6b3a7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b3a7-115">子元素</span><span class="sxs-lookup"><span data-stu-id="6b3a7-115">Child Elements</span></span>  
  
|<span data-ttu-id="6b3a7-116">項目</span><span class="sxs-lookup"><span data-stu-id="6b3a7-116">Element</span></span>|<span data-ttu-id="6b3a7-117">說明</span><span class="sxs-lookup"><span data-stu-id="6b3a7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b3a7-118">\<filter></span><span class="sxs-lookup"><span data-stu-id="6b3a7-118">\<filter></span></span>](filter.md)|<span data-ttu-id="6b3a7-119">包含您希望路由服務在無法連上主要端點時使用的端點清單。</span><span class="sxs-lookup"><span data-stu-id="6b3a7-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="6b3a7-120">.</span><span class="sxs-lookup"><span data-stu-id="6b3a7-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b3a7-121">父項目</span><span class="sxs-lookup"><span data-stu-id="6b3a7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6b3a7-122">項目</span><span class="sxs-lookup"><span data-stu-id="6b3a7-122">Element</span></span>|<span data-ttu-id="6b3a7-123">描述</span><span class="sxs-lookup"><span data-stu-id="6b3a7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b3a7-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="6b3a7-124">\<routing></span></span>](routing.md)|<span data-ttu-id="6b3a7-125">表示定義一組路由篩選的設定區段，其決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型，以及將目標端點定義為的路由表。當篩選準則相符時，將訊息傳送至。</span><span class="sxs-lookup"><span data-stu-id="6b3a7-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b3a7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b3a7-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
