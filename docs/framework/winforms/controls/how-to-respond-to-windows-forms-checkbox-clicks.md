---
title: 回應 CheckBox 點選
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: 6ff20c443519446d3804b325924cb3c5cbedea97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141922"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="e424f-102">如何：回應 Windows Form CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="e424f-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="e424f-103">每當使用者按一下 Windows 表單<xref:System.Windows.Forms.CheckBox>控制項時，都會<xref:System.Windows.Forms.Control.Click>發生該事件。</span><span class="sxs-lookup"><span data-stu-id="e424f-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="e424f-104">您可以根據核取方塊的狀態對應用程式進行程式設計以執行某些操作。</span><span class="sxs-lookup"><span data-stu-id="e424f-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="e424f-105">回應核取方塊點擊</span><span class="sxs-lookup"><span data-stu-id="e424f-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="e424f-106">在事件<xref:System.Windows.Forms.Control.Click>處理常式中，使用<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性確定控制項的狀態，並執行任何必要的操作。</span><span class="sxs-lookup"><span data-stu-id="e424f-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="e424f-107">如果使用者嘗試按兩下<xref:System.Windows.Forms.CheckBox>控制項，則每次按一下將單獨處理;如果使用者嘗試按兩下控制項，則每次按一下都將單獨處理。也就是說，<xref:System.Windows.Forms.CheckBox>控制項不支援按兩下事件。</span><span class="sxs-lookup"><span data-stu-id="e424f-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e424f-108">當<xref:System.Windows.Forms.CheckBox.AutoCheck%2A>屬性為`true`（預設值）時，<xref:System.Windows.Forms.CheckBox>按一下時會自動選擇或清除 該屬性。</span><span class="sxs-lookup"><span data-stu-id="e424f-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="e424f-109">否則，在<xref:System.Windows.Forms.Control.Click>事件發生時必須手動設置<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e424f-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="e424f-110">您還可以使用控制項<xref:System.Windows.Forms.CheckBox>來確定操作過程。</span><span class="sxs-lookup"><span data-stu-id="e424f-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="e424f-111">在按一下核取方塊時確定操作過程</span><span class="sxs-lookup"><span data-stu-id="e424f-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="e424f-112">使用 case 語句查詢<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性的值以確定操作過程。</span><span class="sxs-lookup"><span data-stu-id="e424f-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="e424f-113">當<xref:System.Windows.Forms.CheckBox.ThreeState%2A>屬性設置為`true`時，<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性可能會返回三個可能的值，表示要選中的框、未選中的框或顯示具有灰色外觀的框以指示該選項不可用的第三個不確定狀態。</span><span class="sxs-lookup"><span data-stu-id="e424f-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="e424f-114">當屬性<xref:System.Windows.Forms.CheckBox.ThreeState%2A>`true`設置為<xref:System.Windows.Forms.CheckBox.Checked%2A>時，屬性將返回`true`和<xref:System.Windows.Forms.CheckState.Checked><xref:System.Windows.Forms.CheckState.Indeterminate>。</span><span class="sxs-lookup"><span data-stu-id="e424f-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e424f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e424f-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="e424f-116">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e424f-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e424f-117">如何：使用 Windows Form CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="e424f-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="e424f-118">核取方塊控制</span><span class="sxs-lookup"><span data-stu-id="e424f-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
