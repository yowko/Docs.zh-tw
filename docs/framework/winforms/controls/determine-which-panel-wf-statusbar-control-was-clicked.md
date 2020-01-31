---
title: 判斷按一下狀態列控制項中的哪個面板
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
ms.openlocfilehash: 94619f8bd426a42e5dafa0db99880e20d24f9963
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746020"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>如何：判斷在 Windows Form StatusBar 控制項中按下的面板
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusStrip> 和 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項的功能，並將其加入。不過，如果您選擇，<xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項都會保留，以提供回溯相容性及未來使用。  
  
 若要程式設計[狀態列控制項](statusbar-control-windows-forms.md)以回應使用者的點擊，請在 <xref:System.Windows.Forms.StatusBar.PanelClick> 事件內使用 case 語句。 事件包含引數（panel 引數），其中包含所按 <xref:System.Windows.Forms.StatusBarPanel>的參考。 使用此參考，您可以判斷所按下的面板索引，並據以進行程式。  
  
> [!NOTE]
> 確定 <xref:System.Windows.Forms.StatusBar> 控制項的 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> 屬性已設定為 [`true`]。  
  
### <a name="to-determine-which-panel-was-clicked"></a>判斷按一下的面板  
  
1. 在 <xref:System.Windows.Forms.StatusBar.PanelClick> 事件處理常式中，使用 `Select Case` （在 Visual Basic）或 `switch case` （Visual C#或 visual C++）語句，藉由檢查事件引數中已按下之面板的索引來判斷按一下的面板。  
  
     下列程式碼範例需要 <xref:System.Windows.Forms.StatusBar> 控制項、`StatusBar1`和兩個 <xref:System.Windows.Forms.StatusBarPanel> 物件的目前狀態，`StatusBarPanel1` 和 `StatusBarPanel2`。  
  
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
  
     （視覺C#效果， C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。  
  
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
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [操作說明：設定狀態列面板的大小](how-to-set-the-size-of-status-bar-panels.md)
- [逐步解說：在執行階段更新狀態列資訊](walkthrough-updating-status-bar-information-at-run-time.md)
- [StatusBar 控制項概觀](statusbar-control-overview-windows-forms.md)
