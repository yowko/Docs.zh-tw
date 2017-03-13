---
title: "逐步解說：篩選 My.Application.Log 輸出 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Log 物件，篩選輸出"
  - "My.Application.Log 物件，篩選輸出"
  - "應用程式事件記錄檔，輸出篩選"
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# 逐步解說：篩選 My.Application.Log 輸出 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本逐步解說示範如何變更預設記錄檔篩選 `My.Application.Log` 物件，以控制哪些資訊會從傳遞 `Log` 的接聽程式及哪些資訊由接聽程式所寫入的物件。 因為組態資訊儲存在應用程式的組態檔中，您可以建置應用程式，即使變更記錄行為。  
  
## <a name="getting-started"></a>快速入門  
 每個訊息， `My.Application.Log` 寫入都具有相關聯的嚴重性層級，哪一個篩選機制用來控制記錄輸出。 此範例應用程式使用 `My.Application.Log` 方法來寫入數個不同的嚴重性層級記錄訊息。  
  
#### <a name="to-build-the-sample-application"></a>若要建置範例應用程式  
  
1.  開啟新 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] Windows 應用程式專案。  
  
2.  加入名為 form1 Button1 的按鈕。  
  
3.  在 <xref:System.Windows.Forms.Control.Click> Button1 事件處理常式中加入下列程式碼︰  
  
     [!code-vb[VbVbcnMyApplicationLogFiltering#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-filtering-my-application-log-output_1.vb)]  
  
4.  偵錯工具執行應用程式。  
  
5.  按下 **Button1**。  
  
     應用程式會寫入應用程式的偵錯輸出與記錄檔中的下列資訊。  
  
     `DefaultSource Information: 0 : In Button1_Click`  
  
     `DefaultSource Error: 2 : Error in the application.`  
  
6.  關閉應用程式。  
  
     如需如何檢視應用程式的偵錯輸出] 視窗，請參閱 [輸出] 視窗](../Topic/Output%20Window.md)。 應用程式的記錄檔的位置上的資訊，請參閱 [逐步解說︰ 判斷其中 My.Application.Log 寫入資訊](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)。  
  
    > [!NOTE]
    >  根據預設，應用程式的應用程式關閉時清除記錄檔輸出。  
  
     在上述範例，第二次呼叫 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> 方法，並以呼叫 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> 方法會產生記錄輸出，在第一個和最後一個呼叫時 `WriteEntry` 方法不會執行。 這是因為的嚴重性層級 `WriteEntry` 和 `WriteException` 是 「 資訊 」 和 「 錯誤 」，這兩種所允許的 `My.Application.Log` 物件的預設記錄檔篩選。 不過，事件的 「 開始 」 和 「 停止 」 的嚴重性層級會防止產生記錄輸出。  
  
## <a name="filtering-for-all-myapplicationlog-listeners"></a>篩選所有 My.Application.Log 接聽程式  
  `My.Application.Log` 物件會使用 <xref:System.Diagnostics.SourceSwitch> 名為 `DefaultSwitch` 來控制其訊息傳遞從 `WriteEntry` 和 `WriteException` 記錄檔接聽程式的方法。 您可以設定 `DefaultSwitch` 應用程式的組態檔，其值設定為其中一個 <xref:System.Diagnostics.SourceLevels> 列舉值。 根據預設，其值為 「 資訊 」。  
  
 下表顯示嚴重性層級所需的記錄檔，以將訊息寫入接聽程式，提供特定 `DefaultSwitch` 設定。  
  
|||  
|-|-|  
|DefaultSwitch 值|所需的輸出訊息嚴重性|  
|`Critical`|`Critical`|  
|`Error`|`Critical` 或 `Error`|  
|`Warning`|`Critical`、`Error` 或 `Warning`|  
|`Information`|`Critical`、`Error`、`Warning` 或 `Information`|  
|`Verbose`|`Critical`、`Error`、`Warning`、`Information` 或 `Verbose`|  
|`ActivityTracing`|`Start`、`Stop`、`Suspend`、`Resume` 或 `Transfer`|  
|`All`|允許所有訊息。|  
|`Off`|所有訊息會遭到都封鎖。|  
  
> [!NOTE]
>   `WriteEntry` 和 `WriteException` 方法都會有未指定嚴重性層級的多載。 隱含的嚴重性層級 `WriteEntry` 多載是 「 資訊 」，而且隱含的嚴重性層級 `WriteException` 是 「 錯誤 」 的多載。  
  
 下表說明上一個範例中所顯示的記錄檔輸出︰ 預設 `DefaultSwitch` 設定的 「 資訊 」，第二個呼叫 `WriteEntry` 方法，並以呼叫 `WriteException` 方法產生記錄輸出。  
  
