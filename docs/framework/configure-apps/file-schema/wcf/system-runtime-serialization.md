---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 5aa5d75e12852fe6a0e4e9a2eb4ae57d25d1022c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272674"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="d1ebc-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="d1ebc-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="d1ebc-103">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="d1ebc-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d1ebc-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="d1ebc-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1ebc-105">語法</span><span class="sxs-lookup"><span data-stu-id="d1ebc-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1ebc-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1ebc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d1ebc-107">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="d1ebc-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1ebc-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d1ebc-108">Attributes</span></span>  
 <span data-ttu-id="d1ebc-109">無。</span><span class="sxs-lookup"><span data-stu-id="d1ebc-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1ebc-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d1ebc-110">Child Elements</span></span>  
  
|<span data-ttu-id="d1ebc-111">項目</span><span class="sxs-lookup"><span data-stu-id="d1ebc-111">Element</span></span>|<span data-ttu-id="d1ebc-112">描述</span><span class="sxs-lookup"><span data-stu-id="d1ebc-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1ebc-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d1ebc-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="d1ebc-114">能夠在還原序列化時，加入要使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="d1ebc-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1ebc-115">父項目</span><span class="sxs-lookup"><span data-stu-id="d1ebc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d1ebc-116">項目</span><span class="sxs-lookup"><span data-stu-id="d1ebc-116">Element</span></span>|<span data-ttu-id="d1ebc-117">描述</span><span class="sxs-lookup"><span data-stu-id="d1ebc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1ebc-118">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="d1ebc-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="d1ebc-119">組態的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="d1ebc-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1ebc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1ebc-120">See also</span></span>
- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="d1ebc-121">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="d1ebc-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="d1ebc-122">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="d1ebc-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
