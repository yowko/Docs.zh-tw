---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152966"
---
# \<system.runtime.serialization>
<span data-ttu-id="1d140-102">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="1d140-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="1d140-103">語法</span><span class="sxs-lookup"><span data-stu-id="1d140-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d140-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1d140-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1d140-105">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="1d140-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d140-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1d140-106">Attributes</span></span>  
 <span data-ttu-id="1d140-107">無。</span><span class="sxs-lookup"><span data-stu-id="1d140-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d140-108">子元素</span><span class="sxs-lookup"><span data-stu-id="1d140-108">Child Elements</span></span>  
  
|<span data-ttu-id="1d140-109">元素</span><span class="sxs-lookup"><span data-stu-id="1d140-109">Element</span></span>|<span data-ttu-id="1d140-110">描述</span><span class="sxs-lookup"><span data-stu-id="1d140-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="1d140-111">能夠在還原序列化時，加入要使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="1d140-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d140-112">父項目</span><span class="sxs-lookup"><span data-stu-id="1d140-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1d140-113">元素</span><span class="sxs-lookup"><span data-stu-id="1d140-113">Element</span></span>|<span data-ttu-id="1d140-114">描述</span><span class="sxs-lookup"><span data-stu-id="1d140-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d140-115">\<configuration>元素</span><span class="sxs-lookup"><span data-stu-id="1d140-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="1d140-116">組態的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="1d140-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d140-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d140-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="1d140-118">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="1d140-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="1d140-119">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="1d140-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
