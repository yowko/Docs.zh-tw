---
title: OpenFileDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: 24327ded50ac927642e2687b40b1f10de9bdf41e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211713"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog 元件概觀 (Windows Form)

Windows Form <xref:System.Windows.Forms.OpenFileDialog> 元件是預先設定的對話方塊。 它會是相同**開啟檔案**Windows 作業系統所公開的對話方塊。 這個元件繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。

## <a name="use-this-component"></a>使用此元件

使用您以 Windows 為基礎的應用程式中的此元件做為簡單的解決方案，不需設定您自己的對話方塊中選擇的檔案。 藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。 不過，要注意，當使用<xref:System.Windows.Forms.OpenFileDialog>元件，您必須撰寫您自己的檔案開啟邏輯。

使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示對話方塊。 您可以讓使用者以複選的檔案以開啟<xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>屬性。 此外，您可以使用<xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>屬性來判斷是否唯讀核取方塊會出現在對話方塊中。 <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A>屬性會指出是否已選取唯讀核取方塊。 最後，<xref:System.Windows.Forms.FileDialog.Filter%2A>屬性會設定目前檔案名稱篩選條件字串，用來決定在對話方塊中的 「 檔案類型 方塊中顯示的選項。

當加入至表單，<xref:System.Windows.Forms.OpenFileDialog>元件會出現在底部的 Windows Form 設計工具，在 Visual Studio 中的紙匣。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog 元件](openfiledialog-component-windows-forms.md)
