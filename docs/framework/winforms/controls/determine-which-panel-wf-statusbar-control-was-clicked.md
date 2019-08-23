---
title: 作法：判斷在 Windows Forms StatusBar 控制項中按下了哪個面板
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: 6229d8965949641105cd0e9708474c3249d52d1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965714"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>HOW TO：判斷在 Windows Forms StatusBar 控制項中按下了哪個面板
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel>和控制項會取代和加入和<xref:System.Windows.Forms.StatusBarPanel>控制項的功能; 不過, 如果您這樣做, 和控制項就會保留, 以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusStrip>決定.  
  
 若要程式設計[狀態列控制項](statusbar-control-windows-forms.md)以回應使用者的點擊, 請在<xref:System.Windows.Forms.StatusBar.PanelClick>事件內使用 case 語句。 事件包含引數 (panel 引數), 其中包含所按下的<xref:System.Windows.Forms.StatusBarPanel>參考。 使用此參考, 您可以判斷所按下的面板索引, 並據以進行程式。  
  
> [!NOTE]
> 請確定<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>控制項的屬性設定為`true`。 <xref:System.Windows.Forms.StatusBar>  
  
### <a name="to-determine-which-panel-was-clicked"></a>判斷按一下的面板  
  
1. `switch case` `Select Case`在事件處理常式中, 使用 (在 Visual Basic 中) 或 ( C# visual 或C++visual) 語句, 藉由檢查事件引數中已按下之面板的索引來判斷按一下的面板。 <xref:System.Windows.Forms.StatusBar.PanelClick>  
  
     下列程式碼<xref:System.Windows.Forms.StatusBar>範例需要`StatusBar1`控制項的目前狀態、和兩個<xref:System.Windows.Forms.StatusBarPanel>物件, `StatusBarPanel1`以及`StatusBarPanel2`。  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     (視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [如何：設定狀態列面板的大小](how-to-set-the-size-of-status-bar-panels.md)
- [逐步解說：在執行時間更新狀態列資訊](walkthrough-updating-status-bar-information-at-run-time.md)
- [StatusBar 控制項概觀](statusbar-control-overview-windows-forms.md)
