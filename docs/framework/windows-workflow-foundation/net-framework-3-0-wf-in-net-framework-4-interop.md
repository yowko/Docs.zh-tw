---
title: "在具有 Interop 活動的 .NET Framework 4 中使用 .NET Framework 3.0 WF 活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 在具有 Interop 活動的 .NET Framework 4 中使用 .NET Framework 3.0 WF 活動
 <xref:System.Activities.Statements.Interop> 活動是 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (WF 4.5) 活動包裝 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] (WF 3.5) 活動 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程。 WF 3 活動可以是單一分葉活動，也可以是完整的活動樹狀。 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 活動的執行 (包括取消及例外狀況處理) 與保存會發生於執行中的 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程執行個體的內容中。  
  
> [!NOTE]
>   <xref:System.Activities.Statements.Interop> 活動不會顯示在工作流程設計工具的工具箱除非工作流程的專案具有其 **目標 Framework** 設定設為 **.NET Framework 4.5**。  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>搭配 Interop 活動使用 WF 3 活動的準則  
 WF 3 活動內成功執行 <xref:System.Activities.Statements.Interop> 活動，必須符合下列準則︰  
  
-   WF 3 活動必須衍生自 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName>。  
  
-   WF 3 活動必須宣告為 `public`，而不可宣告為 `abstract`。  
  
-   WF 3 活動必須具有公用的預設建構函式。  
  
-   因為在介面中的限制類型 <xref:System.Activities.Statements.Interop> 活動可支援， <xref:System.Workflow.Activities.HandleExternalEventActivity> 和 <xref:System.Workflow.Activities.CallExternalMethodActivity> 不能直接使用但衍生活動可以用於建立使用工作流程通訊活動] 工具 (WCA.exe)。 請參閱 [Windows Workflow Foundation 工具](http://go.microsoft.com/fwlink/?LinkId=178889) 如需詳細資訊。  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>設定 Interop 活動內的 WF3 活動  
 若要設定和跨互通界限 WF 3 活動內外傳遞資料，WF 3 活動的屬性和中繼資料屬性所公開 <xref:System.Activities.Statements.Interop> 活動。 WF 3 活動的中繼資料屬性 (例如 <xref:System.Workflow.ComponentModel.Activity.Name%2A>) 透過公開 <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> 集合。 這是名稱/值組的集合，用於定義 WF3 活動之中繼資料屬性的值。 中繼資料屬性是由相依性屬性支援的屬性 <xref:System.Workflow.ComponentModel.DependencyPropertyOptions> 旗標設定。  
  
 WF 3 活動的屬性透過公開 <xref:System.Activities.Statements.Interop.ActivityProperties%2A> 集合。 這是一組名稱 / 值組，其中每個值 <xref:System.Activities.Argument> 物件，用於定義 WF 3 活動之屬性的引數。 由於無法推斷 WF 3 活動屬性的方向，每個屬性會呈現為 <xref:System.Activities.InArgument>/<xref:System.Activities.OutArgument> 配對。 根據活動的使用方式的屬性，您可能想要提供 <xref:System.Activities.InArgument> 項目， <xref:System.Activities.OutArgument> 項目，或兩者。 預期的名稱 <xref:System.Activities.InArgument> 集合中的項目是在 WF 3 活動定義屬性的名稱。 預期的名稱 <xref:System.Activities.OutArgument> 集合中的項目是屬性的名稱和字串"Out"的串連。  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>在 Interop 活動內使用 WF3 活動的限制  
 WF 3 系統提供的活動不可直接包裝在 <xref:System.Activities.Statements.Interop> 活動。 對部分 WF 3 活動，例如 <xref:System.Workflow.Activities.DelayActivity>, ，這是因為有類似的 WF 4.5 活動。 對其他活動而言，則是因為不支援該活動的功能。 所包裝的工作流程中，可以使用許多 WF 3 系統提供活動 <xref:System.Activities.Statements.Interop> 活動，但必須遵守下列限制︰  
  
1.  <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.Receive> 不能在 <xref:System.Activities.Statements.Interop> 活動。  
  
2.  <xref:System.Workflow.Activities.WebServiceInputActivity>, ，<xref:System.Workflow.Activities.WebServiceOutputActivity>, ，和 <xref:System.Workflow.Activities.WebServiceFaultActivity> 不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
3.  <xref:System.Workflow.Activities.InvokeWorkflowActivity> 不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
4.  <xref:System.Workflow.ComponentModel.SuspendActivity> 不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
5.  與補償相關的活動不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
 也有一些行為的特殊事項，以了解有關 WF 3 活動內使用 <xref:System.Activities.Statements.Interop> 活動︰  
  
1.  WF 3 活動內含 <xref:System.Activities.Statements.Interop> 活動時初始化 <xref:System.Activities.Statements.Interop> 活動執行。 在 WF 4.5 中，工作流程執行個體執行前沒有初始化階段。  
  
2.  WF 4.5 執行階段不會檢查點工作流程執行個體狀態在交易開始時，無論該交易的開始 (內部或外部的 <xref:System.Activities.Statements.Interop> 活動)。  
  
3.  WF 3 追蹤記錄內的活動 <xref:System.Activities.Statements.Interop> 活動提供給 WF 4.5 追蹤參與者做為 <xref:System.Activities.Tracking.InteropTrackingRecord> 物件。 <xref:System.Activities.Tracking.InteropTrackingRecord> 是 <xref:System.Activities.Tracking.CustomTrackingRecord>。  
  
4.  WF 3 自訂活動可以使用互通環境內的工作流程佇列存取資料，方式就和在 WF3 工作流程執行階段中完全相同。 不需要變更任何自訂活動程式碼。 在主機上的資料會加入 wf3 工作流程佇列繼續 <xref:System.Activities.Bookmark>。 書籤的名稱是字串的形式 <xref:System.IComparable> 工作流程佇列名稱。  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 4.5 工作流程中使用.NET Framework 3.0 或.NET Framework 3.5 活動](../../../docs/framework/windows-workflow-foundation/samples/using-a-net-3-0-or-net-3-5-activity-in-a-net-4-5-workflow.md)