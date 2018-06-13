---
title: 篩選 My.Application.Log 輸出 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: 43ac92cefe717b4bfa64969839b289e944980b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591881"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a>逐步解說：篩選 My.Application.Log 輸出 (Visual Basic)
本逐步解說示範如何變更 `My.Application.Log` 物件的預設記錄檔篩選，以控制哪些資訊會從 `Log` 物件傳遞至接聽程式，而哪些資訊會由接聽程式寫入。 由於組態資訊是儲存在應用程式的組態檔中，因此即使在建置應用程式之後，您仍可以變更記錄行為。  
  
## <a name="getting-started"></a>快速入門  
 `My.Application.Log` 寫入的每個訊息都有相關聯的嚴重性層級，而篩選機制會使用這個層級來控制記錄檔輸出。 此範例應用程式會使用 `My.Application.Log` 方法，寫入數個不同嚴重性層級的記錄檔訊息。  
  
#### <a name="to-build-the-sample-application"></a>若要安裝範例應用程式  
  
1.  開啟新的 Visual Basic Windows 應用程式專案。  
  
2.  加入名為 "Button1 to Form1" 的按鈕。  
  
3.  在 Button1 的 <xref:System.Windows.Forms.Control.Click> 事件處理常式中新增下列程式碼：  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  在偵錯工具中執行應用程式。  
  
5.  按下 **Button1**。  
  
     應用程式會將下列資訊寫入應用程式的偵錯輸出與記錄檔中。  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  關閉應用程式。  
  
     如需如何檢視應用程式偵錯輸出視窗的資訊，請參閱[輸出視窗](/visualstudio/ide/reference/output-window)。 如需應用程式記錄檔位置的資訊，請參閱[逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)。  
  
    > [!NOTE]
    >  根據預設，應用程式會在應用程式關閉時清除記錄檔輸出。  
  
     在上述範例，第二次呼叫 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> 方法和呼叫 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> 方法會產生記錄輸出，而第一次和最後一次呼叫 `WriteEntry` 方法則不會。 這是因為 `WriteEntry` 和 `WriteException` 的嚴重性層級為 "Information" 和 "Error"，兩者皆為 `My.Application.Log` 物件的預設記錄檔篩選所允許。 不過，具有 "Start" 和 "Stop" 嚴重性層級的事件會阻礙記錄檔輸出的產生。  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>篩選所有 My.Application.Log 接聽程式  
 `My.Application.Log` 物件會使用名為 `DefaultSwitch` 的 <xref:System.Diagnostics.SourceSwitch>，來控制要將 `WriteEntry` 和 `WriteException` 方法的哪些訊息傳遞給記錄檔接聽程式。 您可以將 `DefaultSwitch` 的值設定為 <xref:System.Diagnostics.SourceLevels> 列舉值之一，以在應用程式的組態檔中設定它。 根據預設，其值為 "Information"。  
  
 下表顯示依據特定 `DefaultSwitch` 設定的假設，記錄檔要將訊息寫入接聽程式所需的嚴重性層級。  
  
|DefaultSwitch 值|輸出所需的訊息嚴重性|  
|---|---| 
|`Critical`|`Critical`|  
|`Error`|`Critical` 或 `Error`|  
|`Warning`|`Critical`、 `Error`或 `Warning`|  
|`Information`|`Critical`、`Error`、`Warning` 或 `Information`|  
|`Verbose`|`Critical`、`Error`、`Warning`、`Information` 或 `Verbose`|  
|`ActivityTracing`|`Start`、`Stop`、`Suspend`、`Resume` 或 `Transfer`|  
|`All`|允許所有訊息。|  
|`Off`|封鎖所有訊息。|  
  
> [!NOTE]
>  `WriteEntry` 和 `WriteException` 方法都有未指定嚴重性層級的多載。 `WriteEntry` 多載的隱含嚴重性層級是 "Information"，而 `WriteException` 多載的隱含嚴重性層級是 "Error"。  
  
 下表說明上一個範例中所顯示的記錄檔輸出︰使用 "Information" 的預設 `DefaultSwitch` 設定時，僅有第二個 `WriteEntry` 方法呼叫，以及 `WriteException` 方法呼叫會產生記錄檔輸出。  
  
#### <a name="to-log-only-activity-tracing-events"></a>若只要記錄活動追蹤事件  
  
1.  在方案總管中，以滑鼠右鍵按一下 app.config，並選取 [開啟]。  
  
     -或-  
  
     如果沒有 app.config 檔案︰  
  
    1.  在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。  
  
    2.  在 [加入新項目]  對話方塊中，選擇 [應用程式組態檔] 。  
  
    3.  按一下 [加入]。  
  
2.  找出位於最上層 `<configuration>` 區段中 `<system.diagnostics>` 區段的 `<switches>` 區段。  
  
3.  尋找可將 `DefaultSwitch` 新增至參數集合的項目。 該項目應該與下列項目類似：  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  將 `value` 屬性值變更為 "ActivityTracing"。  
  
5.  App.config 檔案的內容應該類似下列 XML：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="ActivityTracing" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
6.  在偵錯工具中執行應用程式。  
  
