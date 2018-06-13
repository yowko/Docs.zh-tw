---
title: WCF 服務及 Windows 的事件追蹤
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809829"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF 服務及 Windows 的事件追蹤
這個範例示範如何使用 Windows Communication Foundation (WCF) 的分析追蹤功能發出的事件追蹤的 Windows (ETW) 事件。 分析追蹤是在 WCF 堆疊中允許的實際執行環境中的 WCF 服務進行疑難排解的關鍵點發出的事件。  
  
 WCF 服務中的分析追蹤追蹤，可以開啟在生產環境中對效能的影響降至最低。 這些追蹤都會做為事件發出至 ETW 工作階段。  
  
 此範例包含基本的 WCF 服務中的事件會從服務發出至事件記錄檔，您可以使用事件檢視器檢視。 它也可啟動專用的 ETW 工作階段接聽事件從 WCF 服務。 這個範例包括指令碼，可建立專用的 ETW 工作階段，用來將事件儲存到可以使用事件檢視器讀取的二進位檔中。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 EtwAnalyticTraceSample.sln 方案檔案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行此方案，請按下 CTRL+F5。  
  
     在 Web 瀏覽器中，按一下**Calculator.svc**。 服務的 WSDL 文件 URI 應該會出現在瀏覽器中。 請複製該 URI。  
  
     根據預設，服務會開始接聽連接埠 1378年上的要求 (http://localhost:1378/Calculator.svc)。  
  
4.  執行 WCF 測試用戶端 (WcfTestClient.exe)。  
  
     WCF 測試用戶端 (WcfTestClient.exe) 位於\< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir> > \Common7\IDE\ WcfTestClient.exe (預設[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]安裝目錄是 C:\Program Files\Microsoft Visual Studio 10.0)。  
  
5.  在 WCF 測試用戶端，將服務新增選取**檔案**，然後**加入服務**。  
  
     在輸入方塊中加入端點位址。 預設值為 http://localhost:1378/Calculator.svc。  
  
6.  開啟 [事件檢視器] 應用程式。  
  
     之前叫用服務，啟動 [事件檢視器] 並確認事件記錄檔正在接聽從 WCF 服務發出的追蹤事件。  
  
7.  從**啟動**功能表上，選取**系統管理工具**，然後**事件檢視器**。  啟用**分析**和**偵錯**記錄檔。  
  
8.  在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後按一下**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**應用程式伺服器-應用程式**，選取**檢視**，然後**顯示分析與偵錯記錄檔**。  
  
     請確認**顯示分析與偵錯記錄檔**核取選項。  
  
9. 啟用**分析**記錄檔。  
  
     在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後按一下**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**分析**選取**啟用記錄**。  
  
#### <a name="to-test-the-service"></a>若要測試服務  
  
1.  切換回 WCF 測試用戶端，並按兩下`Divide`並保留預設值，其中將分母指定為 0。  
  
     如果分母為 0，則服務會擲回錯誤。  
  
2.  請查看服務所發出的事件。  
  
     切換回 [事件檢視器] 並瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後按一下**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**分析**選取**重新整理**。  
  
     WCF 分析追蹤事件會在事件檢視器中顯示。 請注意，由於服務擲回錯誤，因此事件檢視器中會顯示錯誤追蹤事件。  
  
3.  重複步驟 1 和 2，但使用有效的輸入。 `N2` 參數的值可以是 0 以外的任何數字。  
  
     重新整理分析通道，就會看見 WCF 事件未包含任何錯誤事件。  
  
 此範例示範 WCF 服務所發出的分析追蹤事件。  
  
#### <a name="to-cleanup-optional"></a>若要清除 (選擇性)  
  
1.  開啟 [事件檢視器]。  
  
2.  瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**分析**選取**停用記錄**。  
  
3.  瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。 以滑鼠右鍵按一下**分析**選取**清除記錄檔**。  
  
4.  選擇**清除**選項可清除事件。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)
