---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: b635f03d1e4a6628a76d678f7366482717276376
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704137"
---
# <a name="datacontractserializer"></a><span data-ttu-id="84351-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="84351-101">\<dataContractSerializer></span></span>
<span data-ttu-id="84351-102">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="84351-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="84351-103">這個項目會出現在兩個不同的階層架構中。</span><span class="sxs-lookup"><span data-stu-id="84351-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="84351-104">其中一個列於接下來的＜結構描述階層架構＞一節，另一個則列於＜備註＞一節中。</span><span class="sxs-lookup"><span data-stu-id="84351-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="84351-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="84351-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="84351-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="84351-106">\<behaviors></span></span>  
<span data-ttu-id="84351-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="84351-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="84351-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="84351-108">\<behavior></span></span>  
<span data-ttu-id="84351-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="84351-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84351-110">語法</span><span class="sxs-lookup"><span data-stu-id="84351-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84351-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="84351-111">Attributes and Elements</span></span>  
 <span data-ttu-id="84351-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="84351-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84351-113">屬性</span><span class="sxs-lookup"><span data-stu-id="84351-113">Attributes</span></span>  
  
|<span data-ttu-id="84351-114">項目</span><span class="sxs-lookup"><span data-stu-id="84351-114">Element</span></span>|<span data-ttu-id="84351-115">描述</span><span class="sxs-lookup"><span data-stu-id="84351-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84351-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="84351-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="84351-117">布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="84351-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="84351-118">此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。</span><span class="sxs-lookup"><span data-stu-id="84351-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="84351-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="84351-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="84351-120">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="84351-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="84351-121">此屬性為 65536。</span><span class="sxs-lookup"><span data-stu-id="84351-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84351-122">子元素</span><span class="sxs-lookup"><span data-stu-id="84351-122">Child Elements</span></span>  
 <span data-ttu-id="84351-123">無。</span><span class="sxs-lookup"><span data-stu-id="84351-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84351-124">父項目</span><span class="sxs-lookup"><span data-stu-id="84351-124">Parent Elements</span></span>  
  
|<span data-ttu-id="84351-125">項目</span><span class="sxs-lookup"><span data-stu-id="84351-125">Element</span></span>|<span data-ttu-id="84351-126">描述</span><span class="sxs-lookup"><span data-stu-id="84351-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84351-127">\<behavior></span><span class="sxs-lookup"><span data-stu-id="84351-127">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="84351-128">服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="84351-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="84351-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="84351-129">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="84351-130">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="84351-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84351-131">備註</span><span class="sxs-lookup"><span data-stu-id="84351-131">Remarks</span></span>  
 <span data-ttu-id="84351-132">本主題簡介所述，這會是第二個階層，在其中\<X509Extension > 項目，就會發生。</span><span class="sxs-lookup"><span data-stu-id="84351-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="84351-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="84351-133">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="84351-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="84351-134">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="84351-135">如需有關已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="84351-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84351-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84351-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="84351-137">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="84351-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="84351-138">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="84351-138">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
