---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: b3683a198ec403fb9966bb902c936108fd043bfa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083639"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="fa3ee-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="fa3ee-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="fa3ee-102">代表組態項目的集合，這些項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="fa3ee-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="fa3ee-103">這可以用來加入自訂 WAS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="fa3ee-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="fa3ee-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fa3ee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa3ee-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="fa3ee-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="fa3ee-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="fa3ee-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa3ee-107">語法</span><span class="sxs-lookup"><span data-stu-id="fa3ee-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa3ee-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fa3ee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fa3ee-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fa3ee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa3ee-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fa3ee-110">Attributes</span></span>  
  
|<span data-ttu-id="fa3ee-111">屬性</span><span class="sxs-lookup"><span data-stu-id="fa3ee-111">Attribute</span></span>|<span data-ttu-id="fa3ee-112">描述</span><span class="sxs-lookup"><span data-stu-id="fa3ee-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa3ee-113">名稱</span><span class="sxs-lookup"><span data-stu-id="fa3ee-113">name</span></span>|<span data-ttu-id="fa3ee-114">傳輸的名稱</span><span class="sxs-lookup"><span data-stu-id="fa3ee-114">The name of the transport</span></span>|  
|<span data-ttu-id="fa3ee-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="fa3ee-115">transportConfigurationType</span></span>|<span data-ttu-id="fa3ee-116">實作傳輸的型別</span><span class="sxs-lookup"><span data-stu-id="fa3ee-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa3ee-117">子元素</span><span class="sxs-lookup"><span data-stu-id="fa3ee-117">Child Elements</span></span>  
  
|<span data-ttu-id="fa3ee-118">項目</span><span class="sxs-lookup"><span data-stu-id="fa3ee-118">Element</span></span>|<span data-ttu-id="fa3ee-119">描述</span><span class="sxs-lookup"><span data-stu-id="fa3ee-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa3ee-120">\<add></span><span class="sxs-lookup"><span data-stu-id="fa3ee-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="fa3ee-121">新增組態項目，此項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="fa3ee-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa3ee-122">父項目</span><span class="sxs-lookup"><span data-stu-id="fa3ee-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fa3ee-123">項目</span><span class="sxs-lookup"><span data-stu-id="fa3ee-123">Element</span></span>|<span data-ttu-id="fa3ee-124">描述</span><span class="sxs-lookup"><span data-stu-id="fa3ee-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa3ee-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="fa3ee-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="fa3ee-126">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="fa3ee-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa3ee-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa3ee-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="fa3ee-128">裝載</span><span class="sxs-lookup"><span data-stu-id="fa3ee-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
