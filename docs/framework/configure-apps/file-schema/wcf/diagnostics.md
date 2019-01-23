---
title: '&lt;diagnostics&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: de11145620e8fdf96785908df85ab5ecdfd2e25e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524584"
---
# <a name="ltdiagnosticsgt"></a>&lt;diagnostics&gt;
`diagnostics` 項目會定義可由系統管理員用於執行階段檢查和控制的設定。  
  
 \<system.ServiceModel>  
\<diagnostics>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|etwProviderId|字串，這個字串會指定 Event-Tracing 提供者的識別項，此識別項會將事件寫入至 ETW 工作階段。|  
|performanceCounters|指定是否啟用組件的效能計數器。 有效值為<br /><br /> 關閉：停用效能計數器。<br />-ServiceOnly:僅啟用與這個服務相關的效能計數器。<br />-所有：可在執行階段檢視效能計數器。<br />-預設值：已建立單一效能計數器執行個體 _WCF_Admin。 這個執行個體用於啟用基礎結構所使用之 SQM 資料的集合。 這個執行個體所有的計數器值都未更新，因此將維持在零。 如果沒有 WCF 的組態，則這是預設值。|  
|wmiProviderEnabled|布林值，指定是否為組件啟用 WMI 提供者。 使用者需要 WMI 提供者來取得 Windows Communication Foundation (WCF) 的檢查和控制功能的執行階段存取權。 預設為 `false`。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<endToEndTracing>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|組態檔項目，此項目可讓您啟用與停用執行服務應用程式期間不同層面的端對端追蹤。|  
|[\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|描述 WCF 訊息記錄的設定。|  
  
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
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
