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
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="4e600-102">HOW TO：判斷在 Windows Forms StatusBar 控制項中按下了哪個面板</span><span class="sxs-lookup"><span data-stu-id="4e600-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="4e600-103"><xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel>和控制項會取代和加入和<xref:System.Windows.Forms.StatusBarPanel>控制項的功能; 不過, 如果您這樣做, 和控制項就會保留, 以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusStrip>決定.</span><span class="sxs-lookup"><span data-stu-id="4e600-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="4e600-104">若要程式設計[狀態列控制項](statusbar-control-windows-forms.md)以回應使用者的點擊, 請在<xref:System.Windows.Forms.StatusBar.PanelClick>事件內使用 case 語句。</span><span class="sxs-lookup"><span data-stu-id="4e600-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="4e600-105">事件包含引數 (panel 引數), 其中包含所按下的<xref:System.Windows.Forms.StatusBarPanel>參考。</span><span class="sxs-lookup"><span data-stu-id="4e600-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="4e600-106">使用此參考, 您可以判斷所按下的面板索引, 並據以進行程式。</span><span class="sxs-lookup"><span data-stu-id="4e600-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e600-107">請確定<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>控制項的屬性設定為`true`。 <xref:System.Windows.Forms.StatusBar></span><span class="sxs-lookup"><span data-stu-id="4e600-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="4e600-108">判斷按一下的面板</span><span class="sxs-lookup"><span data-stu-id="4e600-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="4e600-109">`switch case` `Select Case`在事件處理常式中, 使用 (在 Visual Basic 中) 或 ( C# visual 或C++visual) 語句, 藉由檢查事件引數中已按下之面板的索引來判斷按一下的面板。 <xref:System.Windows.Forms.StatusBar.PanelClick></span><span class="sxs-lookup"><span data-stu-id="4e600-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="4e600-110">下列程式碼<xref:System.Windows.Forms.StatusBar>範例需要`StatusBar1`控制項的目前狀態、和兩個<xref:System.Windows.Forms.StatusBarPanel>物件, `StatusBarPanel1`以及`StatusBarPanel2`。</span><span class="sxs-lookup"><span data-stu-id="4e600-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="4e600-111">(視覺C#效果, C++視覺效果)將下列程式碼放在表單的函式中, 以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4e600-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e600-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e600-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="4e600-113">如何：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="4e600-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="4e600-114">逐步解說：在執行時間更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="4e600-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="4e600-115">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="4e600-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
