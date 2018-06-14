---
title: ColorDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526034"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog 元件概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.ColorDialog>元件是預先設定的對話方塊，可讓使用者從調色盤選取色彩，並將自訂色彩加入該調色盤。 這是您在其他 Windows 應用程式中看到可選取色彩的相同對話方塊。 只要在 Windows 應用程式中使用這個控制項，便不需要設定自己的對話方塊。  
  
 在對話方塊中選取的色彩中傳回<xref:System.Windows.Forms.ColorDialog.Color%2A>屬性。 如果<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>屬性設定為`false`、 」 定義自訂色彩 」 按鈕已停用，而且使用者是限制為預先定義的色彩調色盤中。 如果<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>屬性設定為`true`，使用者無法選取遞色的色彩。 若要顯示對話方塊中，您必須呼叫其<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog 元件](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [對話方塊控制項和元件](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [操作說明：變更 Windows Forms ColorDialog 元件的外觀](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
