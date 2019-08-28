---
title: 設定訊息記錄
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: f9324370539b41d21365e0bd126c2f632ac67789
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044288"
---
# <a name="configuring-message-logging"></a>設定訊息記錄

本主題描述如何針對不同的案例設定訊息記錄。

## <a name="enabling-message-logging"></a>啟用訊息記錄

Windows Communication Foundation (WCF) 預設不會記錄訊息。 若要啟動訊息記錄，您必須將追蹤接聽項加入至 `System.ServiceModel.MessageLogging` 追蹤來源，並在組態檔中設定 `<messagelogging>` 項目的屬性。

下列範例示範如何啟用記錄並指定其他選項。

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
         <add name="messages"
              type="System.Diagnostics.XmlWriterTraceListener"
              initializeData="c:\logs\messages.svclog" />
        </listeners>
    </source>
  </sources>
</system.diagnostics>

<system.serviceModel>
  <diagnostics>
    <messageLogging
         logEntireMessage="true"
         logMalformedMessages="false"
         logMessagesAtServiceLevel="true"
         logMessagesAtTransportLevel="false"
         maxMessagesToLog="3000"
         maxSizeOfMessageToLog="2000"/>
  </diagnostics>
</system.serviceModel>
```

如需訊息記錄設定的詳細資訊, 請參閱[追蹤和訊息記錄的建議設定](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)。

您可以使用 `add` 來指定所要使用之接聽項的名稱和型別。 在範例組態中，我們已將接聽項命名為 "messages"，並且加入標準 .NET Framework 追蹤接聽項 (`System.Diagnostics.XmlWriterTraceListener`) 做為要使用的型別。 如果您要使用 `System.Diagnostics.XmlWriterTraceListener`，就必須在組態檔中指定輸出檔案位置和名稱。 將 `initializeData` 設定為記錄檔的名稱，即可做到這點。 否則，系統會擲回例外狀況 (Exception)。 您也可以實作會將記錄發出到預設檔案的自訂接聽項。

> [!NOTE]
> 由於訊息記錄會存取磁碟空間，因此您應該要限制為特定服務寫入磁碟的訊息數目。 當抵達訊息限制時，便會在資訊層上產生追蹤，並停止所有的訊息記錄。

在記錄層級和選項 (本頁面可能為英文) 一節中，對於記錄層級以及其他選項都有加以討論。

`switchValue` 的 `source` 屬性只對追蹤有效。 如果您依下面所示指定 `switchValue`的 `System.ServiceModel.MessageLogging` 屬性，該屬性並不會產生作用。

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
```

