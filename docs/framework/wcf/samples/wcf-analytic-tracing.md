---
title: "WCF 分析追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c238d4c923b00a6c3387caa9bdafd69b126753c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-analytic-tracing"></a>WCF 分析追蹤
此範例示範如何將您自己的追蹤事件加入至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 寫入到 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 之 ETW 的分析追蹤資料流。 分析追蹤的用意在於輕鬆取得服務的可視性，而不必付出高效能的代價。 此範例示範如何使用 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API 撰寫與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務整合的事件。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API 的詳細資訊，請參閱 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>。  
  
 若要了解有關在 Windows 事件追蹤的詳細資訊，請參閱[改善偵錯和效能微調與 ETW](http://go.microsoft.com/fwlink/?LinkId=166488)。  
  
## <a name="disposing-eventprovider"></a>處置 EventProvider  
 此範例使用實作 <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> 的 <xref:System.IDisposable?displayProperty=nameWithType> 類別。 實作 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的追蹤時，您可能會在服務的存留時間中使用 <xref:System.Diagnostics.Eventing.EventProvider> 的資源。 因此，為了便於讀取，此範例絕不會處置已包裝的 <xref:System.Diagnostics.Eventing.EventProvider>。 如果您的服務因為任何原因而有不同的追蹤需求，而且您必須處置這個資源，則應根據處置 Unmanaged 資源的最佳作法修改此範例。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]處置 unmanaged 的資源，請參閱[實作 Dispose 方法](http://go.microsoft.com/fwlink/?LinkId=166436)。  
  
## <a name="self-hosting-vs-web-hosting"></a>自我裝載與Web 裝載  
 為 Web 託管服務，WCF 的分析追蹤會提供名為"HostReference"，這用來識別發出追蹤服務的欄位。 可延伸的使用者追蹤可以參與這個模型，而且此範例會示範其最佳作法。 格式，Web 主控件的參考時管道 ' &#124;' 字元實際出現在產生字串可以是下列任何一個：  
  
-   如果應用程式不在根目錄：  
  
     \<站台名稱 >\<ApplicationVirtualPath > &#124;\<ServiceVirtualPath > &#124;\<ServiceName >  
  
-   如果應用程式在根目錄：  
  
     \<站台名稱 > &#124;\<ServiceVirtualPath > &#124;\<ServiceName >  
  
 對於自我裝載服務，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]的分析追蹤不會填入"HostReference"欄位。 此範例中的 `WCFUserEventProvider` 類別與自我裝載之服務所使用的類別行為一致。  
  
## <a name="custom-event-details"></a>自訂事件詳細資料  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的 ETW 事件提供者資訊清單會定義設計為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務作者從服務程式碼中所發出的三個事件。 下表為顯示這三個事件的分解。  
  
|事件|描述|事件 ID|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|在服務中發生需要注意但不是問題的事件，發出此事件。 例如，您可能會在成功呼叫資料庫之後發出事件。|301|  
|UserDefinedWarningOccurred|發生未來可能導致失敗的問題時，發出此事件。 例如，當資料庫的呼叫失敗，但您能夠透過恢復成多餘的資料存放區來復原時，您可能會發出警告事件。|302|  
|UserDefinedErrorOccurred|當您的服務無法如預期運作時，發出此事件。 例如，如果資料庫的呼叫失敗，而且您無法從其他地方擷取資料，您可能會發出事件。|303|  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 WCFAnalyticTracingExtensibility.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
     在 Web 瀏覽器中，按一下**Calculator.svc**。 服務的 WSDL 文件 URI 應該會出現在瀏覽器中。 請複製該 URI。  
  
4.  執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 測試用戶端 (WcfTestClient.exe)。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]測試用戶端 (WcfTestClient.exe) 位於\< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir> > \Common7\IDE\ WcfTestClient.exe (預設[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]安裝目錄是 C:\Program Files\Microsoft Visual Studio 10.0)。  
  
5.  內[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]測試用戶端中，選取 加入服務**檔案**，然後**加入服務**。  
  
     在輸入方塊中加入端點位址。  
  
6.  按一下**確定**以關閉對話方塊。  
  
     ICalculator 服務會在左窗格中加入**我的服務專案**。  
  
7.  開啟 [事件檢視器] 應用程式。  
  
     叫用服務之前，啟動 [事件檢視器] 並確認事件記錄正在接聽從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務發出的追蹤事件。  
  
8.  從**啟動**功能表上，選取**系統管理工具**，然後**事件檢視器**。 啟用**分析**和**偵錯**記錄檔。  
  
9. 在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後按一下**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**應用程式伺服器-應用程式**，選取**檢視**，然後**顯示分析與偵錯記錄檔**。  
  
     請確認**顯示分析與偵錯記錄檔**核取選項。 啟用**分析**記錄檔。  
  
     在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**，然後**分析**。 以滑鼠右鍵按一下**分析**選取**啟用記錄**。  
  
10. 使用 WCF 測試用戶端測試此服務。  
  
    1.  在 WCF 測試用戶端中，按兩下**add （)** ICalculator 服務節點下。  
  
         **Add （)**方法會出現在右窗格具有兩個參數。  
  
    2.  輸入 2 供第一個參數使用，並輸入 3 供第二個參數使用。  
  
    3.  按一下**Invoke**叫用方法。  
  
11. 移至**事件檢視器**已經開啟的視窗。 瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器應用程式**。  
  
12. 以滑鼠右鍵按一下**分析**節點，然後選取**重新整理**。  
  
     這些事件會出現在右窗格中。  
  
13. 找出識別碼為 303 的事件，然後按兩下它即可開啟並檢查其內容。  
  
     此事件由發出`Add()`ICalculator 服務的方法，且其裝載等於"2 + 3 = 5"。  
  
#### <a name="to-clean-up-optional"></a>若要清除 (選擇性)  
  
1.  開啟**事件檢視器**。  
  
2.  瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**分析**選取**停用記錄**。  
  
3.  瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**，然後**分析**。 以滑鼠右鍵按一下**分析**選取**清除記錄檔**。  
  
4.  按一下**清除**可清除事件。  
  
## <a name="known-issue"></a>已知問題  
 中的已知問題**事件檢視器**位置可能無法為 ETW 事件解碼。 您可能會看到錯誤訊息，指出: 「 事件識別碼的描述\<識別碼 > 來源 Microsoft Windows 應用程式伺服器-應用程式找不到。 本機電腦可能並未安裝引發此事件的元件，或安裝已損毀。 您可以安裝或修復本機電腦上的元件。 」 如果您遇到這個錯誤，請選取**重新整理**從**動作**功能表。 接著，事件應該就會正確解碼。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)
