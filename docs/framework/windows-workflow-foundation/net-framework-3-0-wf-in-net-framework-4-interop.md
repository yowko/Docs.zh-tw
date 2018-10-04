---
title: 在具有 Interop 活動的 .NET Framework 4 中使用 .NET Framework 3.0 WF 活動
ms.date: 03/30/2017
ms.assetid: 71f112ba-abb0-46f7-b05f-a5d2eb9d0c5c
ms.openlocfilehash: 386f71f21a4164f6f0ffc0ed19aab68abbe5a0b5
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48263332"
---
# <a name="using-net-framework-30-wf-activities-in-net-framework-4-with-the-interop-activity"></a>在具有 Interop 活動的 .NET Framework 4 中使用 .NET Framework 3.0 WF 活動
<xref:System.Activities.Statements.Interop> 活動是 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] (WF 4.5) 活動，它會將 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] (WF 3.5) 活動包裝在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程中。 WF 3 活動可以是單一分葉活動，也可以是完整的活動樹狀結構。 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 活動的執行 (包括取消及例外狀況處理) 與保存會發生於執行中的 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程執行個體的內容中。  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop>活動不會顯示在工作流程設計工具工具箱除非工作流程的專案具有其**目標 Framework**設定設為 **.NET Framework 4.5**。  
  
## <a name="criteria-for-using-a-wf-3-activity-with-an-interop-activity"></a>搭配 Interop 活動使用 WF 3 活動的準則  
 若要讓 WF 3 活動順利在 <xref:System.Activities.Statements.Interop> 活動中執行，必須符合下列準則：  
  
-   WF 3 活動必須衍生自 <xref:System.Workflow.ComponentModel.Activity?displayProperty=nameWithType>。  
  
-   WF 3 活動必須宣告為 `public`，而不可宣告為 `abstract`。  
  
-   WF 3 活動必須具有公用的預設建構函式。  
  
-   由於 <xref:System.Activities.Statements.Interop> 活動可支援的介面型別有限，所以無法直接使用<xref:System.Workflow.Activities.HandleExternalEventActivity> 與 <xref:System.Workflow.Activities.CallExternalMethodActivity>，但可使用以 [工作流程通訊活動] 工具 (WCA.exe) 所建立的衍生活動。 請參閱[Windows Workflow Foundation 工具](https://go.microsoft.com/fwlink/?LinkId=178889)如需詳細資訊。  
  
## <a name="configuring-a-wf-3-activity-within-an-interop-activity"></a>設定 Interop 活動內的 WF3 活動  
 為了設定資料並跨互通性界限在 WF3 活動內外傳遞該資料，WF 3 活動的屬性和中繼資料屬性會由 <xref:System.Activities.Statements.Interop> 活動公開。 WF 3 活動的中繼資料屬性 (例如 <xref:System.Workflow.ComponentModel.Activity.Name%2A>) 會透過 <xref:System.Activities.Statements.Interop.ActivityMetaProperties%2A> 集合公開。 這是名稱/值組的集合，用於定義 WF3 活動之中繼資料屬性的值。 中繼資料屬性是相依性屬性 (已設定其 <xref:System.Workflow.ComponentModel.DependencyPropertyOptions.Metadata> 旗標) 所支援的屬性。  
  
 WF 3 活動的屬性會透過 <xref:System.Activities.Statements.Interop.ActivityProperties%2A> 集合公開。 這是一組名稱-值組，其中每個值均為一個 <xref:System.Activities.Argument> 物件，用於定義 WF 3 活動之屬性的引數。 因為無法推斷 WF 3 活動屬性的方向，每個屬性會呈現為<xref:System.Activities.InArgument> / <xref:System.Activities.OutArgument>組。 視活動使用屬性的方式而定，您可以提供 <xref:System.Activities.InArgument> 項目、<xref:System.Activities.OutArgument> 項目，或同時使用兩者。 集合中 <xref:System.Activities.InArgument> 項目預期的名稱是在 WF 3 活動定義的屬性名稱。 預期的名稱<xref:System.Activities.OutArgument>集合中的項目是屬性的名稱和字串"Out"的串連。  
  
## <a name="limitations-of-using-a-wf-3-activity-within-an-interop-activity"></a>在 Interop 活動內使用 WF3 活動的限制  
 WF 3 系統提供的活動不可直接包裝在 <xref:System.Activities.Statements.Interop> 活動中。 對部分 WF 3 活動 (例如 <xref:System.Workflow.Activities.DelayActivity>) 而言，這是因為已有類似的 WF 4.5 活動。 對其他活動而言，則是因為不支援該活動的功能。 許多 WF 3 系統提供的活動均可在由 <xref:System.Activities.Statements.Interop> 活動包裝的工作流程中使用，但必須遵守下列限制：  
  
1.  <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.Receive> 不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
2.  <xref:System.Workflow.Activities.WebServiceInputActivity>、<xref:System.Workflow.Activities.WebServiceOutputActivity> 和 <xref:System.Workflow.Activities.WebServiceFaultActivity> 不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
3.  <xref:System.Workflow.Activities.InvokeWorkflowActivity> 不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
4.  <xref:System.Workflow.ComponentModel.SuspendActivity> 不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
5.  與補償相關的活動不可用於 <xref:System.Activities.Statements.Interop> 活動。  
  
 針對在 <xref:System.Activities.Statements.Interop> 活動中使用 WF3 活動的詳細資訊，您也需要了解一些特定的行為資訊：  
  
1.  包含在 <xref:System.Activities.Statements.Interop> 活動中的 WF 3 活動會在執行 <xref:System.Activities.Statements.Interop> 活動時初始化。 在 WF 4.5 中，工作流程執行個體執行前沒有初始化階段。  
  
2.  WF 4.5 執行階段不會在交易開始時針對工作流程執行個體狀態執行檢查點，無論該交易的開始點為何 (在 <xref:System.Activities.Statements.Interop> 活動以內或以外)。  
  
3.  會將 <xref:System.Activities.Statements.Interop> 活動內的活動 WF 3 追蹤記錄當成 <xref:System.Activities.Tracking.InteropTrackingRecord> 物件提供給 WF 4.5 追蹤參與者。 <xref:System.Activities.Tracking.InteropTrackingRecord> 是 <xref:System.Activities.Tracking.CustomTrackingRecord> 的衍生物。  
  
4.  WF 3 自訂活動可以使用互通環境內的工作流程佇列存取資料，方式就和在 WF3 工作流程執行階段中完全相同。 不需要變更任何自訂活動程式碼。 在主機上，資料會透過繼續 <xref:System.Activities.Bookmark> 而加入 WF3 工作流程佇列。 書籤的名稱是 <xref:System.IComparable> 工作流程佇列名稱的字串形式。
