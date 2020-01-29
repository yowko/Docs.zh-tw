---
title: ColorDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736960"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog 元件概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.ColorDialog> 元件是預先設定的對話方塊，可讓使用者從調色板選取色彩，並將自訂色彩新增至該色板。 這是您在其他 Windows 應用程式中看到可選取色彩的相同對話方塊。 只要在 Windows 應用程式中使用這個控制項，便不需要設定自己的對話方塊。  
  
 在對話方塊中選取的色彩會在 <xref:System.Windows.Forms.ColorDialog.Color%2A> 屬性中傳回。 如果 [<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>] 屬性設定為 [`false`]，則會停用 [定義自訂色彩] 按鈕，並將使用者限制為調色板中預先定義的色彩。 如果 [<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>] 屬性設定為 [`true`]，使用者就無法選取遞色。 若要顯示對話方塊，您必須呼叫其 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog 元件](colordialog-component-windows-forms.md)
- [對話方塊控制項和元件](dialog-box-controls-and-components-windows-forms.md)
- [如何：變更 Windows Forms ColorDialog 元件的外觀](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
