---
title: "&lt;serviceBehaviors&gt; 的 &lt;behavior&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;serviceBehaviors&gt; 的 &lt;behavior&gt;
`behavior` 項目包含服務行為之設定的集合。  各個行為是依其 `name` 進行索引。  服務可透過使用 [\<endpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) 項目之 `behaviorConfiguration` 屬性的這個名稱，連結至每一個行為。  如此可允許端點共用通用行為組態，而不用重新定義設定。  從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。  如需預設組態和無名稱繫結與行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
> [!NOTE]
>  Windows 工作流程活動特有的行為項目 \(例如 [\<sendMessageChannelCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md) 項目\) 記載於[\<serviceBehaviors\> 的 \<behavior\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) 頁面中。  
  
## 語法  
  
```  
  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
       <behavior name="String" />  
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|唯一的字串，其中包含行為的組態名稱。  這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。  從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。  如需預設組態和無名稱繫結與行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<dataContractSerializer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)|包含 DataContractSerializer 的組態資料。|  
|[\<persistenceProvider\>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistenceprovider.md)|指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。|  
|[\<傳送\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|提供於執行階段存取路由服務的功能，可用來動態修改路由組態。|  
|[\<serviceAuthenticationManager\>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthenticationmanager.md)|提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。|  
|[\<serviceAuthorization\>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)|指定將存取權授權給服務作業的設定。|  
|[\<serviceCredentials\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|指定要用於驗證 \(Authenticate\) 服務的認證，以及用戶端認證的驗證 \(Validation\) 相關設定。|  
|[\<serviceDebug\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)|指定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務的偵錯和說明資訊功能。|  
|[\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)|指定服務端點的探索能力。|  
|[\<serviceMetadata\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)|指定服務中繼資料和相關資訊的發行。|  
|[\<serviceSecurityAudit\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)|指定在服務作業期間啟用安全性事件稽核的設定。|  
|[\<serviceThrottling\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)|指定 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務的節流機制。|  
|[\<serviceTimeouts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicetimeouts.md)|指定服務的逾時。|  
|[\<workflowRuntime\>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|指定裝載工作流程架構的 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務時 WorkflowRuntime 之執行個體的設定。|  
|[\<useRequestHeadersForMetadataAddress\>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|允許從要求訊息標題擷取中繼資料位址資訊。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|服務行為項目的集合。|