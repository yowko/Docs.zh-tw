---
title: 回應 CheckBox 點選
description: 瞭解如何根據核取方塊的狀態，將您的 Windows Forms 應用程式設計成執行某些動作。
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
ms.openlocfilehash: 58944bc421f990343b6c58484aaab3d79c8bda5e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174493"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="6ff95-103">如何：回應 Windows Form CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="6ff95-103">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="6ff95-104">每當使用者按一下 Windows Forms 控制項時 <xref:System.Windows.Forms.CheckBox> ， <xref:System.Windows.Forms.Control.Click> 就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="6ff95-104">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="6ff95-105">您可以根據核取方塊的狀態，將您的應用程式設計成執行某些動作。</span><span class="sxs-lookup"><span data-stu-id="6ff95-105">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="6ff95-106">若要回應核取方塊按一下</span><span class="sxs-lookup"><span data-stu-id="6ff95-106">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="6ff95-107">在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，使用 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性來判斷控制項的狀態，並執行任何必要的動作。</span><span class="sxs-lookup"><span data-stu-id="6ff95-107">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="6ff95-108">如果使用者嘗試按兩下 <xref:System.Windows.Forms.CheckBox> 控制項，則每次按一下都會單獨處理，也就是說， <xref:System.Windows.Forms.CheckBox> 控制項不支援按兩下事件。</span><span class="sxs-lookup"><span data-stu-id="6ff95-108">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6ff95-109">當 <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> 屬性 `true` (預設) 時，會在 <xref:System.Windows.Forms.CheckBox> 按一下時自動選取或清除。</span><span class="sxs-lookup"><span data-stu-id="6ff95-109">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="6ff95-110">否則， <xref:System.Windows.Forms.CheckBox.Checked%2A> 當事件發生時，您必須手動設定屬性 <xref:System.Windows.Forms.Control.Click> 。</span><span class="sxs-lookup"><span data-stu-id="6ff95-110">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="6ff95-111">您也可以使用 <xref:System.Windows.Forms.CheckBox> 控制項來判斷動作的執行過程。</span><span class="sxs-lookup"><span data-stu-id="6ff95-111">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="6ff95-112">若要判斷按一下核取方塊時的動作課程</span><span class="sxs-lookup"><span data-stu-id="6ff95-112">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="6ff95-113">使用 case 語句來查詢屬性的值 <xref:System.Windows.Forms.CheckBox.CheckState%2A> ，以判斷動作的執行過程。</span><span class="sxs-lookup"><span data-stu-id="6ff95-113">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="6ff95-114">當 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設定為時 `true` ， <xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性可能會傳回三個可能的值，分別代表要檢查的方塊、未核取的方塊，或第三個不定狀態，其中方塊會以暗灰色的外觀顯示，表示無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="6ff95-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="6ff95-115">當 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設定為時 `true` ，屬性會傳回 <xref:System.Windows.Forms.CheckBox.Checked%2A> `true` 和的 <xref:System.Windows.Forms.CheckState.Checked> <xref:System.Windows.Forms.CheckState.Indeterminate> 。</span><span class="sxs-lookup"><span data-stu-id="6ff95-115">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff95-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ff95-116">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="6ff95-117">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="6ff95-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="6ff95-118">如何：使用 Windows Form CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="6ff95-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="6ff95-119">CheckBox 控制項</span><span class="sxs-lookup"><span data-stu-id="6ff95-119">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
