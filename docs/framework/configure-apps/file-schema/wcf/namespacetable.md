---
title: <namespaceTable>
ms.date: 03/30/2017
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
ms.openlocfilehash: ee7a0c23adca883af279addf9d1f221bd4056d00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269571"
---
# <a name="namespacetable"></a><span data-ttu-id="7630a-101">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="7630a-101">\<namespaceTable></span></span>

<span data-ttu-id="7630a-102">代表定義一組項目的組態區段，其中包含前置詞對應的命名空間，這些對應稍後可在 XPath 篩選條件中用於路由。</span><span class="sxs-lookup"><span data-stu-id="7630a-102">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>

<span data-ttu-id="7630a-103">**\<system.serviceModel>** </span><span class="sxs-lookup"><span data-stu-id="7630a-103">**\<system.serviceModel>** </span></span>  
<span data-ttu-id="7630a-104">&nbsp;&nbsp;**\<routing>** </span><span class="sxs-lookup"><span data-stu-id="7630a-104">&nbsp;&nbsp;**\<routing>** </span></span>  
<span data-ttu-id="7630a-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span><span class="sxs-lookup"><span data-stu-id="7630a-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="7630a-106">語法</span><span class="sxs-lookup"><span data-stu-id="7630a-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String"
           prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7630a-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="7630a-107">Attributes and elements</span></span>

<span data-ttu-id="7630a-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7630a-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7630a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7630a-109">Attributes</span></span>

<span data-ttu-id="7630a-110">無</span><span class="sxs-lookup"><span data-stu-id="7630a-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="7630a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7630a-111">Child elements</span></span>

|     | <span data-ttu-id="7630a-112">描述</span><span class="sxs-lookup"><span data-stu-id="7630a-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7630a-113">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="7630a-113">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="7630a-114">定義用於 XPath 運算式的命名空間前置詞對應。</span><span class="sxs-lookup"><span data-stu-id="7630a-114">Defines a namespace prefix mapping used for XPath expressions.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="7630a-115">父元素</span><span class="sxs-lookup"><span data-stu-id="7630a-115">Parent elements</span></span>

|     | <span data-ttu-id="7630a-116">描述</span><span class="sxs-lookup"><span data-stu-id="7630a-116">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7630a-117">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="7630a-117">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="7630a-118">代表定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>評估內送訊息，以及路由資料表定義目標端點時要使用將訊息傳送至篩選條件的比對。</span><span class="sxs-lookup"><span data-stu-id="7630a-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="7630a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7630a-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
