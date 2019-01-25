---
title: 逐步解說：在執行階段更新狀態列資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: 3de554d4c8c3963948159bc6b8c2196f9ebc10ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745879"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>逐步解說：在執行階段更新狀態列資訊
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>及<xref:System.Windows.Forms.ToolStripStatusLabel>控制項會取代及新增功能<xref:System.Windows.Forms.StatusBar>並<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項保留回溯相容性和未來使用，如果您選擇。  
  
 通常，程式會為您呼叫，根據應用程式狀態或其他使用者互動的變更，在執行階段以動態方式更新狀態列面板的內容。 這是常見的方法來通知使用者，例如 CAPS LOCK、NUM LOCK 或 SCROLL LOCK 鍵已啟用，或者提供日期或時鐘以做為方便參考。  
  
 在下列範例中，您將使用的執行個體<xref:System.Windows.Forms.StatusBarPanel>類別來裝載時鐘。  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>若要準備狀態列進行更新  
  
1.  建立新的 Windows Form。  
  
2.  新增 <xref:System.Windows.Forms.StatusBar> 控制項至表單。 如需詳細資訊，請參閱[How to:將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
3.  加入至狀態列面板您<xref:System.Windows.Forms.StatusBar>控制項。 如需詳細資訊，請參閱[How to:將面板新增至 StatusBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)。  
  
4.  針對<xref:System.Windows.Forms.StatusBar>控制項新增至表單，設定<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性設`true`。  
  
5.  加入 Windows Form<xref:System.Windows.Forms.Timer>元件至表單。  
  
    > [!NOTE]
    >  Windows Form<xref:System.Windows.Forms.Timer?displayProperty=nameWithType>元件專為 Windows Form 環境。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。  
  
6.  將 <xref:System.Windows.Forms.Timer.Enabled%2A> 屬性設定為 `true`。  
  
7.  設定<xref:System.Windows.Forms.Timer.Interval%2A>屬性<xref:System.Windows.Forms.Timer>為 30000。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer.Interval%2A>屬性<xref:System.Windows.Forms.Timer>元件會設定為 30 秒 （30,000 毫秒），以確保正確的時間會反映在顯示的時間。  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>若要實作計時器以更新狀態列  
  
1.  下列程式碼插入的事件處理常式<xref:System.Windows.Forms.Timer>元件，以更新的面板<xref:System.Windows.Forms.StatusBar>控制項。  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     此時，您已經準備好執行應用程式，並且觀察在狀態列面板中執行的時鐘。  
  
### <a name="to-test-the-application"></a>若要測試應用程式  
  
1.  針對應用程式進行偵錯，並且按下 F5 鍵以執行它。 如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。  
  
    > [!NOTE]
    >  需要大約 30 秒的時間讓時鐘出現在狀態列中。 這是為了盡可能取得最準確的時間。 相反地，若要讓時鐘更早出現，您可以減少的值<xref:System.Windows.Forms.Timer.Interval%2A>您在之前程序中的步驟 7 中設定的屬性。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [如何：將面板新增至 StatusBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)
- [如何：判斷按下 Windows Forms StatusBar 控制項中的面板](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar 控制項概觀](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
