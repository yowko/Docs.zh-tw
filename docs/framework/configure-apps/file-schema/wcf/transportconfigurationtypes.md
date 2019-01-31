---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 560da96c50e99461d25c1fd65def2dc10c284470
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261663"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="f86db-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="f86db-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="f86db-102">代表組態項目的集合，這些項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="f86db-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="f86db-103">這可以用來加入自訂 WAS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f86db-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="f86db-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f86db-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f86db-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="f86db-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="f86db-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="f86db-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86db-107">語法</span><span class="sxs-lookup"><span data-stu-id="f86db-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f86db-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f86db-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f86db-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f86db-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f86db-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f86db-110">Attributes</span></span>  
  
|<span data-ttu-id="f86db-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f86db-111">Attribute</span></span>|<span data-ttu-id="f86db-112">描述</span><span class="sxs-lookup"><span data-stu-id="f86db-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f86db-113">name</span><span class="sxs-lookup"><span data-stu-id="f86db-113">name</span></span>|<span data-ttu-id="f86db-114">傳輸的名稱</span><span class="sxs-lookup"><span data-stu-id="f86db-114">The name of the transport</span></span>|  
|<span data-ttu-id="f86db-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="f86db-115">transportConfigurationType</span></span>|<span data-ttu-id="f86db-116">實作傳輸的型別</span><span class="sxs-lookup"><span data-stu-id="f86db-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f86db-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f86db-117">Child Elements</span></span>  
  
|<span data-ttu-id="f86db-118">項目</span><span class="sxs-lookup"><span data-stu-id="f86db-118">Element</span></span>|<span data-ttu-id="f86db-119">描述</span><span class="sxs-lookup"><span data-stu-id="f86db-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f86db-120">\<add></span><span class="sxs-lookup"><span data-stu-id="f86db-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="f86db-121">新增組態項目，此項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="f86db-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f86db-122">父項目</span><span class="sxs-lookup"><span data-stu-id="f86db-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f86db-123">項目</span><span class="sxs-lookup"><span data-stu-id="f86db-123">Element</span></span>|<span data-ttu-id="f86db-124">描述</span><span class="sxs-lookup"><span data-stu-id="f86db-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f86db-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="f86db-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="f86db-126">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="f86db-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f86db-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f86db-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="f86db-128">裝載</span><span class="sxs-lookup"><span data-stu-id="f86db-128">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
