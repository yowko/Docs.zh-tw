---
title: 使用效能計數器
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 724580c1725cf6513e1d85f03b0abfdefb4d040a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044535"
---
# <a name="using-performance-counters"></a>使用效能計數器
這個範例會示範如何存取 Windows Communication Foundation (WCF) 效能計數器, 以及如何建立使用者定義的效能計數器。 這個範例是以[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。  
  
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
  
 這項工作也可以使用設定[編輯器工具 (svcconfigeditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)來完成。  
  
 啟用效能計數器時, 會為服務啟用整個 WCF 效能計數器套件。 .NET Framework 自動在三個層級保有效能資料：`ServiceModelService`、`ServiceModelEndpoint` 和 `ServiceModelOperation`。 這些層級中的每個層級都有效能計數器，例如「呼叫」、「每秒的呼叫數」和「未授權的安全性呼叫數」。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
### <a name="to-view-performance-data"></a>若要檢視效能資料  
  
1. 依序按一下 [**開始**]、[**執行 ...** ] `perfmon` 、輸入並按一下 **[確定],** 或從 [控制台] 選取 [系統**管理工具**], 然後按兩下 [**效能**], 以啟動 [效能監視器] 工具。  
  
    > [!NOTE]
    > 在範例程式碼執行後才能新增計數器。  
  
2. 選擇列出的效能計數器，然後按 Delete 鍵將它們刪除。  
  
3. 以滑鼠右鍵按一下 [圖表] 窗格, 然後選取 [**新增計數器**], 以新增 WCF 計數器。 在 [**新增計數器**] 對話方塊中, 選取 [效能物件] 下拉式清單方塊中的 [ **ServiceModelOperation 3.0.0.0]、[ServiceModelEndpoint 3.0.0.0] 或 [ServiceModelService 3.0.0.0** ]。 從清單中選取您要檢視的計數器。  
  
    > [!NOTE]
    > 如果電腦上沒有執行 WCF 服務, 則不會有服務的 WCF 效能計數器。  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>若要使用組態編輯器來啟用計數器  
  
1. 開啟 SvcConfigEditor.exe 的執行個體。  
  
2. 在 [檔案] 功能表上, 按一下 [**開啟**], 然後按一下 [**設定檔 ...** ]。  
  
3. 巡覽至範例應用程式的服務資料夾，並開啟 Web.config 檔案。  
  
4. 按一下設定樹狀目錄上的 [**診斷**]。  
  
5. 切換 [**診斷**] 視窗中的**效能計數器**, 以顯示 [全部]。  
  
6. 儲存組態檔並結束編輯器。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監視範例](https://go.microsoft.com/fwlink/?LinkId=193959)
