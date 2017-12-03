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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9dd9faf63ade725bb8bea12b40390fd30c91973
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="bc88f-102">&lt;routing&gt; 的 &lt;filters&gt;</span><span class="sxs-lookup"><span data-stu-id="bc88f-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="bc88f-103">代表組態區段，用於定義一組路由篩選條件，這些篩選條件可判斷傳入訊息時要使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別。</span><span class="sxs-lookup"><span data-stu-id="bc88f-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="bc88f-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="bc88f-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="bc88f-105">&nbsp;&nbsp;[**\<路由 >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="bc88f-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="bc88f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="bc88f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bc88f-107">語法</span><span class="sxs-lookup"><span data-stu-id="bc88f-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="bc88f-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="bc88f-108">Attributes and elements</span></span>

<span data-ttu-id="bc88f-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bc88f-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc88f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="bc88f-110">Attributes</span></span>

<span data-ttu-id="bc88f-111">無</span><span class="sxs-lookup"><span data-stu-id="bc88f-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc88f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="bc88f-112">Child elements</span></span>

|     | <span data-ttu-id="bc88f-113">說明</span><span class="sxs-lookup"><span data-stu-id="bc88f-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bc88f-114">**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="bc88f-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="bc88f-115">包含路由篩選條件，這些篩選條件會判斷傳入訊息時所使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別。</span><span class="sxs-lookup"><span data-stu-id="bc88f-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="bc88f-116">父元素</span><span class="sxs-lookup"><span data-stu-id="bc88f-116">Parent elements</span></span>

|     | <span data-ttu-id="bc88f-117">說明</span><span class="sxs-lookup"><span data-stu-id="bc88f-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bc88f-118">**\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="bc88f-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="bc88f-119">代表定義一組路由篩選條件的組態區段，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 (定義當篩選條件相符時的訊息傳送目標端點)。</span><span class="sxs-lookup"><span data-stu-id="bc88f-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="bc88f-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc88f-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
