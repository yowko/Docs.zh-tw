---
title: 如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: 789a0a25c65185b101ef427ff62871fa490c7f1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525210"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="80a6d-102">如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更</span><span class="sxs-lookup"><span data-stu-id="80a6d-102">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="80a6d-103">Windows Form 的常見用法<xref:System.Windows.Forms.RichTextBox>控制項已格式化文字的字型選項或段落樣式等屬性。</span><span class="sxs-lookup"><span data-stu-id="80a6d-103">A common use of the Windows Forms <xref:System.Windows.Forms.RichTextBox> control is formatting text with attributes such as font options or paragraph styles.</span></span> <span data-ttu-id="80a6d-104">您的應用程式可能需要追蹤的文字格式設定用來顯示工具列，就像許多文書處理應用程式中的任何變更。</span><span class="sxs-lookup"><span data-stu-id="80a6d-104">Your application may need to keep track of any changes in text formatting for the purpose of displaying a toolbar, as in many word-processing applications.</span></span>  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a><span data-ttu-id="80a6d-105">若要回應的格式屬性變更</span><span class="sxs-lookup"><span data-stu-id="80a6d-105">To respond to changes in formatting attributes</span></span>  
  
1.  <span data-ttu-id="80a6d-106">在撰寫程式碼<xref:System.Windows.Forms.RichTextBox.SelectionChanged>事件處理常式執行適當動作的屬性值而定。</span><span class="sxs-lookup"><span data-stu-id="80a6d-106">Write code in the <xref:System.Windows.Forms.RichTextBox.SelectionChanged> event handler to perform an appropriate action depending on the value of the attribute.</span></span> <span data-ttu-id="80a6d-107">下列範例會變更工具列按鈕的值而定的外觀<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="80a6d-107">The following example changes the appearance of a toolbar button depending on the value of the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="80a6d-108">當插入點移動控制項中，將只會更新工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="80a6d-108">The toolbar button will only be updated when the insertion point is moved in the control.</span></span>  
  
     <span data-ttu-id="80a6d-109">以下範例假設的表單具有<xref:System.Windows.Forms.RichTextBox>控制項和<xref:System.Windows.Forms.ToolBar>包含的工具列按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="80a6d-109">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control and a <xref:System.Windows.Forms.ToolBar> control that contains a toolbar button.</span></span> <span data-ttu-id="80a6d-110">如需工具列和工具列按鈕的詳細資訊，請參閱[How to： 將按鈕加入 ToolBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)。</span><span class="sxs-lookup"><span data-stu-id="80a6d-110">For more information about toolbars and toolbar buttons, see [How to: Add Buttons to a ToolBar Control](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md).</span></span>  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="80a6d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80a6d-111">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="80a6d-112">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="80a6d-112">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="80a6d-113">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="80a6d-113">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
