---
title: 如何：建立唯讀文字方塊 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 06e03f67bd1f084b30bce85c3d81ad7b8c97a1b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>如何：建立唯讀文字方塊 (Windows Form)
您可以將可編輯的 Windows Form 文字方塊中轉換成唯讀的控制項。 例如，文字方塊可能會顯示值通常編輯，但可能不是目前，因為應用程式的狀態。  
  
### <a name="to-create-a-read-only-text-box"></a>若要建立唯讀文字方塊  
  
1.  設定<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性`true`。 屬性設定為`true`，使用者仍可以捲動及反白顯示 不允許變更 在文字方塊中的文字。 A**複製**命令仍在文字方塊中，但**剪下**和**貼上** 命令。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性只會影響執行階段的使用者互動。 您仍然可以變更文字方塊內容以程式設計方式在執行階段變更<xref:System.Windows.Forms.TextBox.Text%2A>文字方塊的屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox 控制項概觀](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [操作說明：控制 Windows Forms TextBox 控制項中的插入點](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [操作說明：使用 Windows Forms TextBox 控制項建立密碼文字方塊](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [操作說明：將引號放入字串中](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [操作說明：在 Windows Forms TextBox 控制項中選取文字](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [操作說明：在 Windows Forms TextBox 控制項中檢視多行](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox 控制項](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
