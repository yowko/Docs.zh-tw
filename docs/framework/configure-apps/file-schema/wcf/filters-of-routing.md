---
title: "&lt;routing&gt; 的 &lt;filters&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9dddd9f9ba5f4c2cea7e92c666e8d224ccf21cee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="e5eb0-102">&lt;routing&gt; 的 &lt;filters&gt;</span><span class="sxs-lookup"><span data-stu-id="e5eb0-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="e5eb0-103">代表組態區段，用於定義一組路由篩選條件，這些篩選條件可判斷傳入訊息時要使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別。</span><span class="sxs-lookup"><span data-stu-id="e5eb0-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="e5eb0-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e5eb0-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="e5eb0-105">&nbsp;&nbsp;[**\<路由 >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="e5eb0-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="e5eb0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="e5eb0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e5eb0-107">語法</span><span class="sxs-lookup"><span data-stu-id="e5eb0-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e5eb0-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="e5eb0-108">Attributes and elements</span></span>

<span data-ttu-id="e5eb0-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5eb0-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5eb0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e5eb0-110">Attributes</span></span>

<span data-ttu-id="e5eb0-111">無</span><span class="sxs-lookup"><span data-stu-id="e5eb0-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5eb0-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e5eb0-112">Child elements</span></span>

|     | <span data-ttu-id="e5eb0-113">說明</span><span class="sxs-lookup"><span data-stu-id="e5eb0-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e5eb0-114">**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="e5eb0-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="e5eb0-115">包含路由篩選條件，這些篩選條件會判斷傳入訊息時所使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別。</span><span class="sxs-lookup"><span data-stu-id="e5eb0-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="e5eb0-116">父元素</span><span class="sxs-lookup"><span data-stu-id="e5eb0-116">Parent elements</span></span>

|     | <span data-ttu-id="e5eb0-117">說明</span><span class="sxs-lookup"><span data-stu-id="e5eb0-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e5eb0-118">**\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="e5eb0-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="e5eb0-119">代表定義一組路由篩選條件的組態區段，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 (定義當篩選條件相符時的訊息傳送目標端點)。</span><span class="sxs-lookup"><span data-stu-id="e5eb0-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e5eb0-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5eb0-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
