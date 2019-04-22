---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8ba16d9cc30b07d3e6b0924e6013ec01443867d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139044"
---
# <a name="datacontractserializer"></a><span data-ttu-id="29a1e-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="29a1e-102">dataContractSerializer</span></span>
<span data-ttu-id="29a1e-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="29a1e-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="29a1e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="29a1e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="29a1e-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="29a1e-105">\<behaviors></span></span>  
<span data-ttu-id="29a1e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="29a1e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="29a1e-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="29a1e-107">\<behavior></span></span>  
<span data-ttu-id="29a1e-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="29a1e-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a1e-109">語法</span><span class="sxs-lookup"><span data-stu-id="29a1e-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29a1e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="29a1e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="29a1e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="29a1e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29a1e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="29a1e-112">Attributes</span></span>  
  
|<span data-ttu-id="29a1e-113">項目</span><span class="sxs-lookup"><span data-stu-id="29a1e-113">Element</span></span>|<span data-ttu-id="29a1e-114">描述</span><span class="sxs-lookup"><span data-stu-id="29a1e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29a1e-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="29a1e-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="29a1e-116">布林值，指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="29a1e-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="29a1e-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="29a1e-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="29a1e-118">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="29a1e-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29a1e-119">子元素</span><span class="sxs-lookup"><span data-stu-id="29a1e-119">Child Elements</span></span>  
 <span data-ttu-id="29a1e-120">無。</span><span class="sxs-lookup"><span data-stu-id="29a1e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29a1e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="29a1e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="29a1e-122">項目</span><span class="sxs-lookup"><span data-stu-id="29a1e-122">Element</span></span>|<span data-ttu-id="29a1e-123">描述</span><span class="sxs-lookup"><span data-stu-id="29a1e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29a1e-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="29a1e-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="29a1e-125">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="29a1e-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29a1e-126">備註</span><span class="sxs-lookup"><span data-stu-id="29a1e-126">Remarks</span></span>  
 <span data-ttu-id="29a1e-127">如需已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer> 文件。</span><span class="sxs-lookup"><span data-stu-id="29a1e-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="29a1e-128">`<dataContractSerializer>` 行為項目 (如果有的話) 必須永遠出現在組態檔中 `<enableWebScript>` 行為項目之前。</span><span class="sxs-lookup"><span data-stu-id="29a1e-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="29a1e-129">否則，產生的行為未定義。</span><span class="sxs-lookup"><span data-stu-id="29a1e-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a1e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29a1e-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="29a1e-131">資料合約已知類型</span><span class="sxs-lookup"><span data-stu-id="29a1e-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="29a1e-132">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="29a1e-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
