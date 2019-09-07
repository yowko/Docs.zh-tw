---
title: <dataContractSerializer>< 的 >。
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398085"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="5119a-102">\<dataContractSerializer > > \<的序列化</span><span class="sxs-lookup"><span data-stu-id="5119a-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="5119a-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="5119a-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="5119a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5119a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5119a-105">&nbsp;&nbsp;[ **\<> 的序列化**](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="5119a-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="5119a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<dataContractSerializer >**</span><span class="sxs-lookup"><span data-stu-id="5119a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5119a-107">語法</span><span class="sxs-lookup"><span data-stu-id="5119a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5119a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5119a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5119a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5119a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5119a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5119a-110">Attributes</span></span>  
  
|<span data-ttu-id="5119a-111">項目</span><span class="sxs-lookup"><span data-stu-id="5119a-111">Element</span></span>|<span data-ttu-id="5119a-112">描述</span><span class="sxs-lookup"><span data-stu-id="5119a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5119a-113">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="5119a-113">ignoreExtensionDataObject</span></span>|<span data-ttu-id="5119a-114">布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="5119a-114">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="5119a-115">此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。</span><span class="sxs-lookup"><span data-stu-id="5119a-115">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="5119a-116">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="5119a-116">maxItemsInObjectGraph</span></span>|<span data-ttu-id="5119a-117">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="5119a-117">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="5119a-118">此屬性為 65536。</span><span class="sxs-lookup"><span data-stu-id="5119a-118">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5119a-119">子元素</span><span class="sxs-lookup"><span data-stu-id="5119a-119">Child Elements</span></span>  
  
|<span data-ttu-id="5119a-120">項目</span><span class="sxs-lookup"><span data-stu-id="5119a-120">Element</span></span>|<span data-ttu-id="5119a-121">描述</span><span class="sxs-lookup"><span data-stu-id="5119a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5119a-122">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="5119a-122">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="5119a-123">包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="5119a-123">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="5119a-124">如需資料合約和已知類型的詳細資訊，請參閱[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5119a-124">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5119a-125">父項目</span><span class="sxs-lookup"><span data-stu-id="5119a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5119a-126">項目</span><span class="sxs-lookup"><span data-stu-id="5119a-126">Element</span></span>|<span data-ttu-id="5119a-127">描述</span><span class="sxs-lookup"><span data-stu-id="5119a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5119a-128">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5119a-128">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="5119a-129">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="5119a-129">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5119a-130">備註</span><span class="sxs-lookup"><span data-stu-id="5119a-130">Remarks</span></span>  
 <span data-ttu-id="5119a-131">如需已知類型的詳細資訊， <xref:System.Runtime.Serialization.DataContractSerializer>請參閱和[資料合約已知類型](../../../wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5119a-131">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5119a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5119a-132">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="5119a-133">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="5119a-133">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
