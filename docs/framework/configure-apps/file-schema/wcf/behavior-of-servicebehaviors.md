---
title: <behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 8c847368934cc4cd8ccaab017ede00b7b8963897
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926409"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="1d906-102">\<serviceBehaviors > 的\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1d906-102">\<behavior> of \<serviceBehaviors></span></span>
<span data-ttu-id="1d906-103">`behavior` 項目包含服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="1d906-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="1d906-104">各個行為是依其 `name` 進行索引。</span><span class="sxs-lookup"><span data-stu-id="1d906-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="1d906-105">服務可以使用`behaviorConfiguration` [ \<端點 >](endpoint-element.md)元素的屬性, 透過這個名稱連結至每個行為。</span><span class="sxs-lookup"><span data-stu-id="1d906-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="1d906-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="1d906-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="1d906-107">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="1d906-107">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1d906-108">如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="1d906-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d906-109">Windows 工作流程活動特定的行為專案 (例如[ \<sendMessageChannelCache >](../windows-workflow-foundation/sendmessagechannelcache.md)元素) 記載于[ \< \<serviceBehaviors >](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)頁面的 [行為] >。</span><span class="sxs-lookup"><span data-stu-id="1d906-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
 <span data-ttu-id="1d906-110">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1d906-110">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d906-111">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1d906-111">\<behaviors></span></span>  
<span data-ttu-id="1d906-112">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1d906-112">\<serviceBehaviors></span></span>  
<span data-ttu-id="1d906-113">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1d906-113">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d906-114">語法</span><span class="sxs-lookup"><span data-stu-id="1d906-114">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d906-115">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1d906-115">Attributes and Elements</span></span>  
 <span data-ttu-id="1d906-116">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1d906-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d906-117">屬性</span><span class="sxs-lookup"><span data-stu-id="1d906-117">Attributes</span></span>  
  
|<span data-ttu-id="1d906-118">屬性</span><span class="sxs-lookup"><span data-stu-id="1d906-118">Attribute</span></span>|<span data-ttu-id="1d906-119">描述</span><span class="sxs-lookup"><span data-stu-id="1d906-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d906-120">NAME</span><span class="sxs-lookup"><span data-stu-id="1d906-120">name</span></span>|<span data-ttu-id="1d906-121">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="1d906-121">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="1d906-122">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="1d906-122">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="1d906-123">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="1d906-123">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1d906-124">如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="1d906-124">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d906-125">子元素</span><span class="sxs-lookup"><span data-stu-id="1d906-125">Child Elements</span></span>  
  
|<span data-ttu-id="1d906-126">項目</span><span class="sxs-lookup"><span data-stu-id="1d906-126">Element</span></span>|<span data-ttu-id="1d906-127">描述</span><span class="sxs-lookup"><span data-stu-id="1d906-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d906-128">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="1d906-128">\<dataContractSerializer></span></span>](datacontractserializer-element.md)|<span data-ttu-id="1d906-129">包含 DataContractSerializer 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="1d906-129">Contains configuration data for the DataContractSerializer.</span></span>|  
|[<span data-ttu-id="1d906-130">\<persistenceProvider></span><span class="sxs-lookup"><span data-stu-id="1d906-130">\<persistenceProvider></span></span>](persistenceprovider.md)|<span data-ttu-id="1d906-131">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="1d906-131">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[<span data-ttu-id="1d906-132">\<routing></span><span class="sxs-lookup"><span data-stu-id="1d906-132">\<routing></span></span>](routing-of-servicebehavior.md)|<span data-ttu-id="1d906-133">提供於執行階段存取路由服務的功能，可用來動態修改路由組態。</span><span class="sxs-lookup"><span data-stu-id="1d906-133">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[<span data-ttu-id="1d906-134">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="1d906-134">\<serviceAuthenticationManager></span></span>](serviceauthenticationmanager.md)|<span data-ttu-id="1d906-135">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="1d906-135">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[<span data-ttu-id="1d906-136">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="1d906-136">\<serviceAuthorization></span></span>](serviceauthorization-element.md)|<span data-ttu-id="1d906-137">指定將存取權授權給服務作業的設定。</span><span class="sxs-lookup"><span data-stu-id="1d906-137">Specifies settings that authorize access to service operations.</span></span>|  
|[<span data-ttu-id="1d906-138">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1d906-138">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="1d906-139">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="1d906-139">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[<span data-ttu-id="1d906-140">\<serviceDebug></span><span class="sxs-lookup"><span data-stu-id="1d906-140">\<serviceDebug></span></span>](servicedebug.md)|<span data-ttu-id="1d906-141">指定 Windows Communication Foundation (WCF) 服務的偵錯工具和說明資訊功能。</span><span class="sxs-lookup"><span data-stu-id="1d906-141">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[<span data-ttu-id="1d906-142">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="1d906-142">\<serviceDiscovery></span></span>](servicediscovery.md)|<span data-ttu-id="1d906-143">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="1d906-143">Specifies the discoverability of service endpoints.</span></span>|  
|[<span data-ttu-id="1d906-144">\<serviceMetadata></span><span class="sxs-lookup"><span data-stu-id="1d906-144">\<serviceMetadata></span></span>](servicemetadata.md)|<span data-ttu-id="1d906-145">指定服務中繼資料和相關資訊的發行。</span><span class="sxs-lookup"><span data-stu-id="1d906-145">Specifies the publication of service metadata and associated information.</span></span>|  
|[<span data-ttu-id="1d906-146">\<serviceSecurityAudit></span><span class="sxs-lookup"><span data-stu-id="1d906-146">\<serviceSecurityAudit></span></span>](servicesecurityaudit.md)|<span data-ttu-id="1d906-147">指定在服務作業期間啟用安全性事件稽核的設定。</span><span class="sxs-lookup"><span data-stu-id="1d906-147">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[<span data-ttu-id="1d906-148">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="1d906-148">\<serviceThrottling></span></span>](servicethrottling.md)|<span data-ttu-id="1d906-149">指定 WCF 服務的節流機制。</span><span class="sxs-lookup"><span data-stu-id="1d906-149">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[<span data-ttu-id="1d906-150">\<serviceTimeouts></span><span class="sxs-lookup"><span data-stu-id="1d906-150">\<serviceTimeouts></span></span>](servicetimeouts.md)|<span data-ttu-id="1d906-151">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="1d906-151">Specifies the timeout for a service.</span></span>|  
|[<span data-ttu-id="1d906-152">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="1d906-152">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="1d906-153">指定用來裝載以工作流程為基礎之 WCF 服務的 WorkflowRuntime 實例設定。</span><span class="sxs-lookup"><span data-stu-id="1d906-153">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[<span data-ttu-id="1d906-154">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="1d906-154">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="1d906-155">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="1d906-155">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d906-156">父項目</span><span class="sxs-lookup"><span data-stu-id="1d906-156">Parent Elements</span></span>  
  
|<span data-ttu-id="1d906-157">項目</span><span class="sxs-lookup"><span data-stu-id="1d906-157">Element</span></span>|<span data-ttu-id="1d906-158">描述</span><span class="sxs-lookup"><span data-stu-id="1d906-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d906-159">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1d906-159">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="1d906-160">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="1d906-160">A collection of service behavior elements.</span></span>|
