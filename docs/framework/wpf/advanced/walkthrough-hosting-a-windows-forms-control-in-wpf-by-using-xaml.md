---
title: 逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: eafed4db9b40d3cd6b83087d0ea4999b0854c417
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845329"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="e3bab-102">逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="e3bab-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="e3bab-103">提供具有豐富功能集的許多控制項。</span><span class="sxs-lookup"><span data-stu-id="e3bab-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="e3bab-104">不過，您有時可以使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制上您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="e3bab-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="e3bab-105">比方說，您可能已長期開發現有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，或您可能會有[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項，提供獨特的功能。</span><span class="sxs-lookup"><span data-stu-id="e3bab-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="e3bab-106">本逐步解說會示範如何裝載 Windows Forms<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>控制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面上，使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e3bab-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="e3bab-107">如需完整的程式碼的清單在本逐步解說所示範的工作，請參閱 <<c0> [ 裝載 Windows Forms 控制項中所使用的 XAML 範例 WPF](https://go.microsoft.com/fwlink/?LinkID=160000)。</span><span class="sxs-lookup"><span data-stu-id="e3bab-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e3bab-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="e3bab-108">Prerequisites</span></span>  

<span data-ttu-id="e3bab-109">您需要完成這個逐步解說 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e3bab-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="e3bab-110">裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e3bab-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="e3bab-111">裝載 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="e3bab-111">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="e3bab-112">建立 WPF 應用程式專案，名為`HostingWfInWpfWithXaml`。</span><span class="sxs-lookup"><span data-stu-id="e3bab-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="e3bab-113">加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="e3bab-113">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="e3bab-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="e3bab-114">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="e3bab-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="e3bab-115">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="e3bab-116">開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e3bab-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="e3bab-117">在 <xref:System.Windows.Window>項目，加入下列命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="e3bab-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="e3bab-118">`wf`命名空間對應會建立包含在 Windows Form 控制項的組件的參考。</span><span class="sxs-lookup"><span data-stu-id="e3bab-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="e3bab-119">在 <xref:System.Windows.Controls.Grid>加入下列 XAML 項目。</span><span class="sxs-lookup"><span data-stu-id="e3bab-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="e3bab-120"><xref:System.Windows.Forms.MaskedTextBox>控制項會建立為子系<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項。</span><span class="sxs-lookup"><span data-stu-id="e3bab-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="e3bab-121">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e3bab-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3bab-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3bab-122">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="e3bab-123">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="e3bab-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [<span data-ttu-id="e3bab-124">逐步解說：在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e3bab-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="e3bab-125">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="e3bab-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="e3bab-126">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="e3bab-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="e3bab-127">Windows Form 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="e3bab-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="e3bab-128">使用 XAML 範例裝載在 WPF 中的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e3bab-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
