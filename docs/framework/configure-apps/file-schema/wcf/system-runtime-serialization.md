---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 84ced06691ce3b3c9c9573fc9d114335096a849d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157105"
---
# \<system.runtime.serialization>

<span data-ttu-id="c8179-102">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="c8179-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="c8179-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8179-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8179-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c8179-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c8179-105">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="c8179-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8179-106">屬性</span><span class="sxs-lookup"><span data-stu-id="c8179-106">Attributes</span></span>  

 <span data-ttu-id="c8179-107">無。</span><span class="sxs-lookup"><span data-stu-id="c8179-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c8179-108">子元素</span><span class="sxs-lookup"><span data-stu-id="c8179-108">Child Elements</span></span>  
  
|<span data-ttu-id="c8179-109">項目</span><span class="sxs-lookup"><span data-stu-id="c8179-109">Element</span></span>|<span data-ttu-id="c8179-110">描述</span><span class="sxs-lookup"><span data-stu-id="c8179-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="c8179-111">能夠在還原序列化時，加入要使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="c8179-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8179-112">父項目</span><span class="sxs-lookup"><span data-stu-id="c8179-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c8179-113">項目</span><span class="sxs-lookup"><span data-stu-id="c8179-113">Element</span></span>|<span data-ttu-id="c8179-114">描述</span><span class="sxs-lookup"><span data-stu-id="c8179-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8179-115">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="c8179-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="c8179-116">組態的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="c8179-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8179-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8179-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="c8179-118">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="c8179-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="c8179-119">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="c8179-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
