---
title: SaveFileDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743107"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog 元件概觀 (Windows Form)

Windows Form <xref:System.Windows.Forms.SaveFileDialog> 元件是預先設定的對話方塊。 這與 Windows 所使用的標準 [**儲存**盤案] 對話方塊相同。 這個元件繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。

## <a name="working-with-the-savefiledialog-component"></a>使用 SaveFileDialog 元件

使用它作為簡單的解決方案，讓使用者可以儲存檔案，而不是設定您自己的對話方塊。 藉由依賴標準 Windows 對話方塊，使用者可以立即熟悉您所建立的應用程式基本功能。 不過要注意的是，使用 <xref:System.Windows.Forms.SaveFileDialog> 元件時，您必須撰寫自己的檔案儲存邏輯。

您可以使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法，在執行時間顯示對話方塊。 您可以使用 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法，在讀取/寫入模式中開啟檔案。

當它新增至表單時，<xref:System.Windows.Forms.SaveFileDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog 元件](savefiledialog-component-windows-forms.md)
