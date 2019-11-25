---
title: 逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 3b4b743b07876f240366b2d2d19667405941a40b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976543"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="410df-102">逐步解說：使用 XAML 在 WPF 中裝載 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="410df-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="410df-103">提供具有豐富功能集的許多控制項。</span><span class="sxs-lookup"><span data-stu-id="410df-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="410df-104">不過，您有時可能會想要在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。</span><span class="sxs-lookup"><span data-stu-id="410df-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="410df-105">例如，您可能會大量投資現有的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，或者您可能會有提供獨特功能的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。</span><span class="sxs-lookup"><span data-stu-id="410df-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="410df-106">本逐步解說將示範如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上裝載 Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> 控制項。</span><span class="sxs-lookup"><span data-stu-id="410df-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="410df-107">如需本逐步解說中所示工作的完整程式代碼清單，請參閱[使用 XAML 在 WPF 中裝載 Windows Forms 控制項](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml)。</span><span class="sxs-lookup"><span data-stu-id="410df-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="410df-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="410df-108">Prerequisites</span></span>  

<span data-ttu-id="410df-109">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="410df-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="410df-110">裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="410df-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="410df-111">裝載 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="410df-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="410df-112">建立名為 `HostingWfInWpfWithXaml`的 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="410df-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="410df-113">加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="410df-113">Add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="410df-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="410df-114">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="410df-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="410df-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="410df-116">在 WPF 設計工具中開啟 Mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="410df-116">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
4. <span data-ttu-id="410df-117">在 <xref:System.Windows.Window> 元素中，新增下列命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="410df-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="410df-118">`wf` 命名空間對應會建立包含 Windows Forms 控制項之元件的參考。</span><span class="sxs-lookup"><span data-stu-id="410df-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="410df-119">在 <xref:System.Windows.Controls.Grid> 元素中，新增下列 XAML。</span><span class="sxs-lookup"><span data-stu-id="410df-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="410df-120"><xref:System.Windows.Forms.MaskedTextBox> 控制項會建立為 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的子系。</span><span class="sxs-lookup"><span data-stu-id="410df-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="410df-121">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="410df-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410df-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="410df-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="410df-123">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="410df-123">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="410df-124">逐步解說：在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="410df-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="410df-125">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="410df-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="410df-126">逐步解說：在 Windows Form 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="410df-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="410df-127">Windows Forms 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="410df-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="410df-128">使用 XAML 在 WPF 中裝載 Windows Forms 控制項範例</span><span class="sxs-lookup"><span data-stu-id="410df-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
