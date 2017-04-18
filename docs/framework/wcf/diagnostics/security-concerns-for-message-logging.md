---
title: "訊息記錄的安全性考量 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
caps.latest.revision: 17
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 17
---
# 訊息記錄的安全性考量
這個主題說明如何保護訊息記錄中的敏感資料免於遭到公開，以及訊息記錄所產生的事件。  
  
## 安全性考量  
  
### 記錄敏感資訊  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 不會修改應用程式特定標頭和本文中的任何資料。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也不會追蹤應用程式特定標頭或本文資料中的個人資訊。  
  
 啟用訊息記錄時，應用程式特定標頭中的個人資訊 \(例如查詢字串\) 和本文資訊 \(例如信用卡號碼\) 會在記錄檔中變得可見。應用程式部署者負責強制針對組態和記錄檔採取存取控制。如果不要讓這類資訊變得可見，您應該停用記錄，如果要共用記錄檔，則應該篩選掉部分資料。  
  
 下列秘訣有助於防止無意間公開記錄檔內容：  
  
-   確定在 Web 主控和自我主控的情況下，記錄檔都受到存取控制清單 \(ACL\) 的保護。  
  
-   您選擇的副檔名不可讓人透過 Web 要求就輕而易舉地取得檔案。例如，.xml 副檔名就不是安全的選擇。請參閱網際網路資訊服務 \(IIS\) 管理手冊，查看可服務的副檔名清單。  
  
-   指定絕對路徑做為記錄檔位置，此位置應該位於 Web 主機 vroot 公用目錄之外，以防止外部人員使用網頁瀏覽器存取記錄檔。  
  
 根據預設，金鑰和個人可識別資訊 \(PII\)，例如使用者名稱和密碼，不會記錄在追蹤和記錄訊息中。不過，電腦的系統管理員還是可以使用 Machine.config 檔案中 `machineSettings` 項目的 `enableLoggingKnownPII` 屬性，來允許電腦上執行的應用程式記錄已知的個人可識別資訊 \(PII\)。下列組態示範如何執行這項操作：  
  
```  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 然後，應用程式部署者可以使用 App.config 或 Web.config 檔案中的 `logKnownPii` 屬性，啟用 PII 記錄，如下所示：  
  
```  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
    </sources>  
</system.diagnostics>  
```  
  
 只有在這兩個設定都是 `true` 時，才會啟用 PII 記錄。結合兩個參數，提供了記錄每個應用程式已知 PII 的彈性。  
  
> [!IMPORTANT]
>  在 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 的 Web.config 檔案或 App.config 檔案中，`logEntireMessage` 和 `logKnownPii` 旗標也必須設定為 `true` 以啟用 PII 記錄，如下列範例 `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …` 所示。  
  
 您應該知道，在組態檔中指定兩個以上的自訂來源時，只會讀取第一個來源的屬性。其他的來源則會被忽略。也就是說，在下列的 App.config 檔案中，即使第二個來源已明確啟用 PII 記錄，還是不會記錄這兩個來源的 PII。  
  
```  
<system.diagnostics>  
   <sources>  
      <source name="System.ServiceModel.MessageLogging"  
              logKnownPii="false">  
              <listeners>  
                 <add name="messages"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\messages.svclog" />  
              </listeners>  
            </source>  
      <source name="System.ServiceModel"   
              logKnownPii="true">  
              <listeners>  
                 <add name="traces"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\traces.svclog" />  
              </listeners>  
      </source>  
   </sources>  
</system.diagnostics>  
```  
  
 如果 `<machineSettings enableLoggingKnownPii="Boolean"/>`<xref:System.Configuration.ConfigurationErrorsException> 項目不在 Machine.config 檔案中，系統就會擲回。  
  
 只有在應用程式啟動或重新啟動時，才能讓變更生效。當這兩個屬性都設定為 `true` 時，啟動時會記錄事件。如果 `logKnownPii` 設定為 `true`，但 `enableLoggingKnownPii` 設定為 `false`，也會記錄事件。  
  
 電腦的系統管理員和應用程式部署人員在使用這兩個參數時，應該特別小心謹慎。如果啟用 PII 記錄，則會記錄安全性金鑰和 PII。如果停用，敏感資料和應用程式特定資料仍然會記錄在訊息標頭和本文中。如需隱私權和保護 PII 免於遭到公開的詳細討論，請參閱[使用者隱私權](http://go.microsoft.com/fwlink/?LinkID=94647) \(英文\)。  
  
> [!CAUTION]
>  格式錯誤的訊息中不會隱藏 PII。這類訊息會依現狀記錄，不做任何修改。上述的屬性在此不會有任何作用。  
  
### 自訂追蹤接聽項  
 在訊息記錄追蹤來源上加入自訂追蹤接聽項，是僅限於系統管理員的權限。這是因為惡意的自訂接聽項可以設定為從遠端傳送訊息，進而導致敏感資訊洩漏。此外，如果您將自訂接聽項設定為在網路上傳送訊息，例如傳送至遠端資料庫，在遠端電腦的訊息記錄檔上應該強制採取適當的存取控制。  
  
## 由訊息記錄所觸發的事件  
 以下列出由訊息記錄所發出的所有事件。  
  
-   Message logging on：在組態中或透過 WMI 啟用訊息記錄時，會發出這個事件。事件內容為「已開啟訊息記錄。可能會以純文字記錄敏感資料，即使在網路傳輸時經過加密，例如，訊息本文」。  
  
-   Message logging off：在組態中或透過 WMI 停用訊息記錄時，會發出這個事件。事件內容為「已關閉訊息記錄」。  
  
-   Log Known PII On：啟用已知 PII 記錄時，會發出這個事件。當 Machine.config 檔案中 `machineSettings` 項目的 `enableLoggingKnownPii` 屬性設定為 `true`，並且 App.config 或 Web.config 檔案中 `source` 項目的 `logKnownPii` 屬性設定為 `true` 時，就會發生這種情況。  
  
-   Log Known PII Not Allowed：不允許記錄已知 PII 時，會發出這個事件。當 App.config 或 Web.config 檔案中 `source` 項目的 `logKnownPii` 屬性設定為 `true`，但 Machine.config 檔案中 `machineSettings` 項目的 `enableLoggingKnownPii` 屬性設定為 `false` 時，就會發生這種情況。不會有例外狀況擲回。  
  
 您可以在 Windows 的 \[事件檢視器\] 工具中檢視這些事件。如需詳細資訊，請參閱[事件記錄](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)。  
  
## 請參閱  
 [訊息記錄](../../../../docs/framework/wcf/diagnostics/message-logging.md)   
 [追蹤的安全性考量及實用秘訣](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)