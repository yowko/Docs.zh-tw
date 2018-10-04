---
title: Visual 工作流程追蹤
ms.date: 03/30/2017
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
ms.openlocfilehash: 4b6dac8020ba8df0fad57b8cbd0853b4aeb4e75d
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261377"
---
# <a name="visual-workflow-tracking"></a>Visual 工作流程追蹤
這個範例示範如何使用透過 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 提供的偵錯功能，撰寫視覺化工作流程追蹤應用程式。

## <a name="sample-details"></a>範例詳細資料
 應用程式會執行簡單的流程圖工作流程 (於 Workflow.xaml 中定義)，並且重新裝載工作流程設計工具，以顯示目前執行的工作流程。 工作流程執行時，目前執行的活動會以黃色外框和偵錯箭頭顯示。 此外，工作流程產生的追蹤記錄也會在應用程式視窗中顯示。 如需有關工作流程追蹤的詳細資訊，請參閱 <<c0> [ 工作流程追蹤](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。 如需有關重新裝載工作流程設計工具的詳細資訊，請參閱 <<c0> [ 重新裝載工作流程設計工具](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)。

 工作流程模擬器是透過維持兩個字典的方式運作。 其中一個包含目前執行的活動物件與活動執行個體化所在的 XAML 行號之間的對應。 另一個包含活動執行個體 ID 與活動物件之間的對應。 使用自訂追蹤設定檔發出追蹤記錄時，應用程式會判斷目前執行之活動的執行個體 ID，並且將它對應回執行個體化該活動的 XAML 檔案。 接著會指示重新裝載的工作流程設計工具在設計工具介面上反白顯示該活動，並且使用與工作流程偵錯工具相同的方法，在活動周圍具體繪製黃色框線，並且在設計工具左側顯示黃色箭頭。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1.  從 Visual Studio 2010 中的範例目錄中開啟 [workflowsimulator.sln] 檔案。

2.  按下 CTRL+SHIFT+B 以建置方案。

3.  按 CTRL+F5 以執行範例。 這樣會在重新裝載的工作流程設計工具視窗中顯示 Workflow.xaml。

4.  按一下 **檔案**功能表，然後選取**執行工作流程...**.

5.  請注意，目前執行的活動會如上所述反白顯示，而追蹤記錄會在應用程式視窗的右側顯示。

6.  當工作流程完成時，您可以按一下任何一項追蹤記錄，查看它所對應的活動。

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`