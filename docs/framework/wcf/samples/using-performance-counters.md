---
title: "使用效能計數器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: 31
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 31
---
# 使用效能計數器
這個範例會示範如何存取 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 效能計數器，以及如何建立使用者定義的效能計數器。這個範例是以[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 在這個範例中，用戶端呼叫 `ICalculator` 服務的四個方法。用戶端持續此操作，直到被使用者中斷為止。服務維持不變。  
  
 效能計數器在用於服務的 Web.config 檔案之診斷區段中啟用，如下列範例組態中所示。  
  
```  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 也可以使用 [組態編輯器工具 \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) 完成此工作。  
  
 當效能監視器啟用時，啟用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 效能計數器的整個套件供服務使用。.NET Framework 自動在三個層級保有效能資料：`ServiceModelService`、`ServiceModelEndpoint` 和 `ServiceModelOperation`。這些層級中的每個層級都有效能計數器，例如「呼叫」、「每秒的呼叫數」和「未授權的安全性呼叫數」。  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
### 若要檢視效能資料  
  
1.  按一下 \[**開始**\]、\[**執行**\]，輸入 `perfmon` 後按一下 \[**確定**\]，或從 \[控制台\] 中選取 \[**系統管理工具**\]，然後按兩下 \[**效能**\] 來啟動 \[效能監視器\] 工具。  
  
    > [!NOTE]
    >  在範例程式碼執行後才能新增計數器。  
  
2.  選擇列出的效能計數器，然後按 Delete 鍵將它們刪除。  
  
3.  以滑鼠右鍵按一下 \[圖形\] 窗格並選取 \[**加入計數器**\] 來新增 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]。在 \[**新增計數器**\] 對話方塊中，選取 \[效能物件\] 下拉式清單方塊中的 \[**ServiceModelOperation 3.0.0.0、ServiceModelEndpoint 3.0.0.0 或 ServiceModelService 3.0.0.0** \]。從清單中選取您要檢視的計數器。  
  
    > [!NOTE]
    >  如果電腦上沒有正在執行的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，就沒有服務的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 效能計數器。  
  
### 若要使用組態編輯器來啟用計數器  
  
1.  開啟 SvcConfigEditor.exe 的執行個體。  
  
2.  在 \[檔案\] 功能表上，按一下 \[**開啟**\]，然後按一下 \[**組態檔**\]。  
  
3.  巡覽至範例應用程式的服務資料夾，並開啟 Web.config 檔案。  
  
4.  按一下組態樹狀目錄上的 \[**診斷**\]。  
  
5.  切換 \[**診斷**\] 視窗中的 \[**效能計數器**\] 以顯示全部。  
  
6.  儲存組態檔並結束編輯器。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## 請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)