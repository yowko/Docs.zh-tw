---
title: "逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65afce3e5a5b113b5243d68fd3b35231e2d92f86
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="103a4-102">逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="103a4-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="103a4-103"> 提供具有豐富功能集的許多控制項。</span><span class="sxs-lookup"><span data-stu-id="103a4-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="103a4-104">不過，您有時可以使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]上的控制項，您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="103a4-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="103a4-105">比方說，您可能必須在現有了大筆投資[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，或您可能會有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，提供唯一的功能。</span><span class="sxs-lookup"><span data-stu-id="103a4-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="103a4-106">本逐步解說會示範如何裝載 Windows Form<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>上控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="103a4-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="103a4-107">本逐步解說中的工作的完整程式碼清單，請參閱[WPF 所使用的 XAML 範例中將 Windows Form 控制項裝載](http://go.microsoft.com/fwlink/?LinkID=160000)。</span><span class="sxs-lookup"><span data-stu-id="103a4-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](http://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="103a4-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="103a4-108">Prerequisites</span></span>  
 <span data-ttu-id="103a4-109">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="103a4-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="103a4-110">.</span><span class="sxs-lookup"><span data-stu-id="103a4-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="103a4-111">裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="103a4-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="103a4-112">裝載 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="103a4-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="103a4-113">建立 WPF 應用程式專案，名為`HostingWfInWpfWithXaml`。</span><span class="sxs-lookup"><span data-stu-id="103a4-113">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="103a4-114">加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="103a4-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="103a4-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="103a4-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="103a4-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="103a4-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="103a4-117">開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="103a4-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="103a4-118">在<xref:System.Windows.Window>項目，加入下列命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="103a4-118">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="103a4-119">`wf`命名空間對應會建立包含組件的參考[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="103a4-119">The `wf` namespace mapping establishes a reference to the assembly that contains the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="103a4-120">在<xref:System.Windows.Controls.Grid>加入下列 XAML 項目。</span><span class="sxs-lookup"><span data-stu-id="103a4-120">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="103a4-121"><xref:System.Windows.Forms.MaskedTextBox>建立控制項的子系<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。</span><span class="sxs-lookup"><span data-stu-id="103a4-121">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="103a4-122">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="103a4-122">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="103a4-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="103a4-123">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="103a4-124">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="103a4-124">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="103a4-125">逐步解說：在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="103a4-125">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="103a4-126">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="103a4-126">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="103a4-127">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="103a4-127">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="103a4-128">Windows Form 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="103a4-128">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="103a4-129">使用 XAML 範例中裝載 WPF 中的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="103a4-129">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160000)
