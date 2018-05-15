---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 422de17f4c1b42579eadc16c7ec1a0037903d1a9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="8b5ab-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="8b5ab-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="8b5ab-103">代表組態項目的集合，這些項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="8b5ab-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="8b5ab-104">這可以用來加入自訂 WAS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="8b5ab-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="8b5ab-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8b5ab-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="8b5ab-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="8b5ab-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="8b5ab-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="8b5ab-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5ab-108">語法</span><span class="sxs-lookup"><span data-stu-id="8b5ab-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b5ab-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8b5ab-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8b5ab-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8b5ab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b5ab-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8b5ab-111">Attributes</span></span>  
  
|<span data-ttu-id="8b5ab-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8b5ab-112">Attribute</span></span>|<span data-ttu-id="8b5ab-113">描述</span><span class="sxs-lookup"><span data-stu-id="8b5ab-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b5ab-114">name</span><span class="sxs-lookup"><span data-stu-id="8b5ab-114">name</span></span>|<span data-ttu-id="8b5ab-115">傳輸的名稱</span><span class="sxs-lookup"><span data-stu-id="8b5ab-115">The name of the transport</span></span>|  
|<span data-ttu-id="8b5ab-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="8b5ab-116">transportConfigurationType</span></span>|<span data-ttu-id="8b5ab-117">實作傳輸的型別</span><span class="sxs-lookup"><span data-stu-id="8b5ab-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b5ab-118">子項目</span><span class="sxs-lookup"><span data-stu-id="8b5ab-118">Child Elements</span></span>  
  
|<span data-ttu-id="8b5ab-119">項目</span><span class="sxs-lookup"><span data-stu-id="8b5ab-119">Element</span></span>|<span data-ttu-id="8b5ab-120">描述</span><span class="sxs-lookup"><span data-stu-id="8b5ab-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b5ab-121">\<add></span><span class="sxs-lookup"><span data-stu-id="8b5ab-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="8b5ab-122">新增組態項目，此項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="8b5ab-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b5ab-123">父項目</span><span class="sxs-lookup"><span data-stu-id="8b5ab-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8b5ab-124">項目</span><span class="sxs-lookup"><span data-stu-id="8b5ab-124">Element</span></span>|<span data-ttu-id="8b5ab-125">描述</span><span class="sxs-lookup"><span data-stu-id="8b5ab-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b5ab-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="8b5ab-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="8b5ab-127">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="8b5ab-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b5ab-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b5ab-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="8b5ab-129">裝載</span><span class="sxs-lookup"><span data-stu-id="8b5ab-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
