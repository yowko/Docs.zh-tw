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
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930977"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>逐步解說：在執行階段更新狀態列資訊
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel>和控制項會取代和加入和<xref:System.Windows.Forms.StatusBarPanel>控制項的功能; 不過, 如果您這樣做, 和控制項就會保留, 以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusStrip>決定.  
  
 通常，程式會為您呼叫，根據應用程式狀態或其他使用者互動的變更，在執行階段以動態方式更新狀態列面板的內容。 這是常見的方法來通知使用者，例如 CAPS LOCK、NUM LOCK 或 SCROLL LOCK 鍵已啟用，或者提供日期或時鐘以做為方便參考。  
  
 在下列範例中, 您將使用<xref:System.Windows.Forms.StatusBarPanel>類別的實例來裝載時鐘。  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>若要準備狀態列進行更新  
  
1. 建立新的 Windows Form。  
  
2. 新增 <xref:System.Windows.Forms.StatusBar> 控制項至表單。 如需詳細資訊，請參閱[如何：將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。  
  
3. 將狀態列面板新增至您<xref:System.Windows.Forms.StatusBar>的控制項。 如需詳細資訊，請參閱[如何：將面板加入至狀態列控制項](how-to-add-panels-to-a-statusbar-control.md)。  
  
4. 針對您<xref:System.Windows.Forms.StatusBar>新增至表單的控制項, <xref:System.Windows.Forms.StatusBar.ShowPanels%2A>將屬性設定為`true`。  
  
5. 將 Windows Forms <xref:System.Windows.Forms.Timer>元件新增至表單。  
  
    > [!NOTE]
    > Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType>元件是針對 Windows Forms 環境所設計。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。  
  
6. 將 <xref:System.Windows.Forms.Timer.Enabled%2A> 屬性設定為 `true`。  
  
7. 將的<xref:System.Windows.Forms.Timer>屬性設定為30000。 <xref:System.Windows.Forms.Timer.Interval%2A>  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.Timer>元件<xref:System.Windows.Forms.Timer.Interval%2A>的屬性會設定為30秒 (30000 毫秒), 以確保正確的時間會反映在所顯示的時間內。  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>若要實作計時器以更新狀態列  
  
1. 將下列程式碼插入<xref:System.Windows.Forms.Timer>元件的事件處理常式, 以更新<xref:System.Windows.Forms.StatusBar>控制項的面板。  
  
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
  
1. 針對應用程式進行偵錯，並且按下 F5 鍵以執行它。 如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](/visualstudio/debugger/debugging-in-visual-studio)。  
  
    > [!NOTE]
    > 需要大約 30 秒的時間讓時鐘出現在狀態列中。 這是為了盡可能取得最準確的時間。 相反地, 若要讓時鐘更快出現, 您可以減少在上<xref:System.Windows.Forms.Timer.Interval%2A>一個程式的步驟7中設定的屬性值。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [如何：將面板新增至狀態列控制項](how-to-add-panels-to-a-statusbar-control.md)
- [如何：判斷按一下 Windows Forms 狀態列控制項中的哪一個面板](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar 控制項概觀](statusbar-control-overview-windows-forms.md)
