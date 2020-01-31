---
title: PageSetupDialog 元件概觀
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: a891cb8cc77007d7591d41461c94f61c077eb300
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744336"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog 元件概觀 (Windows Form)

Windows Forms <xref:System.Windows.Forms.PageSetupDialog> 元件是預先設定的對話方塊，用來設定以 Windows 為基礎的應用程式中列印的頁面詳細資料。 在以 Windows 為基礎的應用程式中使用它作為簡單的解決方案，讓使用者可以設定頁面喜好設定，而不需要設定您自己的對話方塊。 您可以讓使用者設定框線和邊界調整、頁首和頁尾，以及直向或橫向方向。 藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。

## <a name="key-properties-and-methods"></a>索引鍵屬性和方法

使用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 方法，在執行時間顯示對話方塊。 此元件具有您可以設定的屬性，其與單一頁面（<xref:System.Drawing.Printing.PrintDocument> 類別）或任何檔（<xref:System.Drawing.Printing.PageSettings> 類別）相關。 此外，<xref:System.Windows.Forms.PageSetupDialog> 元件可以用來判斷特定印表機設定，這些設定會儲存在 <xref:System.Drawing.Printing.PrinterSettings> 類別中。

當它新增至表單時，<xref:System.Windows.Forms.PageSetupDialog> 元件會出現在 Visual Studio Windows Form 設計工具底部的紙匣中。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.PageSetupDialog>
- [PageSetupDialog Component](pagesetupdialog-component-windows-forms.md)
