---
title: 在 Visual Basic 中使用應用程式記錄檔
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 9e62224ba4d53e09416819ca68004063dd189551
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592037"
---
# <a name="working-with-application-logs-in-visual-basic"></a>在 Visual Basic 中使用應用程式記錄檔
`My.Applicaton.Log` 和 `My.Log` 物件讓您輕鬆地將記錄和追蹤資訊寫入記錄檔。  
  
## <a name="how-messages-are-logged"></a>記錄訊息的方式  
 首先，會以記錄檔之 <xref:System.Diagnostics.TraceSource.Switch%2A> 屬性中的 <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> 屬性檢查訊息的嚴重性。 根據預設，只有嚴重性為「資訊」和更高等級的訊息會傳遞至追蹤接聽項 (該追蹤接聽項於記錄檔的 `TraceListener` 集合中指定)。 然後，每個接聽程式會將訊息嚴重性和接聽程式的 <xref:System.Diagnostics.TraceSource.Switch%2A> 屬性進行比較。 如果訊息的嚴重性夠高，接聽程式會寫出訊息。  
  
 下列圖表顯示寫入至 `WriteEntry` 方法的訊息如何傳遞至記錄檔追蹤接聽項的 `WriteLine` 方法︰  
  
 ![My 記錄檔呼叫](../../../../visual-basic/developing-apps/programming/log-info/media/mylogcall.png "MyLogCall")  
  
 您可以藉由變更應用程式的組態檔來變更記錄檔和追蹤接聽項的行為。 下列圖表顯示記錄檔組件和組態檔之間的通信。  
  
 ![My 記錄檔組態](../../../../visual-basic/developing-apps/programming/log-info/media/mylogconfig.png "MyLogConfig")  
  
## <a name="where-messages-are-logged"></a>記錄訊息的位置  
 如果組件沒有組態檔， `My.Application.Log` 和 `My.Log` 物件會寫入至應用程式的偵錯輸出 (透過 <xref:System.Diagnostics.DefaultTraceListener> 類別)。 此外，`My.Application.Log` 物件會寫入組件的記錄檔 (透過 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> 類別)，而 `My.Log` 物件會寫入 ASP.NET 網頁的輸出 (透過 <xref:System.Web.WebPageTraceListener> 類別)。  
  
 以偵錯模式執行應用程式時，您可以在 Visual Studio [輸出] 視窗中檢視偵錯輸出。 若要開啟 [輸出] 視窗，請按一下 [偵錯] 功能表項目並指向 [Windows] ，然後按一下 [輸出] 。 在 [輸出]  視窗中，從 [顯示輸出來源]  方塊中選取 [偵錯]  。  
  
 根據預設， `My.Application.Log` 寫入至位於使用者應用程式資料路徑中的記錄檔。 您可以從 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> 物件的 <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> 屬性取得路徑。 該路徑的格式如下所示︰  
  
 `BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`  
  
 `BasePath` 的一般值如下所示。  
  
 C:\Documents and Settings\\`username`\Application Data  
  
 `CompanyName`、 `ProductName`和 `ProductVersion` 的值都來自應用程式的組件資訊。 記錄檔名稱的格式為 *AssemblyName*.log，其中 *AssemblyName* 為不含副檔名的組件檔案名稱。 若需要多個記錄檔 (像是當應用程式嘗試寫入至記錄檔而原始記錄檔無法使用時)，記錄檔名稱的格式為 *AssemblyName*-*iteration*.log，其中 `iteration` 為正 `Integer`。  
  
 您可以藉由加入或變更電腦和應用程式的組態檔以覆寫預設行為。 如需詳細資訊，請參閱 [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)。  
  
## <a name="configuring-log-settings"></a>設定記錄檔設定  
 `Log` 物件具有不需應用程式組態檔 app.config 即可運作的預設實作。若要變更預設，您必須加入具有新設定的組態檔。 如需詳細資訊，請參閱 [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)。  
  
 記錄檔組態區段位於 app.config 檔案主 `<system.diagnostics>` 節點的 `<configuration>` 節點中。 記錄檔資訊在數個節點內定義︰  
  
-   `Log` 物件的接聽程式在名為 DefaultSource 的 `<sources>` 節點中定義。  
  
-   `Log` 物件的嚴重性篩選條件在名為 DefaultSwitch 的 `<switches>` 節點中定義。  
  
-   記錄檔接聽程式在 `<sharedListeners>` 節點中定義。  
  
 `<sources>`、 `<switches>`和 `<sharedListeners>` 節點的範例於下列程式碼內顯示︰  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="DefaultSource" switchName="DefaultSwitch">  
        <listeners>  
          <add name="FileLog"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="DefaultSwitch" value="Information" />  
    </switches>  
    <sharedListeners>  
      <add name="FileLog"  
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,  
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"  
        initializeData="FileLogWriter"  
      />  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="changing-log-settings-after-deployment"></a>在部署後變更記錄檔設定  
 當您開發應用程式時，其組態設定儲存在 app.config 檔案中，如上述範例所示。 部署應用程式之後，您仍然可以透過編輯組態檔來設定記錄檔。 在以 Windows 為基礎的應用程式中，此檔案名稱為 *applicationName*.exe.config，而且必須位於與可執行檔相同的資料夾內。 若為 Web 應用程式，這會是與專案關聯的 Web.config 檔案。  
  
 當應用程式第一次執行建立類別執行個體的程式碼時，會檢查組態檔是否具有物件的相關資訊。 對 `Log` 物件來說，這發生在第一次存取 `Log` 物件時。 系統只會針對組態檔是否有任何特定物件進行單次檢查，也就是在應用程式第一次建立物件時。 因此，您可能需要重新啟動應用程式以使變更生效。  
  
 在部署的應用程式中，您可以在應用程式啟動前，藉由重新設定交換器物件來啟用追蹤程式碼。 這通常涉及開啟和關閉交換器物件，或是變更追蹤層級，然後再重新啟動應用程式。  
  
## <a name="security-considerations"></a>安全性考量  
 將資料寫入至記錄檔時，請考慮下列項目︰  
  
-   **避免流失使用者資訊。** 確保您的應用程式僅將核准的資訊寫入記錄檔。 例如，應用程式記錄檔或許可以包含使用者名稱，但不能包含使用者密碼。  
  
-   **保護記錄檔位置的安全。** 任何包含潛在機密資訊的記錄都應該儲存在安全的位置。  
  
-   **避免可能造成誤導的資訊。** 一般情況下，您的應用程式應該先驗證所有使用者輸入的資料，然後才能使用該資料。 這包括將資料寫入至應用程式記錄檔。  
  
-   **避免拒絕服務的發生。** 如果您的應用程式將過多的資訊寫入記錄檔，它可能會填滿記錄檔或讓您難以尋找重要資訊。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [記錄來自應用程式的資訊](../../../../visual-basic/developing-apps/programming/log-info/logging-information-from-the-application.md)
