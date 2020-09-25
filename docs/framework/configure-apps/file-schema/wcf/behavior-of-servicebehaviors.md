---
title: <behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 739f95f527fd73062c8cec43efc6777efeb077f3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195151"
---
# <a name="behavior-of-servicebehaviors"></a>\<behavior> 的 \<serviceBehaviors>

`behavior` 項目包含服務行為之設定的集合。 各個行為是依其 `name` 進行索引。 服務可以使用專案的屬性，透過這個名稱連結到每個行為 `behaviorConfiguration` [\<endpoint>](endpoint-element.md) 。 如此可允許端點共用通用行為組態，而不用重新定義設定。 從 .NET Framework 4 開始，系結和行為不需要有名稱。 如需預設設定和無值系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)[的 WCF 服務設定和簡化的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。  
  
> [!NOTE]
> Windows 工作流程活動專屬的行為專案，例如 [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) 元素，會記載于頁面的[ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)中。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|唯一的字串，其中包含行為的組態名稱。 這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。 從 .NET Framework 4 開始，系結和行為不需要有名稱。 如需預設設定和無值系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)[的 WCF 服務設定和簡化的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|包含 DataContractSerializer 的組態資料。|  
|[\<persistenceProvider>](persistenceprovider.md)|指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。|  
|[\<routing>](routing-of-servicebehavior.md)|提供於執行階段存取路由服務的功能，可用來動態修改路由組態。|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|指定將存取權授權給服務作業的設定。|  
|[\<serviceCredentials>](servicecredentials.md)|指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。|  
|[\<serviceDebug>](servicedebug.md)|針對 Windows Communication Foundation (WCF) 服務指定偵錯工具和說明資訊功能。|  
|[\<serviceDiscovery>](servicediscovery.md)|指定服務端點的探索能力。|  
|[\<serviceMetadata>](servicemetadata.md)|指定服務中繼資料和相關資訊的發行。|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|指定在服務作業期間啟用安全性事件稽核的設定。|  
|[\<serviceThrottling>](servicethrottling.md)|指定 WCF 服務的節流機制。|  
|[\<serviceTimeouts>](servicetimeouts.md)|指定服務的逾時。|  
|[\<workflowRuntime>](workflowruntime.md)|指定用於裝載以工作流程為基礎的 WCF 服務之 WorkflowRuntime 實例的設定。|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|允許從要求訊息標題擷取中繼資料位址資訊。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|服務行為項目的集合。|
