---
title: "如何：叫用列印對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "叫用列印對話方塊"
  - "列印對話方塊, 叫用"
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：叫用列印對話方塊
若要提供從應用程式進行列印的功能，則只需要建立並開啟 <xref:System.Windows.Controls.PrintDialog> 物件。  
  
## 範例  
 <xref:System.Windows.Controls.PrintDialog> 控制項可提供 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、組態與 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 工作提交的單一進入點。  這個控制項十分容易使用，而且可以使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 標記或程式碼具現化 \(Instantiate\)。  下列範例示範如何使用程式碼具現化和開啟控制項，以及如何從中進行列印。  也會顯示如何確保對話方塊提供選項，讓使用者設定特定範圍的頁數。  這個範例程式碼假設在 C: 磁碟機的根目錄中有 FixedDocumentSequence.xps 檔案。  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 開啟對話方塊之後，使用者就可以從他們電腦上安裝的印表機中進行選取。  他們也可以選擇選取 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319) \(英文\) 來建立 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] 檔案，而不是進行列印。  
  
> [!NOTE]
>  本主題討論之 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 的 <xref:System.Windows.Controls.PrintDialog?displayProperty=fullName> 控制項，不應該與 [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] 的 <xref:System.Windows.Forms.PrintDialog?displayProperty=fullName> 元件混淆。  
  
 嚴格來說，您可以使用 <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> 方法，而不需開啟對話方塊。  就該意義而言，控制項可以用做看不見的列印元件。  但為了效能理由，最好使用 <xref:System.Printing.PrintQueue.AddJob%2A> 方法或其中一個 <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>，以及 <xref:System.Windows.Xps.XpsDocumentWriter> 的 <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> 方法。  如需此方面的詳細資訊，請參閱 [以程式設計方式列印 XPS 檔](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md)。  
  
## 請參閱  
 <xref:System.Windows.Controls.PrintDialog>   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)