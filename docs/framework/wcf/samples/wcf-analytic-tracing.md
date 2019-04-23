---
title: WCF 分析追蹤
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 9ed89bdbe2469a96f2a959c9fda8442e80b6f7ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332309"
---
# <a name="wcf-analytic-tracing"></a>WCF 分析追蹤
這個範例會示範如何將您自己的追蹤事件加入至 Windows Communication Foundation (WCF) 寫入至 ETW 的分析追蹤的資料流[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]。 分析追蹤的用意在於輕鬆取得服務的可視性，而不必付出高效能的代價。 此範例示範如何使用<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>Api 來與 WCF 服務整合的寫入事件。  
  
 如需詳細資訊<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>Api，請參閱<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>。  
  
 若要深入了解在 Windows 事件追蹤，請參閱[改善偵錯和效能調整使用 ETW](https://go.microsoft.com/fwlink/?LinkId=166488)。  
  
## <a name="disposing-eventprovider"></a>處置 EventProvider  
 此範例使用實作 <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> 的 <xref:System.IDisposable?displayProperty=nameWithType> 類別。 在實作 WCF 服務的追蹤時，很可能您可以使用<xref:System.Diagnostics.Eventing.EventProvider>的服務的存留期內的資源。 因此，為了便於讀取，此範例絕不會處置已包裝的 <xref:System.Diagnostics.Eventing.EventProvider>。 如果您的服務因為任何原因而有不同的追蹤需求，而且您必須處置這個資源，則應根據處置 Unmanaged 資源的最佳作法修改此範例。 如需有關如何處置 unmanaged 的資源的詳細資訊，請參閱[實作 Dispose 方法](https://go.microsoft.com/fwlink/?LinkId=166436)。  
  
## <a name="self-hosting-vs-web-hosting"></a>自我裝載與Web 裝載  
 為 Web 託管服務，WCF 的分析追蹤會提供名為"HostReference"，用以識別發出追蹤服務的欄位。 可延伸的使用者追蹤可以參與這個模型，而且此範例會示範其最佳作法。 格式的 Web 主機參考當管道 '&#124;' 字元實際出現在產生字串可以是下列任一項：  
  
-   如果應用程式不在根目錄：  
  
     \<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
-   如果應用程式在根目錄：  
  
     \<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
 對於自我裝載的服務，WCF 的分析追蹤不會填入"HostReference"欄位。 此範例中的 `WCFUserEventProvider` 類別與自我裝載之服務所使用的類別行為一致。  
  
## <a name="custom-event-details"></a>自訂事件詳細資料  
 WCF 的 ETW 事件提供者資訊清單會定義三種專為 WCF 服務作者從服務程式碼中發出的事件。 下表為顯示這三個事件的分解。  
  
|Event - 事件|描述|事件 ID|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|在服務中發生需要注意但不是問題的事件，發出此事件。 例如，您可能會在成功呼叫資料庫之後發出事件。|301|  
|UserDefinedWarningOccurred|發生未來可能導致失敗的問題時，發出此事件。 例如，當資料庫的呼叫失敗，但您能夠透過恢復成多餘的資料存放區來復原時，您可能會發出警告事件。|302|  
|UserDefinedErrorOccurred|當您的服務無法如預期運作時，發出此事件。 例如，如果資料庫的呼叫失敗，而且您無法從其他地方擷取資料，您可能會發出事件。|303|  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1. 使用 Visual Studio 2012，請開啟 WCFAnalyticTracingExtensibility.sln 方案檔案。  
  
2. 若要建置此方案，請按 CTRL+SHIFT+B。  
  
3. 若要執行此方案，請按下 CTRL+F5。  
  
     在網頁瀏覽器中，按一下**Calculator.svc**。 服務的 WSDL 文件 URI 應該會出現在瀏覽器中。 請複製該 URI。  
  
4. 執行 WCF 測試用戶端 (WcfTestClient.exe)。  
  
     WCF 測試用戶端 (WcfTestClient.exe) 位於`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`。 預設 Visual Studio 2012 的安裝目錄是`C:\Program Files\Microsoft Visual Studio 10.0`。  
  
5. 在 WCF 測試用戶端，將服務新增所選取**檔案**，然後**加入服務**。  
  
     在輸入方塊中加入端點位址。  
  
6. 按一下 **確定**以關閉對話方塊。  
  
     ICalculator 服務會在左窗格中加入**我的服務專案**。  
  
7. 開啟 [事件檢視器] 應用程式。  
  
     之前叫用服務，啟動 [事件檢視器] 並確認事件記錄檔正在接聽從 WCF 服務所發出的追蹤事件。  
  
8. 從**開始**功能表上，選取**系統管理工具**，然後**事件檢視器**。 啟用**分析**並**偵錯**記錄檔。  
  
9. 在樹狀檢視中 事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**應用程式伺服器-應用程式**，選取**檢視**，然後**顯示分析與偵錯記錄檔**。  
  
     請確認**顯示分析與偵錯記錄檔**核取選項。 啟用**分析**記錄檔。  
  
     在樹狀檢視中 事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**，然後**分析**。 以滑鼠右鍵按一下**分析**，然後選取**啟用記錄**。  
  
10. 使用 WCF 測試用戶端測試此服務。  
  
    1.  在 WCF 測試用戶端中，按兩下**add （)** ICalculator 服務節點底下。  
  
         **Add （)** 方法會出現在右窗格具有兩個參數。  
  
    2.  輸入 2 供第一個參數使用，並輸入 3 供第二個參數使用。  
  
    3.  按一下  **Invoke**叫用方法。  
  
11. 移至**事件檢視器**您已經開啟的視窗。 瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**。  
  
12. 以滑鼠右鍵按一下**分析**節點，然後選取**重新整理**。  
  
     這些事件會出現在右窗格中。  
  
13. 找出識別碼為 303 的事件，然後按兩下它即可開啟並檢查其內容。  
  
     此事件由發出`Add()`ICalculator 服務的方法，且其裝載等於"2 + 3 = 5"。  
  
#### <a name="to-clean-up-optional"></a>若要清除 (選擇性)  
  
1. 開啟**事件檢視器**。  
  
2. 瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**分析**，然後選取**停用記錄**。  
  
3. 瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**，然後**分析**。 以滑鼠右鍵按一下**分析**，然後選取**清除記錄檔**。  
  
4. 按一下 **清除**可清除事件。  
  
## <a name="known-issue"></a>已知問題  
 沒有已知的問題**事件檢視器**其中可能無法為 ETW 事件解碼。 您可能會看到錯誤訊息，指出：「 事件識別碼的描述\<識別碼 > 找不到 Microsoft Windows 應用程式伺服器-應用程式的來源。 本機電腦可能並未安裝引發此事件的元件，或安裝已損毀。 您可以安裝或修復該元件在本機電腦上的。 」 如果您遇到這個錯誤，請選取**重新整理**從**動作**功能表。 接著，事件應該就會正確解碼。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](https://go.microsoft.com/fwlink/?LinkId=193959)
