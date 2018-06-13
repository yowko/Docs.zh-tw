---
title: 使用流程追蹤判斷工作流程的執行
ms.date: 03/30/2017
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
ms.openlocfilehash: 9f9c65f2c873d54da443db14e7f5797ef1e14174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515081"
---
# <a name="determining-workflow-execution-duration-using-tracing"></a>使用流程追蹤判斷工作流程的執行
本主題示範如何判斷成功完成的自行裝載工作流程使用工作流程追蹤來執行所需的時間。  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a>若要使用工作流程追蹤來判斷工作流程應用程式執行的持續期間  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  選取**檔案**，**新**，**專案**。  在下**C#**，選取**工作流程**節點。  選取**工作流程主控台應用程式**從範本清單。  將新專案`WorkflowDurationTracing`按一下**確定**。  
  
2.  開啟 Workflow1.xaml。  將 <xref:System.Activities.Statements.Delay> 活動拖曳至設計工具介面上。 將 00:00:10 值 (十秒鐘) 指派給活動的 Duration 屬性。  
  
3.  開啟事件檢視器，依序按一下**啟動**，**執行**，並輸入`eventvwr.exe`。  
  
4.  如果您尚未啟用工作流程追蹤，展開**Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**. 選取**檢視**，**顯示分析與偵錯記錄檔**。 以滑鼠右鍵按一下**偵錯**選取**啟用記錄**。 讓 [事件檢視器] 保持開啟狀態，如此在工作流程執行之後就能檢視追蹤。  
  
5.  按 CTRL+SHIFT+B 執行工作流程應用程式。  
  
6.  在 [事件檢視器] 中，尋找 ID 為 1009 的最近事件，並尋找類似以下的訊息。 請記下當初記錄訊息的時間。  
  
 **父活動 '、 DisplayName: '、 InstanceId: ' 已排的程子活動 'WorkflowDurationTracking.Workflow1'、 DisplayName: 'Workflow1'、 InstanceId: '1'。**  
  
7.  尋找 ID 為 1001 的另一個最近事件，並尋找類似以下的訊息。  從這個訊息的記錄值中減去上一個訊息的時間，以判斷工作流程執行的持續期間，應該大約 10 秒鐘左右。  
  
 **WorkflowInstance Id: ' 1bbac57b-3322-498e-9e27-8833fda3a5bf' 已在 Closed 狀態中完成。**  
  
## <a name="see-also"></a>另請參閱  
 [工作流程追蹤](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [Windows Server App Fabric 監控](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [使用 App Fabric 監控應用程式](http://go.microsoft.com/fwlink/?LinkId=201275)
