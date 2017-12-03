---
title: "&lt;診斷&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d558bf6ac71a3a19fb8c28989fd9262e7a13f0f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiagnosticsgt"></a>&lt;診斷&gt;
`diagnostics` 項目會定義可由系統管理員用於執行階段檢查和控制的設定。  
  
 \<系統。ServiceModel >  
\<診斷 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>  
   <diagnostics etwProviderId="String"       performanceCounters="Off/ServiceOnly/All/Default"              wmiProviderEnabled="Boolean" >       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
          maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
             <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|etwProviderId|字串，這個字串會指定 Event-Tracing 提供者的識別項，此識別項會將事件寫入至 ETW 工作階段。|  
|performanceCounters|指定是否啟用組件的效能計數器。 有效值為<br /><br /> -設為 off： 停用效能計數器。<br />-ServiceOnly： 只相關的效能計數器到此服務會啟用。<br />-所有： 可以在執行階段檢視計數器的效能。<br />預設： 建立單一效能計數器執行個體 _WCF_Admin。 這個執行個體用於啟用基礎結構所使用之 SQM 資料的集合。 這個執行個體所有的計數器值都未更新，因此將維持在零。 如果沒有 WCF 的組態，則這是預設值。|  
|wmiProviderEnabled|布林值，指定是否為組件啟用 WMI 提供者。 使用者需要 WMI 提供者來取得 Windows Communication Foundation (WCF) 的檢查和控制功能的執行階段存取權。 預設為 `false`。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<endToEndTracing >](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。|  
|[\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|描述 WCF 訊息記錄的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|serviceModel|所有 WCF 組態項目的根項目。|  
  
## <a name="remarks"></a>備註  
 `diagnostics` 區段會定義位於組件中所有服務的診斷設定。 無法在服務等級上定義個別的診斷設定，除非組件中只有一個服務。 根據區段的需求設定屬性。  
  
## <a name="example"></a>範例  
  
```xml  
<diagnostics wmiProviderEnabled="false"  
       performanceCounters="all">  
       <messageLogging logEntireMessage="true"  
          logMalformedMessages="true"  
          logMessagesAtServiceLevel="true"  
          logMessagesAtTransportLevel="true"  
          maxMessagesToLog="42"  
          maxSizeOfMessageToLog="42">  
         <filters>  
         <clear />  
    </filters>  
       </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
