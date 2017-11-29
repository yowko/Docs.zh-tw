---
title: "如何：回應 Windows Form CheckBox 按一下動作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f15adb84f92c9434d6835e80f08bf1d9bd500ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="56c7a-102">如何：回應 Windows Form CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="56c7a-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="56c7a-103">每當使用者按一下 Windows Form<xref:System.Windows.Forms.CheckBox>控制項，<xref:System.Windows.Forms.Control.Click>就會發生事件。</span><span class="sxs-lookup"><span data-stu-id="56c7a-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="56c7a-104">您可以設計您的應用程式，以執行某些動作的核取方塊狀態而定。</span><span class="sxs-lookup"><span data-stu-id="56c7a-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="56c7a-105">若要回應 CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="56c7a-105">To respond to CheckBox clicks</span></span>  
  
1.  <span data-ttu-id="56c7a-106">在<xref:System.Windows.Forms.Control.Click>事件處理常式，使用<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性以判斷控制項的狀態，並執行任何必要的動作。</span><span class="sxs-lookup"><span data-stu-id="56c7a-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    >  <span data-ttu-id="56c7a-107">如果使用者嘗試按兩下<xref:System.Windows.Forms.CheckBox>控制項，將會個別處理每按一下，亦即，<xref:System.Windows.Forms.CheckBox>控制項不支援按兩下事件。</span><span class="sxs-lookup"><span data-stu-id="56c7a-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56c7a-108">當<xref:System.Windows.Forms.CheckBox.AutoCheck%2A>屬性是`true`（預設）、<xref:System.Windows.Forms.CheckBox>自動選取或清除按一下時其。</span><span class="sxs-lookup"><span data-stu-id="56c7a-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="56c7a-109">否則，您必須手動設定<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性時<xref:System.Windows.Forms.Control.Click>就會發生事件。</span><span class="sxs-lookup"><span data-stu-id="56c7a-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="56c7a-110">您也可以使用<xref:System.Windows.Forms.CheckBox>控制項來決定採取的動作。</span><span class="sxs-lookup"><span data-stu-id="56c7a-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="56c7a-111">按一下來決定採取的動作時核取方塊</span><span class="sxs-lookup"><span data-stu-id="56c7a-111">To determine a course of action when a check box is clicked</span></span>  
  
1.  <span data-ttu-id="56c7a-112">若要查詢的值中使用 case 陳述式<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性來決定採取的動作。</span><span class="sxs-lookup"><span data-stu-id="56c7a-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="56c7a-113">當<xref:System.Windows.Forms.CheckBox.ThreeState%2A>屬性設定為`true`、<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性可能會傳回三個可能的值，代表要檢查的方塊，方塊未選取，或是第三個不定狀態顯示此方塊以呈現暗灰色無法使用外觀上與指定的選項。</span><span class="sxs-lookup"><span data-stu-id="56c7a-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    >  <span data-ttu-id="56c7a-114">當<xref:System.Windows.Forms.CheckBox.ThreeState%2A>屬性設定為`true`、<xref:System.Windows.Forms.CheckBox.Checked%2A>屬性會傳回`true`兩者<xref:System.Windows.Forms.CheckState.Checked>和<xref:System.Windows.Forms.CheckState.Indeterminate>。</span><span class="sxs-lookup"><span data-stu-id="56c7a-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c7a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56c7a-115">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="56c7a-116">CheckBox 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="56c7a-116">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="56c7a-117">操作說明：使用 Windows Forms CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="56c7a-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="56c7a-118">CheckBox 控制項</span><span class="sxs-lookup"><span data-stu-id="56c7a-118">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
