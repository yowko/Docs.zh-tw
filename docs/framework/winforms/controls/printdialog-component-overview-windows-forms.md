---
title: PrintDialog 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 2478990e3cec00df9a748dbd9875485e5f060ed7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211748"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog 元件概觀 (Windows Form)

Windows Forms [PrintDialog](printdialog-component-windows-forms.md)元件是預先設定的對話方塊，用來選取印表機、 選擇要列印的頁面以及決定其他列印相關設定以 Windows 為基礎的應用程式中。 使用它做為印表機和列印相關設定選擇的簡單解決方案，就不需設定您自己的對話方塊。 您可以讓使用者列印文件中的許多部分： 列印全部、 列印選取的頁面範圍或列印選取的範圍。 藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。 <xref:System.Windows.Forms.PrintDialog>元件繼承自<xref:System.Windows.Forms.CommonDialog>類別。

## <a name="working-with-the-component"></a>使用元件

使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示的對話方塊。 這個元件有指單一列印工作的屬性 (<xref:System.Drawing.Printing.PrintDocument>類別) 或個別的印表機設定 (<xref:System.Drawing.Printing.PrinterSettings>類別)。 任一種，反而會共用由多部印表機。

當加入至表單，<xref:System.Windows.Forms.PrintDialog>元件會出現在底部的 Windows Form 設計工具，在 Visual Studio 中的紙匣。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog 元件](printdialog-component-windows-forms.md)
