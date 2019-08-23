---
title: 偵錯工作流程
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 12b85260f8eab87fc9b98a99ca1192fd307313d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915416"
---
# <a name="debugging-workflows"></a>偵錯工作流程
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]提供一些從開發環境進行偵錯工作流程的選項。 可在設計工具、XAML 與程式碼中將工作流程偵錯。  
  
## <a name="debugging-in-the-workflow-designer"></a>在工作流程設計工具中偵錯  
 您可以在工作流程設計工具中的活動上設定中斷點, 方法是反白顯示活動並按**F9**鍵, 或使用活動的內容功能表。 執行工作流程，然後當工作流程主機正在偵錯模式中執行時中斷。 在下列螢幕擷取畫面中，工作流程的執行已暫停於一個中斷點。 如需詳細資訊, 請參閱[使用工作流程設計工具來偵錯工具工作流程](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer)。  
  
## <a name="debugging-in-xaml"></a>在 XAML 中偵錯  
 如果工作流程在設計工具中的中斷點上暫停，即可在 XAML 中偵錯工作流程。 若要在 XAML 中查看執行點, 請在工作流程執行暫停時, 在工作流程設計工具中選取 [ **XAML 視圖**]。 從解決方案總管的設計工具中重新開啟工作流程，即可將偵錯切換回設計工具。 如需詳細資訊，請參閱[如何：使用工作流程設計工具](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer)的 Debug XAML。  
  
## <a name="debugging-in-code"></a>在程式碼中偵錯  
 在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中使用程式碼中斷點的方式與用於其他命令式應用程式相同。 按一下程式碼窗格的左邊界來建立程式碼中斷點, 或按下**F9**鍵, 將中斷點放在游標位置。  
  
## <a name="attaching-to-a-workflow-process"></a>附加至工作流程處理序  
 工作流程偵錯也支援使用 Visual Studio 的基礎結構來附加至處理序。 這可讓工作流程的作者在不同的主機環境中 (例如 Internet Information Services (IIS) 7.0) 執行時偵錯工作流程。  
  
## <a name="remote-debugging"></a>Remote Debugging  
 Windows Workflow Foundation (WF) 遠端偵錯程式與其他 Visual Studio 元件的遠端偵錯功能相同。 如需使用遠端偵錯程式的詳細[資訊, 請參閱如何:啟用遠端偵錯](https://go.microsoft.com/fwlink/?LinkId=196257)。  
  
> [!NOTE]
> 如果工作流應用程式的目標為 x86 架構, 並裝載在執行64位作業系統的電腦上, 則除非遠端電腦上已安裝 Visual Studio, 或工作流程應用程式的目標變更為, 否則遠端偵錯程式將無法運作。**任何 CPU**。  
  
## <a name="extending-the-workflow-debugging-service"></a>擴充工作流程偵錯服務  
 現在已公開工作流程偵錯程式服務，且可用於建立自訂應用程式，例如在重新裝載的設計工具中監控、模擬和偵錯。 如需詳細資訊，請參閱 <xref:System.Activities.Presentation.Debug.DebuggerService> 主題。
