---
title: <messageLogging>
ms.date: 03/30/2017
ms.assetid: 1d06a7e6-9633-4a12-8c5d-123adbbc19c5
ms.openlocfilehash: 70fb2df1d37af23d9ec19932806989ce3329bf3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191564"
---
# <a name="messagelogging"></a>\<messageLogging>
這個項目會定義 Windows Communication Foundation (WCF) 的訊息記錄功能設定。  
  
 \<system.ServiceModel>  
\<diagnostic>  
\<messageLogging>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>
  <diagnostics>
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
|`logEntireMessage`|布林值，指定是否記錄整個訊息 (訊息標頭和本文)。 預設為 `false`，意指只會記錄訊息標頭。 這個設定會影響所有的訊息記錄層級 (服務、傳輸和格式錯誤)。|  
|`logMalformedMessages`|布林值，指定是否記錄格式錯誤的訊息。 格式錯誤的訊息不會計入 `maxMessagesToLog`。 預設為 `false`。|  
|`logMessagesAtServiceLevel`|布林值，指定是否在服務層級追蹤訊息 (在加密和傳輸相關轉換之前)。 預設為 `false`。|  
|`logMessagesAtTransportLevel`|布林值，指定是否在傳輸層級追蹤訊息。 在組態檔中指定的任何篩選條件都會套用，且只會追蹤符合篩選條件的訊息。 預設為 `false`。|  
|`maxMessagesToLog`|正整數，指定要記錄的訊息數目上限。 預設值為 1000。|  
|`maxSizeOfMessageToLog`|正整數，指定要記錄之訊息的大小上限 (以位元組為單位)。 大於限制的訊息將不會記錄。 這個設定會影響所有的追蹤層級。 預設為 262144(0x4000)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|篩選條件|`filters` 項目含有 XPath 篩選條件的集合。 當啟用傳輸訊息記錄時 (`logMessagesAtTransportLevel` 是 `true`)，將只記錄符合篩選條件的訊息。<br /><br /> 篩選條件只會在傳輸層套用。 服務等級和格式錯誤訊息記錄不受篩選條件的影響。<br /><br /> `filter` 這個項目的唯一屬性為 XpathFilter。<br /><br /> `<filters>     <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">/soap:Envelope</add> </filters>`|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|診斷|為系統管理員定義執行階段檢查和控制的 WCF 設定。|  
  
## <a name="remarks"></a>備註  
 訊息會記錄在堆疊中的三個不同層級：服務、傳輸和格式錯誤。 每個層級可個別啟動。  
  
 可以加入 XPath 篩選條件，以記錄傳輸和服務層級的特定訊息。 如果沒有定義篩選條件，便會記錄所有的訊息。 篩選條件只會套用於訊息的標頭。 本文會被忽略。 WCF 會忽略訊息本文，以增進效能。 如果您希望根據本文的內容進行篩選，可以使用執行這項工作的篩選條件來建立自訂接聽程式。  
  
 您必須建立追蹤接聽程式，以啟動訊息追蹤。 接聽程式本身可以是與 <xref:System.Diagnostics> 追蹤架構搭配使用的任何接聽程式。 下列範例示範如何建立這類接聽程式。  
  
```xml  
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel"
            switchValue="Verbose">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="ServiceModel Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
        <clear />
        <add type="System.Diagnostics.DefaultTraceListener"
             name="Default"
             traceOutputOptions="None" />
        <add name="MessageLogging Listener"
             traceOutputOptions="None" />
      </listeners>
    </source>
  </sources>
  <sharedListeners>
    <add initializeData="C:\ItProTools\TraceLog.xml"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="ServiceModel Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
    <add initializeData="C:\ItProTools\MessageLog.log"
         type="System.Diagnostics.XmlWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         name="MessageLogging Listener"
         traceOutputOptions="LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack" />
  </sharedListeners>
</system.diagnostics>
```  
  
## <a name="example"></a>範例  
  
```xml  
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
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- [設定訊息記錄](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
