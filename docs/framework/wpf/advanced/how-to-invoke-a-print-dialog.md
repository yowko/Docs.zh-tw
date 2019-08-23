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
ms.openlocfilehash: cd7b06030e0fb2bba74590ee80c07c34047c5b47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950615"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="c8e92-102">作法：叫用 [列印] 對話方塊</span><span class="sxs-lookup"><span data-stu-id="c8e92-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="c8e92-103">若要提供從您的應用程式列印的功能, 您可以直接建立並<xref:System.Windows.Controls.PrintDialog>開啟物件。</span><span class="sxs-lookup"><span data-stu-id="c8e92-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8e92-104">範例</span><span class="sxs-lookup"><span data-stu-id="c8e92-104">Example</span></span>  
 <span data-ttu-id="c8e92-105"><xref:System.Windows.Controls.PrintDialog> 控制項提供 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 組態的單一進入點和 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 工作提交。</span><span class="sxs-lookup"><span data-stu-id="c8e92-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="c8e92-106">控制項很容易使用, 而且可以使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]標記或程式碼來具現化。</span><span class="sxs-lookup"><span data-stu-id="c8e92-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="c8e92-107">下列範例示範如何在程式碼中具現化和開啟控制項, 以及如何從它進行列印。</span><span class="sxs-lookup"><span data-stu-id="c8e92-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="c8e92-108">它也會示範如何確保對話方塊會提供使用者設定特定頁面範圍的選項。</span><span class="sxs-lookup"><span data-stu-id="c8e92-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="c8e92-109">範例程式碼假設 C: 磁片磁碟機的根目錄中有一個檔案 FixedDocumentSequence。</span><span class="sxs-lookup"><span data-stu-id="c8e92-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="c8e92-110">對話方塊開啟之後, 使用者就可以從安裝在其電腦上的印表機中選取。</span><span class="sxs-lookup"><span data-stu-id="c8e92-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="c8e92-111">他們也可以選擇選取[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] [Microsoft XPS 檔寫入器](https://go.microsoft.com/fwlink/?LinkId=147319)來建立檔案, 而不是列印。</span><span class="sxs-lookup"><span data-stu-id="c8e92-111">They will also have the option of selecting the [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8e92-112">本主題中[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]討論的<xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> 控制項不應該與WindowsForms<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>的元件混淆。</span><span class="sxs-lookup"><span data-stu-id="c8e92-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="c8e92-113">嚴格來說, 您可以使用<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>方法, 而不需要開啟對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c8e92-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="c8e92-114">就這一點而言, 控制項可用來做為看不見的列印元件。</span><span class="sxs-lookup"><span data-stu-id="c8e92-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="c8e92-115">但基於效能的考慮, 最好是<xref:System.Printing.PrintQueue.AddJob%2A>使用方法或的多<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>個和<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法<xref:System.Windows.Xps.XpsDocumentWriter>其中之一。</span><span class="sxs-lookup"><span data-stu-id="c8e92-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="c8e92-116">如需詳細資訊, 請參閱以程式設計[方式列印 XPS](how-to-programmatically-print-xps-files.md)檔案和。</span><span class="sxs-lookup"><span data-stu-id="c8e92-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e92-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8e92-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="c8e92-118">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="c8e92-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="c8e92-119">列印概觀</span><span class="sxs-lookup"><span data-stu-id="c8e92-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="c8e92-120">Microsoft XPS 檔寫入器</span><span class="sxs-lookup"><span data-stu-id="c8e92-120">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
