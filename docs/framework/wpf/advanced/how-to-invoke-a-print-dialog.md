---
title: 如何：叫用列印對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 271652fe9e98f9a381da5655bd313e12f8ee917d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068546"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="50627-102">如何：叫用列印對話方塊</span><span class="sxs-lookup"><span data-stu-id="50627-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="50627-103">若要讓您能夠從您的應用程式列印，可以只建立並開啟<xref:System.Windows.Controls.PrintDialog>物件。</span><span class="sxs-lookup"><span data-stu-id="50627-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50627-104">範例</span><span class="sxs-lookup"><span data-stu-id="50627-104">Example</span></span>  
 <span data-ttu-id="50627-105"><xref:System.Windows.Controls.PrintDialog> 控制項提供 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 組態的單一進入點和 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] 工作提交。</span><span class="sxs-lookup"><span data-stu-id="50627-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="50627-106">控制項很容易使用且可以具現化使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]標記或程式碼。</span><span class="sxs-lookup"><span data-stu-id="50627-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="50627-107">下列範例會示範如何具現化，並開啟程式碼中的控制項，以及如何從中進行列印。</span><span class="sxs-lookup"><span data-stu-id="50627-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="50627-108">它也會示範如何確保對話方塊會授與使用者設定特定的頁面範圍的選項。</span><span class="sxs-lookup"><span data-stu-id="50627-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="50627-109">範例程式碼假設 c： 磁碟機的根目錄中的檔案 FixedDocumentSequence.xps。</span><span class="sxs-lookup"><span data-stu-id="50627-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="50627-110">對話方塊開啟之後，使用者將能夠從他們的電腦上安裝的印表機中選取。</span><span class="sxs-lookup"><span data-stu-id="50627-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="50627-111">它們也會選取的選項[Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319)建立[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]檔案而不列印。</span><span class="sxs-lookup"><span data-stu-id="50627-111">They will also have the option of selecting the [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50627-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>控制[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，已討論過本主題中，不應混淆與<xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType>Windows Forms 的元件。</span><span class="sxs-lookup"><span data-stu-id="50627-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="50627-113">嚴格來說，您可以使用<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>方法，而不需要不斷開啟對話方塊。</span><span class="sxs-lookup"><span data-stu-id="50627-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="50627-114">這點而言，此控制項可用來當做看不見的列印元件。</span><span class="sxs-lookup"><span data-stu-id="50627-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="50627-115">但基於效能考量，它會使用其中一個<xref:System.Printing.PrintQueue.AddJob%2A>方法，或任何一種<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>並<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>方法<xref:System.Windows.Xps.XpsDocumentWriter>。</span><span class="sxs-lookup"><span data-stu-id="50627-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="50627-116">如需詳細資訊，請參閱 <<c0> [ 以程式設計方式列印 XPS 檔](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md)和。</span><span class="sxs-lookup"><span data-stu-id="50627-116">For more about this, see [Programmatically Print XPS Files](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50627-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50627-117">See Also</span></span>  
 <xref:System.Windows.Controls.PrintDialog>  
 [<span data-ttu-id="50627-118">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="50627-118">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="50627-119">列印概觀</span><span class="sxs-lookup"><span data-stu-id="50627-119">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="50627-120">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="50627-120">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
