---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: cc7c1a64f9481a7ab41cf35241ade04bd690dae0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275570"
---
# <a name="routing"></a><span data-ttu-id="25706-101">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="25706-101">\<routing></span></span>

<span data-ttu-id="25706-102">代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>評估內送訊息，以及路由資料表定義目標端點時要使用將訊息傳送至篩選條件的比對。</span><span class="sxs-lookup"><span data-stu-id="25706-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="25706-103">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="25706-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="25706-104">&nbsp;&nbsp;**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="25706-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="25706-105">語法</span><span class="sxs-lookup"><span data-stu-id="25706-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25706-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="25706-106">Attributes and elements</span></span>

<span data-ttu-id="25706-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="25706-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="25706-108">屬性</span><span class="sxs-lookup"><span data-stu-id="25706-108">Attributes</span></span>

<span data-ttu-id="25706-109">無</span><span class="sxs-lookup"><span data-stu-id="25706-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="25706-110">子元素</span><span class="sxs-lookup"><span data-stu-id="25706-110">Child elements</span></span>

|     | <span data-ttu-id="25706-111">描述</span><span class="sxs-lookup"><span data-stu-id="25706-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="25706-112">**\<filters>**</span><span class="sxs-lookup"><span data-stu-id="25706-112">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="25706-113">包含一組路由篩選，以決定評估內送訊息時，就會使用 Windows Communication Foundation (WCF) MessageFilter 的型別。</span><span class="sxs-lookup"><span data-stu-id="25706-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="25706-114">**\<filterTables>**</span><span class="sxs-lookup"><span data-stu-id="25706-114">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="25706-115">包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。</span><span class="sxs-lookup"><span data-stu-id="25706-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="25706-116">父元素</span><span class="sxs-lookup"><span data-stu-id="25706-116">Parent elements</span></span>

|     | <span data-ttu-id="25706-117">描述</span><span class="sxs-lookup"><span data-stu-id="25706-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="25706-118">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="25706-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="25706-119">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="25706-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="25706-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25706-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
