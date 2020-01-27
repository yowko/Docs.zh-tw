---
title: 判斷在 RichTextBox 控制項中格式化屬性何時變更
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
ms.openlocfilehash: f9b2a1028f79059ec7d4d6bf3683100455bb5dea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746044"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="c35e5-102">如何：判斷 Windows Form RichTextBox 控制項中的格式屬性何時變更</span><span class="sxs-lookup"><span data-stu-id="c35e5-102">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="c35e5-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> 控制項的常見用法是使用字型選項或段落樣式等屬性來格式化文字。</span><span class="sxs-lookup"><span data-stu-id="c35e5-103">A common use of the Windows Forms <xref:System.Windows.Forms.RichTextBox> control is formatting text with attributes such as font options or paragraph styles.</span></span> <span data-ttu-id="c35e5-104">您的應用程式可能需要追蹤文字格式的任何變更，以顯示工具列，如同許多文字處理應用程式一樣。</span><span class="sxs-lookup"><span data-stu-id="c35e5-104">Your application may need to keep track of any changes in text formatting for the purpose of displaying a toolbar, as in many word-processing applications.</span></span>  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a><span data-ttu-id="c35e5-105">若要回應格式化屬性的變更</span><span class="sxs-lookup"><span data-stu-id="c35e5-105">To respond to changes in formatting attributes</span></span>  
  
1. <span data-ttu-id="c35e5-106">在 <xref:System.Windows.Forms.RichTextBox.SelectionChanged> 事件處理常式中撰寫程式碼，以根據屬性的值執行適當的動作。</span><span class="sxs-lookup"><span data-stu-id="c35e5-106">Write code in the <xref:System.Windows.Forms.RichTextBox.SelectionChanged> event handler to perform an appropriate action depending on the value of the attribute.</span></span> <span data-ttu-id="c35e5-107">下列範例會根據 <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> 屬性的值來變更工具列按鈕的外觀。</span><span class="sxs-lookup"><span data-stu-id="c35e5-107">The following example changes the appearance of a toolbar button depending on the value of the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="c35e5-108">只有當插入點在控制項中移動時，工具列按鈕才會更新。</span><span class="sxs-lookup"><span data-stu-id="c35e5-108">The toolbar button will only be updated when the insertion point is moved in the control.</span></span>  
  
     <span data-ttu-id="c35e5-109">下列範例假設有一個表單具有 <xref:System.Windows.Forms.RichTextBox> 控制項，以及一個包含工具列按鈕的 <xref:System.Windows.Forms.ToolBar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="c35e5-109">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control and a <xref:System.Windows.Forms.ToolBar> control that contains a toolbar button.</span></span> <span data-ttu-id="c35e5-110">如需工具列和工具列按鈕的詳細資訊，請參閱[如何：將按鈕加入至工具列控制項](how-to-add-buttons-to-a-toolbar-control.md)。</span><span class="sxs-lookup"><span data-stu-id="c35e5-110">For more information about toolbars and toolbar buttons, see [How to: Add Buttons to a ToolBar Control](how-to-add-buttons-to-a-toolbar-control.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c35e5-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="c35e5-111">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="c35e5-112">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="c35e5-112">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="c35e5-113">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="c35e5-113">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
