---
title: 如何：判斷在 Windows Form StatusBar 控制項中按下的面板
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
ms.openlocfilehash: b83dc7273c612e914840307bc749abef780284ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>如何：判斷在 Windows Form StatusBar 控制項中按下的面板
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>和<xref:System.Windows.Forms.ToolStripStatusLabel>控制項取代，並將功能加入至<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項是被保留為回溯相容性及未來使用，如果您選擇。  
  
 程式[StatusBar 控制項](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md)控制項回應使用者按鍵動作，請使用 case 陳述式內<xref:System.Windows.Forms.StatusBar.PanelClick>事件。 事件包含引數 （面板引數），其中包含參考按的<xref:System.Windows.Forms.StatusBarPanel>。 使用此參考，您就可以判斷按下的面板的索引，並依此進行程式設計。  
  
> [!NOTE]
>  請確認<xref:System.Windows.Forms.StatusBar>控制項的<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性設定為`true`。  
  
### <a name="to-determine-which-panel-was-clicked"></a>若要判斷已按下的面板  
  
1.  在<xref:System.Windows.Forms.StatusBar.PanelClick>事件處理常式，使用`Select Case`（在 Visual Basic) 或`switch case`(Visual C# 或[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 陳述式來判斷哪個面板已按下藉由檢查事件引數中按下的面板的索引。  
  
     下列程式碼範例需要是否存在，請在表單上的<xref:System.Windows.Forms.StatusBar>控制項， `StatusBar1`，和兩個<xref:System.Windows.Forms.StatusBarPanel>物件`StatusBarPanel1`和`StatusBarPanel2`。  
  
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
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。  
  
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
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [操作說明：設定狀態列面板的大小](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [逐步解說：在執行階段更新狀態列資訊](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [StatusBar 控制項概觀](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
