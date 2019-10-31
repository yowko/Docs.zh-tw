---
title: 逐步解說：在 WPF 中裝載 Windows Form 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 3cd01126e22927151f3c7fb08726c006c710dd34
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197919"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="65487-102">逐步解說：在 WPF 中裝載 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="65487-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="65487-103">提供具有豐富功能集的許多控制項。</span><span class="sxs-lookup"><span data-stu-id="65487-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="65487-104">不過，您有時可能會想要在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。</span><span class="sxs-lookup"><span data-stu-id="65487-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="65487-105">例如，您可能會大量投資現有的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項，或者您可能會有提供獨特功能的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。</span><span class="sxs-lookup"><span data-stu-id="65487-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>

<span data-ttu-id="65487-106">本逐步解說將示範如何使用程式碼，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面上裝載 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> 控制項。</span><span class="sxs-lookup"><span data-stu-id="65487-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="65487-107">如需本逐步解說中所示工作的完整程式代碼清單，請參閱[在 WPF 中裝載 Windows Forms 控制項範例](https://go.microsoft.com/fwlink/?LinkID=160057)。</span><span class="sxs-lookup"><span data-stu-id="65487-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=160057).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65487-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="65487-108">Prerequisites</span></span>

<span data-ttu-id="65487-109">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="65487-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="65487-110">裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="65487-110">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="65487-111">裝載 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="65487-111">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="65487-112">建立名為 `HostingWfInWpf`的 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="65487-112">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="65487-113">加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="65487-113">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="65487-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="65487-114">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="65487-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="65487-115">System.Windows.Forms</span></span>

3. <span data-ttu-id="65487-116">在 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]中開啟 Mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="65487-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

4. <span data-ttu-id="65487-117">將 <xref:System.Windows.Controls.Grid> 元素命名為 `grid1`。</span><span class="sxs-lookup"><span data-stu-id="65487-117">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="65487-118">在設計檢視或 XAML 視圖中，選取 [<xref:System.Windows.Window>] 元素。</span><span class="sxs-lookup"><span data-stu-id="65487-118">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="65487-119">在 屬性視窗中，按一下 **事件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="65487-119">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="65487-120">按兩下 [<xref:System.Windows.FrameworkElement.Loaded>] 事件。</span><span class="sxs-lookup"><span data-stu-id="65487-120">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="65487-121">插入下列程式碼以處理 <xref:System.Windows.FrameworkElement.Loaded> 事件。</span><span class="sxs-lookup"><span data-stu-id="65487-121">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="65487-122">在檔案的頂端，新增下列 `Imports` 或 `using` 語句。</span><span class="sxs-lookup"><span data-stu-id="65487-122">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="65487-123">按 **F5** 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="65487-123">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="65487-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="65487-124">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="65487-125">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="65487-125">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="65487-126">逐步解說：使用 XAML 在 WPF 中裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="65487-126">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="65487-127">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="65487-127">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="65487-128">逐步解說：在 Windows Form 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="65487-128">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="65487-129">Windows Forms 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="65487-129">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- <span data-ttu-id="65487-130">[Hosting a Windows Forms Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=160057) (在 WPF 中裝載 Windows Forms 控制項的範例)</span><span class="sxs-lookup"><span data-stu-id="65487-130">[Hosting a Windows Forms Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=160057)</span></span>
