---
title: 使用效能計數器
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143573"
---
# <a name="using-performance-counters"></a>使用效能計數器
此示例演示如何訪問 Windows 通信基礎 （WCF） 效能計數器以及如何創建使用者定義的效能計數器。 此示例基於[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 在這個範例中，用戶端呼叫 `ICalculator` 服務的四個方法。 用戶端持續此操作，直到被使用者中斷為止。 服務維持不變。  
  
 效能計數器在用於服務的 Web.config 檔案之診斷區段中啟用，如下列範例組態中所示。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 此任務也可以使用[配置編輯器工具 （SvcConfigEditor.exe）](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)完成。  
  
 啟用效能計數器後，將為服務啟用整個 WCF 效能計數器套件。 .NET Framework 自動在三個層級保有效能資料：`ServiceModelService`、`ServiceModelEndpoint` 和 `ServiceModelOperation`。 這些層級中的每個層級都有效能計數器，例如「呼叫」、「每秒的呼叫數」和「未授權的安全性呼叫數」。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 要在單電腦或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
### <a name="to-view-performance-data"></a>若要檢視效能資料  
  
1. 通過按一下"**開始**、**運行..."、** 輸入`perfmon`並按一下"**確定"** 或"從控制台"啟動效能監視器工具，選擇 **"管理工具**"並按兩下 **"性能**"。  
  
    > [!NOTE]
    > 在範例程式碼執行後才能新增計數器。  
  
2. 選擇列出的效能計數器，然後按 Delete 鍵將它們刪除。  
  
3. 通過按右鍵圖形窗格並選擇 **"添加計數器**"來添加 WCF 計數器。 在 **"添加計數器"** 對話方塊中，在"性能"物件下拉式清單方塊中選擇 **"服務模型操作 3.0.0.0"、服務模型終結點 3.0.0.0 或"服務模型服務 3.0.0.0"。"** 下拉式清單方塊中。 從清單中選取您要檢視的計數器。  
  
    > [!NOTE]
    > 如果電腦上沒有運行 WCF 服務，則服務沒有 WCF 效能計數器。  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>若要使用組態編輯器來啟用計數器  
  
1. 開啟 SvcConfigEditor.exe 的執行個體。  
  
2. 在"檔"功能表上，按一下 **"打開"，** 然後按一下"**設定檔..."。**  
  
3. 巡覽至範例應用程式的服務資料夾，並開啟 Web.config 檔案。  
  
4. 按一下"配置樹上的**診斷**"。  
  
5. 在 **"診斷"** 視窗中切換**效能計數器**以顯示"全部"。  
  
6. 儲存組態檔並結束編輯器。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
