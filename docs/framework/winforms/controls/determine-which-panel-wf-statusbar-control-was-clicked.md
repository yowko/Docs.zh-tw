---
title: HOW TO：判斷按下 Windows Forms StatusBar 控制項中的面板
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
ms.openlocfilehash: 2907b6344cd4fcc7c7d84c110dbc638cdc86f23c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708320"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="64625-102">HOW TO：判斷按下 Windows Forms StatusBar 控制項中的面板</span><span class="sxs-lookup"><span data-stu-id="64625-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="64625-103"><xref:System.Windows.Forms.StatusStrip>及<xref:System.Windows.Forms.ToolStripStatusLabel>控制項會取代及新增功能<xref:System.Windows.Forms.StatusBar>並<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項保留回溯相容性和未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="64625-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="64625-104">來計劃[StatusBar 控制項](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md)回應使用者點選動作，請使用 case 陳述式內的控制項<xref:System.Windows.Forms.StatusBar.PanelClick>事件。</span><span class="sxs-lookup"><span data-stu-id="64625-104">To program the [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="64625-105">事件包含引數 （面板引數），其中包含的參考已按下 的<xref:System.Windows.Forms.StatusBarPanel>。</span><span class="sxs-lookup"><span data-stu-id="64625-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="64625-106">使用此參考，您就可以判斷所按的面板的索引，並依此進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="64625-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64625-107">請確認<xref:System.Windows.Forms.StatusBar>控制項的<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="64625-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="64625-108">若要判斷已按下的面板</span><span class="sxs-lookup"><span data-stu-id="64625-108">To determine which panel was clicked</span></span>  
  
1.  <span data-ttu-id="64625-109">在 <xref:System.Windows.Forms.StatusBar.PanelClick>事件處理常式，使用`Select Case`（在 Visual Basic) 或`switch case`(VisualC#或[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 陳述式來判斷已按下的面板藉由檢查事件引數中所按面板的索引。</span><span class="sxs-lookup"><span data-stu-id="64625-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="64625-110">下列程式碼範例的需要，請在目前狀態，在表單中，<xref:System.Windows.Forms.StatusBar>控制項中， `StatusBar1`，並將兩個<xref:System.Windows.Forms.StatusBarPanel>物件`StatusBarPanel1`和`StatusBarPanel2`。</span><span class="sxs-lookup"><span data-stu-id="64625-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="64625-111">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="64625-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64625-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64625-112">See also</span></span>
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="64625-113">如何：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="64625-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="64625-114">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="64625-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="64625-115">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="64625-115">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
