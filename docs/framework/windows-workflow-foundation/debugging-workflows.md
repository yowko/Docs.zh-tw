---
title: "偵錯工作流程 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 偵錯工作流程
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]提供一些從開發環境進行偵錯工作流程的選項。  可在設計工具、XAML 與程式碼中將工作流程偵錯。  
  
## 在工作流程設計工具中偵錯  
 可反白活動並按下 **F9** 鍵，或使用活動的內容功能表，在工作流程設計工具中設定活動的中斷點。  執行工作流程，然後當工作流程主機正在偵錯模式中執行時中斷。  在下列螢幕擷取畫面中，工作流程的執行已暫停於一個中斷點。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][使用工作流程設計工具偵錯工作流程](../Topic/Debugging%20Workflows%20with%20the%20Workflow%20Designer.md)。  
  
## 在 XAML 中偵錯  
 如果工作流程在設計工具中的中斷點上暫停，即可在 XAML 中偵錯工作流程。  若要在 XAML 中檢視執行點，請在暫停工作流程的執行時，選取工作流程設計工具中的 \[**XAML 檢視**\]。  從解決方案總管的設計工具中重新開啟工作流程，即可將偵錯切換回設計工具。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][HOW TO：使用工作流程設計工具偵測 XAML](../Topic/How%20to:%20Debug%20XAML%20with%20the%20Workflow%20Designer.md)。  
  
## 在程式碼中偵錯  
 在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中使用程式碼中斷點的方式與用於其他命令式應用程式相同。  按一下程式碼窗格的左邊界來建立程式碼中斷點，或按下 **F9** 鍵來將中斷點放置於游標的位置。  
  
## 附加至工作流程處理序  
 工作流程偵錯也支援使用 Visual Studio 的基礎結構來附加至處理序。  這可讓工作流程的作者在不同的主機環境中 \(例如 Internet Information Services \(IIS\) 7.0\) 執行時偵錯工作流程。  
  
## 遠端偵錯  
 [!INCLUDE[wf](../../../includes/wf-md.md)] 遠端偵錯的運作方式與其他 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 元件的遠端偵錯功能相同。  如需使用遠端偵錯的詳細資訊，請參閱[HOW TO：啟用遠端偵錯](http://go.microsoft.com/fwlink/?LinkId=196257)。  
  
> [!NOTE]
>  如果工作流程應用程式的目標為 x86 架構，並裝載在執行 64 位元作業系統的電腦上，則遠端偵錯將不會運作，除非 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 安裝在遠端電腦上，或工作流程應用程式的目標變更為 \[**任何 CPU**\]。  
  
## 擴充工作流程偵錯服務  
 現在已公開工作流程偵錯程式服務，且可用於建立自訂應用程式，例如在重新裝載的設計工具中監控、模擬和偵錯。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] <xref:System.Activities.Presentation.Debug.DebuggerService> 主題。