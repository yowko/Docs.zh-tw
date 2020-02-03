---
title: OpenFileDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728432"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog 元件概觀 (Windows Form)

Windows Form <xref:System.Windows.Forms.OpenFileDialog> 元件是預先設定的對話方塊。 這是 Windows 作業系統所公開的相同 [**開啟**檔案] 對話方塊。 這個元件繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。

## <a name="use-this-component"></a>使用此元件

在以 Windows 為基礎的應用程式中使用此元件，做為檔案選取的簡單解決方案，而不是設定您自己的對話方塊。 藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。 不過要注意的是，使用 <xref:System.Windows.Forms.OpenFileDialog> 元件時，您必須撰寫自己的檔案開啟邏輯。

使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法，在執行時間顯示對話方塊。 您可以讓使用者透過 [<xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>] 屬性，以多重選取要開啟的檔案。 此外，您可以使用 [<xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>] 屬性來判斷對話方塊中是否出現唯讀核取方塊。 [<xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A>] 屬性會指出是否已選取 [唯讀] 核取方塊。 最後，<xref:System.Windows.Forms.FileDialog.Filter%2A> 屬性會設定目前的檔案名篩選字串，以決定出現在對話方塊中 [檔案類型] 方塊中的選項。

當它新增至表單時，<xref:System.Windows.Forms.OpenFileDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog 元件](openfiledialog-component-windows-forms.md)
