---
title: "&lt;serviceBehaviors&gt; 的 &lt;behavior&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b86d685cd3b5fc26f2df2d3e722a908c04422d50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt"></a><span data-ttu-id="0a216-102">&lt;serviceBehaviors&gt; 的 &lt;behavior&gt;</span><span class="sxs-lookup"><span data-stu-id="0a216-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt;</span></span>
<span data-ttu-id="0a216-103">`behavior` 項目包含服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="0a216-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="0a216-104">各個行為是依其 `name` 進行索引。</span><span class="sxs-lookup"><span data-stu-id="0a216-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="0a216-105">服務可以連結至每個行為，透過使用此名稱`behaviorConfiguration`屬性[\<端點 >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="0a216-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="0a216-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="0a216-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="0a216-107">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="0a216-107">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0a216-108">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0a216-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a216-109">行為項目的特定 Windows 工作流程活動，例如[ \<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)項目，會記載於[\<行為 > 的\<serviceBehaviors >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)頁面。</span><span class="sxs-lookup"><span data-stu-id="0a216-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
 <span data-ttu-id="0a216-110">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0a216-110">\<system.ServiceModel></span></span>  
<span data-ttu-id="0a216-111">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="0a216-111">\<behaviors></span></span>  
<span data-ttu-id="0a216-112">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0a216-112">\<serviceBehaviors></span></span>  
<span data-ttu-id="0a216-113">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="0a216-113">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a216-114">語法</span><span class="sxs-lookup"><span data-stu-id="0a216-114">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
       <behavior name="String" />  
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a216-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0a216-115">Attributes and Elements</span></span>  
 <span data-ttu-id="0a216-116">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0a216-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a216-117">屬性</span><span class="sxs-lookup"><span data-stu-id="0a216-117">Attributes</span></span>  
  
|<span data-ttu-id="0a216-118">屬性</span><span class="sxs-lookup"><span data-stu-id="0a216-118">Attribute</span></span>|<span data-ttu-id="0a216-119">描述</span><span class="sxs-lookup"><span data-stu-id="0a216-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a216-120">name</span><span class="sxs-lookup"><span data-stu-id="0a216-120">name</span></span>|<span data-ttu-id="0a216-121">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="0a216-121">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="0a216-122">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="0a216-122">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="0a216-123">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="0a216-123">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0a216-124">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0a216-124">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a216-125">子元素</span><span class="sxs-lookup"><span data-stu-id="0a216-125">Child Elements</span></span>  
  
|<span data-ttu-id="0a216-126">項目</span><span class="sxs-lookup"><span data-stu-id="0a216-126">Element</span></span>|<span data-ttu-id="0a216-127">描述</span><span class="sxs-lookup"><span data-stu-id="0a216-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a216-128">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="0a216-128">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|<span data-ttu-id="0a216-129">包含 DataContractSerializer 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="0a216-129">Contains configuration data for the DataContractSerializer.</span></span>|  
|[<span data-ttu-id="0a216-130">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="0a216-130">\<persistenceProvider></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|<span data-ttu-id="0a216-131">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="0a216-131">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[<span data-ttu-id="0a216-132">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="0a216-132">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="0a216-133">提供於執行階段存取路由服務的功能，可用來動態修改路由組態。</span><span class="sxs-lookup"><span data-stu-id="0a216-133">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[<span data-ttu-id="0a216-134">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="0a216-134">\<serviceAuthenticationManager></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|<span data-ttu-id="0a216-135">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="0a216-135">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[<span data-ttu-id="0a216-136">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="0a216-136">\<serviceAuthorization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|<span data-ttu-id="0a216-137">指定將存取權授權給服務作業的設定。</span><span class="sxs-lookup"><span data-stu-id="0a216-137">Specifies settings that authorize access to service operations.</span></span>|  
|[<span data-ttu-id="0a216-138">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="0a216-138">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="0a216-139">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="0a216-139">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[<span data-ttu-id="0a216-140">\<serviceDebug ></span><span class="sxs-lookup"><span data-stu-id="0a216-140">\<serviceDebug></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|<span data-ttu-id="0a216-141">指定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務的偵錯和說明資訊功能。</span><span class="sxs-lookup"><span data-stu-id="0a216-141">Specifies debugging and help information features for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
|[<span data-ttu-id="0a216-142">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="0a216-142">\<serviceDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|<span data-ttu-id="0a216-143">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="0a216-143">Specifies the discoverability of service endpoints.</span></span>|  
|[<span data-ttu-id="0a216-144">\<serviceMetadata ></span><span class="sxs-lookup"><span data-stu-id="0a216-144">\<serviceMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|<span data-ttu-id="0a216-145">指定服務中繼資料和相關資訊的發行。</span><span class="sxs-lookup"><span data-stu-id="0a216-145">Specifies the publication of service metadata and associated information.</span></span>|  
|[<span data-ttu-id="0a216-146">\<serviceSecurityAudit ></span><span class="sxs-lookup"><span data-stu-id="0a216-146">\<serviceSecurityAudit></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|<span data-ttu-id="0a216-147">指定在服務作業期間啟用安全性事件稽核的設定。</span><span class="sxs-lookup"><span data-stu-id="0a216-147">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[<span data-ttu-id="0a216-148">\<serviceThrottling ></span><span class="sxs-lookup"><span data-stu-id="0a216-148">\<serviceThrottling></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|<span data-ttu-id="0a216-149">指定 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務的節流機制。</span><span class="sxs-lookup"><span data-stu-id="0a216-149">Specifies the throttling mechanism of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span>|  
|[<span data-ttu-id="0a216-150">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="0a216-150">\<serviceTimeouts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|<span data-ttu-id="0a216-151">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="0a216-151">Specifies the timeout for a service.</span></span>|  
|[<span data-ttu-id="0a216-152">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="0a216-152">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="0a216-153">指定裝載工作流程架構的 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務時 WorkflowRuntime 之執行個體的設定。</span><span class="sxs-lookup"><span data-stu-id="0a216-153">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services.</span></span>|  
|[<span data-ttu-id="0a216-154">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="0a216-154">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="0a216-155">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="0a216-155">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a216-156">父項目</span><span class="sxs-lookup"><span data-stu-id="0a216-156">Parent Elements</span></span>  
  
|<span data-ttu-id="0a216-157">項目</span><span class="sxs-lookup"><span data-stu-id="0a216-157">Element</span></span>|<span data-ttu-id="0a216-158">描述</span><span class="sxs-lookup"><span data-stu-id="0a216-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a216-159">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0a216-159">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="0a216-160">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="0a216-160">A collection of service behavior elements.</span></span>|
