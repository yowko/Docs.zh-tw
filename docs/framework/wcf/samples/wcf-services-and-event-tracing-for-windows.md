---
title: WCF 服務及 Windows 的事件追蹤
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183204"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF 服務及 Windows 的事件追蹤
此示例演示如何使用 Windows 通信基礎 （WCF） 中的分析跟蹤在 Windows 事件跟蹤 （ETW） 中發出事件。 分析跟蹤是在 WCF 堆疊中的關鍵點發出的事件，允許在生產環境中對 WCF 服務進行故障排除。

 WCF 服務中的分析跟蹤是可在生產環境中打開的跟蹤，對性能的影響最小。 這些追蹤都會做為事件發出至 ETW 工作階段。

 此示例包括一個基本的 WCF 服務，其中事件從服務發送到事件日誌，可以使用事件檢視器查看。 還可以啟動專用 ETW 會話，該會話偵聽來自 WCF 服務的事件。 這個範例包括指令碼，可建立專用的 ETW 工作階段，用來將事件儲存到可以使用事件檢視器讀取的二進位檔中。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2012，打開 EtwAnalyticTraceSample.sln 解決方案檔。

2. 若要建置此方案，請按 CTRL+SHIFT+B。

3. 若要執行此方案，請按下 CTRL+F5。

     在 Web 瀏覽器中，按一下**計算機.svc**。 服務的 WSDL 文件 URI 應該會出現在瀏覽器中。 請複製該 URI。

     預設情況下，服務開始偵聽埠 1378`http://localhost:1378/Calculator.svc`上的請求。

4. 運行 WCF 測試用戶端 （WcfTestClient.exe）。

     WCF 測試用戶端 （WcfTestClient.exe） 位於`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`。  預設的 Visual Studio 2012`C:\Program Files\Microsoft Visual Studio 10.0`安裝 dir 是 。

5. 在 WCF 測試用戶端中，通過選擇**File**添加服務，然後**添加服務**。

     在輸入方塊中加入端點位址。 預設值為 `http://localhost:1378/Calculator.svc`。

6. 開啟 [事件檢視器] 應用程式。

     在調用服務之前，啟動事件檢視器並確保事件日誌偵聽從 WCF 服務發出的事件。

7. 在 **"開始"** 功能表中，選擇 **"管理工具**"，然後選擇**事件檢視器**。  啟用**分析和****調試**日誌。

8. 在事件檢視器中的樹狀檢視中，導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows，** 然後是**應用程式伺服器應用程式**。 按右鍵**應用程式伺服器應用程式**，選擇 **"查看**"，然後**顯示分析和調試日誌**。

     確保選中 **"顯示分析日誌"和"調試日誌"** 選項。

9. 啟用**分析**日誌。

     在事件檢視器中的樹狀檢視中，導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows，** 然後是**應用程式伺服器應用程式**。 按右鍵 **"分析"** 並選擇**啟用日誌**。

#### <a name="to-test-the-service"></a>若要測試服務

1. 切換回 WCF 測試用戶端並按兩下`Divide`並保留預設值，其中指定分母 0。

     如果分母為 0，則服務會擲回錯誤。

2. 請查看服務所發出的事件。

     切換回事件檢視器，並導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows，** 然後是**應用程式伺服器應用程式**。 按右鍵 **"分析"** 並選擇 **"刷新**"。

     WCF 分析追蹤事件會在事件檢視器中顯示。 請注意，由於服務擲回錯誤，因此事件檢視器中會顯示錯誤追蹤事件。

3. 重複步驟 1 和 2，但使用有效的輸入。 `N2` 參數的值可以是 0 以外的任何數字。

     重新整理分析通道，就會看見 WCF 事件未包含任何錯誤事件。

 此範例示範 WCF 服務所發出的分析追蹤事件。

#### <a name="to-cleanup-optional"></a>若要清除 (選擇性)

1. 開啟 [事件檢視器]。

2. 導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows，** 然後是**應用程式-伺服器應用程式**。 按右鍵 **"分析"** 並選擇 **"禁用日誌**"。

3. 導航到**事件檢視器**、**應用程式和服務日誌**、**微軟****、Windows，** 然後是**應用程式-伺服器應用程式**。 按右鍵 **"分析"** 並選擇 **"清除日誌**"。

4. 選擇 **"清除"** 選項以清除事件。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
