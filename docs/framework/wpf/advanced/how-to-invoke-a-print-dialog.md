---
title: "如何：叫用列印對話方塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8831566daca6ca36b40fbaaedbec9ff3ca8aaa99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-invoke-a-print-dialog"></a>如何：叫用列印對話方塊
若要讓您能夠從您的應用程式列印，可以只建立並開啟<xref:System.Windows.Controls.PrintDialog>物件。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.PrintDialog> 控制項提供 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 組態的單一進入點和 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 工作提交。 控制項是簡單易用，而且可以使用具現化[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]標記或程式碼。 下列範例會示範如何具現化及開啟程式碼中的控制項，以及如何從中進行列印。 它也會示範如何確定對話方塊將會授與使用者設定特定的頁面範圍的選項。 程式碼範例假設檔案 FixedDocumentSequence.xps c： 磁碟機根目錄中。  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 一旦開啟對話方塊，使用者將能夠從他們的電腦上安裝的印表機中選取。 它們也會具有選擇[Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)建立[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]檔案而不列印。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>控制[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，本主題討論應不與混淆<xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType>元件[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]。  
  
 嚴格來說，您可以使用<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>方法，而不開啟對話方塊。 該意義而言，控制項可用來當作看不見的列印元件。 但基於效能考量，最好是使用<xref:System.Printing.PrintQueue.AddJob%2A>方法或任何一種<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>和<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法<xref:System.Windows.Xps.XpsDocumentWriter>。 如需有關此，請參閱[以程式設計方式列印 XPS 檔](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md)和。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Controls.PrintDialog>  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)
