---
title: HOW TO：叫用 [列印] 對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 2ced508eb83e2955fdcd1ad87fb6415e2052446f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206040"
---
# <a name="how-to-invoke-a-print-dialog"></a>HOW TO：叫用 [列印] 對話方塊
若要讓您能夠從您的應用程式列印，可以只建立並開啟<xref:System.Windows.Controls.PrintDialog>物件。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Controls.PrintDialog> 控制項提供 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 組態的單一進入點和 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 工作提交。 控制項很容易使用且可以具現化使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]標記或程式碼。 下列範例會示範如何具現化，並開啟程式碼中的控制項，以及如何從中進行列印。 它也會示範如何確保對話方塊會授與使用者設定特定的頁面範圍的選項。 範例程式碼假設 c： 磁碟機的根目錄中的檔案 FixedDocumentSequence.xps。  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 對話方塊開啟之後，使用者將能夠從他們的電腦上安裝的印表機中選取。 它們也會選取的選項[Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)建立[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]檔案而不列印。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>控制[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，已討論過本主題中，不應混淆與<xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType>Windows Forms 的元件。  
  
 嚴格來說，您可以使用<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>方法，而不需要不斷開啟對話方塊。 這點而言，此控制項可用來當做看不見的列印元件。 但基於效能考量，它會使用其中一個<xref:System.Printing.PrintQueue.AddJob%2A>方法，或任何一種<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>並<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法<xref:System.Windows.Xps.XpsDocumentWriter>。 如需詳細資訊，請參閱 <<c0> [ 以程式設計方式列印 XPS 檔](how-to-programmatically-print-xps-files.md)和。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.PrintDialog>
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
- [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)
