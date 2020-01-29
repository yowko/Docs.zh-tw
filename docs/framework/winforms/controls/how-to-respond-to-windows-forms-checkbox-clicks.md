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
ms.openlocfilehash: ba2afb52939a6274978ce725dac19b5622419b99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735671"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="77523-102">如何：回應 Windows Form CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="77523-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="77523-103">每當使用者按一下 Windows Forms <xref:System.Windows.Forms.CheckBox> 控制項時，就會發生 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="77523-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="77523-104">您可以根據核取方塊的狀態，將您的應用程式設計成執行某些動作。</span><span class="sxs-lookup"><span data-stu-id="77523-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="77523-105">若要回應核取方塊按一下</span><span class="sxs-lookup"><span data-stu-id="77523-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="77523-106">在 <xref:System.Windows.Forms.Control.Click> 事件處理常式中，使用 [<xref:System.Windows.Forms.CheckBox.Checked%2A>] 屬性來判斷控制項的狀態，並執行任何必要的動作。</span><span class="sxs-lookup"><span data-stu-id="77523-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="77523-107">如果使用者嘗試按兩下 <xref:System.Windows.Forms.CheckBox> 控制項，則每次按一下都會單獨處理;也就是說，<xref:System.Windows.Forms.CheckBox> 控制項不支援按兩下事件。</span><span class="sxs-lookup"><span data-stu-id="77523-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="77523-108">當 <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> 屬性 `true` （預設值）時，<xref:System.Windows.Forms.CheckBox> 會在按一下時自動選取或清除。</span><span class="sxs-lookup"><span data-stu-id="77523-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="77523-109">否則，當發生 <xref:System.Windows.Forms.Control.Click> 事件時，您必須手動設定 <xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="77523-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="77523-110">您也可以使用 <xref:System.Windows.Forms.CheckBox> 控制項來判斷動作的執行過程。</span><span class="sxs-lookup"><span data-stu-id="77523-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="77523-111">若要判斷按一下核取方塊時的動作課程</span><span class="sxs-lookup"><span data-stu-id="77523-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="77523-112">使用 case 語句來查詢 <xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性的值，以判斷動作的執行過程。</span><span class="sxs-lookup"><span data-stu-id="77523-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="77523-113">當 [<xref:System.Windows.Forms.CheckBox.ThreeState%2A>] 屬性設定為 [`true`] 時，<xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性可能會傳回三個可能的值，這代表要檢查的方塊、未核取的方塊，或第三個不定狀態，其中方塊顯示為暗灰色外觀，表示無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="77523-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="77523-114">當 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設定為 `true`時，<xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性會同時傳回 <xref:System.Windows.Forms.CheckState.Checked> 和 <xref:System.Windows.Forms.CheckState.Indeterminate>的 `true`。</span><span class="sxs-lookup"><span data-stu-id="77523-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77523-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="77523-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="77523-116">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="77523-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="77523-117">操作說明：使用 Windows Forms CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="77523-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="77523-118">CheckBox 控制項</span><span class="sxs-lookup"><span data-stu-id="77523-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
