---
title: HOW TO：建立唯讀文字方塊 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 72dc188993474ad4b39f0cfa74cadffdb99ff46f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308571"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>HOW TO：建立唯讀文字方塊 (Windows Form)
您可以將可編輯的 Windows Form 文字方塊中轉換成唯讀的控制項。 例如，文字方塊可能會顯示值通常進行編輯，但可能不是目前因為應用程式的狀態。  
  
### <a name="to-create-a-read-only-text-box"></a>若要建立唯讀文字方塊  
  
1. 設定<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性設`true`。 屬性設為`true`，使用者仍然可以捲動，並反白顯示 不允許變更 文字 方塊中的文字。 A**複製**命令會在文字方塊中中, 運作，但**剪下**並**貼上**命令不是。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性只會影響在執行階段的使用者互動。 您仍然可以變更文字方塊內容以程式設計方式在執行階段變更<xref:System.Windows.Forms.TextBox.Text%2A>文字方塊的屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
- [HOW TO：控制 Windows Forms TextBox 控制項的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [HOW TO：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [HOW TO：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [HOW TO：選取 Windows Forms TextBox 控制項的文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [HOW TO：檢視 Windows Forms TextBox 控制項中的多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
