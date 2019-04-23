---
title: PageSetupDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 30ac782cae830ac996132046cbbc57392067c0ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228311"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog 元件概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.PageSetupDialog>元件是預先設定的對話方塊，用於以 Windows 為基礎的應用程式中設定列印的頁面詳細資料。 它用於應用程式內以 Windows 為基礎的簡單解決方案，為使用者設定頁面的喜好設定，不需設定您自己的對話方塊。 您可以讓使用者設定框線和邊界調整、 頁首和頁尾和直向或橫向方向。 藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示對話方塊。 這個元件有您可以設定為單一頁面的相關屬性 (<xref:System.Drawing.Printing.PrintDocument>類別) 或任何文件 (<xref:System.Drawing.Printing.PageSettings>類別)。 此外，<xref:System.Windows.Forms.PageSetupDialog>元件可以用來判斷特定的印表機設定，會儲存在<xref:System.Drawing.Printing.PrinterSettings>類別。  
  
 當加入至表單，<xref:System.Windows.Forms.PageSetupDialog>元件會出現在底部的 Windows Form 設計工具的紙匣。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PageSetupDialog>
- [PageSetupDialog 元件](pagesetupdialog-component-windows-forms.md)
