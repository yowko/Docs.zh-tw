---
title: '&lt;transportConfigurationTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa136f75fda4a87171a8ca3e369e7cb8621ac398
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportconfigurationtypesgt"></a><span data-ttu-id="b425c-102">&lt;transportConfigurationTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="b425c-102">&lt;transportConfigurationTypes&gt;</span></span>
<span data-ttu-id="b425c-103">代表組態項目的集合，這些項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="b425c-103">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="b425c-104">這可以用來加入自訂 WAS 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="b425c-104">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="b425c-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b425c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b425c-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="b425c-106">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="b425c-107">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="b425c-107">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b425c-108">語法</span><span class="sxs-lookup"><span data-stu-id="b425c-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b425c-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b425c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b425c-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b425c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b425c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b425c-111">Attributes</span></span>  
  
|<span data-ttu-id="b425c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b425c-112">Attribute</span></span>|<span data-ttu-id="b425c-113">描述</span><span class="sxs-lookup"><span data-stu-id="b425c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b425c-114">name</span><span class="sxs-lookup"><span data-stu-id="b425c-114">name</span></span>|<span data-ttu-id="b425c-115">傳輸的名稱</span><span class="sxs-lookup"><span data-stu-id="b425c-115">The name of the transport</span></span>|  
|<span data-ttu-id="b425c-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="b425c-116">transportConfigurationType</span></span>|<span data-ttu-id="b425c-117">實作傳輸的型別</span><span class="sxs-lookup"><span data-stu-id="b425c-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b425c-118">子元素</span><span class="sxs-lookup"><span data-stu-id="b425c-118">Child Elements</span></span>  
  
|<span data-ttu-id="b425c-119">項目</span><span class="sxs-lookup"><span data-stu-id="b425c-119">Element</span></span>|<span data-ttu-id="b425c-120">描述</span><span class="sxs-lookup"><span data-stu-id="b425c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b425c-121">\<add></span><span class="sxs-lookup"><span data-stu-id="b425c-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|<span data-ttu-id="b425c-122">新增組態項目，此項目會識別特定傳輸的類型。</span><span class="sxs-lookup"><span data-stu-id="b425c-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b425c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="b425c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b425c-124">項目</span><span class="sxs-lookup"><span data-stu-id="b425c-124">Element</span></span>|<span data-ttu-id="b425c-125">說明</span><span class="sxs-lookup"><span data-stu-id="b425c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b425c-126">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="b425c-126">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="b425c-127">定義服務裝載環境為特定傳輸產生的類型。</span><span class="sxs-lookup"><span data-stu-id="b425c-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b425c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b425c-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [<span data-ttu-id="b425c-129">裝載</span><span class="sxs-lookup"><span data-stu-id="b425c-129">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
