---
title: FontDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 3a4707ffe471161988d0526ce0908b37299f3e07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog 元件概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.FontDialog>元件是預先設定的對話方塊，這是標準的 Windows**字型**對話方塊用來公開目前安裝在系統的字型。 使用 Windows 架構應用程式做為簡單的解決方案內它就不需設定您自己的對話方塊中的字型選項。  
  
 根據預設，對話方塊會顯示清單方塊的字型、 字型樣式和大小。刪除線及底線; 等效果的核取方塊下拉式清單，如指令碼。和字型會如何出現的範例。 （指令碼指不同的字元可供指定之字型的指令碼，例如希伯來文或日文）。若要顯示 [字型] 對話方塊，請呼叫<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。  
  
## <a name="key-properties"></a>索引鍵內容  
 此元件的許多設定外觀屬性。 設定對話方塊中選取的屬性是<xref:System.Windows.Forms.FontDialog.Font%2A>和<xref:System.Windows.Forms.FontDialog.Color%2A>。 <xref:System.Windows.Forms.FontDialog.Font%2A>屬性會設定字型、 樣式、 大小、 指令碼，以及影響; 例如， `Arial, 10pt, style=Italic, Strikeout`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FontDialog>  
 [FontDialog 元件](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
