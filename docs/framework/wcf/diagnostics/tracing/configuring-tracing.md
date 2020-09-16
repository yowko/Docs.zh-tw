---
title: 設定追蹤
description: 瞭解如何啟用追蹤、設定追蹤來源、設定活動追蹤和傳播，以及設定追蹤接聽項以存取 WCF 中的追蹤。
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: 7b0cc58975ee145e5234adf51e24109898853e1c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558897"
---
# <a name="configuring-tracing"></a>設定追蹤
本主題將說明如何啟用追蹤、設定追蹤來源以發出追蹤並設定追蹤層級、設定活動追蹤與傳播以支援端對端追蹤相互關聯，以及設定追蹤接聽項來存取追蹤。  
  
 針對在生產或偵測環境中的追蹤設定建議，請參閱 [追蹤和訊息記錄的建議設定](recommended-settings-for-tracing-and-message-logging.md)。  
  
> [!IMPORTANT]
> 在 Windows 8 上，您必須提高權限來執行應用程式 (以系統管理員身分執行)，您的應用程式才能產生追蹤記錄。  
  
## <a name="enabling-tracing"></a>啟用追蹤  
 Windows Communication Foundation (WCF) 會輸出下列資料以進行診斷追蹤：  
  
- 追蹤應用程式所有元件的流程里程碑，例如作業呼叫、程式碼例外狀況、警告和其他重大處理事件。  
  
