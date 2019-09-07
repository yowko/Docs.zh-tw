---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400438"
---
# <a name="datacontractserializer"></a><span data-ttu-id="7ba40-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="7ba40-102">dataContractSerializer</span></span>
<span data-ttu-id="7ba40-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="7ba40-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="7ba40-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7ba40-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7ba40-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7ba40-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7ba40-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7ba40-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="7ba40-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7ba40-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="7ba40-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7ba40-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="7ba40-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dataContractSerializer >**</span><span class="sxs-lookup"><span data-stu-id="7ba40-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ba40-110">語法</span><span class="sxs-lookup"><span data-stu-id="7ba40-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ba40-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7ba40-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7ba40-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7ba40-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ba40-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7ba40-113">Attributes</span></span>  
  
|<span data-ttu-id="7ba40-114">項目</span><span class="sxs-lookup"><span data-stu-id="7ba40-114">Element</span></span>|<span data-ttu-id="7ba40-115">說明</span><span class="sxs-lookup"><span data-stu-id="7ba40-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ba40-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="7ba40-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="7ba40-117">布林值，指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="7ba40-117">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="7ba40-118">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="7ba40-118">maxItemsInObjectGraph</span></span>|<span data-ttu-id="7ba40-119">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="7ba40-119">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ba40-120">子元素</span><span class="sxs-lookup"><span data-stu-id="7ba40-120">Child Elements</span></span>  
 <span data-ttu-id="7ba40-121">無。</span><span class="sxs-lookup"><span data-stu-id="7ba40-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ba40-122">父項目</span><span class="sxs-lookup"><span data-stu-id="7ba40-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7ba40-123">項目</span><span class="sxs-lookup"><span data-stu-id="7ba40-123">Element</span></span>|<span data-ttu-id="7ba40-124">說明</span><span class="sxs-lookup"><span data-stu-id="7ba40-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ba40-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7ba40-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7ba40-126">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="7ba40-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ba40-127">備註</span><span class="sxs-lookup"><span data-stu-id="7ba40-127">Remarks</span></span>  
 <span data-ttu-id="7ba40-128">如需已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer> 文件。</span><span class="sxs-lookup"><span data-stu-id="7ba40-128">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7ba40-129">`<dataContractSerializer>` 行為項目 (如果有的話) 必須永遠出現在組態檔中 `<enableWebScript>` 行為項目之前。</span><span class="sxs-lookup"><span data-stu-id="7ba40-129">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="7ba40-130">否則，產生的行為未定義。</span><span class="sxs-lookup"><span data-stu-id="7ba40-130">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba40-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ba40-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="7ba40-132">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="7ba40-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="7ba40-133">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="7ba40-133">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
