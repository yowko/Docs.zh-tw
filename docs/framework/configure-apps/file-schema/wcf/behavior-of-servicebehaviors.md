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
# <a name="behavior-of-servicebehaviors"></a>\<behavior> 的 \<serviceBehaviors>
`behavior` 項目包含服務行為之設定的集合。 各個行為是依其 `name` 進行索引。 服務可以使用元素的屬性，透過這個名稱連結至每個行為 `behaviorConfiguration` [\<endpoint>](endpoint-element.md) 。 如此可允許端點共用通用行為組態，而不用重新定義設定。 從 .NET Framework 4 開始，系結和行為都不需要有名稱。 如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。  
  
> [!NOTE]
> Windows 工作流程活動特有的行為專案（例如專案 [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) ）會記錄在頁面中[ \<behavior> \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a>語法  
  
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
|NAME|唯一的字串，其中包含行為的組態名稱。 這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。 從 .NET Framework 4 開始，系結和行為都不需要有名稱。 如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|包含 DataContractSerializer 的組態資料。|  
|[\<persistenceProvider>](persistenceprovider.md)|指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。|  
|[\<routing>](routing-of-servicebehavior.md)|提供於執行階段存取路由服務的功能，可用來動態修改路由組態。|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|指定將存取權授權給服務作業的設定。|  
|[\<serviceCredentials>](servicecredentials.md)|指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。|  
|[\<serviceDebug>](servicedebug.md)|指定 Windows Communication Foundation （WCF）服務的偵錯工具和說明資訊功能。|  
|[\<serviceDiscovery>](servicediscovery.md)|指定服務端點的探索能力。|  
|[\<serviceMetadata>](servicemetadata.md)|指定服務中繼資料和相關資訊的發行。|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|指定在服務作業期間啟用安全性事件稽核的設定。|  
|[\<serviceThrottling>](servicethrottling.md)|指定 WCF 服務的節流機制。|  
|[\<serviceTimeouts>](servicetimeouts.md)|指定服務的逾時。|  
|[\<workflowRuntime>](workflowruntime.md)|指定用來裝載以工作流程為基礎之 WCF 服務的 WorkflowRuntime 實例設定。|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|允許從要求訊息標題擷取中繼資料位址資訊。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|服務行為項目的集合。|
