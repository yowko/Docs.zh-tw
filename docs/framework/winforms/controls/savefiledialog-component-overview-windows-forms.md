---
title: SaveFileDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 93bf0f63e18ee3a384aa062c80faa991b68a6abe
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721498"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog 元件概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.SaveFileDialog> 元件是預先設定的對話方塊。 它等同於標準**儲存檔案**Windows 所使用的對話方塊。 這個元件繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。  
  
## <a name="working-with-the-savefiledialog-component"></a>使用 SaveFileDialog 元件  
 使用它作為簡單的解決方案可讓使用者儲存檔案，而不是設定您自己的對話方塊。 藉由標準 Windows 對話方塊，您所建立的應用程式的基本功能是使用者可立即熟悉。 不過，要注意，當使用<xref:System.Windows.Forms.SaveFileDialog>元件，您必須撰寫您自己的檔案儲存邏輯。  
  
 您可以使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示的對話方塊。 您可以開啟檔案讀取/寫入模式使用<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>方法。  
  
 當加入至表單，<xref:System.Windows.Forms.SaveFileDialog>元件會出現在底部的 Windows Form 設計工具的紙匣。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog 元件](savefiledialog-component-windows-forms.md)
