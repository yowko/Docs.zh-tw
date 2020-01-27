---
title: PrintDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0ed7f7a1f9770f71b75ae744a056b6943335c852
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728675"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog 元件概觀 (Windows Form)

Windows Forms [PrintDialog](printdialog-component-windows-forms.md)元件是預先設定的對話方塊，用來選取印表機、選擇要列印的頁面，以及判斷 Windows 應用程式中的其他列印相關設定。 使用它做為印表機和列印相關設定選擇的簡單解決方案，就不需設定您自己的對話方塊。 您可以讓使用者列印檔案的許多部分： [列印全部]、[列印選取的頁面範圍] 或 [列印選取專案]。 藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。 <xref:System.Windows.Forms.PrintDialog> 元件繼承自 <xref:System.Windows.Forms.CommonDialog> 類別。

## <a name="working-with-the-component"></a>使用元件

使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法，在執行時間顯示對話方塊。 此元件具有與單一列印工作（<xref:System.Drawing.Printing.PrintDocument> 類別）或個別印表機（<xref:System.Drawing.Printing.PrinterSettings> 類別）設定相關的屬性。 其中任何一項都可以由多台印表機共用。

當它新增至表單時，<xref:System.Windows.Forms.PrintDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog 元件](printdialog-component-windows-forms.md)
