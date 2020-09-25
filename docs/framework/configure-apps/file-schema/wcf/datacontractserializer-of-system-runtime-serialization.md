---
title: <dataContractSerializer> <system.string>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: a8d379e7a37bca0cdb58836a6afdf814320e2411
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190185"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="90f27-102">\<dataContractSerializer> 的 \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="90f27-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>

<span data-ttu-id="90f27-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="90f27-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="90f27-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="90f27-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90f27-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90f27-105">Attributes and Elements</span></span>  

 <span data-ttu-id="90f27-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="90f27-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90f27-107">屬性</span><span class="sxs-lookup"><span data-stu-id="90f27-107">Attributes</span></span>  
  
|<span data-ttu-id="90f27-108">項目</span><span class="sxs-lookup"><span data-stu-id="90f27-108">Element</span></span>|<span data-ttu-id="90f27-109">描述</span><span class="sxs-lookup"><span data-stu-id="90f27-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90f27-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="90f27-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="90f27-111">布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="90f27-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="90f27-112">此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。</span><span class="sxs-lookup"><span data-stu-id="90f27-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="90f27-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="90f27-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="90f27-114">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="90f27-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="90f27-115">此屬性為 65536。</span><span class="sxs-lookup"><span data-stu-id="90f27-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90f27-116">子元素</span><span class="sxs-lookup"><span data-stu-id="90f27-116">Child Elements</span></span>  
  
|<span data-ttu-id="90f27-117">項目</span><span class="sxs-lookup"><span data-stu-id="90f27-117">Element</span></span>|<span data-ttu-id="90f27-118">描述</span><span class="sxs-lookup"><span data-stu-id="90f27-118">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="90f27-119">包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="90f27-119">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="90f27-120">如需資料合約和已知型別的詳細資訊，請參閱 [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="90f27-120">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90f27-121">父項目</span><span class="sxs-lookup"><span data-stu-id="90f27-121">Parent Elements</span></span>  
  
|<span data-ttu-id="90f27-122">項目</span><span class="sxs-lookup"><span data-stu-id="90f27-122">Element</span></span>|<span data-ttu-id="90f27-123">描述</span><span class="sxs-lookup"><span data-stu-id="90f27-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="90f27-124">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="90f27-124">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90f27-125">備註</span><span class="sxs-lookup"><span data-stu-id="90f27-125">Remarks</span></span>  

 <span data-ttu-id="90f27-126">如需已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer> 和 [資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="90f27-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f27-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90f27-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="90f27-128">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="90f27-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