7.  按下 **Button1**。  
  
     應用程式會將下列資訊寫入應用程式的偵錯輸出與記錄檔中：  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  關閉應用程式。  
  
9. 將 `value` 屬性值變更回 "Information"。  
  
    > [!NOTE]
    >  `DefaultSwitch` 參數設定只會控制 `My.Application.Log`。 它不會變更 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Debug?displayProperty=nameWithType> 類別的行為。  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>個別篩選 My.Application.Log 接聽程式  
 上一個範例示範如何變更所有 `My.Application.Log` 輸出的篩選。 此範例示範如何篩選個別的記錄檔接聽程式。 應用程式預設會有兩個接聽程式，以寫入應用程式的偵錯輸出和記錄檔。  
  
 組態檔可讓每個記錄檔接聽程式都有一個篩選條件 (類似 `My.Application.Log` 的參數)，以控制記錄檔接聽程式的行為。 僅有當記錄檔的 `DefaultSwitch` 和記錄檔接聽程式的篩選條件皆允許訊息的嚴重性時，記錄檔接聽程式才會輸出訊息。  
  
 此範例示範如何設定新偵錯接聽程式的篩選，並將它新增至 `Log` 物件。 您應該從 `Log` 物件移除預設的偵錯接聽程式，以保證偵錯訊息是來自新的偵錯接聽程式。  
  
#### <a name="to-log-only-activity-tracing-events"></a>若只要記錄活動追蹤事件  
  
1.  在方案總管中，以滑鼠右鍵按一下 app.config，並選擇 [開啟]。  
  
     -或-  
  
     如果沒有 app.config 檔案︰  
  
    1.  在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。  
  
    2.  在 [加入新項目]  對話方塊中，選擇 [應用程式組態檔] 。  
  
    3.  按一下 [加入] 。  
  
2.  在方案總管中，以滑鼠右鍵按一下 app.config。 選擇 [開啟]。  
  
3.  找出 `<listeners>` 區段，其位於具有 `name` 屬性 "DefaultSource" 之 `<source>` 區段中的 `<sources>` 區段下方。 `<sources>` 區段位於最上層 `<configuration>` 區段中的 `<system.diagnostics>` 區段下方。  
  
4.  將此項目新增至 `<listeners>` 區段：  
  
    ```xml  
    <!-- Remove the default debug listener. -->  
    <remove name="Default"/>  
    <!-- Add a filterable debug listener. -->  
    <add name="NewDefault"/>  
    ```  
  
5.  找出位於最上層 `<sharedListeners>` 區段中 `<system.diagnostics>` 區段的 `<configuration>` 區段。  
  
6.  將此項目加入至該 `<sharedListeners>` 區段︰  
  
    ```xml  
    <add name="NewDefault"   
         type="System.Diagnostics.DefaultTraceListener,   
               System, Version=2.0.0.0, Culture=neutral,   
               PublicKeyToken=b77a5c561934e089,   
               processorArchitecture=MSIL">  
        <filter type="System.Diagnostics.EventTypeFilter"   
                initializeData="Error" />  
    </add>  
    ```  
  
     <xref:System.Diagnostics.EventTypeFilter> 篩選會採用 <xref:System.Diagnostics.SourceLevels> 列舉值之一作為其 `initializeData` 屬性。  
  
7.  App.config 檔案的內容應該類似下列 XML：  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <!-- This section configures My.Application.Log -->  
          <source name="DefaultSource" switchName="DefaultSwitch">  
            <listeners>  
              <add name="FileLog"/>  
              <!-- Remove the default debug listener. -->  
              <remove name="Default"/>  
              <!-- Add a filterable debug listener. -->  
              <add name="NewDefault"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="DefaultSwitch" value="Information" />  
        </switches>  
        <sharedListeners>  
          <add name="FileLog"  
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
                     Microsoft.VisualBasic, Version=8.0.0.0,   
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,   
                     processorArchitecture=MSIL"   
               initializeData="FileLogWriter"/>  
          <add name="NewDefault"   
               type="System.Diagnostics.DefaultTraceListener,   
                     System, Version=2.0.0.0, Culture=neutral,   
                     PublicKeyToken=b77a5c561934e089,   
                     processorArchitecture=MSIL">  
            <filter type="System.Diagnostics.EventTypeFilter"   
                    initializeData="Error" />  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
8.  在偵錯工具中執行應用程式。  
  
9. 按下 **Button1**。  
  
     應用程式會將下列資訊寫入應用程式的記錄檔中：  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     由於篩選更加嚴格，因此應用程式會將較少資訊寫入應用程式的偵錯輸出。  
  
     `Default Error   2   Error`  
  
10. 關閉應用程式。  
  
 如需在部署後變更記錄檔設定的詳細資訊，請參閱[使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)。  
  
## <a name="see-also"></a>請參閱  
 [逐步解說：判斷 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [逐步解說：變更 My.Application.Log 寫入資訊的位置](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [逐步解說：建立自訂的記錄檔接聽程式](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 [如何：寫入記錄檔訊息](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [追蹤參數](../../../../framework/debug-trace-profile/trace-switches.md)  
 [記錄來自應用程式的資訊](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
