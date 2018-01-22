---
title: "逐步解說：在 WPF 中裝載 Windows Form 控制項"
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
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce6920e8a6cea08f4aba083b99d56b4252409827
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="86616-102">逐步解說：在 WPF 中裝載 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="86616-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="86616-103"> 提供具有豐富功能集的許多控制項。</span><span class="sxs-lookup"><span data-stu-id="86616-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="86616-104">不過，您有時可以使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]上的控制項，您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="86616-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="86616-105">比方說，您可能必須在現有了大筆投資[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，或您可能會有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，提供唯一的功能。</span><span class="sxs-lookup"><span data-stu-id="86616-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="86616-106">本逐步解說會示範如何裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>上控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面上，使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="86616-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>  
  
 <span data-ttu-id="86616-107">本逐步解說中的工作的完整程式碼清單，請參閱[裝載 Windows Form 控制項中 WPF 範例](http://go.microsoft.com/fwlink/?LinkID=160057)。</span><span class="sxs-lookup"><span data-stu-id="86616-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="86616-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="86616-108">Prerequisites</span></span>  
 <span data-ttu-id="86616-109">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="86616-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="86616-110">.</span><span class="sxs-lookup"><span data-stu-id="86616-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="86616-111">裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="86616-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="86616-112">裝載 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="86616-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="86616-113">建立 WPF 應用程式專案，名為`HostingWfInWpf`。</span><span class="sxs-lookup"><span data-stu-id="86616-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>  
  
2.  <span data-ttu-id="86616-114">加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="86616-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="86616-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="86616-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="86616-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="86616-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="86616-117">開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="86616-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="86616-118">名稱<xref:System.Windows.Controls.Grid>元素`grid1`。</span><span class="sxs-lookup"><span data-stu-id="86616-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  <span data-ttu-id="86616-119">在 [設計] 檢視或 [XAML] 檢視中，選取<xref:System.Windows.Window>項目。</span><span class="sxs-lookup"><span data-stu-id="86616-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="86616-120">在 屬性 視窗中，按一下**事件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="86616-120">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="86616-121">按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="86616-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="86616-122">插入下列程式碼來處理<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="86616-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. <span data-ttu-id="86616-123">在檔案頂端，加入下列`Imports`或`using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="86616-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. <span data-ttu-id="86616-124">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="86616-124">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86616-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="86616-125">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="86616-126">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="86616-126">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="86616-127">逐步解說：使用 XAML 在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="86616-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [<span data-ttu-id="86616-128">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="86616-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="86616-129">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="86616-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="86616-130">Windows Form 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="86616-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 <span data-ttu-id="86616-131">[Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057) (在 WPF 中裝載 Windows Forms 控制項的範例)</span><span class="sxs-lookup"><span data-stu-id="86616-131">[Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057)</span></span>
