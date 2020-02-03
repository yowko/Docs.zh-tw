---
title: 變更 ColorDialog 元件的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746644"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>如何：變更 Windows Form ColorDialog 元件的外觀
您可以使用多個屬性來設定 Windows Forms <xref:System.Windows.Forms.ColorDialog> 元件的外觀。 對話方塊有兩個區段：一個顯示基本色彩，另一個則可讓使用者定義自訂色彩。  
  
 大部分的屬性會限制使用者可以從對話方塊中選取的色彩。 如果 [<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>] 屬性設定為 [`true`]，則允許使用者定義自訂色彩。 如果對話方塊已展開以定義自訂色彩，則會 `true` [<xref:System.Windows.Forms.ColorDialog.FullOpen%2A>] 屬性;否則，使用者必須按一下 [定義自訂色彩] 按鈕。 當 [<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>] 屬性設定為 [`true`] 時，對話方塊會顯示一組基本色彩中的所有可用色彩。 如果 [<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>] 屬性設為 [`true`]，使用者就無法選取遞色色彩;只有純色可供選取。  
  
 如果 [<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>] 屬性設定為 [`true`]，則對話方塊上會出現 [說明] 按鈕。 當使用者按一下 [說明] 按鈕時，就會引發 <xref:System.Windows.Forms.ColorDialog> 元件的 <xref:System.Windows.Forms.CommonDialog.HelpRequest> 事件。  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>設定 [色彩] 對話方塊的外觀  
  
1. 將 [<xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>]、[<xref:System.Windows.Forms.ColorDialog.AnyColor%2A>]、[<xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>] 和 [<xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>] 屬性設為所需的值。  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog 元件](colordialog-component-windows-forms.md)
- [ColorDialog 元件概觀](colordialog-component-overview-windows-forms.md)
