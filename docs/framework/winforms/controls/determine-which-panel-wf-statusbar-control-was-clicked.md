---
title: 確定按一下狀態列控制項中的哪個面板
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
ms.openlocfilehash: eb3b10d515ba5b62236594e063ca7f060b34b73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182369"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="5d055-102">如何：判斷在 Windows Form StatusBar 控制項中按下的面板</span><span class="sxs-lookup"><span data-stu-id="5d055-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="5d055-103"><xref:System.Windows.Forms.StatusStrip>和<xref:System.Windows.Forms.ToolStripStatusLabel>控制項將 功能替換並添加到<xref:System.Windows.Forms.StatusBar><xref:System.Windows.Forms.StatusBarPanel>和 控制項;但是，如果<xref:System.Windows.Forms.StatusBar>願意<xref:System.Windows.Forms.StatusBarPanel>，將保留 和 控制項以進行向後相容性和未來使用。</span><span class="sxs-lookup"><span data-stu-id="5d055-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="5d055-104">要對[狀態列控制項](statusbar-control-windows-forms.md)進行程式設計以回應使用者按一下，請在<xref:System.Windows.Forms.StatusBar.PanelClick>事件中使用案例語句。</span><span class="sxs-lookup"><span data-stu-id="5d055-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="5d055-105">該事件包含一個參數（面板參數），其中包含對已<xref:System.Windows.Forms.StatusBarPanel>按一下的 的 引用。</span><span class="sxs-lookup"><span data-stu-id="5d055-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="5d055-106">使用此引用，您可以確定按一下面板的索引，並相應地進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="5d055-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d055-107">確保<xref:System.Windows.Forms.StatusBar>控制項的屬性<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="5d055-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="5d055-108">確定按一下哪個面板</span><span class="sxs-lookup"><span data-stu-id="5d055-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="5d055-109">在<xref:System.Windows.Forms.StatusBar.PanelClick>事件處理常式中，使用`Select Case`（在視覺化基本版中）`switch case`或（Visual C# 或視覺C++）語句通過檢查事件參數中按一下的面板的索引來確定按一下的面板。</span><span class="sxs-lookup"><span data-stu-id="5d055-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="5d055-110">以下代碼示例要求在表單上存在<xref:System.Windows.Forms.StatusBar>控制項`StatusBar1`和 兩<xref:System.Windows.Forms.StatusBarPanel>個物件`StatusBarPanel1`以及`StatusBarPanel2`。</span><span class="sxs-lookup"><span data-stu-id="5d055-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="5d055-111">（視覺 C#，視覺C++）將以下代碼放在表單的建構函式中以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5d055-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d055-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d055-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="5d055-113">如何：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="5d055-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="5d055-114">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="5d055-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="5d055-115">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="5d055-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
