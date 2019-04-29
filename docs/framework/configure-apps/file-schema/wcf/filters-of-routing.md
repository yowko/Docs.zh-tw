---
title: <filters> 的 <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 8b2c735a19c4cece16dcb77e3ec548eb2d39ec18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701030"
---
# <a name="filters-of-routing"></a><span data-ttu-id="168fd-102">\<篩選條件 > 的\<路由 ></span><span class="sxs-lookup"><span data-stu-id="168fd-102">\<filters> of \<routing></span></span>

<span data-ttu-id="168fd-103">代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息時使用。</span><span class="sxs-lookup"><span data-stu-id="168fd-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="168fd-104">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="168fd-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="168fd-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="168fd-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="168fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span><span class="sxs-lookup"><span data-stu-id="168fd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="168fd-107">語法</span><span class="sxs-lookup"><span data-stu-id="168fd-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="168fd-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="168fd-108">Attributes and elements</span></span>

<span data-ttu-id="168fd-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="168fd-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="168fd-110">屬性</span><span class="sxs-lookup"><span data-stu-id="168fd-110">Attributes</span></span>

<span data-ttu-id="168fd-111">None</span><span class="sxs-lookup"><span data-stu-id="168fd-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="168fd-112">子元素</span><span class="sxs-lookup"><span data-stu-id="168fd-112">Child elements</span></span>

|     | <span data-ttu-id="168fd-113">描述</span><span class="sxs-lookup"><span data-stu-id="168fd-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="168fd-114">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="168fd-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="168fd-115">包含路由篩選條件，決定類型的 Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息時，會使用。</span><span class="sxs-lookup"><span data-stu-id="168fd-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="168fd-116">父元素</span><span class="sxs-lookup"><span data-stu-id="168fd-116">Parent elements</span></span>

|     | <span data-ttu-id="168fd-117">描述</span><span class="sxs-lookup"><span data-stu-id="168fd-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="168fd-118">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="168fd-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="168fd-119">代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>評估內送訊息，以及路由資料表定義目標端點時要使用將訊息傳送至篩選條件的比對。</span><span class="sxs-lookup"><span data-stu-id="168fd-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="168fd-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="168fd-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