#### <a name="to-log-only-activity-tracing-events"></a>若記錄唯一活動追蹤事件  
  
1.  以滑鼠右鍵按一下 app.config 中的 **方案總管] 中** ，然後選取 **開啟**。  
  
     -或-  
  
     如果沒有 app.config 檔案︰  
  
    1.  在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。  
  
    2.  在 [加入新項目]  對話方塊中，選擇 [應用程式組態檔] 。  
  
    3.  按一下 [加入] 。  
  
2.  找出 `<switches>` 區段中，也就是在 `<system.diagnostics>` 區段中，也就是在最上層 `<configuration>` 一節。  
  
3.  尋找項目加入 `DefaultSwitch` 參數的集合。 它看起來應該類似於這個項目︰  
  
     `<add name="DefaultSwitch" value="Information" />`  
  
4.  值變更 `value` 屬性設定為 「 ActivityTracing 」。  
  
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
  
6.  偵錯工具執行應用程式。  
  
7.  按下 **Button1**。  
  
     應用程式會寫入應用程式的偵錯輸出與記錄檔中的下列資訊︰  
  
     `DefaultSource Start: 4 : Entering Button1_Click`  
  
     `DefaultSource Stop: 5 : Leaving Button1_Click`  
  
8.  關閉應用程式。  
  
9. 值變更 `value` 屬性 「 資訊 」。  
  
    > [!NOTE]
    >   `DefaultSwitch` 切換只設定控制 `My.Application.Log`。 它不會變更如何 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] <xref:System.Diagnostics.Trace?displayProperty=fullName> 和 <xref:System.Diagnostics.Debug?displayProperty=fullName> 類別的行為。  
  
## <a name="individual-filtering-for-myapplicationlog-listeners"></a>個別篩選 My.Application.Log 接聽程式  
 先前的範例示範如何變更所有篩選 `My.Application.Log` 輸出。 此範例示範如何篩選個別的記錄檔接聽程式。 根據預設，應用程式會有兩個接聽程式的應用程式的偵錯輸出和記錄檔的寫入。  
  
 組態檔控制記錄檔接聽程式的行為可以讓每個有篩選條件，也就是類似的交換器 `My.Application.Log`。 記錄檔接聽程式會輸出一則訊息，才允許這兩個記錄訊息的嚴重性 `DefaultSwitch` 和記錄檔接聽程式的篩選。  
  
 這個範例示範如何設定新的偵錯接聽程式的篩選，並將它加入至 `Log` 物件。 預設的偵錯接聽程式應該從 `Log` 物件，這樣就能偵錯訊息來自新的偵錯接聽程式。  
  
#### <a name="to-log-only-activity-tracing-events"></a>記錄只活動追蹤事件  
  
1.  以滑鼠右鍵按一下 app.config 中的 **方案總管] 中** 選擇 **開啟**。  
  
     -或-  
  
     如果沒有 app.config 檔案︰  
  
    1.  在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。  
  
    2.  在 [加入新項目]  對話方塊中，選擇 [應用程式組態檔] 。  
  
    3.  按一下 [加入] 。  
  
2.  以滑鼠右鍵按一下 app.config 中的 **方案總管] 中**。 選擇 **開啟**。  
  
3.  找出 `<listeners>` 區段的 `<source>` 區段 `name` 屬性 」 預設資料來源 」，也就是下 `<sources>` 一節。  `<sources>` 區段低於 `<system.diagnostics>` 區段中的，在最上層 `<configuration>` 一節。  
  
4.  將此項目加入 `<listeners>` 區段︰  
  
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
  
      <xref:System.Diagnostics.EventTypeFilter> 篩選條件要花其中 <xref:System.Diagnostics.SourceLevels> 列舉值做為其 `initializeData` 屬性。  
  
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
  
8.  偵錯工具執行應用程式。  
  
9. 按下 **Button1**。  
  
     應用程式會寫入應用程式的記錄檔中的下列資訊︰  
  
     `Default Information: 0 : In Button1_Click`  
  
     `Default Error: 2 : Error in the application.`  
  
     應用程式會將較少資訊寫入應用程式的偵錯輸出因為更嚴格的篩選。  
  
     `Default Error   2   Error`  
  
10. 關閉應用程式。  
  
 如需在部署後變更記錄設定的詳細資訊，請參閱 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說︰ 判斷 My.Application.Log 寫入資訊](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)   
 [逐步解說︰ 變更 My.Application.Log 寫入資訊](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)   
 [逐步解說︰ 建立自訂記錄檔接聽程式](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)   
 [如何︰ 寫入記錄訊息](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [追蹤參數](../Topic/Trace%20Switches.md)   
 [記錄來自應用程式的資訊](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)