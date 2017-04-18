---
title: "NoPersistScope 活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# NoPersistScope 活動
這個範例示範如何在工作流程中操作不可序列化和可處置的狀態。重要的是工作流程不會嘗試保存不可序列化的狀態，同樣重要的是可處置的物件在工作流程中使用之後一定要清除。  
  
## 示範  
 `NoPersistScope` 自訂活動和設計工具。  
  
## 使用 NoPersistZone 活動  
 當範例工作流程執行時，名為 `CreateTextWriter` 的自訂活動會建立 <xref:System.IO.TextWriter> 類型的物件，並將它儲存在工作流程變數中。<xref:System.IO.TextWriter> 是 <xref:System.IDisposable> 物件。這個 <xref:System.IO.TextWriter> 設定會在執行範例的目錄中寫入至 'out.txt' 檔案，<xref:System.Activities.Statements.WriteLine> 活動在回應您於主控台輸入的任何文字時使用這個物件。  
  
 回應邏輯執行於 `NoPersistScope` 活動中 \(其程式碼也是這個範例的一部分\)，可防止工作流程保存。如果您在主控台輸入 `unload`，主機會嘗試保存工作流程執行個體，但這項作業會逾時，因為工作流程保留在 `NoPersistScope` 中。當工作流程完成使用 <xref:System.IO.TextWriter> 時，工作流程也會利用名為 `Dispose` 的自訂活動來處置此物件。`Dispose` 活動是放置在宣告 <xref:System.IO.TextWriter> 變數之 <xref:System.Activities.Statements.TryCatch> 活動的 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區塊中，以確保 Try 區塊執行期間即使發生例外狀況，也會執行此活動。  
  
 您可以輸入 `exit` 以完成工作流程執行個體並結束程式。  
  
#### 若要執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 NoPersistZone.sln 方案。  
  
2.  若要建置方案，請按 CTRL\+SHIFT\+B 或選取 \[**建置**\] 功能表中的 \[**建置方案**\]。  
  
3.  成功建置後，按 F5 或選取 \[**偵錯**\] 功能表中的 \[**開始偵錯**\]，或者，您可以按 CTRL\+F5 或選取 \[**偵錯**\] 功能表中的 \[**啟動但不偵錯**\]，執行範例但不偵錯。  
  
#### 若要清除 \(選擇性\)  
  
1.  若要移除 SQL 執行個體存放區，請執行 Cleanup.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`  
  
## 請參閱