---
title: "PageSetupDialog 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd2162cd2b538b5c6277991fab0ce40762f6c07d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog 元件概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.PageSetupDialog>元件是預先設定的對話方塊，用來設定 Windows 架構應用程式中列印的頁面詳細資料。 它應用程式中使用 windows 做為簡單的解決方案使用者設定 頁面就不需設定您自己的對話方塊。 您可以讓使用者設定框線和邊界調整、 頁首和頁尾和縱向或橫向。 藉由標準 Windows 對話方塊，建立使用者可立即熟悉基本功能的應用程式。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以在執行階段顯示對話方塊。 這個元件有您可以設定的屬性與相關的是單一頁面 (<xref:System.Drawing.Printing.PrintDocument>類別) 或任何文件 (<xref:System.Drawing.Printing.PageSettings>類別)。 此外，<xref:System.Windows.Forms.PageSetupDialog>元件可以用來判斷特定的印表機設定，儲存在<xref:System.Drawing.Printing.PrinterSettings>類別。  
  
 當加入至表單，<xref:System.Windows.Forms.PageSetupDialog>元件會出現在 Windows Form 設計工具底部的紙匣。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [PageSetupDialog 元件](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
