---
title: HOW TO：建立唯讀文字方塊 (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971948"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>作法：建立唯讀文字方塊 (Windows Forms)

您可以將可編輯的 Windows Forms 文字方塊轉換成隻讀控制項。 例如, 因為應用程式的狀態, 文字方塊可能會顯示通常已編輯但目前可能不是的值。

## <a name="to-create-a-read-only-text-box"></a>若要建立唯讀文字方塊

1. 將控制項的<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>屬性設為`true`。 <xref:System.Windows.Forms.TextBox> 當屬性設定為`true`時, 使用者仍然可以在文字方塊中滾動並反白顯示文字, 而不允許變更。 **複製**命令在文字方塊中可正常運作, 但**剪**下和**貼**上命令則不會。

    > [!NOTE]
    > 屬性<xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>只會影響執行時間的使用者互動。 您仍然可以藉由變更文字方塊的<xref:System.Windows.Forms.TextBox.Text%2A>屬性, 在執行時間以程式設計方式變更文字方塊內容。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控制項概觀](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows Forms TextBox 控制項中的插入點](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：使用 Windows Forms TextBox 控制項建立密碼文字方塊](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：將引號放入字串中](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：選取 Windows Forms TextBox 控制項中的文字](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows Forms TextBox 控制項中查看多行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控制項](textbox-control-windows-forms.md)
