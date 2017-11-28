---
title: "&lt;路由&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed2dd4e68584d6e79e18fc9b61fcc8f078615dac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltroutinggt"></a><span data-ttu-id="31738-102">&lt;路由&gt;</span><span class="sxs-lookup"><span data-stu-id="31738-102">&lt;routing&gt;</span></span>

<span data-ttu-id="31738-103">代表定義一組路由篩選條件的組態區段，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 (定義當篩選條件相符時的訊息傳送目標端點)。</span><span class="sxs-lookup"><span data-stu-id="31738-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="31738-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="31738-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="31738-105">&nbsp;&nbsp;**\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="31738-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="31738-106">語法</span><span class="sxs-lookup"><span data-stu-id="31738-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="31738-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="31738-107">Attributes and elements</span></span>

<span data-ttu-id="31738-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="31738-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="31738-109">屬性</span><span class="sxs-lookup"><span data-stu-id="31738-109">Attributes</span></span>

<span data-ttu-id="31738-110">無</span><span class="sxs-lookup"><span data-stu-id="31738-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="31738-111">子元素</span><span class="sxs-lookup"><span data-stu-id="31738-111">Child elements</span></span>

|     | <span data-ttu-id="31738-112">說明</span><span class="sxs-lookup"><span data-stu-id="31738-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="31738-113">**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="31738-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="31738-114">包含一組路由篩選條件，這些篩選條件會判斷傳入訊息時所使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter 的型別。</span><span class="sxs-lookup"><span data-stu-id="31738-114">Contains a set of routing filters that determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="31738-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="31738-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="31738-116">包含路由篩選條件與目標端點之間的對應，可指定當篩選條件符合時所使用的端點。</span><span class="sxs-lookup"><span data-stu-id="31738-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="31738-117">父元素</span><span class="sxs-lookup"><span data-stu-id="31738-117">Parent elements</span></span>

|     | <span data-ttu-id="31738-118">說明</span><span class="sxs-lookup"><span data-stu-id="31738-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="31738-119">**\<系統。ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="31738-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="31738-120">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="31738-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="31738-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="31738-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
