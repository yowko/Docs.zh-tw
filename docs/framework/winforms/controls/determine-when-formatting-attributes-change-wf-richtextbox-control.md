---
title: 確定"格式設置屬性在富文本盒"控制項中何時更改
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
ms.openlocfilehash: a190c3479b58464763e0eefdd32d14e88a1f05e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142260"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="292ec-102">如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更</span><span class="sxs-lookup"><span data-stu-id="292ec-102">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="292ec-103">Windows 表單<xref:System.Windows.Forms.RichTextBox>控制項的常見用途是使用字體選項或段落樣式等屬性設置文本格式。</span><span class="sxs-lookup"><span data-stu-id="292ec-103">A common use of the Windows Forms <xref:System.Windows.Forms.RichTextBox> control is formatting text with attributes such as font options or paragraph styles.</span></span> <span data-ttu-id="292ec-104">應用程式可能需要跟蹤文本格式的任何更改，以便顯示工具列，如許多文字處理應用程式中。</span><span class="sxs-lookup"><span data-stu-id="292ec-104">Your application may need to keep track of any changes in text formatting for the purpose of displaying a toolbar, as in many word-processing applications.</span></span>  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a><span data-ttu-id="292ec-105">回應格式屬性的更改</span><span class="sxs-lookup"><span data-stu-id="292ec-105">To respond to changes in formatting attributes</span></span>  
  
1. <span data-ttu-id="292ec-106">在事件處理常式中<xref:System.Windows.Forms.RichTextBox.SelectionChanged>編寫代碼以執行適當的操作，具體取決於屬性的值。</span><span class="sxs-lookup"><span data-stu-id="292ec-106">Write code in the <xref:System.Windows.Forms.RichTextBox.SelectionChanged> event handler to perform an appropriate action depending on the value of the attribute.</span></span> <span data-ttu-id="292ec-107">下面的示例根據屬性的值更改工具列按鈕的外觀<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>。</span><span class="sxs-lookup"><span data-stu-id="292ec-107">The following example changes the appearance of a toolbar button depending on the value of the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="292ec-108">僅當插入點在控制項中移動時，才會更新工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="292ec-108">The toolbar button will only be updated when the insertion point is moved in the control.</span></span>  
  
     <span data-ttu-id="292ec-109">下面的示例假定表單具有<xref:System.Windows.Forms.RichTextBox>控制項和包含工具列按鈕的<xref:System.Windows.Forms.ToolBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="292ec-109">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control and a <xref:System.Windows.Forms.ToolBar> control that contains a toolbar button.</span></span> <span data-ttu-id="292ec-110">有關工具列和工具列按鈕的詳細資訊，請參閱[如何：將按鈕添加到工具列控制項](how-to-add-buttons-to-a-toolbar-control.md)。</span><span class="sxs-lookup"><span data-stu-id="292ec-110">For more information about toolbars and toolbar buttons, see [How to: Add Buttons to a ToolBar Control](how-to-add-buttons-to-a-toolbar-control.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="292ec-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="292ec-111">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="292ec-112">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="292ec-112">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="292ec-113">在 Windows Form 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="292ec-113">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
