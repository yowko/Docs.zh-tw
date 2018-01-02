---
title: '&lt;system.runtime.serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab66252ebc5b87c197b3e4ac7b6def9355e5f201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="f2db0-102">&lt;system.runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="f2db0-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="f2db0-103">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="f2db0-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="f2db0-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="f2db0-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2db0-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2db0-105">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
             <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2db0-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f2db0-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f2db0-107">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f2db0-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2db0-108">屬性</span><span class="sxs-lookup"><span data-stu-id="f2db0-108">Attributes</span></span>  
 <span data-ttu-id="f2db0-109">無。</span><span class="sxs-lookup"><span data-stu-id="f2db0-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2db0-110">子元素</span><span class="sxs-lookup"><span data-stu-id="f2db0-110">Child Elements</span></span>  
  
|<span data-ttu-id="f2db0-111">項目</span><span class="sxs-lookup"><span data-stu-id="f2db0-111">Element</span></span>|<span data-ttu-id="f2db0-112">描述</span><span class="sxs-lookup"><span data-stu-id="f2db0-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2db0-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="f2db0-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="f2db0-114">能夠在還原序列化時，加入要使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="f2db0-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2db0-115">父項目</span><span class="sxs-lookup"><span data-stu-id="f2db0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f2db0-116">項目</span><span class="sxs-lookup"><span data-stu-id="f2db0-116">Element</span></span>|<span data-ttu-id="f2db0-117">描述</span><span class="sxs-lookup"><span data-stu-id="f2db0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2db0-118">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="f2db0-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f2db0-119">組態的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="f2db0-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2db0-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2db0-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="f2db0-121">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="f2db0-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="f2db0-122">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="f2db0-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
