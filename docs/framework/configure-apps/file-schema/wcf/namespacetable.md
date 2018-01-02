---
title: '&lt;a d d&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28bbeae9d1dbe43ad787c391ae461b44a8e85147
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltnamespacetablegt"></a><span data-ttu-id="14921-102">&lt;a d d&gt;</span><span class="sxs-lookup"><span data-stu-id="14921-102">&lt;namespaceTable&gt;</span></span>

<span data-ttu-id="14921-103">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="14921-103">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="14921-104">**\<system.serviceModel >** </span><span class="sxs-lookup"><span data-stu-id="14921-104">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="14921-105">&nbsp;&nbsp;**\<路由 >** </span><span class="sxs-lookup"><span data-stu-id="14921-105">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="14921-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<a d d >**</span><span class="sxs-lookup"><span data-stu-id="14921-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>

## <a name="syntax"></a><span data-ttu-id="14921-107">語法</span><span class="sxs-lookup"><span data-stu-id="14921-107">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a><span data-ttu-id="14921-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="14921-108">Attributes and elements</span></span>

<span data-ttu-id="14921-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="14921-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="14921-110">屬性</span><span class="sxs-lookup"><span data-stu-id="14921-110">Attributes</span></span>

<span data-ttu-id="14921-111">無</span><span class="sxs-lookup"><span data-stu-id="14921-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="14921-112">子元素</span><span class="sxs-lookup"><span data-stu-id="14921-112">Child elements</span></span>

|     | <span data-ttu-id="14921-113">描述</span><span class="sxs-lookup"><span data-stu-id="14921-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="14921-114">**\<篩選條件 >**</span><span class="sxs-lookup"><span data-stu-id="14921-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="14921-115">定義用於 XPath 運算式的命名空間前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="14921-115">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="14921-116">父元素</span><span class="sxs-lookup"><span data-stu-id="14921-116">Parent elements</span></span>

|     | <span data-ttu-id="14921-117">描述</span><span class="sxs-lookup"><span data-stu-id="14921-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="14921-118">**\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="14921-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="14921-119">代表定義一組路由篩選條件的組態區段，這些篩選條件會判斷傳入訊息時所用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別及路由表 (定義當篩選條件相符時的訊息傳送目標端點)。</span><span class="sxs-lookup"><span data-stu-id="14921-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="14921-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14921-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
