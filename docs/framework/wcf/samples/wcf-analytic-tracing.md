---
title: WCF 分析追蹤
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: ef636a672d9384e8e3d658f0488cfaadb8d293e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183223"
---
# <a name="wcf-analytic-tracing"></a>WCF 分析追蹤
此示例演示如何將您自己的跟蹤事件添加到 Windows 通信基礎 （WCF） 寫入 ETW 的分析跟蹤流中[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]。 分析追蹤的用意在於輕鬆取得服務的可視性，而不必付出高效能的代價。 此示例演示如何使用<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>API 編寫與 WCF 服務集成的事件。  
  
 有關 API 的詳細資訊<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>，請參閱<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>。  
  
 要瞭解有關 Windows 中事件跟蹤的更多資訊，請參閱[使用 ETW 改進調試和性能調優](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)。  
  
## <a name="disposing-eventprovider"></a>處置 EventProvider  
 此範例使用實作 <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> 的 <xref:System.IDisposable?displayProperty=nameWithType> 類別。 實現 WCF 服務的跟蹤時，您可能會在服務的存留期內使用<xref:System.Diagnostics.Eventing.EventProvider>'的資源。 因此，為了便於讀取，此範例絕不會處置已包裝的 <xref:System.Diagnostics.Eventing.EventProvider>。 如果您的服務因為任何原因而有不同的追蹤需求，而且您必須處置這個資源，則應根據處置 Unmanaged 資源的最佳作法修改此範例。 有關處置非託管資源的詳細資訊，請參閱[實現處置方法](https://docs.microsoft.com/dotnet/standard/garbage-collection/implementing-dispose)。  
  
## <a name="self-hosting-vs-web-hosting"></a>自我裝載與 Web 裝載的比較  
 對於 Web 託管的服務，WCF 的分析跟蹤提供了一個欄位，稱為"HostReference"，用於標識發出跟蹤的服務。 可延伸的使用者追蹤可以參與這個模型，而且此範例會示範其最佳作法。 當管道"&#124;"字元實際出現在生成的字串中時，Web 主機引用的格式可以是以下任一項：  
  
- 如果應用程式不在根目錄：  
  
     \<網站名稱>\<應用程式虛擬路徑>&#124;\<服務虛擬路徑>&#124;\<服務名稱>  
  
- 如果應用程式在根目錄：  
  
     \<網站名稱>&#124;\<服務虛擬路徑>&#124;\<服務名稱>  
  
 對於自託管服務，WCF 的分析跟蹤不會填充"主機引用"欄位。 此範例中的 `WCFUserEventProvider` 類別與自我裝載之服務所使用的類別行為一致。  
  
## <a name="custom-event-details"></a>自訂事件詳細資料  
 WCF 的 ETW 事件提供程式清單定義了三個事件，這些事件旨在由 WCF 服務作者從服務代碼中發出。 下表為顯示這三個事件的分解。  
  
|事件|描述|事件識別碼|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|在服務中發生需要注意但不是問題的事件，發出此事件。 例如，您可能會在成功呼叫資料庫之後發出事件。|301|  
|UserDefinedWarningOccurred|發生未來可能導致失敗的問題時，發出此事件。 例如，當資料庫的呼叫失敗，但您能夠透過恢復成多餘的資料存放區來復原時，您可能會發出警告事件。|302|  
|UserDefinedErrorOccurred|當您的服務無法如預期運作時，發出此事件。 例如，如果資料庫的呼叫失敗，而且您無法從其他地方擷取資料，您可能會發出事件。|303|  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1. 使用 Visual Studio 2012，打開 WCF 分析跟蹤 Extens.sln 解決方案檔。  
  
2. 若要建置此方案，請按 CTRL+SHIFT+B。  
  
3. 若要執行此方案，請按下 CTRL+F5。  
  
     在 Web 瀏覽器中，按一下**計算機.svc**。 服務的 WSDL 文件 URI 應該會出現在瀏覽器中。 請複製該 URI。  
  
4. 運行 WCF 測試用戶端 （WcfTestClient.exe）。  
  
     WCF 測試用戶端 （WcfTestClient.exe） 位於`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`。 預設的 Visual Studio 2012`C:\Program Files\Microsoft Visual Studio 10.0`安裝 dir 是 。  
  
5. 在 WCF 測試用戶端中，通過選擇**File**添加服務，然後**添加服務**。  
  
     在輸入方塊中加入端點位址。  
  
6. 按一下 **[確定]** 關閉對話方塊。  
  
     I計算機服務在 **"我的服務專案**"下的左側窗格中添加。  
  
7. 開啟 [事件檢視器] 應用程式。  
  
     在調用服務之前，啟動事件檢視器並確保事件日誌偵聽從 WCF 服務發出的事件。  
  
8. 在 **"開始"** 功能表中，選擇 **"管理工具**"，然後選擇**事件檢視器**。 啟用**分析和****調試**日誌。  
  
9. 在事件檢視器中的樹狀檢視中，導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows，** 然後是**應用程式伺服器應用程式**。 按右鍵**應用程式伺服器應用程式**，選擇 **"查看**"，然後**顯示分析和調試日誌**。  
  
     確保選中 **"顯示分析日誌"和"調試日誌"** 選項。 啟用**分析**日誌。  
  
     在事件檢視器中的樹狀檢視中，導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows、****應用程式伺服器應用程式**，然後**進行分析**。 按右鍵 **"分析"** 並選擇**啟用日誌**。  
  
10. 使用 WCF 測試用戶端測試此服務。  
  
    1. 在 WCF 測試用戶端中，按兩下 I計算機服務節點下的 **"添加（"）。**  
  
         **Add（）** 方法顯示在包含兩個參數的右側窗格中。  
  
    2. 輸入 2 供第一個參數使用，並輸入 3 供第二個參數使用。  
  
    3. 按一下 **"調用"** 以調用該方法。  
  
11. 轉到已打開**的事件檢視器**視窗。 導航到**事件檢視器**，**應用程式和服務日誌**，**微軟**，**視窗**，**應用程式伺服器應用程式**.  
  
12. 按右鍵**分析**節點並選擇 **"刷新**"。  
  
     這些事件會出現在右窗格中。  
  
13. 找出識別碼為 303 的事件，然後按兩下它即可開啟並檢查其內容。  
  
     此事件由 I計算機`Add()`服務的方法發出，其有效負載等於"2+3=5"。  
  
#### <a name="to-clean-up-optional"></a>若要清除 (選擇性)  
  
1. 開啟 [事件檢視器] ****。  
  
2. 導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows，** 然後是**應用程式-伺服器應用程式**。 按右鍵 **"分析"** 並選擇 **"禁用日誌**"。  
  
3. 導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows、****應用程式-伺服器應用程式**，然後**分析**。 按右鍵 **"分析"** 並選擇 **"清除日誌**"。  
  
4. 按一下 **"清除"** 以清除事件。  
  
## <a name="known-issue"></a>已知問題  
 **事件檢視器**中存在一個已知問題，它可能無法解碼 ETW 事件。 您可能會看到一條錯誤訊息，指出："找不到源 Microsoft-Windows-\<應用程式伺服器應用程式的事件 ID>說明。 可能是引發此事件的元件未安裝在您的本機電腦上，或安裝已損毀。 您可以在本地電腦上安裝或修復元件。 如果遇到此錯誤，請從 **"操作"** 功能表中選擇 **"刷新**"。 接著，事件應該就會正確解碼。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
