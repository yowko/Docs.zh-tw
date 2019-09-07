---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: b67f51e634d1294830690dad8c8cffb1fc9a6cd2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399455"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="f858f-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="f858f-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="f858f-103">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="f858f-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="f858f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f858f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f858f-105">&nbsp;&nbsp; **\<> 的序列化**</span><span class="sxs-lookup"><span data-stu-id="f858f-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f858f-106">語法</span><span class="sxs-lookup"><span data-stu-id="f858f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f858f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f858f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f858f-108">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f858f-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f858f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f858f-109">Attributes</span></span>  
 <span data-ttu-id="f858f-110">無。</span><span class="sxs-lookup"><span data-stu-id="f858f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f858f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f858f-111">Child Elements</span></span>  
  
|<span data-ttu-id="f858f-112">項目</span><span class="sxs-lookup"><span data-stu-id="f858f-112">Element</span></span>|<span data-ttu-id="f858f-113">描述</span><span class="sxs-lookup"><span data-stu-id="f858f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f858f-114">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f858f-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="f858f-115">能夠在還原序列化時，加入要使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="f858f-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f858f-116">父項目</span><span class="sxs-lookup"><span data-stu-id="f858f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f858f-117">項目</span><span class="sxs-lookup"><span data-stu-id="f858f-117">Element</span></span>|<span data-ttu-id="f858f-118">描述</span><span class="sxs-lookup"><span data-stu-id="f858f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f858f-119">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="f858f-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="f858f-120">組態的最上層項目。</span><span class="sxs-lookup"><span data-stu-id="f858f-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f858f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f858f-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="f858f-122">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="f858f-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="f858f-123">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="f858f-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
 