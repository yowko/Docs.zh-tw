---
title: 追蹤的安全性考量及實用秘訣
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 0dadf89ecbd7623735debe37355761aea3d62db4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580391"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>追蹤的安全性考量及實用秘訣
此主題描述如何保護敏感資訊以防公開，以及使用 WebHost 時的實用秘訣。  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>使用自訂追蹤接聽項來搭配 WebHost  
 如果您正在撰寫自己的追蹤接聽項，應該知道追蹤有可能在 Web 裝載服務的情況中遺失。 當 WebHost 進行回收，會關閉即時處理序以讓複本接手。 然而，視接聽項型別而定，這兩個處理序必須同時存取相同資源一段時間。 在此情況中，`XmlWriterTraceListener` 會為第二個處理序建立新的追蹤檔；而 Windows 事件追蹤則負責管理相同工作階段中的多個處理序，並存取相同的檔案。 如果您自己的接聽項無法提供類似的功能，當兩個處理序鎖住該檔案，追蹤可能會遺失。  
  
 您應該同時了解到，自訂追蹤接聽項可以透過網路傳送追蹤與訊息，例如，傳送至遠端資料庫。 身為應用程式的部署者，您應該使用適當的存取控制來設定自訂接聽項。 您應該同時針對任何可以在遠端位置上公開的個人資訊套用安全性控制。  
  
## <a name="logging-sensitive-information"></a>記錄敏感資訊  
 當訊息在範圍內時，追蹤就包含訊息標頭。 啟用追蹤時，應用程式特定標頭中的個人資訊 (例如查詢字串) 和本文資訊 (例如信用卡號碼) 會在記錄檔中變得可見。 應用程式部署者負責強制針對組態和追蹤檔採取存取控制。 如果不要讓這類資訊變得可見，您應該停用追蹤，如果要共用追蹤記錄檔，則應該篩選掉部分資料。  
  
 下列秘訣有助於防止無意間公開追蹤檔內容：  
  
-   確定在 WebHost 和自我裝載的情況下，記錄檔都受到存取控制清單 (ACL) 的保護。  
  
-   您選擇的副檔名不可讓人透過 Web 要求就輕而易舉地取得檔案。 例如，.xml 副檔名就不是安全的選擇。 請參閱 IIS 管理手冊，查看可服務的副檔名清單。  
  
-   指定絕對路徑做為記錄檔位置，此位置應該位於 WebHost vroot 公用目錄之外，以防止外部人員使用網頁瀏覽器存取記錄檔。  
  
 根據預設，金鑰和個人可識別資訊 (PII)，例如使用者名稱和密碼，不會記錄在追蹤和記錄訊息中。 不過，電腦的系統管理員還是可以使用 Machine.config 檔案中 `enableLoggingKnownPII` 項目的 `machineSettings` 屬性，來允許電腦上執行的應用程式記錄已知的個人可識別資訊 (PII)，如下列所示：  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>   
```  
  
 然後，應用程式部署者可以使用 App.config 或 Web.config 檔案中的 `logKnownPii` 屬性，啟用 PII 記錄，如下所示：  
  
```xml  
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
  
 只有在這兩個設定都是 `true` 時，才會啟用 PII 記錄。 結合兩個參數，提供了記錄每個應用程式已知 PII 的彈性。  
  
 您應該知道，在組態檔中指定兩個以上的自訂來源時，只會讀取第一個來源的屬性。 其他的來源則會被忽略。 這表示，在下列的 App.config 檔案中，即使第二個來源已明確啟用 PII 記錄，但不會記錄這兩個來源的 PII。  
  
```xml  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 如果`<machineSettings enableLoggingKnownPii="Boolean"/>`t:system.configuration.configurationerrorsexception 項目不在 Machine.config 檔案，系統會擲回<xref:System.Configuration.ConfigurationErrorsException>。  
  
 只有在應用程式啟動或重新啟動時，才能讓變更生效。 當這兩個屬性都設定為 `true` 時，啟動時會記錄事件。 如果 `logKnownPii` 設定為 `true`，但 `enableLoggingKnownPii` 設定為 `false`，也會記錄事件。  
  
 如需有關 PII 記錄的詳細資訊，請參閱[PII 安全性鎖定](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md)範例。  
  
 電腦的系統管理員和應用程式部署人員在使用這兩個參數時，應該特別小心謹慎。 如果啟用 PII 記錄，則會記錄安全性金鑰和 PII。 如果停用，敏感資料和應用程式特定資料仍然會記錄在訊息標頭和本文中。 如需隱私權和保護 PII 免於遭到公開的更完整討論，請參閱 <<c0> [ 使用者隱私權](https://go.microsoft.com/fwlink/?LinkID=94647)。  
  
 此外，每次連線以進行連線導向的傳輸，或是每次以其他方式傳送訊息時，都會記錄一次訊息寄件者的 IP 位址。 這不需要寄件者的同意就能進行。 但是，這種記錄行為只會發生在 [資訊] 或 [詳細資料] 追蹤層級中 (不屬於實際執行的預設或建議追蹤層級)，除了即時偵錯以外。  
  
## <a name="see-also"></a>另請參閱
- [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
