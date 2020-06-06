---
title: <filters> 的 <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855244"
---
# <a name="filters-of-routing"></a><span data-ttu-id="c9f7b-102">\<filters> 的 \<routing></span><span class="sxs-lookup"><span data-stu-id="c9f7b-102">\<filters> of \<routing></span></span>

<span data-ttu-id="c9f7b-103">表示定義一組路由篩選的設定區段，其決定在 <xref:System.ServiceModel.Dispatcher.MessageFilter> 評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型。</span><span class="sxs-lookup"><span data-stu-id="c9f7b-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="c9f7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9f7b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9f7b-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="c9f7b-105">Attributes and elements</span></span>

<span data-ttu-id="c9f7b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c9f7b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9f7b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c9f7b-107">Attributes</span></span>

<span data-ttu-id="c9f7b-108">無</span><span class="sxs-lookup"><span data-stu-id="c9f7b-108">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9f7b-109">子元素</span><span class="sxs-lookup"><span data-stu-id="c9f7b-109">Child elements</span></span>

|     | <span data-ttu-id="c9f7b-110">描述</span><span class="sxs-lookup"><span data-stu-id="c9f7b-110">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="c9f7b-111">包含路由篩選準則，決定在 <xref:System.ServiceModel.Dispatcher.MessageFilter> 評估傳入訊息時，將使用的 Windows Communication Foundation 類型（WCF）。</span><span class="sxs-lookup"><span data-stu-id="c9f7b-111">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="c9f7b-112">父元素</span><span class="sxs-lookup"><span data-stu-id="c9f7b-112">Parent elements</span></span>

|     | <span data-ttu-id="c9f7b-113">描述</span><span class="sxs-lookup"><span data-stu-id="c9f7b-113">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="c9f7b-114">表示定義一組路由篩選的設定區段，其會決定在評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及定義當篩選準則符合時，要傳送訊息的目標端點的路由表。</span><span class="sxs-lookup"><span data-stu-id="c9f7b-114">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="c9f7b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9f7b-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
