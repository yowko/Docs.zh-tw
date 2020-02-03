---
title: FontDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745700"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog 元件概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.FontDialog> 元件是預先設定的對話方塊，這是標準的 Windows**字型** 對話方塊，用來公開目前安裝于系統上的字型。 在以 Windows 為基礎的應用程式中使用它做為字型選擇的簡單解決方案，而不是設定自己的對話方塊。  
  
 根據預設，對話方塊會顯示字型、字型樣式和大小的清單方塊;像是刪除線和底線等效果的核取方塊;腳本的下拉式清單;以及字型外觀的範例。 （腳本是指適用于指定字型的不同字元腳本，例如希伯來文或日文）。若要顯示 [字型] 對話方塊，請呼叫 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法。  
  
## <a name="key-properties"></a>索引鍵內容  
 元件有數個屬性可設定其外觀。 設定對話方塊選項的屬性會 <xref:System.Windows.Forms.FontDialog.Font%2A> 並 <xref:System.Windows.Forms.FontDialog.Color%2A>。 <xref:System.Windows.Forms.FontDialog.Font%2A> 屬性會設定字型、樣式、大小、腳本和效果;例如，`Arial, 10pt, style=Italic, Strikeout`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FontDialog>
- [FontDialog 元件](fontdialog-component-windows-forms.md)