如果想要停用追蹤來源，您就應該改成使用 `logMessagesAtServiceLevel` 項目的 `logMalformedMessages`、`logMessagesAtTransportLevel` 及 `messageLogging` 屬性。 您應該將所有這些屬性都設定為 `false`。 使用先前程式碼範例中的組態檔、透過組態編輯器 UI 介面，或是使用 WMI，都可以做到這點。 如需設定編輯器工具的詳細資訊, 請參閱設定[編輯器工具 (svcconfigeditor.exe .exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)。 如需 WMI 的詳細資訊, 請參閱[使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)。

## <a name="logging-levels-and-options"></a>記錄層級和選項

對於傳入的訊息，系統會緊接在訊息形成之後、在訊息到達服務層級中的使用者程式碼之前，以及在偵測到格式錯誤的訊息時進行記錄。

對於傳出的訊息，系統會緊接在訊息離開使用者程式碼之後，以及在訊息傳送到網路上之前進行記錄。

WCF 會記錄兩個不同層級、服務和傳輸的訊息。 格式錯誤的訊息也會加以記錄。 三個分類彼此獨立，而且可以透過組態來個別啟動。

您可以設定 `logMessagesAtServiceLevel` 項目的 `logMalformedMessages`、`logMessagesAtTransportLevel` 及 `messageLogging` 屬性以控制記錄層級。

### <a name="service-level"></a>服務層級

記錄在這層的是即將進入 (進行接收時) 或離開 (進行傳送時) 使用者程式碼的訊息。 如果有定義篩選條件，就只會記錄符合篩選條件的訊息。 否則，便會記錄服務層級中的所有訊息。 基礎結構訊息 (交易、對等通道及安全性) 也會記錄在此層級，除了可信賴傳訊訊息以外。 若是已進行資料流處理的訊息，則只記錄標頭。 此外，安全訊息會以解密形式記錄在此層級。

### <a name="transport-level"></a>傳輸層級

記錄在這層的是要送到網路上傳輸或是在傳輸後而要進行編碼或解碼的訊息。 如果有定義篩選條件，就只會記錄符合篩選條件的訊息。 否則，便會記錄傳輸層級中的所有訊息。 所有的基礎結構訊息都會記錄在這層，其中包括可信賴傳訊訊息。 若是已進行資料流處理的訊息，則只記錄標頭。 此外，安全訊息會以加密形式記錄在此層級，除了使用 HTTPS 一類的安全傳輸的情況以外。

### <a name="malformed-level"></a>格式錯誤層級

格式不正確的訊息是由 WCF 堆疊在處理的任何階段遭到拒絕的訊息。 格式錯誤訊息會依現狀加以記錄：也就是若有加密，便會以加密形式記錄，並包含不正確的 XML 和其他格式。 `maxSizeOfMessageToLog` 定義了要以 CDATA 形式記錄之訊息的大小。 根據預設，`maxSizeOfMessageToLog` 會等於 256 K。 如需此屬性的詳細資訊, 請參閱其他選項一節。

### <a name="other-options"></a>其他選項

除了記錄層級，使用者也可以指定下列選項：

- 記錄整個訊息 (`logEntireMessage`屬性):這個值會指定是否記錄整個訊息 (訊息標頭和本文)。 預設值為 `false`，表示只記錄標頭。 這項設定會影響到服務和傳輸訊息記錄層級。

- 要記錄的訊息上限`maxMessagesToLog` (屬性):這個值會指定要記錄的訊息數目上限。 所有的訊息 (服務、傳輸及格式錯誤訊息) 都會計算到此配額內。 當抵達配額時，便會發出追蹤，而且不再記錄其他訊息。 預設值為10000。

- 要記錄的訊息大小上限 (`maxSizeOfMessageToLog`屬性):這個值會指定要記錄的訊息大小上限 (以位元組為單位)。 不記錄超過大小限制的訊息，而且也不針對該訊息執行任何其他活動。 這個設定會影響所有的追蹤層級。 如果有開啟 ServiceModel 追蹤，便會在第一個記錄點 (ServiceModelSend* 或 TransportReceive) 發出警告層級追蹤以通知使用者。 服務層級和傳輸層級等訊息的預設值是 256 K，而格式錯誤訊息的預設值是 4 K。

  > [!CAUTION]
  > 經過計算以便與 `maxSizeOfMessageToLog` 比較的訊息大小，就是進行序列化之前在記憶體中的訊息大小。 這個大小可能不同於已記錄之訊息字串的實際長度，而且在許多情況下都會大於實際大小。 如此一來，訊息可能就不會加以記錄。 您可以將 `maxSizeOfMessageToLog` 屬性指定為超過預期訊息大小的 10%，這樣就可以解決這個情形。 此外，如果有記錄格式錯誤訊息，由訊息記錄應用的實際磁碟空間大小最多可為 `maxSizeOfMessageToLog` 所指定值的 5 倍。

如果組態檔中未定義追蹤接聽項，則無論指定的記錄層級為何，都不會產生記錄輸出。

包含本節所描述屬性的訊息記錄選項，可以在執行階段使用 Windows Management Instrumentation (WMI) 來加以變更。 這可以藉由存取[AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)實例來完成, 這會公開下列布林值`LogMessagesAtServiceLevel`屬性`LogMessagesAtTransportLevel`:、 `LogMalformedMessages`和。 因此，如果您為訊息記錄設定一個追蹤接聽項，但在組態中將這些選項設定為 `false`，那麼您可以在稍後應用程式執行時，將選項變更為 `true`。 這會在執行階段有效地啟用訊息記錄。 同樣地，如果您在組態檔中啟用訊息記錄，則您可以在執行階段使用 WMI 來停用訊息記錄。 如需詳細資訊, 請參閱[使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)。

訊息記錄中的 `source` 欄位會指定要用哪種內容來記錄訊息：何時傳送/接收要求訊息、針對要求-回覆或單向要求、在服務模型或傳輸層，或是在發生格式錯誤訊息的情況下。

`source` 若`Malformed`為格式錯誤的訊息, 會等於。 否則，便依據內容將來源指定為下列值。

針對要求/回覆

||傳送要求|接收要求|傳送回覆|接收回覆|
|-|------------------|---------------------|----------------|-------------------|
|服務模型層|服務<br /><br /> 層級<br /><br /> 傳送<br /><br /> 要求|服務<br /><br /> 層級<br /><br /> 接收<br /><br /> 要求|服務<br /><br /> 層級<br /><br /> 傳送<br /><br /> 回覆|服務<br /><br /> 層級<br /><br /> 接收<br /><br /> 回覆|
|傳輸層|Transport<br /><br /> 傳送|Transport<br /><br /> 接收|Transport<br /><br /> 傳送|Transport<br /><br /> 接收|

針對單向要求

||傳送要求|接收要求|
|-|------------------|---------------------|
|服務模型層|服務<br /><br /> 層級<br /><br /> 傳送<br /><br /> 資料包|服務<br /><br /> 層級<br /><br /> 接收<br /><br /> 資料包|
|傳輸層|Transport<br /><br /> 傳送|Transport<br /><br /> 接收|

## <a name="message-filters"></a>訊息篩選條件

訊息篩選條件會定義於 `messageLogging` 組態區段的 `diagnostics` 組態項目中。 訊息篩選條件會套用在服務和傳輸層級上。 當定義一個或多個篩選條件時，只會記錄符合至少其中一個篩選條件的訊息。 如果沒有定義篩選條件，所有訊息都會通過。

篩選條件支援完整的 XPath 語法，並依其出現在組態檔中的順序套用。 語法不正確的篩選條件會造成組態例外狀況。

篩選條件也提供使用 `nodeQuota` 屬性的安全性功能，該屬性會限制 XPath DOM 中的節點數目上限，而這些節點可加以檢查來比對篩選條件。

下列範例示範如何設定只記錄含有 SOAP 標頭區段之訊息的篩選條件。

```xml
<messageLogging logEntireMessage="true"
    logMalformedMessages="true"
    logMessagesAtServiceLevel="true"
    logMessagesAtTransportLevel="true"
    maxMessagesToLog="420">
    <filters>
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
                 /soap:Envelope/soap:Header
        </add>
     </filters>
</messageLogging>
```

篩選條件無法套用至訊息的本文。 系統會從篩選條件的清單中移除嘗試操作訊息本文的篩選條件， 而且也會發出事件以表明此點。 例如，系統會從篩選資料表中移除下列篩選條件。

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>設定自訂接聽項

您也可以運用其他選項來設定自訂接聽項。 要在記錄之前從訊息中篩選應用程式特定的 PII 項目時，便可以使用自訂接聽項。 下列範例示範了自訂接聽項組態。

```xml
<system.diagnostics>
   <sources>
     <source name="System.ServiceModel.MessageLogging">
           <listeners>
             <add name="MyListener"
                    type="YourCustomListener"
                    initializeData="c:\logs\messages.svclog"
                    maxDiskSpace="1000"/>
           </listeners>
     </source>
   </sources>
</system.diagnostics>
```

請注意，`type` 屬性應該設定為此型別的限定組件名稱。

## <a name="see-also"></a>另請參閱

- [\<messageLogging>](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
- [訊息記錄](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [追蹤與訊息記錄的建議設定](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)
