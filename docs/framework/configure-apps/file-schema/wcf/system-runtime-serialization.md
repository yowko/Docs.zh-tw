---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c34eba2614a354f1753d8da077f8653f2c260a97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165889"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="020e2-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="020e2-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="020e2-103">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="020e2-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="020e2-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="020e2-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="020e2-105">語法</span><span class="sxs-lookup"><span data-stu-id="020e2-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="020e2-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="020e2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="020e2-107">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="020e2-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="020e2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="020e2-108">Attributes</span></span>  
 <span data-ttu-id="020e2-109">無。</span><span class="sxs-lookup"><span data-stu-id="020e2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="020e2-110">子元素</span><span class="sxs-lookup"><span data-stu-id="020e2-110">Child Elements</span></span>  
  
|<span data-ttu-id="020e2-111">項目</span><span class="sxs-lookup"><span data-stu-id="020e2-111">Element</span></span>|<span data-ttu-id="020e2-112">描述</span><span class="sxs-lookup"><span data-stu-id="020e2-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="020e2-113">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="020e2-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="020e2-114">能夠在還原序列化時，加入要使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="020e2-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="020e2-115">父項目</span><span class="sxs-lookup"><span data-stu-id="020e2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="020e2-116">項目</span><span class="sxs-lookup"><span data-stu-id="020e2-116">Element</span></span>|<span data-ttu-id="020e2-117">描述</span><span class="sxs-lookup"><span data-stu-id="020e2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="020e2-118">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="020e2-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="020e2-119">組態的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="020e2-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="020e2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="020e2-120">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="020e2-121">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="020e2-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="020e2-122">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="020e2-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
