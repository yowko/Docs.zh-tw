---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 7e440810fee1dddb7025d1385b1edb4838d98a39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925916"
---
# <a name="datacontractserializer"></a><span data-ttu-id="1ca41-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="1ca41-101">\<dataContractSerializer></span></span>
<span data-ttu-id="1ca41-102">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="1ca41-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="1ca41-103">這個項目會出現在兩個不同的階層架構中。</span><span class="sxs-lookup"><span data-stu-id="1ca41-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="1ca41-104">其中一個列於接下來的＜結構描述階層架構＞一節，另一個則列於＜備註＞一節中。</span><span class="sxs-lookup"><span data-stu-id="1ca41-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="1ca41-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1ca41-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ca41-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1ca41-106">\<behaviors></span></span>  
<span data-ttu-id="1ca41-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1ca41-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="1ca41-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1ca41-108">\<behavior></span></span>  
<span data-ttu-id="1ca41-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="1ca41-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca41-110">語法</span><span class="sxs-lookup"><span data-stu-id="1ca41-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ca41-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1ca41-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1ca41-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1ca41-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ca41-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1ca41-113">Attributes</span></span>  
  
|<span data-ttu-id="1ca41-114">項目</span><span class="sxs-lookup"><span data-stu-id="1ca41-114">Element</span></span>|<span data-ttu-id="1ca41-115">描述</span><span class="sxs-lookup"><span data-stu-id="1ca41-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ca41-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="1ca41-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="1ca41-117">布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="1ca41-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="1ca41-118">此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。</span><span class="sxs-lookup"><span data-stu-id="1ca41-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="1ca41-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="1ca41-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="1ca41-120">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="1ca41-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="1ca41-121">此屬性為 65536。</span><span class="sxs-lookup"><span data-stu-id="1ca41-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ca41-122">子元素</span><span class="sxs-lookup"><span data-stu-id="1ca41-122">Child Elements</span></span>  
 <span data-ttu-id="1ca41-123">無。</span><span class="sxs-lookup"><span data-stu-id="1ca41-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ca41-124">父項目</span><span class="sxs-lookup"><span data-stu-id="1ca41-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1ca41-125">項目</span><span class="sxs-lookup"><span data-stu-id="1ca41-125">Element</span></span>|<span data-ttu-id="1ca41-126">說明</span><span class="sxs-lookup"><span data-stu-id="1ca41-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ca41-127">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1ca41-127">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="1ca41-128">服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="1ca41-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="1ca41-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="1ca41-129">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="1ca41-130">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="1ca41-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ca41-131">備註</span><span class="sxs-lookup"><span data-stu-id="1ca41-131">Remarks</span></span>  
 <span data-ttu-id="1ca41-132">如本主題簡介中所述, 這是發生\<X509Extension > 元素的第二個階層。</span><span class="sxs-lookup"><span data-stu-id="1ca41-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="1ca41-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="1ca41-133">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="1ca41-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="1ca41-134">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="1ca41-135">如需有關已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="1ca41-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca41-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ca41-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="1ca41-137">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="1ca41-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="1ca41-138">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="1ca41-138">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
