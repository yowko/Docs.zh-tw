---
title: WCF 分析追蹤
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 490c67c92407626a67ea8561a378ef3e70266fe2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243660"
---
# <a name="wcf-analytic-tracing"></a>WCF 分析追蹤

這個範例會示範如何將您自己的追蹤事件加入至分析追蹤的資料流程中，Windows Communication Foundation (WCF) 寫入中的 ETW [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 。 分析追蹤的用意在於輕鬆取得服務的可視性，而不必付出高效能的代價。 此範例說明如何使用 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> api 來撰寫與 WCF 服務整合的事件。  
  
 如需 api 的詳細資訊 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> ，請參閱 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> 。  
  
 若要深入瞭解 Windows 中的事件追蹤，請參閱 [使用 ETW 改善調試和效能微調](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)。  
  
## <a name="disposing-eventprovider"></a>處置 EventProvider  

 此範例使用實作 <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> 的 <xref:System.IDisposable?displayProperty=nameWithType> 類別。 在執行 WCF 服務的追蹤時，您可能會在 <xref:System.Diagnostics.Eventing.EventProvider> 服務的存留期內使用的資源。 因此，為了便於讀取，此範例絕不會處置已包裝的 <xref:System.Diagnostics.Eventing.EventProvider>。 如果您的服務因為任何原因而有不同的追蹤需求，而且您必須處置這個資源，則應根據處置 Unmanaged 資源的最佳作法修改此範例。 如需處置非受控資源的詳細資訊，請參閱實 [作為處置方法](../../../standard/garbage-collection/implementing-dispose.md)。  
  
## <a name="self-hosting-vs-web-hosting"></a>自我裝載與 Web 裝載的比較  

 若為 Web 託管服務，WCF 的分析追蹤會提供稱為 "HostReference" 的欄位，用來識別發出追蹤的服務。 可延伸的使用者追蹤可以參與這個模型，而且此範例會示範其最佳作法。 當管道 ' &#124; ' 字元實際出現在產生的字串中時，Web 主機參考的格式可以是下列其中一項：  
  
- 如果應用程式不在根目錄：  
  
     \<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
- 如果應用程式在根目錄：  
  
     \<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
 對於自我裝載的服務，WCF 的分析追蹤不會填入 "HostReference" 欄位。 此範例中的 `WCFUserEventProvider` 類別與自我裝載之服務所使用的類別行為一致。  
  
## <a name="custom-event-details"></a>自訂事件詳細資料  

 WCF 的 ETW 事件提供者資訊清單會定義三個事件，而這些事件是設計成由 WCF 服務作者從服務程式代碼中發出。 下表為顯示這三個事件的分解。  
  
|事件|描述|事件識別碼|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|在服務中發生需要注意但不是問題的事件，發出此事件。 例如，您可能會在成功呼叫資料庫之後發出事件。|301|  
|UserDefinedWarningOccurred|發生未來可能導致失敗的問題時，發出此事件。 例如，當資料庫的呼叫失敗，但您能夠透過恢復成多餘的資料存放區來復原時，您可能會發出警告事件。|302|  
|UserDefinedErrorOccurred|當您的服務無法如預期運作時，發出此事件。 例如，如果資料庫的呼叫失敗，而且您無法從其他地方擷取資料，您可能會發出事件。|303|  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1. 使用 Visual Studio 2012，開啟 WCFAnalyticTracingExtensibility .sln 方案檔。  
  
2. 若要建置此方案，請按 CTRL+SHIFT+B。  
  
3. 若要執行此方案，請按下 CTRL+F5。  
  
     在網頁瀏覽器中，按一下 [ **計算機**]。 服務的 WSDL 文件 URI 應該會出現在瀏覽器中。 請複製該 URI。  
  
4.  ( # A0) 中執行 WCF 測試用戶端。  
  
     WCF 測試用戶端 ( # A0) 位於 `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe` 。 預設的 Visual Studio 2012 安裝目錄是 `C:\Program Files\Microsoft Visual Studio 10.0` 。  
  
5. 在 WCF 測試用戶端 **中，依序選取 [** 檔案] 和 [ **新增服務**] 來加入服務。  
  
     在輸入方塊中加入端點位址。  
  
6. 按一下 **[確定]** 關閉對話方塊。  
  
     ICalculator 服務會新增至 [ **我的服務專案**] 下的左窗格中。  
  
7. 開啟 [事件檢視器] 應用程式。  
  
     在叫用服務之前，請先開始事件檢視器，並確定事件記錄檔正在接聽從 WCF 服務發出的追蹤事件。  
  
8. 從 [ **開始** ] 功能表選取 [系統 **管理工具**]，然後 **事件檢視器**]。 啟用 **分析** 和 **調試** 記錄。  
  
9. 在事件檢視器的樹狀檢視中，流覽至 [ **事件檢視器**]、[ **應用程式及服務記錄** 檔]、[ **Microsoft**]、[ **Windows**]、[ **應用程式伺服器應用程式**]。 以滑鼠右鍵按一下 [ **應用程式伺服器-應用程式**]，選取 [ **View**]，然後 **顯示分析和偵錯工具記錄**。  
  
     確定已核取 [ **顯示分析和偵錯工具記錄** 檔] 選項。 啟用 **分析** 記錄檔。  
  
     在事件檢視器的樹狀檢視中，流覽至 [**事件檢視器**]、[**應用程式及服務記錄** 檔]、[ **Microsoft**]、[ **Windows**]、[**應用程式伺服器-應用程式**] 和 [**分析** 以滑鼠右鍵按一下 [ **分析** ]，然後選取 [ **啟用記錄**]。  
  
10. 使用 WCF 測試用戶端測試此服務。  
  
    1. 在 WCF 測試用戶端中，按兩下 [ICalculator 服務] 節點底下的 [ **加入] ( # B1** 。  
  
         **Add ( # B1** 方法會出現在右窗格中，其中包含兩個參數。  
  
    2. 輸入 2 供第一個參數使用，並輸入 3 供第二個參數使用。  
  
    3. 按一下 **[** 叫用] 以叫用方法。  
  
11. 移至您已經開啟的 **事件檢視器** 視窗。 流覽至 **事件檢視器**、 **應用程式和服務記錄** 檔、 **Microsoft**、 **Windows**、 **應用程式伺服器-應用程式**。  
  
12. 以滑鼠右鍵按一下 [ **分析** ] 節點， **然後選取 [** 重新整理]。  
  
     這些事件會出現在右窗格中。  
  
13. 找出識別碼為 303 的事件，然後按兩下它即可開啟並檢查其內容。  
  
     此事件是由 `Add()` ICalculator 服務的方法發出，且承載等於 "2 + 3 = 5"。  
  
#### <a name="to-clean-up-optional"></a>若要清除 (選擇性)  
  
1. 開啟 [事件檢視器]。  
  
2. 流覽至 **事件檢視器**、 **應用程式和服務記錄** 檔、 **Microsoft**、 **Windows**，然後流覽至 **應用程式伺服器應用程式**。 以滑鼠右鍵按一下 [ **分析** ]，然後選取 [ **停用記錄**]。  
  
3. 流覽至 **事件檢視器**、 **應用程式和服務記錄** 檔、 **Microsoft**、 **Windows**、 **應用程式伺服器應用程式**，然後進行 **分析**。 以滑鼠右鍵按一下 [ **分析** ]，然後選取 [ **清除記錄** 檔]。  
  
4. 按一下 [ **清除** ] 以清除事件。  
  
## <a name="known-issue"></a>已知問題  

 **事件檢視器** 中有一個已知的問題，可能無法解碼 ETW 事件。 您可能會看到一則錯誤訊息，指出：「 \<id> 找不到來自來源 Microsoft Windows-Application Server-Applications 的事件識別碼描述。 可能是引發此事件的元件未安裝在您的本機電腦上，或安裝已損毀。 您可以在本機電腦上安裝或修復元件。」 如果您遇到這個錯誤，請 **從 [** **動作** ] 功能表中選取 [重新整理]。 接著，事件應該就會正確解碼。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](/previous-versions/appfabric/ff383407(v=azure.10))
