---
title: 作法：叫用 [列印] 對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 4bad8158925fea8af529f70f92aad74e2a6bbec0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254104"
---
# <a name="how-to-invoke-a-print-dialog"></a>HOW TO：叫用 [列印] 對話方塊
若要提供從您的應用程式列印的功能, 您可以直接建立並<xref:System.Windows.Controls.PrintDialog>開啟物件。  
  
## <a name="example"></a>範例  
 控制項提供[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、設定和 XPS 工作提交的單一進入點。 <xref:System.Windows.Controls.PrintDialog> 控制項很容易使用, 而且可以使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]標記或程式碼來具現化。 下列範例示範如何在程式碼中具現化和開啟控制項, 以及如何從它進行列印。 它也會示範如何確保對話方塊會提供使用者設定特定頁面範圍的選項。 範例程式碼假設 C: 磁片磁碟機的根目錄中有一個檔案 FixedDocumentSequence。  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 對話方塊開啟之後, 使用者就可以從安裝在其電腦上的印表機中選取。 他們也可以選擇選取[MICROSOFT XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)來建立 XML 檔規格 (Xps) 檔案, 而不是列印。  
  
> [!NOTE]
> 本主題中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]討論的<xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> 控制項不應該與WindowsForms<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>的元件混淆。  
  
 嚴格來說, 您可以使用<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>方法, 而不需要開啟對話方塊。 就這一點而言, 控制項可用來做為看不見的列印元件。 但基於效能的考慮, 最好是<xref:System.Printing.PrintQueue.AddJob%2A>使用方法或的多<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>個和<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法<xref:System.Windows.Xps.XpsDocumentWriter>其中之一。 如需詳細資訊, 請參閱以程式設計[方式列印 XPS](how-to-programmatically-print-xps-files.md)檔案和。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.PrintDialog>
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
- [Microsoft XPS 檔寫入器](https://go.microsoft.com/fwlink/?LinkId=147319)
