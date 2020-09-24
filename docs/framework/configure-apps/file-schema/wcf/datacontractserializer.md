---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 0e4cbc50c25d4fa1f67f283f2b52d4b174428cd3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153920"
---
# <a name="datacontractserializer"></a><span data-ttu-id="58be7-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="58be7-102">dataContractSerializer</span></span>

<span data-ttu-id="58be7-103">包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="58be7-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="58be7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="58be7-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58be7-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="58be7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="58be7-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="58be7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58be7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="58be7-107">Attributes</span></span>  
  
|<span data-ttu-id="58be7-108">項目</span><span class="sxs-lookup"><span data-stu-id="58be7-108">Element</span></span>|<span data-ttu-id="58be7-109">描述</span><span class="sxs-lookup"><span data-stu-id="58be7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58be7-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="58be7-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="58be7-111">布林值，指定當端點序列化或還原序列化時，是否略過端點所提供的資料。</span><span class="sxs-lookup"><span data-stu-id="58be7-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="58be7-112">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="58be7-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="58be7-113">整數，指定要序列化或還原序列化的項目數上限。</span><span class="sxs-lookup"><span data-stu-id="58be7-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58be7-114">子元素</span><span class="sxs-lookup"><span data-stu-id="58be7-114">Child Elements</span></span>  

 <span data-ttu-id="58be7-115">無。</span><span class="sxs-lookup"><span data-stu-id="58be7-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58be7-116">父項目</span><span class="sxs-lookup"><span data-stu-id="58be7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="58be7-117">項目</span><span class="sxs-lookup"><span data-stu-id="58be7-117">Element</span></span>|<span data-ttu-id="58be7-118">描述</span><span class="sxs-lookup"><span data-stu-id="58be7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="58be7-119">指定端點行為。</span><span class="sxs-lookup"><span data-stu-id="58be7-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58be7-120">備註</span><span class="sxs-lookup"><span data-stu-id="58be7-120">Remarks</span></span>  

 <span data-ttu-id="58be7-121">如需已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer> 文件。</span><span class="sxs-lookup"><span data-stu-id="58be7-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="58be7-122">`<dataContractSerializer>` 行為項目 (如果有的話) 必須永遠出現在組態檔中 `<enableWebScript>` 行為項目之前。</span><span class="sxs-lookup"><span data-stu-id="58be7-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="58be7-123">否則，產生的行為未定義。</span><span class="sxs-lookup"><span data-stu-id="58be7-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58be7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58be7-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="58be7-125">資料合約已知型別</span><span class="sxs-lookup"><span data-stu-id="58be7-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="58be7-126">資料傳輸與序列化</span><span class="sxs-lookup"><span data-stu-id="58be7-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
