---
title: Windows Workflow Foundation 的新功能
description: 瞭解 .NET Framework 4 中的 Windows Workflow Foundation 變更。 建立、執行和維護工作流程變得更容易。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: b25b71a61f8a96d59c79e780d9fe5cd03abfa299
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419339"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>Windows Workflow Foundation 的新功能

.NET Framework 4 中的 Windows Workflow Foundation （WF）變更了舊版的幾個開發範例。 現在，建立、執行與維護工作流程以及實作新功能的主機都變得更簡單了。 如需有關遷移 .NET 3.0 和 .NET 3.5 工作流程應用程式以使用最新版本的詳細資訊，請參閱[遷移指引](migration-guidance.md)。  
  
## <a name="workflow-activity-model"></a>工作流程活動模型  
 現在建立工作流程的基底單元是活動，而非使用 <xref:System.Workflow.Activities.SequentialWorkflowActivity> 或 <xref:System.Workflow.Activities.StateMachineWorkflowActivity> 類別。 <xref:System.Activities.Activity> 類別可提供工作流程行為的基底抽象部分。 活動作者之後可以針對基本自訂活動功能實作 <xref:System.Activities.CodeActivity>，或是針對使用執行階段範圍的自訂活動功能實作 <xref:System.Activities.NativeActivity>。 <xref:System.Activities.Activity>是活動作者用來根據其他、、或物件以宣告方式表示新行為的類別 <xref:System.Activities.NativeActivity> <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.DynamicActivity> ，不論它們是自訂開發或包含在內[建活動程式庫](net-framework-4-5-built-in-activity-library.md)中。  
  
## <a name="rich-composite-activity-options"></a>豐富的複合活動選項  
 <xref:System.Activities.Statements.Flowchart> 是一個功能強大的新控制流程活動，允許作者建立任意迴圈和條件分支模型。 <xref:System.Activities.Statements.Flowchart> 提供一個事件驅動的程式設計模型，此設計模型原來只能以 <xref:System.Workflow.Activities.StateMachineWorkflowActivity> 實作。 以傳統流程控制結構為模型的新的流程控制活動 (例如 <xref:System.Activities.Statements.TryCatch> 和 <xref:System.Activities.Statements.Switch%601>) 對程序性工作流程頗有助益。  
  
## <a name="expanded-built-in-activity-library"></a>擴充的內建活動程式庫  
 活動程式庫的新功能包括：  
  
- 新的流程控制活動，例如 <xref:System.Activities.Statements.DoWhile>、<xref:System.Activities.Statements.Pick>、<xref:System.Activities.Statements.TryCatch>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.Switch%601> 和 <xref:System.Activities.Statements.ParallelForEach%601>。  
  
- 用於處理成員資料的活動 (例如 <xref:System.Activities.Statements.Assign>) 與集合活動 (例如 <xref:System.Activities.Statements.AddToCollection%601>)。  
  
- 用於控制交易的活動，例如 <xref:System.Activities.Statements.TransactionScope> 和 <xref:System.Activities.Statements.Compensate>。  
  
- 新的傳訊活動，例如 <xref:System.ServiceModel.Activities.SendContent> 和 <xref:System.ServiceModel.Activities.ReceiveReply>。  
  
## <a name="explicit-activity-data-model"></a>明確的活動資料模型  
 .NET Framework 4 包含儲存或移動資料的新選項。 使用 <xref:System.Activities.Variable> 可將資料儲存在活動中。 將資料移入與移出活動時，會使用特殊的引數型別來判斷資料的移動方向。 這些型別為 <xref:System.Activities.InArgument>、<xref:System.Activities.InOutArgument> 與 <xref:System.Activities.OutArgument>。 如需詳細資訊，請參閱[Windows Workflow Foundation 資料模型](data-model.md)。  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>增強型裝載、保存及追蹤選項  
 .NET Framework 4 包含持續性增強功能，如下所示：  
  
- 此外，還有更多用於執行工作流程的選項，包括 <xref:System.ServiceModel.Activities.WorkflowServiceHost>、<xref:System.Activities.WorkflowApplication> 與 <xref:System.Activities.WorkflowInvoker>。  
  
- 使用 <xref:System.Activities.Statements.Persist> 活動可明確保存工作流程狀態資料。  
  
- 主機可以保存而不卸載 <xref:System.Activities.ActivityInstance>。  
  
- 工作流程可以指定不保存區，同時處理不能保存的資料，將持續性延遲到不保存區結束為止。  
  
- 使用 <xref:System.Activities.Statements.TransactionScope> 可以將異動流動至工作流程中。  
  
- 使用 <xref:System.Activities.Tracking.TrackingParticipant> 可更輕鬆地完成追蹤。  
  
- 系統事件記錄檔追蹤會使用 <xref:System.Activities.Tracking.EtwTrackingParticipant> 提供。  
  
- 現在，恢復暫止中的工作流程會利用 <xref:System.Activities.Bookmark> 物件來管理。  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>更易於擴充 WF 設計工具經驗的能力  
 新的 WF 設計工具是以 Windows Presentation Foundation （WPF）為基礎，可提供更簡單的模型，讓您在 Visual Studio 之外重新裝載 WF 設計工具，也提供更簡單的機制來建立自訂活動設計工具。 如需詳細資訊，請參閱[自訂工作流程設計經驗](customizing-the-workflow-design-experience.md)。
