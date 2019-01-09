---
title: '&lt;system.runtime.serialization&gt; 的 &lt;dataContractSerializer&gt;'
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: f31dd8479f3bd6b36915b3ff00ff53babe3c0248
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150171"
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="53ab4-102">&lt;system.runtime.serialization&gt; 的 &lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="53ab4-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="53ab4-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="53ab4-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="53ab4-104">\<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="53ab4-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="53ab4-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="53ab4-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ab4-106">語法</span><span class="sxs-lookup"><span data-stu-id="53ab4-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53ab4-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="53ab4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="53ab4-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="53ab4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53ab4-109">屬性</span><span class="sxs-lookup"><span data-stu-id="53ab4-109">Attributes</span></span>  
  
|<span data-ttu-id="53ab4-110">元素</span><span class="sxs-lookup"><span data-stu-id="53ab4-110">Element</span></span>|<span data-ttu-id="53ab4-111">描述</span><span class="sxs-lookup"><span data-stu-id="53ab4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53ab4-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="53ab4-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="53ab4-113">布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="53ab4-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="53ab4-114">此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。</span><span class="sxs-lookup"><span data-stu-id="53ab4-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="53ab4-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="53ab4-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="53ab4-116">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="53ab4-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="53ab4-117">此屬性為 65536。</span><span class="sxs-lookup"><span data-stu-id="53ab4-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53ab4-118">子元素</span><span class="sxs-lookup"><span data-stu-id="53ab4-118">Child Elements</span></span>  
  
|<span data-ttu-id="53ab4-119">項目</span><span class="sxs-lookup"><span data-stu-id="53ab4-119">Element</span></span>|<span data-ttu-id="53ab4-120">描述</span><span class="sxs-lookup"><span data-stu-id="53ab4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53ab4-121">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="53ab4-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="53ab4-122">包含還原序列化時，<xref:System.Runtime.Serialization.DataContractSerializer> 使用的已知型別。</span><span class="sxs-lookup"><span data-stu-id="53ab4-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="53ab4-123">如需資料合約和已知型別的詳細資訊，請參閱 < [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="53ab4-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53ab4-124">父項目</span><span class="sxs-lookup"><span data-stu-id="53ab4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="53ab4-125">項目</span><span class="sxs-lookup"><span data-stu-id="53ab4-125">Element</span></span>|<span data-ttu-id="53ab4-126">描述</span><span class="sxs-lookup"><span data-stu-id="53ab4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53ab4-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="53ab4-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="53ab4-128">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="53ab4-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53ab4-129">備註</span><span class="sxs-lookup"><span data-stu-id="53ab4-129">Remarks</span></span>  
 <span data-ttu-id="53ab4-130">如需已知型別的詳細資訊，請參閱<xref:System.Runtime.Serialization.DataContractSerializer>並[Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="53ab4-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ab4-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53ab4-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="53ab4-132">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="53ab4-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
