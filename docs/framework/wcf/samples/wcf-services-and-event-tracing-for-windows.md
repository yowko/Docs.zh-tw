---
title: WCF 服務及 Windows 的事件追蹤
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: e1ee7154e2ad5b22ff0debcdd15d5809fc55df13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044522"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF 服務及 Windows 的事件追蹤
這個範例示範如何使用 Windows Communication Foundation (WCF) 中的分析追蹤, 在 Windows 事件追蹤 (ETW) 中發出事件。 分析追蹤是在 WCF 堆疊中的關鍵點發出的事件, 可讓您在生產環境中進行 WCF 服務的疑難排解。

 WCF 服務中的分析追蹤是可以在實際執行環境中開啟的追蹤, 而且對效能的影響最小。 這些追蹤都會做為事件發出至 ETW 工作階段。

 這個範例包含基本 WCF 服務, 其中事件會從服務發出至事件記錄檔, 您可以使用事件檢視器來加以查看。 您也可以啟動專用的 ETW 會話, 以接聽來自 WCF 服務的事件。 這個範例包括指令碼，可建立專用的 ETW 工作階段，用來將事件儲存到可以使用事件檢視器讀取的二進位檔中。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2012, 開啟 [EtwAnalyticTraceSample] 方案檔。

2. 若要建置此方案，請按 CTRL+SHIFT+B。

3. 若要執行此方案，請按下 CTRL+F5。

     在網頁瀏覽器中, 按一下 [**計算機 .svc**]。 服務的 WSDL 文件 URI 應該會出現在瀏覽器中。 請複製該 URI。

     根據預設, 服務會開始接聽埠 1378 `http://localhost:1378/Calculator.svc`上的要求。

4. 執行 WCF 測試用戶端 (WcfTestClient .exe)。

     WCF 測試用戶端 (WcfTestClient) 位於`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`。  預設 Visual Studio 2012 安裝目錄是`C:\Program Files\Microsoft Visual Studio 10.0`。

5. 在 WCF 測試用戶端中, 依序選取 [檔案] 和 [**新增服務**] 來新增服務。

     在輸入方塊中加入端點位址。 預設為 `http://localhost:1378/Calculator.svc`。

6. 開啟 [事件檢視器] 應用程式。

     叫用服務之前, 請先啟動事件檢視器, 並確定事件記錄檔正在接聽從 WCF 服務發出的追蹤事件。

7. 在 **開始** 功能表中, 選取 系統**管理工具**, 然後**事件檢視器**。  啟用**分析**和**Debug**記錄。

8. 在事件檢視器的樹狀檢視中, 流覽至 [**事件檢視器**]、[**應用程式及服務記錄**檔]、[ **Microsoft**]、[ **Windows**] 和 [**應用程式伺服器應用程式**]。 以滑鼠右鍵按一下 [**應用程式伺服器-應用程式**], 選取 [ **View**], 然後**顯示 [分析與偵錯工具記錄**]。

     確定已核取 [**顯示分析和偵錯工具記錄**檔] 選項。

9. 啟用**分析**記錄檔。

     在事件檢視器的樹狀檢視中, 流覽至 [**事件檢視器**]、[**應用程式及服務記錄**檔]、[ **Microsoft**]、[ **Windows**] 和 [**應用程式伺服器應用程式**]。 以滑鼠右鍵按一下 [**分析**], 然後選取 [**啟用記錄**]。

#### <a name="to-test-the-service"></a>若要測試服務

1. 切換回 [WCF 測試用戶端], 然後`Divide`按兩下並保留預設值, 其指定的分母為0。

     如果分母為 0，則服務會擲回錯誤。

2. 請查看服務所發出的事件。

     切換回事件檢視器並流覽至 [**事件檢視器**]、[**應用程式及服務記錄**檔]、[ **Microsoft**]、[ **Windows**] 和 [**應用程式伺服器應用程式**]。 以滑鼠右鍵按一下 [**分析**], 然後選取 [重新整理]。

     WCF 分析追蹤事件會在事件檢視器中顯示。 請注意，由於服務擲回錯誤，因此事件檢視器中會顯示錯誤追蹤事件。

3. 重複步驟 1 和 2，但使用有效的輸入。 `N2` 參數的值可以是 0 以外的任何數字。

     重新整理分析通道，就會看見 WCF 事件未包含任何錯誤事件。

 此範例示範 WCF 服務所發出的分析追蹤事件。

#### <a name="to-cleanup-optional"></a>若要清除 (選擇性)

1. 開啟 [事件檢視器]。

2. 流覽至**事件檢視器**、**應用程式和服務記錄**檔、 **Microsoft**、 **Windows**和**應用程式伺服器應用程式**。 以滑鼠右鍵按一下 [**分析**], 然後選取 [**停用記錄**]。

3. 流覽至**事件檢視器**、**應用程式和服務記錄**檔、 **Microsoft**、 **Windows**和**應用程式伺服器應用程式**。 以滑鼠右鍵按一下 [**分析**], 然後選取 [**清除記錄**]。

4. 選擇 [**清除**] 選項以清除事件。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監視範例](https://go.microsoft.com/fwlink/?LinkId=193959)
