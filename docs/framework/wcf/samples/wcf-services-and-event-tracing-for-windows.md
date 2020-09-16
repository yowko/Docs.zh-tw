---
title: WCF 服務及 Windows 的事件追蹤
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 38e26c369d17f4aa9ccb39d2ae649facffe65418
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552962"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF 服務及 Windows 的事件追蹤
這個範例示範如何使用 Windows Communication Foundation (WCF) 中的分析追蹤，在 Windows 的事件追蹤 (ETW) 中發出事件。 分析追蹤是在 WCF 堆疊的關鍵點發出的事件，可讓您在生產環境中進行 WCF 服務的疑難排解。

 WCF 服務中的分析追蹤是可在實際執行環境中開啟的追蹤，對效能的影響降至低。 這些追蹤都會做為事件發出至 ETW 工作階段。

 此範例包含基本的 WCF 服務，其中的事件是從服務發出到事件記錄檔，您可以使用事件檢視器來查看。 您也可以啟動專用的 ETW 會話，以接聽來自 WCF 服務的事件。 這個範例包括指令碼，可建立專用的 ETW 工作階段，用來將事件儲存到可以使用事件檢視器讀取的二進位檔中。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2012，開啟 EtwAnalyticTraceSample .sln 方案檔。

2. 若要建置此方案，請按 CTRL+SHIFT+B。

3. 若要執行此方案，請按下 CTRL+F5。

     在網頁瀏覽器中，按一下 [ **計算機**]。 服務的 WSDL 文件 URI 應該會出現在瀏覽器中。 請複製該 URI。

     根據預設，服務會開始接聽埠1378上的要求 `http://localhost:1378/Calculator.svc` 。

4.  ( # A0) 中執行 WCF 測試用戶端。

     WCF 測試用戶端 ( # A0) 位於 `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe` 。  預設的 Visual Studio 2012 安裝目錄是 `C:\Program Files\Microsoft Visual Studio 10.0` 。

5. 在 WCF 測試用戶端 **中，依序選取 [** 檔案] 和 [ **新增服務**] 來加入服務。

     在輸入方塊中加入端點位址。 預設為 `http://localhost:1378/Calculator.svc`。

6. 開啟 [事件檢視器] 應用程式。

     在叫用服務之前，請先開始事件檢視器，並確定事件記錄檔正在接聽從 WCF 服務發出的追蹤事件。

7. 從 [ **開始** ] 功能表選取 [系統 **管理工具**]，然後 **事件檢視器**]。  啟用 **分析** 和 **調試** 記錄。

8. 在事件檢視器的樹狀檢視中，流覽至 [ **事件檢視器**]、[ **應用程式及服務記錄**檔]、[ **Microsoft**]、[ **Windows**]、[ **應用程式伺服器應用程式**]。 以滑鼠右鍵按一下 [ **應用程式伺服器-應用程式**]，選取 [ **View**]，然後 **顯示分析和偵錯工具記錄**。

     確定已核取 [ **顯示分析和偵錯工具記錄** 檔] 選項。

9. 啟用 **分析** 記錄檔。

     在事件檢視器的樹狀檢視中，流覽至 [ **事件檢視器**]、[ **應用程式及服務記錄**檔]、[ **Microsoft**]、[ **Windows**]、[ **應用程式伺服器應用程式**]。 以滑鼠右鍵按一下 [ **分析** ]，然後選取 [ **啟用記錄**]。

#### <a name="to-test-the-service"></a>若要測試服務

1. 切換回 WCF 測試用戶端，然後按兩下 `Divide` 並保留預設值，以指定0的分母。

     如果分母為 0，則服務會擲回錯誤。

2. 請查看服務所發出的事件。

     切換回事件檢視器，然後流覽至 **事件檢視器**、 **應用程式和服務記錄**檔、 **Microsoft**、 **Windows**，然後 **應用程式伺服器應用程式**。 以滑鼠右鍵按一下 [ **分析** ]， **然後選取 [** 重新整理]。

     WCF 分析追蹤事件會在事件檢視器中顯示。 請注意，由於服務擲回錯誤，因此事件檢視器中會顯示錯誤追蹤事件。

3. 重複步驟 1 和 2，但使用有效的輸入。 `N2` 參數的值可以是 0 以外的任何數字。

     重新整理分析通道，就會看見 WCF 事件未包含任何錯誤事件。

 此範例示範 WCF 服務所發出的分析追蹤事件。

#### <a name="to-cleanup-optional"></a>若要清除 (選擇性)

1. 開啟 [事件檢視器]。

2. 流覽至 **事件檢視器**、 **應用程式和服務記錄**檔、 **Microsoft**、 **Windows**，然後流覽至 **應用程式伺服器應用程式**。 以滑鼠右鍵按一下 [ **分析** ]，然後選取 [ **停用記錄**]。

3. 流覽至 **事件檢視器**、 **應用程式和服務記錄**檔、 **Microsoft**、 **Windows**，然後流覽至 **應用程式伺服器應用程式**。 以滑鼠右鍵按一下 [ **分析** ]，然後選取 [ **清除記錄**檔]。

4. 選擇 [ **清除** ] 選項以清除事件。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](/previous-versions/appfabric/ff383407(v=azure.10))
