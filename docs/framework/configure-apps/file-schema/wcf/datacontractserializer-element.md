---
title: '&lt;DataContractSerializer&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: c79c8e8db2a4ea4526000bcbe336d1e664f9c4c2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150951"
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="3eb7b-102">&lt;DataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="3eb7b-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="3eb7b-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="3eb7b-104">這個項目會出現在兩個不同的階層架構中。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="3eb7b-105">其中一個列於接下來的＜結構描述階層架構＞一節，另一個則列於＜備註＞一節中。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="3eb7b-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3eb7b-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="3eb7b-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3eb7b-107">\<behaviors></span></span>  
<span data-ttu-id="3eb7b-108">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3eb7b-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="3eb7b-109">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3eb7b-109">\<behavior></span></span>  
<span data-ttu-id="3eb7b-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3eb7b-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb7b-111">語法</span><span class="sxs-lookup"><span data-stu-id="3eb7b-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eb7b-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3eb7b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3eb7b-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eb7b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="3eb7b-114">Attributes</span></span>  
  
|<span data-ttu-id="3eb7b-115">元素</span><span class="sxs-lookup"><span data-stu-id="3eb7b-115">Element</span></span>|<span data-ttu-id="3eb7b-116">描述</span><span class="sxs-lookup"><span data-stu-id="3eb7b-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3eb7b-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="3eb7b-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="3eb7b-118">布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="3eb7b-119">此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="3eb7b-120">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="3eb7b-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="3eb7b-121">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="3eb7b-122">此屬性為 65536。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3eb7b-123">子元素</span><span class="sxs-lookup"><span data-stu-id="3eb7b-123">Child Elements</span></span>  
 <span data-ttu-id="3eb7b-124">無。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3eb7b-125">父項目</span><span class="sxs-lookup"><span data-stu-id="3eb7b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3eb7b-126">項目</span><span class="sxs-lookup"><span data-stu-id="3eb7b-126">Element</span></span>|<span data-ttu-id="3eb7b-127">描述</span><span class="sxs-lookup"><span data-stu-id="3eb7b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eb7b-128">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3eb7b-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="3eb7b-129">服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="3eb7b-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="3eb7b-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="3eb7b-131">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eb7b-132">備註</span><span class="sxs-lookup"><span data-stu-id="3eb7b-132">Remarks</span></span>  
 <span data-ttu-id="3eb7b-133">本主題簡介所述，這會是第二個階層，在其中\<X509Extension > 項目，就會發生。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="3eb7b-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="3eb7b-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="3eb7b-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="3eb7b-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="3eb7b-136">如需有關已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="3eb7b-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb7b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3eb7b-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="3eb7b-138">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="3eb7b-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="3eb7b-139">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="3eb7b-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
