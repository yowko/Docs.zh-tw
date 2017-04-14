---
title: "WCF 服務及 Windows 的事件追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# WCF 服務及 Windows 的事件追蹤
這個範例示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的分析追蹤功能發出 Windows 事件追蹤 \(ETW\) 中的事件。  分析追蹤是在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 堆疊中的關鍵點發出，該堆疊允許在實際執行環境中進行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的疑難排解。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務中的分析追蹤是可以在實際執行環境中開啟的追蹤功能，對效能產生的影響相當小。  這些追蹤都會做為事件發出至 ETW 工作階段。  
  
 這個範例包括基本的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，其中事件會從服務發出至事件記錄檔，而使用事件檢視器即可檢視此事件記錄檔。  此外還可以啟動專用的 ETW 工作階段，以接聽來自 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的事件。  這個範例包括指令碼，可建立專用的 ETW 工作階段，用來將事件儲存到可以使用事件檢視器讀取的二進位檔中。  
  
#### 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 EtwAnalyticTraceSample.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL\+SHIFT\+B。  
  
3.  若要執行此方案，請按下 CTRL\+F5。  
  
     在 Web 瀏覽器中按一下 \[**Calculator.svc**\]。  服務的 WSDL 文件 URI 應該會出現在瀏覽器中。  請複製該 URI。  
  
     根據預設，服務會開始接聽連接埠 1378 \(http:\/\/localhost:1378\/Calculator.svc\) 上的要求。  
  
4.  執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 測試用戶端 \(WcfTestClient.exe\)。  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 測試用戶端 \(WcfTestClient.exe\) 位於 \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 安裝目錄\>\\Common7\\IDE\\ WcfTestClient.exe \(預設的 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 安裝目錄為 C:\\Program Files\\Microsoft Visual Studio 10.0\)。  
  
5.  在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 測試用戶端內依序選取 \[**檔案**\] 和 \[**新增服務**\]，藉此加入服務。  
  
     在輸入方塊中加入端點位址。  預設為 http:\/\/localhost:1378\/Calculator.svc。  
  
6.  開啟 \[事件檢視器\] 應用程式。  
  
     叫用服務之前，啟動 \[事件檢視器\] 並確認事件記錄正在接聽從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務發出的追蹤事件。  
  
7.  從 \[**開始**\] 功能表中，依序選取 \[**系統管理工具**\] 和 \[**事件檢視器**\]。  啟用 \[**分析**\] 和 \[**偵錯**\] 記錄檔。  
  
8.  在事件檢視器的樹狀檢視中，依序巡覽至 \[**事件檢視器**\]、\[**應用程式與服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\] 和 \[**應用程式伺服器\-應用程式**\]。  以滑鼠右鍵按一下 \[**應用程式伺服器\-應用程式**\]，然後依序選取 \[**檢視**\]、\[**顯示分析與偵錯記錄檔**\]。  
  
     確認已核取 \[**顯示分析與偵錯記錄檔**\] 選項。  
  
9. 啟用 \[**分析**\] 記錄檔。  
  
     在事件檢視器的樹狀檢視中，依序巡覽至 \[**事件檢視器**\]、\[**應用程式與服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\] 和 \[**應用程式伺服器\-應用程式**\]。  以滑鼠右鍵按一下 \[**分析**\]，然後選取 \[**啟用記錄**\]。  
  
#### 若要測試服務  
  
1.  切換回 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 測試用戶端，然後按兩下 `Divide` 並且保留預設值，這樣會將分母指定為 0。  
  
     如果分母為 0，則服務會擲回錯誤。  
  
2.  請查看服務所發出的事件。  
  
     切換回 \[事件檢視器\]，並依序巡覽至 \[**事件檢視器**\]、\[**應用程式及服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\] 和 \[**應用程式伺服器\-應用程式**\]。  以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**重新整理**\]。  
  
     WCF 分析追蹤事件會在事件檢視器中顯示。  請注意，由於服務擲回錯誤，因此事件檢視器中會顯示錯誤追蹤事件。  
  
3.  重複步驟 1 和 2，但使用有效的輸入。  `N2` 參數的值可以是 0 以外的任何數字。  
  
     重新整理分析通道，就會看見 WCF 事件未包含任何錯誤事件。  
  
 此範例示範 WCF 服務所發出的分析追蹤事件。  
  
#### 若要清除 \(選擇性\)  
  
1.  開啟 \[事件檢視器\]。  
  
2.  依序巡覽至 \[**事件檢視器**\]、\[**應用程式與服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\] 和 \[**應用程式伺服器\-應用程式**\]。  以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**停用記錄**\]。  
  
3.  依序巡覽至 \[**事件檢視器**\]、\[**應用程式與服務記錄檔**\]、\[**Microsoft**\]、\[**Windows**\] 和 \[**應用程式伺服器\-應用程式**\]。  以滑鼠右鍵按一下 \[**分析**\]，並選取 \[**清除記錄**\]。  
  
4.  選擇 \[**清除**\] 選項可清除事件。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。  請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[適用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。  此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## 請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)