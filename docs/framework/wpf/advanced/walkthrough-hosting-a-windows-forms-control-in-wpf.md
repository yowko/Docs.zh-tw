---
title: 在 WPF 中裝載 Windows Forms 控制項
description: 瞭解如何在 Windows Presentation Foundation 中裝載 Windows Forms 控制項，其已提供許多具有豐富功能集的控制項。
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164979"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="85353-103">逐步解說：將 Windows Forms 控制項裝載在 WPF 中</span><span class="sxs-lookup"><span data-stu-id="85353-103">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="85353-104">提供具有豐富功能集的許多控制項。</span><span class="sxs-lookup"><span data-stu-id="85353-104">provides many controls with a rich feature set.</span></span> <span data-ttu-id="85353-105">不過，您有時可能會想要在頁面上使用 Windows Forms 控制項 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="85353-105">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="85353-106">例如，您可能會大量投資現有的 Windows Forms 控制項，或者您可能會有提供獨特功能的 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="85353-106">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="85353-107">本逐步解說將示範如何 <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> 使用程式碼，在頁面上裝載 Windows Forms 控制項 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="85353-107">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="85353-108">如需本逐步解說中所示工作的完整程式代碼清單，請參閱[在 WPF 中裝載 Windows Forms 控制項範例](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)。</span><span class="sxs-lookup"><span data-stu-id="85353-108">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="85353-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="85353-109">Prerequisites</span></span>

<span data-ttu-id="85353-110">若要完成這個逐步解說，您必須具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="85353-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="85353-111">裝載 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="85353-111">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="85353-112">裝載 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="85353-112">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="85353-113">建立名為的 WPF 應用程式專案 `HostingWfInWpf` 。</span><span class="sxs-lookup"><span data-stu-id="85353-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="85353-114">加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="85353-114">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="85353-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="85353-115">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="85353-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="85353-116">System.Windows.Forms</span></span>

3. <span data-ttu-id="85353-117">在 WPF 設計工具中開啟 Mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="85353-117">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="85353-118">將元素命名為 <xref:System.Windows.Controls.Grid> `grid1` 。</span><span class="sxs-lookup"><span data-stu-id="85353-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="85353-119">在設計檢視或 XAML 視圖中，選取 <xref:System.Windows.Window> 元素。</span><span class="sxs-lookup"><span data-stu-id="85353-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="85353-120">在 [屬性視窗中，按一下 [**事件**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="85353-120">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="85353-121">按兩下 <xref:System.Windows.FrameworkElement.Loaded> 事件。</span><span class="sxs-lookup"><span data-stu-id="85353-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="85353-122">插入下列程式碼來處理 <xref:System.Windows.FrameworkElement.Loaded> 事件。</span><span class="sxs-lookup"><span data-stu-id="85353-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="85353-123">在檔案的頂端，新增下列 `Imports` 或 `using` 語句。</span><span class="sxs-lookup"><span data-stu-id="85353-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="85353-124">按 **F5** 以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="85353-124">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="85353-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85353-125">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="85353-126">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="85353-126">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="85353-127">逐步解說：使用 XAML 將 Windows Forms 控制項裝載在 WPF 中</span><span class="sxs-lookup"><span data-stu-id="85353-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="85353-128">逐步解說：將 Windows Forms 複合控制項裝載在 WPF 中</span><span class="sxs-lookup"><span data-stu-id="85353-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="85353-129">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="85353-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="85353-130">Windows Form 控制項和對等 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="85353-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- <span data-ttu-id="85353-131">[Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF) (在 WPF 中裝載 Windows Forms 控制項的範例)</span><span class="sxs-lookup"><span data-stu-id="85353-131">[Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)</span></span>
