---
title: <behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139728"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="4acf3-102">\<behavior> 的 \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4acf3-102">\<behavior> of \<serviceBehaviors></span></span>
<span data-ttu-id="4acf3-103">`behavior` 項目包含服務行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="4acf3-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="4acf3-104">各個行為是依其 `name` 進行索引。</span><span class="sxs-lookup"><span data-stu-id="4acf3-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="4acf3-105">服務可以使用元素的屬性，透過這個名稱連結至每個行為 `behaviorConfiguration` [\<endpoint>](endpoint-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="4acf3-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="4acf3-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="4acf3-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="4acf3-107">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="4acf3-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4acf3-108">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="4acf3-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4acf3-109">Windows 工作流程活動特有的行為專案（例如專案 [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) ）會記錄在頁面中[ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) 。</span><span class="sxs-lookup"><span data-stu-id="4acf3-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="4acf3-110">語法</span><span class="sxs-lookup"><span data-stu-id="4acf3-110">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4acf3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4acf3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4acf3-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4acf3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4acf3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4acf3-113">Attributes</span></span>  
  
|<span data-ttu-id="4acf3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="4acf3-114">Attribute</span></span>|<span data-ttu-id="4acf3-115">描述</span><span class="sxs-lookup"><span data-stu-id="4acf3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4acf3-116">NAME</span><span class="sxs-lookup"><span data-stu-id="4acf3-116">name</span></span>|<span data-ttu-id="4acf3-117">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="4acf3-117">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="4acf3-118">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="4acf3-118">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="4acf3-119">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="4acf3-119">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4acf3-120">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="4acf3-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4acf3-121">子元素</span><span class="sxs-lookup"><span data-stu-id="4acf3-121">Child Elements</span></span>  
  
|<span data-ttu-id="4acf3-122">元素</span><span class="sxs-lookup"><span data-stu-id="4acf3-122">Element</span></span>|<span data-ttu-id="4acf3-123">描述</span><span class="sxs-lookup"><span data-stu-id="4acf3-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="4acf3-124">包含 DataContractSerializer 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="4acf3-124">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="4acf3-125">指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。</span><span class="sxs-lookup"><span data-stu-id="4acf3-125">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="4acf3-126">提供於執行階段存取路由服務的功能，可用來動態修改路由組態。</span><span class="sxs-lookup"><span data-stu-id="4acf3-126">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="4acf3-127">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="4acf3-127">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="4acf3-128">指定將存取權授權給服務作業的設定。</span><span class="sxs-lookup"><span data-stu-id="4acf3-128">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="4acf3-129">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="4acf3-129">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="4acf3-130">指定 Windows Communication Foundation （WCF）服務的偵錯工具和說明資訊功能。</span><span class="sxs-lookup"><span data-stu-id="4acf3-130">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="4acf3-131">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="4acf3-131">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="4acf3-132">指定服務中繼資料和相關資訊的發行。</span><span class="sxs-lookup"><span data-stu-id="4acf3-132">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="4acf3-133">指定在服務作業期間啟用安全性事件稽核的設定。</span><span class="sxs-lookup"><span data-stu-id="4acf3-133">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="4acf3-134">指定 WCF 服務的節流機制。</span><span class="sxs-lookup"><span data-stu-id="4acf3-134">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="4acf3-135">指定服務的逾時。</span><span class="sxs-lookup"><span data-stu-id="4acf3-135">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="4acf3-136">指定用來裝載以工作流程為基礎之 WCF 服務的 WorkflowRuntime 實例設定。</span><span class="sxs-lookup"><span data-stu-id="4acf3-136">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="4acf3-137">允許從要求訊息標題擷取中繼資料位址資訊。</span><span class="sxs-lookup"><span data-stu-id="4acf3-137">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4acf3-138">父項目</span><span class="sxs-lookup"><span data-stu-id="4acf3-138">Parent Elements</span></span>  
  
|<span data-ttu-id="4acf3-139">元素</span><span class="sxs-lookup"><span data-stu-id="4acf3-139">Element</span></span>|<span data-ttu-id="4acf3-140">描述</span><span class="sxs-lookup"><span data-stu-id="4acf3-140">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="4acf3-141">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="4acf3-141">A collection of service behavior elements.</span></span>|
