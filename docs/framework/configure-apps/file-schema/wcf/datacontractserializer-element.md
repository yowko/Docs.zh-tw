---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: e24dae47171f741af064ca2eaa822928690acf6e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400444"
---
# \<dataContractSerializer>
<span data-ttu-id="bdb83-101">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="bdb83-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="bdb83-102">這個項目會出現在兩個不同的階層架構中。</span><span class="sxs-lookup"><span data-stu-id="bdb83-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="bdb83-103">其中一個列於接下來的＜結構描述階層架構＞一節，另一個則列於＜備註＞一節中。</span><span class="sxs-lookup"><span data-stu-id="bdb83-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="bdb83-104">語法</span><span class="sxs-lookup"><span data-stu-id="bdb83-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdb83-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bdb83-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bdb83-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bdb83-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdb83-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bdb83-107">Attributes</span></span>  
  
|<span data-ttu-id="bdb83-108">元素</span><span class="sxs-lookup"><span data-stu-id="bdb83-108">Element</span></span>|<span data-ttu-id="bdb83-109">描述</span><span class="sxs-lookup"><span data-stu-id="bdb83-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bdb83-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="bdb83-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="bdb83-111">布林值，該值會指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="bdb83-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="bdb83-112">此屬性只能在 `<dataContractSerializer>` 項目下的 `<behavior>` 設定。</span><span class="sxs-lookup"><span data-stu-id="bdb83-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="bdb83-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="bdb83-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="bdb83-114">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="bdb83-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="bdb83-115">此屬性為 65536。</span><span class="sxs-lookup"><span data-stu-id="bdb83-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdb83-116">子元素</span><span class="sxs-lookup"><span data-stu-id="bdb83-116">Child Elements</span></span>  
 <span data-ttu-id="bdb83-117">無。</span><span class="sxs-lookup"><span data-stu-id="bdb83-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdb83-118">父項目</span><span class="sxs-lookup"><span data-stu-id="bdb83-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bdb83-119">元素</span><span class="sxs-lookup"><span data-stu-id="bdb83-119">Element</span></span>|<span data-ttu-id="bdb83-120">描述</span><span class="sxs-lookup"><span data-stu-id="bdb83-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="bdb83-121">服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="bdb83-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="bdb83-122">代表 <xref:System.Runtime.Serialization> 命名空間區段的根項目，而且包含用來設定 <xref:System.Runtime.Serialization.DataContractSerializer> 選項的項目。</span><span class="sxs-lookup"><span data-stu-id="bdb83-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdb83-123">備註</span><span class="sxs-lookup"><span data-stu-id="bdb83-123">Remarks</span></span>  
 <span data-ttu-id="bdb83-124">如本主題簡介中所述，這是專案發生所在的第二個階層 \<X509Extension> 。</span><span class="sxs-lookup"><span data-stu-id="bdb83-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="bdb83-125">如需有關已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer>。</span><span class="sxs-lookup"><span data-stu-id="bdb83-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb83-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdb83-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="bdb83-127">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="bdb83-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="bdb83-128">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="bdb83-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
