---
title: <filters> 的 <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855244"
---
# <a name="filters-of-routing"></a><span data-ttu-id="402d1-102">\<> 路由 > \<的篩選準則</span><span class="sxs-lookup"><span data-stu-id="402d1-102">\<filters> of \<routing></span></span>

<span data-ttu-id="402d1-103">表示定義一組路由篩選的設定區段，其決定在評估傳入訊息時所使用的 Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型。</span><span class="sxs-lookup"><span data-stu-id="402d1-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="402d1-104">[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="402d1-104">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="402d1-105">&nbsp;&nbsp;[ **\<routing>** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="402d1-105">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="402d1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<filters>**</span><span class="sxs-lookup"><span data-stu-id="402d1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="402d1-107">語法</span><span class="sxs-lookup"><span data-stu-id="402d1-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="402d1-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="402d1-108">Attributes and elements</span></span>

<span data-ttu-id="402d1-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="402d1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="402d1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="402d1-110">Attributes</span></span>

<span data-ttu-id="402d1-111">無</span><span class="sxs-lookup"><span data-stu-id="402d1-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="402d1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="402d1-112">Child elements</span></span>

|     | <span data-ttu-id="402d1-113">描述</span><span class="sxs-lookup"><span data-stu-id="402d1-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="402d1-114"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="402d1-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="402d1-115">包含路由篩選準則，決定在評估傳入訊息時，將<xref:System.ServiceModel.Dispatcher.MessageFilter>使用的 Windows Communication Foundation 類型（WCF）。</span><span class="sxs-lookup"><span data-stu-id="402d1-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="402d1-116">父元素</span><span class="sxs-lookup"><span data-stu-id="402d1-116">Parent elements</span></span>

|     | <span data-ttu-id="402d1-117">說明</span><span class="sxs-lookup"><span data-stu-id="402d1-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="402d1-118"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="402d1-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="402d1-119">表示定義一組路由篩選的設定區段，其決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型，以及將目標端點定義為的路由表。當篩選準則相符時，將訊息傳送至。</span><span class="sxs-lookup"><span data-stu-id="402d1-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="402d1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="402d1-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