- 追蹤功能故障時出現的 Windows 錯誤事件。 請參閱 [事件記錄](../event-logging/index.md)。  
  
 WCF 追蹤建置於之上 <xref:System.Diagnostics> 。 若要使用追蹤，您應該透過組態檔或程式碼來定義追蹤來源。 WCF 會定義每個 WCF 元件的追蹤來源。 `System.ServiceModel`追蹤來源是最常見的 wcf 追蹤來源，並且會記錄跨 WCF 通訊堆疊的處理里程碑，從進入/離開傳輸到進入/離開使用者程式碼。 `System.ServiceModel.MessageLogging` 追蹤來源會記錄在系統之間來回傳送的所有訊息。  
  
 預設不會啟用追蹤。 若要啟動追蹤，您必須建立追蹤接聽程式，並針對設定中的選取追蹤來源，將追蹤層級設定為 [關閉]。否則，WCF 不會產生任何追蹤。 如果您沒有指定接聽項，就會自動停用追蹤。 如果已定義接聽項，但是未指定層級，則預設會將層級設定為「關閉」，這表示將不會發出任何追蹤。  
  
 如果您使用 WCF 擴充性點，例如自訂作業啟動程式，您應該發出自己的追蹤。 這是因為如果您執行了擴充點，WCF 將無法再于預設路徑中發出標準追蹤。 如果您沒有透過發出追蹤來實作手動追蹤支援，可能無法看見預期的追蹤。  
  
 您可以藉由編輯應用程式的設定檔來設定追蹤，也就是針對 Web 裝載的應用程式 Web.config，或自我裝載應用程式的 Appname.exe.config。 下列是這類編輯的範例。 如需這些設定的詳細資訊，請參閱「設定追蹤接聽程式以使用追蹤」一節。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"
                   type="System.Diagnostics.XmlWriterTraceListener"
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
> 若要在 Visual Studio 中編輯 WCF 服務專案的設定檔，請以滑鼠右鍵按一下應用程式的設定檔（Web.config 適用于 Web 裝載的應用程式），或 **方案總管**中自我裝載應用程式的 Appname.exe.config。 然後選擇 [ **編輯 WCF** 設定] 內容功能表項目。 這會啟動設定 [編輯器工具 ( # A0) ](../../configuration-editor-tool-svcconfigeditor-exe.md)，可讓您使用圖形化使用者介面修改 WCF 服務的設定。  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>設定追蹤來源來發出追蹤  
 WCF 會定義每個元件的追蹤來源。 組件中產生的追蹤是由針對該來源而定義的接聽項所存取。 下列為定義的追蹤來源：  
  
- System.servicemodel：記錄 WCF 處理的所有階段，每當讀取設定、在傳輸過程中處理訊息、安全性處理、在使用者程式碼中分派訊息等等。  
  
- System.ServiceModel.MessageLogging：記錄在整個系統來回傳送的所有訊息。  
  
- System.IdentityModel。  
  
- System.ServiceModel.Activation。  
  
- System.IO.Log：記錄一般記錄檔系統 (CLFS) 的 .NET Framework 介面。  
  
- System.Runtime.Serialization：記錄何時讀取或寫入物件。  
  
- CardSpace。  
  
 您可以設定每個追蹤來源來使用相同 (共用) 的接聽項，如下列組態範例所示。  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 此外，您可以新增使用者定義的追蹤來源 (如下列範例所示範) 來發出使用者程式碼追蹤。  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />
</system.diagnostics>  
```  
  
 如需建立使用者定義的追蹤來源的詳細資訊，請參閱 [擴充追蹤](../../samples/extending-tracing.md)。  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>設定追蹤接聽項來使用追蹤  
 在執行時間，WCF 會將追蹤資料摘要至接聽程式，以處理資料。 WCF 提供數個預先定義的接聽程式 <xref:System.Diagnostics> ，其不同于用於輸出的格式。 您也可以新增自訂接聽項型別。  
  
 您可以使用 `add` 來指定要使用的追蹤接聽項名稱與型別。 在我們的組態範例中，我們將接聽項命名為 `traceListener` 並將標準 .NET Framework 追蹤接聽項 (`System.Diagnostics.XmlWriterTraceListener`) 當成要使用的型別加入。 您可以為每一個來源新增任何數量的追蹤接聽項。 如果追蹤接聽項將追蹤發出到檔案中，則您必須在組態檔中指定輸出檔案位置與名稱。 您可以將 `initializeData` 設定為該接聽項的檔案名稱來完成。 如果您沒有指定檔案名稱，就會根據使用的接聽項型別產生隨機檔案名稱。 如果使用了 <xref:System.Diagnostics.XmlWriterTraceListener>，則會產生不含副檔名的檔名。 如果您實作自訂接聽項，也可以同時使用此屬性來接收初始化資料 (而不是檔名)。 例如，您可以為此屬性指定資料庫識別項。  
  
 您可以設定自訂追蹤接聽項，以將追蹤傳送到 Wire，例如傳送至遠端資料庫。 身為應用程式的部署者，您應該在遠端電腦的追蹤記錄上強制執行適當的存取控制。  
  
 您也可以使用程式設計方式來設定追蹤接聽項。 如需詳細資訊，請參閱 [如何：建立和初始化追蹤](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) 接聽項，以及 [建立自訂 TraceListener](/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)。  
  
> [!CAUTION]
> 因為 `System.Diagnostics.XmlWriterTraceListener` 不具備執行緒安全，追蹤來源可能會在輸出追蹤時特別鎖定資源。 當許多執行緒將追蹤輸出至設定為使用此接聽項的追蹤來源時，可能會發生資源爭用的情況，進而造成顯著的效能問題。 若要解決這個問題，您應該實作具備執行緒安全的自訂接聽項。  
  
## <a name="trace-level"></a>追蹤層級  
 追蹤層級是透過追蹤來源的 `switchValue` 設定來控制。 下表描述可使用的追蹤層級。  
  
|追蹤層級|追蹤事件的本質|追蹤事件的內容|追蹤事件|使用者目標|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|關閉|N/A|N/A|未發出任何追蹤。|N/A|  
|重大|「負面」事件：指出未預期處理或錯誤狀況的事件。||已記錄包含下列的未處理例外狀況：<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (CLR 會叫用任何 ThreadAbortExceptionHandler) <br />-無法攔截到 StackOverflowException () <br />-ConfigurationErrorsException<br />-SEHException<br />-應用程式啟動錯誤<br />-Failfast 事件<br />-系統停止回應<br />-有害訊息：導致應用程式失敗的訊息追蹤。|Administrators<br /><br /> 應用程式開發人員|  
|錯誤|「負面」事件：指出未預期處理或錯誤狀況的事件。|發生未預期的處理。 應用程式無法如預期般執行工作。 然而，應用程式仍舊繼續執行。|已記錄所有例外狀況。|Administrators<br /><br /> 應用程式開發人員|  
|警告|「負面」事件：指出未預期處理或錯誤狀況的事件。|潛在問題已經發生或是可能發生，但是應用程式仍舊正常運作。 然而，它可能無法繼續正常運作。|-應用程式收到的要求超過其節流設定所允許的數目。<br />-接收的佇列接近設定的最大容量。<br />-已超過超時。<br />-認證遭到拒絕。|Administrators<br /><br /> 應用程式開發人員|  
|資訊|「正面」事件：標示成功里程碑的事件|不管應用程式是否正常運作，都屬於應用程式執行的重要與成功里程碑。|一般來說，會產生對監控與診斷系統狀態、衡量效能，或描述分析有幫助的訊息。 您可以使用這類資訊來進行容量規劃與效能管理：<br /><br /> -建立通道。<br />-已建立端點接聽程式。<br />-Message 進入/離開傳輸。<br />-已取出安全性權杖。<br />-Configuration 設定為 read。|Administrators<br /><br /> 應用程式開發人員<br /><br /> 產品開發人員。|  
|「詳細資訊」|「正面」事件：標示成功里程碑的事件。|發出使用者程式碼和服務的低層級事件。|一般來說，您可以使用此層級來進行偵錯或應用程式最佳化。<br /><br /> -瞭解訊息標頭。|Administrators<br /><br /> 應用程式開發人員<br /><br /> 產品開發人員。|  
|ActivityTracing||介於處理活動與元件之間的流程事件。|這個層級可以讓系統管理員與開發人員相互關聯相同應用程式定義域中的多個應用程式：<br /><br /> -活動界限的追蹤，例如啟動/停止。<br />-傳輸追蹤。|全部|  
|全部||應用程式可以正常運作。 已發出所有事件。|所有先前的事件。|全部|  
  
 從「詳細資訊」到「嚴重」的層級會彼此交互堆疊，也就是說，每一個追蹤層級都會包含其上的所有層級 (除了「關閉」層級以外)。 例如，在「警告」層級上接聽的接聽項會收到「嚴重」、「錯誤」以及「警告」追蹤。 「全部」層級包含從「詳細資訊」到「嚴重」與「活動」追蹤事件的所有事件。  
  
> [!CAUTION]
> 「資訊」、「詳細資訊」以及「ActivityTracing」層級會產生許多追蹤，如果您已經用完電腦上所有可用的資源，則這些追蹤可能會對訊息輸送量產生負面的影響。  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>設定活動追蹤與傳播來進行相互關聯  
 針對 `activityTracing` 屬性而指定的 `switchValue` 值可用來啟用活動追蹤，活動追蹤會為活動界限發出追蹤並在端點之間進行傳送。  
  
> [!NOTE]
> 當您在 WCF 中使用某些擴充功能時，您可能會在 <xref:System.NullReferenceException> 啟用活動追蹤時取得。 若要修正這個問題，請檢查您應用程式的組態檔，並確定追蹤來源的 `switchValue` 屬性不是設定為 `activityTracing`。  
  
 `propagateActivity` 屬性會指出是否應該將活動傳播至其他參與訊息交換的端點。 將這個值設定為 `true` 之後，您就可以使用任意兩個端點所產生的追蹤檔，來觀察一個端點上的一組追蹤如何流動至另一個端點的一組追蹤。  
  
 如需活動追蹤和傳播的詳細資訊，請參閱 [傳播](propagation.md)。  
  
 `propagateActivity`和 `ActivityTracing` 布林值都適用于 system.servicemodel TraceSource。 此 `ActivityTracing` 值也適用于任何追蹤來源，包括 WCF 或使用者定義的來源。  
  
 您無法使用具有使用者定義追蹤來源的 `propagateActivity` 屬性。 若要進行使用者程式碼活動識別碼傳播，請確定您未設定 ServiceModel `ActivityTracing`，而且讓 ServiceModel `propagateActivity` 屬性仍舊設定為 `true`。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](index.md)
- [系統管理與診斷](../index.md)
- [作法：建立和初始化追蹤接聽項](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [建立自訂的 TraceListener](/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
