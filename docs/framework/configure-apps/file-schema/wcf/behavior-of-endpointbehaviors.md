---
title: "&lt;endpointBehaviors&gt; 的 &lt;behavior&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bef07c6cdd80874bfa17994dffafe4d3f2cfc5a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltbehaviorgt-of-ltendpointbehaviorsgt"></a>&lt;endpointBehaviors&gt; 的 &lt;behavior&gt;
`behavior` 項目包含端點行為之設定的集合。 各個行為是依其 `name` 進行索引。 端點可透過這個名稱連結至每一個行為。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
 \<系統。ServiceModel >  
\<行為 >  
\<endpointBehaviors >  
\<行為 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <endpointBehaviors>  
       <behavior name="String" />  
    </endpointBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|唯一的字串，其中包含行為的組態名稱。 這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|指定用來對服務驗證用戶端的認證。|  
|[\<callbackDebug >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbackdebug.md)|指定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 回呼物件的服務偵錯。|  
|[\<callbackTimeouts >](../../../../../docs/framework/configure-apps/file-schema/wcf/callbacktimeouts.md)|指定用戶端回呼的逾時。|  
|[\<clientVia >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientvia.md)|指定訊息應採用的路徑。|  
|[\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer.md)|包含 DataContractSerializer 的組態資料。|  
|[\<dispatcherSynchronization >](../../../../../docs/framework/configure-apps/file-schema/wcf/dispatchersynchronization.md)|指定可讓服務以非同步方式傳送回覆的端點行為。|  
|[\<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)|可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。 行為應該只用於搭配  \<webHttpBinding > 標準繫結，或\<webMessageEncoding > 繫結項目。|  
|[\<endpointDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。|  
|[\<soapProcessing >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)|定義用戶端端點行為，這個行為會用來封送處理不同繫結型別和訊息版本之間的訊息。|  
|[\<synchronousReceive >](../../../../../docs/framework/configure-apps/file-schema/wcf/synchronousreceive-element.md)|指定在服務或用戶端應用程式中接收訊息的執行階段行為。 它沒有任何屬性或子項目。|  
|[\<transactedBatching >](../../../../../docs/framework/configure-apps/file-schema/wcf/transactedbatching.md)|指定是否支援接收作業的異動批次處理。|  
|[\<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)|透過組態指定端點上的 WebHttpBehavior。 此行為，當搭配\<webHttpBinding > 標準繫結，可讓 Web 程式設計模型[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]服務。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<endpointBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|端點行為項目的集合。|
