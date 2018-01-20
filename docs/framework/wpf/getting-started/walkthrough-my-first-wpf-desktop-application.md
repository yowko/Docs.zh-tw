---
title: "逐步解說： 第一個 WPF 桌面應用程式"
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
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16ed99181f8462e805638b5d3881464b16f21177
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="6c221-102">逐步解說： 第一個 WPF 桌面應用程式</span><span class="sxs-lookup"><span data-stu-id="6c221-102">Walkthrough: My first WPF desktop application</span></span>
<span data-ttu-id="6c221-103">本逐步解說提供的應用程式開發簡介[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]包含項目通用於大多數的應用程式[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式：[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]標記、 程式碼後置、 應用程式定義、 控制項、 版面配置，資料繫結和樣式。</span><span class="sxs-lookup"><span data-stu-id="6c221-103">This walkthrough provides an introduction to the development of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application that includes the elements that are common to most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> 
  
 <span data-ttu-id="6c221-104">本逐步解說會引導您完成簡單的開發[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式使用下列步驟。</span><span class="sxs-lookup"><span data-stu-id="6c221-104">This walkthrough guides you through the development of a simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application using the following steps.</span></span> 
  
-   <span data-ttu-id="6c221-105">定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設計的應用程式的外觀[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c221-105">Defining [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to design the appearance of the application's [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="6c221-106">撰寫程式碼以建置應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="6c221-106">Writing code to build the application's behavior.</span></span> 
  
-   <span data-ttu-id="6c221-107">建立應用程式定義以管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c221-107">Creating an application definition to manage the application.</span></span> 
  
-   <span data-ttu-id="6c221-108">加入控制項，並建立來撰寫應用程式配置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c221-108">Adding controls and creating the layout to compose the application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="6c221-109">建立樣式來建立應用程式的外觀的一致性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c221-109">Creating styles to create a consistent appearance throughout an application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="6c221-110">繫結[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]兩者的資料填入[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]資料和保留資料及[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]同步處理。</span><span class="sxs-lookup"><span data-stu-id="6c221-110">Binding the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to data to both populate the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] from data and keep the data and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronized.</span></span> 
  
 <span data-ttu-id="6c221-111">本逐步解說結束時，您會建立獨立[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]應用程式，讓使用者選取的人員檢視經費支出報表。</span><span class="sxs-lookup"><span data-stu-id="6c221-111">By the end of the walkthrough, you will have built a standalone [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="6c221-112">應用程式將由數個[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]裝載在瀏覽器樣式視窗中的頁面。</span><span class="sxs-lookup"><span data-stu-id="6c221-112">The application will be composed of several [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages that are hosted in a browser-style window.</span></span> 
  
 <span data-ttu-id="6c221-113">用來建立這個逐步解說的範例程式碼都可用[!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]和[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]在[建置 WPF 應用程式簡介](http://go.microsoft.com/fwlink/?LinkID=160008)。</span><span class="sxs-lookup"><span data-stu-id="6c221-113">The sample code that is used to build this walkthrough is available for both [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] and [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] at  [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="6c221-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="6c221-114">Prerequisites</span></span>  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="6c221-115"> (含) 以後版本</span><span class="sxs-lookup"><span data-stu-id="6c221-115"> or later</span></span>

<span data-ttu-id="6c221-116">如需安裝最新版本的 Visual Studio 的詳細資訊，請參閱[安裝 Visual Studio](/visualstudio/install/install-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="6c221-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>
  
## <a name="creating-the-application-project"></a><span data-ttu-id="6c221-117">建立應用程式專案</span><span class="sxs-lookup"><span data-stu-id="6c221-117">Creating the application project</span></span>  
 <span data-ttu-id="6c221-118">在本節中，您會建立應用程式基礎結構，包括一個應用程式定義、兩個頁面和一個影像。</span><span class="sxs-lookup"><span data-stu-id="6c221-118">In this section, you create the application infrastructure, which includes an application definition, two pages, and an image.</span></span> 
  
1. <span data-ttu-id="6c221-119">在 Visual Basic 或 Visual C# 中，建立名為 `ExpenseIt` 的新 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="6c221-119">Create a new WPF Application project in Visual Basic or Visual C# named `ExpenseIt`.</span></span> <span data-ttu-id="6c221-120">如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。</span><span class="sxs-lookup"><span data-stu-id="6c221-120">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="6c221-121">本逐步解說使用<xref:System.Windows.Controls.DataGrid>使用.NET Framework 4 中的控制項。</span><span class="sxs-lookup"><span data-stu-id="6c221-121">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4.</span></span> <span data-ttu-id="6c221-122">為確定您的專案目標.NET Framework 4 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="6c221-122">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="6c221-123">如需詳細資訊，請參閱[How to： 以.NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。</span><span class="sxs-lookup"><span data-stu-id="6c221-123">For more information, see[How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
2. <span data-ttu-id="6c221-124">開啟 Application.xaml (Visual Basic) 或 App.xaml (C#)。</span><span class="sxs-lookup"><span data-stu-id="6c221-124">Open Application.xaml (Visual Basic) or App.xaml (C#).</span></span> 
  
     <span data-ttu-id="6c221-125">這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案會定義[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式和應用程式的任何資源。</span><span class="sxs-lookup"><span data-stu-id="6c221-125">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file defines a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application and any application resources.</span></span> <span data-ttu-id="6c221-126">您也使用此檔案來指定[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]也會自動顯示在應用程式啟動; 在此情況下，將 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-126">You also use this file to specify the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that automatically shows when the application starts; in this case, MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="6c221-127">您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6c221-127">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     <span data-ttu-id="6c221-128">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="6c221-128">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. <span data-ttu-id="6c221-129">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-129">Open MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="6c221-130">這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案是您的應用程式的主視窗，並顯示在頁面中建立的內容。</span><span class="sxs-lookup"><span data-stu-id="6c221-130">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="6c221-131"><xref:System.Windows.Window>類別定義的視窗中，其標題、 大小或圖示，例如屬性和處理事件，例如關閉或隱藏。</span><span class="sxs-lookup"><span data-stu-id="6c221-131">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span> 
  
4. <span data-ttu-id="6c221-132">變更<xref:System.Windows.Window>元素<xref:System.Windows.Navigation.NavigationWindow>。</span><span class="sxs-lookup"><span data-stu-id="6c221-132">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="6c221-133">這個應用程式會根據使用者的互動巡覽至不同的內容。</span><span class="sxs-lookup"><span data-stu-id="6c221-133">This application will navigate to different content depending on the user interaction.</span></span> <span data-ttu-id="6c221-134">因此，主要<xref:System.Windows.Window>需要變更以<xref:System.Windows.Navigation.NavigationWindow>。</span><span class="sxs-lookup"><span data-stu-id="6c221-134">Therefore, the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="6c221-135"><xref:System.Windows.Navigation.NavigationWindow>繼承的所有屬性<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="6c221-135"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="6c221-136"><xref:System.Windows.Navigation.NavigationWindow> XAML 檔案中的項目建立的執行個體<xref:System.Windows.Navigation.NavigationWindow>類別。</span><span class="sxs-lookup"><span data-stu-id="6c221-136">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="6c221-137">如需詳細資訊，請參閱[覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-137">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span> 
  
5. <span data-ttu-id="6c221-138">變更下列屬性上<xref:System.Windows.Navigation.NavigationWindow>項目：</span><span class="sxs-lookup"><span data-stu-id="6c221-138">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>  
  
    -   <span data-ttu-id="6c221-139">設定<xref:System.Windows.Window.Title%2A>"ExpenseIt"的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c221-139">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span> 
  
    -   <span data-ttu-id="6c221-140">設定<xref:System.Windows.FrameworkElement.Width%2A>500 像素為單位的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c221-140">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span> 
  
    -   <span data-ttu-id="6c221-141">設定<xref:System.Windows.FrameworkElement.Height%2A>350 像素為單位的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c221-141">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span> 
  
    -   <span data-ttu-id="6c221-142">移除<xref:System.Windows.Controls.Grid>之間的項目<xref:System.Windows.Navigation.NavigationWindow>標記。</span><span class="sxs-lookup"><span data-stu-id="6c221-142">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span> 
  
     <span data-ttu-id="6c221-143">您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6c221-143">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     <span data-ttu-id="6c221-144">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="6c221-144">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. <span data-ttu-id="6c221-145">開啟 MainWindow.xaml.vb 或 MainWindow.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="6c221-145">Open MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span> 
  
     <span data-ttu-id="6c221-146">這個檔案是程式碼後置檔案，其中包含的程式碼可處理 MainWindow.xaml 中所宣告的事件。</span><span class="sxs-lookup"><span data-stu-id="6c221-146">This file is a code-behind file that contains code to handle the events declared in MainWindow.xaml.</span></span> <span data-ttu-id="6c221-147">這個檔案包含 XAML 中定義之視窗的部分類別。</span><span class="sxs-lookup"><span data-stu-id="6c221-147">This file contains a partial class for the window defined in XAML.</span></span> 
  
7. <span data-ttu-id="6c221-148">如果您使用的 C#，變更`MainWindow`類別衍生自<xref:System.Windows.Navigation.NavigationWindow>。</span><span class="sxs-lookup"><span data-stu-id="6c221-148">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="6c221-149">在 Visual Basic 中，當您在 XAML 中變更視窗時會自動發生。</span><span class="sxs-lookup"><span data-stu-id="6c221-149">In Visual Basic, this happens automatically when you change the window in XAML.</span></span> 
  
     <span data-ttu-id="6c221-150">您的程式碼應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="6c221-150">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a><span data-ttu-id="6c221-151">將檔案加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="6c221-151">Adding files to the application</span></span>  
 <span data-ttu-id="6c221-152">在本節中，您要加入兩個頁面及一個影像到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="6c221-152">In this section, you add two pages and an image to the application.</span></span> 
  
1. <span data-ttu-id="6c221-153">將新的頁面 (WPF) 加入至名為專案`ExpenseItHome.xaml`。</span><span class="sxs-lookup"><span data-stu-id="6c221-153">Add a new Page (WPF) to the project named `ExpenseItHome.xaml`.</span></span> <span data-ttu-id="6c221-154">如需詳細資訊，請參閱[如何： 加入新項目加入至 WPF 專案](http://msdn.microsoft.com/library/17e6b238-fc32-4385-98ef-2f66ca09d9ad)。</span><span class="sxs-lookup"><span data-stu-id="6c221-154">For more information, see [How to: Add New Items to a WPF Project](http://msdn.microsoft.com/library/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span></span> 
  
     <span data-ttu-id="6c221-155">這個頁面是應用程式啟動時顯示的第一個頁面。</span><span class="sxs-lookup"><span data-stu-id="6c221-155">This page is the first page that is displayed when the application is launched.</span></span> <span data-ttu-id="6c221-156">它會顯示一份人員清單，使用者可從中選取一名人員查看其費用報表。</span><span class="sxs-lookup"><span data-stu-id="6c221-156">It will show a list of people from which a user can select a person to show an expense report for.</span></span> 
  
2. <span data-ttu-id="6c221-157">開啟 ExpenseItHome.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-157">Open ExpenseItHome.xaml.</span></span> 
  
3. <span data-ttu-id="6c221-158">設定<xref:System.Windows.Controls.Page.Title%2A>至 「 ExpenseIt-首頁 」。</span><span class="sxs-lookup"><span data-stu-id="6c221-158">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span> 
  
     <span data-ttu-id="6c221-159">您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6c221-159">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     <span data-ttu-id="6c221-160">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="6c221-160">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. <span data-ttu-id="6c221-161">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-161">Open MainWindow.xaml.</span></span> 
  
5. <span data-ttu-id="6c221-162">設定<xref:System.Windows.Navigation.NavigationWindow.Source%2A>屬性<xref:System.Windows.Navigation.NavigationWindow>至 「 ExpenseItHome.xaml"。</span><span class="sxs-lookup"><span data-stu-id="6c221-162">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span> 
  
     <span data-ttu-id="6c221-163">這會將 ExpenseItHome.xaml 設成應用程式啟動時開啟的第一個頁面。</span><span class="sxs-lookup"><span data-stu-id="6c221-163">This sets ExpenseItHome.xaml to be the first page opened when the application starts.</span></span> <span data-ttu-id="6c221-164">您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6c221-164">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     <span data-ttu-id="6c221-165">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="6c221-165">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. <span data-ttu-id="6c221-166">將新的頁面 (WPF) 加入至名為專案`ExpenseReportPage.xaml`。</span><span class="sxs-lookup"><span data-stu-id="6c221-166">Add a new Page (WPF) to the project named `ExpenseReportPage.xaml`.</span></span> 
  
     <span data-ttu-id="6c221-167">這個頁面會顯示 ExpenseItHome.xaml 中所選取之人員的費用報表。</span><span class="sxs-lookup"><span data-stu-id="6c221-167">This page will show the expense report for the person that is selected on ExpenseItHome.xaml.</span></span> 
  
7. <span data-ttu-id="6c221-168">開啟 ExpenseReportPage.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-168">Open ExpenseReportPage.xaml.</span></span> 
  
8. <span data-ttu-id="6c221-169">設定<xref:System.Windows.Controls.Page.Title%2A>至 「 ExpenseIt-檢視費用報表 」。</span><span class="sxs-lookup"><span data-stu-id="6c221-169">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span> 
  
     <span data-ttu-id="6c221-170">您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應該在 Visual Basic 中看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="6c221-170">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     <span data-ttu-id="6c221-171">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="6c221-171">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. <span data-ttu-id="6c221-172">開啟 ExpenseItHome.xaml.vb 和 ExpenseReportPage.xaml.vb，或是 ExpenseItHome.xaml.cs 和 ExpenseReportPage.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="6c221-172">Open ExpenseItHome.xaml.vb and ExpenseReportPage.xaml.vb, or ExpenseItHome.xaml.cs and ExpenseReportPage.xaml.cs.</span></span> 
  
     <span data-ttu-id="6c221-173">當您建立新的頁面檔案時，Visual Studio 會自動建立程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="6c221-173">When you create a new Page file, Visual Studio automatically creates a code behind file.</span></span> <span data-ttu-id="6c221-174">這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。</span><span class="sxs-lookup"><span data-stu-id="6c221-174">These code-behind files handle the logic for responding to user input.</span></span> 
  
     <span data-ttu-id="6c221-175">您的程式碼應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="6c221-175">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. <span data-ttu-id="6c221-176">將名為 watermark.png 的影像加入至專案。</span><span class="sxs-lookup"><span data-stu-id="6c221-176">Add an image named watermark.png to the project.</span></span> <span data-ttu-id="6c221-177">您可以建立自己的影像，或是從範例程式碼複製檔案。</span><span class="sxs-lookup"><span data-stu-id="6c221-177">You can either create your own image, or copy the file from the sample code.</span></span> <span data-ttu-id="6c221-178">如需詳細資訊，請參閱[NIB： 如何： 加入現有項目加入至專案](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)。</span><span class="sxs-lookup"><span data-stu-id="6c221-178">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span> 

## <a name="building-and-running-the-application"></a><span data-ttu-id="6c221-179">建置和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="6c221-179">Building and running the application</span></span>  
 <span data-ttu-id="6c221-180">在本節中，您會建置和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c221-180">In this section, you build and run the application.</span></span> 
  
1. <span data-ttu-id="6c221-181">建置並執行應用程式，請按 F5 或選取**開始偵錯**從**偵錯**功能表。</span><span class="sxs-lookup"><span data-stu-id="6c221-181">Build and run the application by pressing F5 or select **Start Debugging** from the **Debug** menu.</span></span> 
  
     <span data-ttu-id="6c221-182">下圖顯示應用程式與<xref:System.Windows.Navigation.NavigationWindow>按鈕。</span><span class="sxs-lookup"><span data-stu-id="6c221-182">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons.</span></span> 
  
     <span data-ttu-id="6c221-183">![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span><span class="sxs-lookup"><span data-stu-id="6c221-183">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span></span>  
  
2. <span data-ttu-id="6c221-184">關閉應用程式以返回[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c221-184">Close the application to return to [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> 
  
## <a name="creating-the-layout"></a><span data-ttu-id="6c221-185">建立版面配置</span><span class="sxs-lookup"><span data-stu-id="6c221-185">Creating the layout</span></span>  
 <span data-ttu-id="6c221-186">版面配置會按照的順序放置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目，以及管理的大小和位置的項目時[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]重新調整大小。</span><span class="sxs-lookup"><span data-stu-id="6c221-186">Layout provides an ordered way to place [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements, and also manages the size and position of those elements when a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is resized.</span></span> <span data-ttu-id="6c221-187">您通常會建立具有下列其中一個版面配置控制項的版面配置：</span><span class="sxs-lookup"><span data-stu-id="6c221-187">You typically create a layout with one of the following layout controls:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="6c221-188">這些版面配置控制項都支援其子元素的特殊版面配置類型。</span><span class="sxs-lookup"><span data-stu-id="6c221-188">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="6c221-189">ExpenseIt 頁面可以調整大小，而且每個頁面都有元素會沿著其他元素水平和垂直排列。</span><span class="sxs-lookup"><span data-stu-id="6c221-189">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="6c221-190">因此，<xref:System.Windows.Controls.Grid>為應用程式的理想的版面配置項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-190">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="6c221-191">如需有關<xref:System.Windows.Controls.Panel>項目，請參閱[面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-191">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="6c221-192">如需有關配置的詳細資訊，請參閱[配置](../../../../docs/framework/wpf/advanced/layout.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-192">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span> 
  
 <span data-ttu-id="6c221-193">在區段中，您建立單一資料行的資料表具有三個資料列和 10 個像素邊界藉由新增資料行和資料列定義，以<xref:System.Windows.Controls.Grid>ExpenseItHome.xaml 中。</span><span class="sxs-lookup"><span data-stu-id="6c221-193">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in ExpenseItHome.xaml.</span></span> 
  
1. <span data-ttu-id="6c221-194">開啟 ExpenseItHome.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-194">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6c221-195">設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性<xref:System.Windows.Controls.Grid>"10,0,10,10 」 對應到左框線、 頂端、 右側和底部邊界的項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-195">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10" which corresponds to left, top, right and bottom margins.</span></span> 
  
3. <span data-ttu-id="6c221-196">加入下列[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]之間<xref:System.Windows.Controls.Grid>標籤來建立資料列和資料行定義。</span><span class="sxs-lookup"><span data-stu-id="6c221-196">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions.</span></span> 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <span data-ttu-id="6c221-197"><xref:System.Windows.Controls.RowDefinition.Height%2A>兩個資料列設<xref:System.Windows.GridLength.Auto%2A>表示將調整大小之資料列的基礎資料列中的內容。</span><span class="sxs-lookup"><span data-stu-id="6c221-197">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A> which means that the rows will be sized base on the content in the rows.</span></span> <span data-ttu-id="6c221-198">預設值<xref:System.Windows.Controls.RowDefinition.Height%2A>是<xref:System.Windows.GridUnitType.Star>調整大小，這表示的資料列會在可用空間的加權的比例。</span><span class="sxs-lookup"><span data-stu-id="6c221-198">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row will be a weighted proportion of the available space.</span></span> <span data-ttu-id="6c221-199">例如，如果有兩列的高度都是 "\*"，則每列的高度會各佔可用空間的一半。</span><span class="sxs-lookup"><span data-stu-id="6c221-199">For example if two rows each have a height of "\*", they will each have a height that is half of the available space.</span></span>  
  
     <span data-ttu-id="6c221-200">您<xref:System.Windows.Controls.Grid>現在應該看起來像下列 XAML:</span><span class="sxs-lookup"><span data-stu-id="6c221-200">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a><span data-ttu-id="6c221-201">加入控制項</span><span class="sxs-lookup"><span data-stu-id="6c221-201">Adding controls</span></span>  
 <span data-ttu-id="6c221-202">在此區段中，在首頁上[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]會更新以顯示使用者可以選取從，以顯示所選人員的經費支出報表的人員清單。</span><span class="sxs-lookup"><span data-stu-id="6c221-202">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated to show a list of people that users can select from to show the expense report for a selected person.</span></span> <span data-ttu-id="6c221-203">控制項是可讓使用者與您應用程式互動的 UI 物件。</span><span class="sxs-lookup"><span data-stu-id="6c221-203">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="6c221-204">如需詳細資訊，請參閱 [控制項](../../../../docs/framework/wpf/controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-204">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span> 
  
 <span data-ttu-id="6c221-205">若要建立這個[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，下列項目會加入 ExpenseItHome.xaml:</span><span class="sxs-lookup"><span data-stu-id="6c221-205">To create this [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], the following elements are added to ExpenseItHome.xaml:</span></span>  
  
-   <span data-ttu-id="6c221-206"><xref:System.Windows.Controls.ListBox>（適用於的人員清單）。</span><span class="sxs-lookup"><span data-stu-id="6c221-206"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span> 
  
-   <span data-ttu-id="6c221-207"><xref:System.Windows.Controls.Label>（適用於清單標頭）。</span><span class="sxs-lookup"><span data-stu-id="6c221-207"><xref:System.Windows.Controls.Label> (for the list header).</span></span> 
  
-   <span data-ttu-id="6c221-208"><xref:System.Windows.Controls.Button>（可以按一下清單中選取的人員檢視經費支出報表）。</span><span class="sxs-lookup"><span data-stu-id="6c221-208"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span> 
  
 <span data-ttu-id="6c221-209">中的資料列位於每個控制項<xref:System.Windows.Controls.Grid>藉由設定<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>附加屬性。</span><span class="sxs-lookup"><span data-stu-id="6c221-209">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="6c221-210">如需附加屬性的詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-210">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span> 
  
1. <span data-ttu-id="6c221-211">開啟 ExpenseItHome.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-211">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6c221-212">加入下列[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]之間<xref:System.Windows.Controls.Grid>標記。</span><span class="sxs-lookup"><span data-stu-id="6c221-212">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. <span data-ttu-id="6c221-213">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c221-213">Build and run the application.</span></span> 
  
 <span data-ttu-id="6c221-214">下圖顯示本節中的 XAML 所建立的控制項。</span><span class="sxs-lookup"><span data-stu-id="6c221-214">The following illustration shows the controls that are created by the XAML in this section.</span></span> 
  
 <span data-ttu-id="6c221-215">![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span><span class="sxs-lookup"><span data-stu-id="6c221-215">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span></span>  
  
## <a name="adding-an-image-and-a-title"></a><span data-ttu-id="6c221-216">加入的映像和標題</span><span class="sxs-lookup"><span data-stu-id="6c221-216">Adding an image and a title</span></span>  
 <span data-ttu-id="6c221-217">在此區段中，在首頁上[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]會更新為映像和頁面標題。</span><span class="sxs-lookup"><span data-stu-id="6c221-217">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated with an image and a page title.</span></span> 
  
1. <span data-ttu-id="6c221-218">開啟 ExpenseItHome.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-218">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6c221-219">加入另一個資料行，<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>固定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>的 230 個像素。</span><span class="sxs-lookup"><span data-stu-id="6c221-219">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels.</span></span> 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. <span data-ttu-id="6c221-220">加入至另一個資料列<xref:System.Windows.Controls.Grid.RowDefinitions%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c221-220">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span></span> 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. <span data-ttu-id="6c221-221">將控制項移到第二個資料行中，藉由設定<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>設為 1。</span><span class="sxs-lookup"><span data-stu-id="6c221-221">Move the controls to the second column by setting <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> to 1.</span></span> <span data-ttu-id="6c221-222">下移一列中中的每個控制項，藉由增加<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>1。</span><span class="sxs-lookup"><span data-stu-id="6c221-222">Move each control down a row, by increasing the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> by 1.</span></span> 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. <span data-ttu-id="6c221-223">設定<xref:System.Windows.Controls.Panel.Background%2A>的<xref:System.Windows.Controls.Grid>watermark.png 映像檔。</span><span class="sxs-lookup"><span data-stu-id="6c221-223">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the watermark.png image file.</span></span> 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. <span data-ttu-id="6c221-224">之前<xref:System.Windows.Controls.Border>，新增<xref:System.Windows.Controls.Label>以內容為頁面的標題的 [檢視費用報表]。</span><span class="sxs-lookup"><span data-stu-id="6c221-224">Before the <xref:System.Windows.Controls.Border>, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report" to be the title of the page.</span></span> 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. <span data-ttu-id="6c221-225">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c221-225">Build and run the application.</span></span> 
  
 <span data-ttu-id="6c221-226">下圖顯示本節的結果。</span><span class="sxs-lookup"><span data-stu-id="6c221-226">The following illustration shows the results of this section.</span></span> 
  
 <span data-ttu-id="6c221-227">![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span><span class="sxs-lookup"><span data-stu-id="6c221-227">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span></span>  
  
## <a name="adding-code-to-handle-events"></a><span data-ttu-id="6c221-228">加入程式碼，來處理事件</span><span class="sxs-lookup"><span data-stu-id="6c221-228">Adding code to handle events</span></span>  
  
1. <span data-ttu-id="6c221-229">開啟 ExpenseItHome.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-229">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6c221-230">新增<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式來<xref:System.Windows.Controls.Button>項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-230">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="6c221-231">如需詳細資訊，請參閱[How to： 建立簡單的事件處理常式](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480)。</span><span class="sxs-lookup"><span data-stu-id="6c221-231">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span> 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. <span data-ttu-id="6c221-232">開啟 ExpenseItHome.xaml.vb 或 ExpenseItHome.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="6c221-232">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="6c221-233">將下列程式碼加入<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式，會造成視窗巡覽至 ExpenseReportPage.xaml 檔案。</span><span class="sxs-lookup"><span data-stu-id="6c221-233">Add the following code to the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler, which causes the window to navigate to the ExpenseReportPage.xaml file.</span></span> 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a><span data-ttu-id="6c221-234">建立 ExpenseReportPage 的 UI</span><span class="sxs-lookup"><span data-stu-id="6c221-234">Creating the UI for ExpenseReportPage</span></span>  
 <span data-ttu-id="6c221-235">ExpenseReportPage.xaml 會顯示在 ExpenseItHome.xaml 上選取之人員的費用報表。</span><span class="sxs-lookup"><span data-stu-id="6c221-235">ExpenseReportPage.xaml displays the expense report for the person that was selected on the ExpenseItHome.xaml.</span></span> <span data-ttu-id="6c221-236">這一節加入的控制項，並建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ExpenseReportPage.xaml 的。</span><span class="sxs-lookup"><span data-stu-id="6c221-236">This section adds controls and creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for ExpenseReportPage.xaml.</span></span> <span data-ttu-id="6c221-237">本章節也會將背景色彩和填滿色彩加入至各種[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-237">This section also adds background and fill colors to the various [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> 
  
1. <span data-ttu-id="6c221-238">開啟 ExpenseReportPage.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-238">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="6c221-239">在 <xref:System.Windows.Controls.Grid> 標記之間加入下列 XAML。</span><span class="sxs-lookup"><span data-stu-id="6c221-239">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
     <span data-ttu-id="6c221-240">此 UI 很類似，除了報表資料會顯示在 ExpenseItHome.xaml 上建立的 ui <xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="6c221-240">This UI is similar to the UI created on ExpenseItHome.xaml except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span> 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. <span data-ttu-id="6c221-241">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c221-241">Build and run the application.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="6c221-242">如果您收到錯誤，<xref:System.Windows.Controls.DataGrid>找不到或不存在，請確定您的專案以.NET Framework 4 或更新版本為目標。</span><span class="sxs-lookup"><span data-stu-id="6c221-242">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="6c221-243">如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。</span><span class="sxs-lookup"><span data-stu-id="6c221-243">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
4. <span data-ttu-id="6c221-244">按一下**檢視** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6c221-244">Click the **View** button.</span></span> 
  
     <span data-ttu-id="6c221-245">報表頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="6c221-245">The expense report page appears.</span></span> 
  
 <span data-ttu-id="6c221-246">下圖顯示[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ExpenseReportPage.xaml 所加入的項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-246">The following illustration shows the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements added to ExpenseReportPage.xaml.</span></span> <span data-ttu-id="6c221-247">請注意，已啟用向後巡覽按鈕。</span><span class="sxs-lookup"><span data-stu-id="6c221-247">Notice that the back navigation button is enabled.</span></span> 
  
 <span data-ttu-id="6c221-248">![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span><span class="sxs-lookup"><span data-stu-id="6c221-248">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span></span>  
  
## <a name="styling-controls"></a><span data-ttu-id="6c221-249">設定控制項的樣式</span><span class="sxs-lookup"><span data-stu-id="6c221-249">Styling controls</span></span>  
 <span data-ttu-id="6c221-250">各種項目的外觀通常可以在相同型別的所有項目的相同[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c221-250">The appearance of various elements can often be the same for all elements of the same type in a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]<span data-ttu-id="6c221-251"> 可使用樣式，使多個元素可重複使用外觀。</span><span class="sxs-lookup"><span data-stu-id="6c221-251"> uses styles to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="6c221-252">重複使用性的樣式有助於簡化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]建立和管理。</span><span class="sxs-lookup"><span data-stu-id="6c221-252">The reusability of styles helps to simplify [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] creation and management.</span></span> <span data-ttu-id="6c221-253">如需有關樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-253">For more information about styles, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span> <span data-ttu-id="6c221-254">本節會將先前步驟中定義的個別元素屬性 (Attribute) 取代為樣式。</span><span class="sxs-lookup"><span data-stu-id="6c221-254">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span> 
  
1. <span data-ttu-id="6c221-255">開啟 Application.xaml 或 App.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-255">Open Application.xaml or App.xaml.</span></span> 
  
2. <span data-ttu-id="6c221-256">加入下列 XAML 之間<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>標記：</span><span class="sxs-lookup"><span data-stu-id="6c221-256">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     <span data-ttu-id="6c221-257">這[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]會加入下列樣式：</span><span class="sxs-lookup"><span data-stu-id="6c221-257">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adds the following styles:</span></span>  
  
    -  <span data-ttu-id="6c221-258">`headerTextStyle`：格式化頁面標題 <xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="6c221-258">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="6c221-259">`labelStyle`：格式化 <xref:System.Windows.Controls.Label> 控制項。</span><span class="sxs-lookup"><span data-stu-id="6c221-259">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span> 
  
    -  <span data-ttu-id="6c221-260">`columnHeaderStyle`：格式化 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。</span><span class="sxs-lookup"><span data-stu-id="6c221-260">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span> 
  
    -  <span data-ttu-id="6c221-261">`listHeaderStyle`：格式化清單標頭 <xref:System.Windows.Controls.Border> 控制項。</span><span class="sxs-lookup"><span data-stu-id="6c221-261">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span> 
  
    -  <span data-ttu-id="6c221-262">`listHeaderTextStyle`： 若要格式化清單標頭<xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="6c221-262">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="6c221-263">`buttonStyle`： 若要格式化<xref:System.Windows.Controls.Button>ExpenseItHome.xaml 上。</span><span class="sxs-lookup"><span data-stu-id="6c221-263">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span> 
  
     <span data-ttu-id="6c221-264">請注意，樣式資源和子系<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>屬性項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-264">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="6c221-265">在這裡，樣式會套用至應用程式中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="6c221-265">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="6c221-266">如需範例的使用中的資源[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]應用程式，請參閱[使用應用程式資源](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-266">For an example of using resources in a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span> 
  
3. <span data-ttu-id="6c221-267">開啟 ExpenseItHome.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-267">Open ExpenseItHome.xaml.</span></span> 
  
4. <span data-ttu-id="6c221-268">取代之間的所有內容<xref:System.Windows.Controls.Grid>以下列 XAML 項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-268">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     <span data-ttu-id="6c221-269">套用樣式會移除並取代諸如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 這類會定義每個控制項外觀的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c221-269">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="6c221-270">例如，`headerTextStyle`套用至 [檢視費用報表] <xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="6c221-270">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span> 
  
5. <span data-ttu-id="6c221-271">開啟 ExpenseReportPage.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-271">Open ExpenseReportPage.xaml.</span></span> 
  
6. <span data-ttu-id="6c221-272">取代之間的所有內容<xref:System.Windows.Controls.Grid>以下列 XAML 項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-272">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     <span data-ttu-id="6c221-273">這樣會將樣式加入 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Border> 項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-273">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span> 
  
7. <span data-ttu-id="6c221-274">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c221-274">Build and run the application.</span></span> 
  
     <span data-ttu-id="6c221-275">在新增之後[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]本節中，應用程式看起來都一樣使用樣式正在更新之前一樣。</span><span class="sxs-lookup"><span data-stu-id="6c221-275">After adding the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] in this section, the application looks the same as it did before being updated with styles.</span></span> 
  
## <a name="binding-data-to-a-control"></a><span data-ttu-id="6c221-276">資料繫結至控制項</span><span class="sxs-lookup"><span data-stu-id="6c221-276">Binding data to a control</span></span>  
 <span data-ttu-id="6c221-277">在本節中，您會建立[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]資料繫結至不同的控制項。</span><span class="sxs-lookup"><span data-stu-id="6c221-277">In this section, you create the [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data that is bound to various controls.</span></span> 
  
1. <span data-ttu-id="6c221-278">開啟 ExpenseItHome.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-278">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6c221-279">在開啟之後<xref:System.Windows.Controls.Grid>項目，加入下列 XAML 建立<xref:System.Windows.Data.XmlDataProvider>其中包含每個人員的資料。</span><span class="sxs-lookup"><span data-stu-id="6c221-279">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person.</span></span> 
  
     <span data-ttu-id="6c221-280">資料會建立為<xref:System.Windows.Controls.Grid>資源。</span><span class="sxs-lookup"><span data-stu-id="6c221-280">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="6c221-281">這通常會載入為檔案，但為求簡化會內嵌資料。</span><span class="sxs-lookup"><span data-stu-id="6c221-281">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. <span data-ttu-id="6c221-282">在<xref:System.Windows.Controls.Grid>資源，加入下列<xref:System.Windows.DataTemplate>，而後者可定義如何顯示資料的<xref:System.Windows.Controls.ListBox>。</span><span class="sxs-lookup"><span data-stu-id="6c221-282">In the <xref:System.Windows.Controls.Grid> resource, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="6c221-283">如需資料範本的詳細資訊，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-283">For more information about data templates, see [Data Templating Overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. <span data-ttu-id="6c221-284">取代現有<xref:System.Windows.Controls.ListBox>以下列 XAML。</span><span class="sxs-lookup"><span data-stu-id="6c221-284">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     <span data-ttu-id="6c221-285">這個 XAML 會繫結<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>屬性<xref:System.Windows.Controls.ListBox>到資料來源，並套用資料範本做為<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c221-285">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span> 
  
## <a name="connecting-data-to-controls"></a><span data-ttu-id="6c221-286">資料連接至控制項</span><span class="sxs-lookup"><span data-stu-id="6c221-286">Connecting data to controls</span></span>  
 <span data-ttu-id="6c221-287">在本節中，您撰寫可擷取目前的項目已選取 [ExpenseItHome.xaml] 頁面上的使用者清單中，並傳遞其參考的建構函式的程式碼`ExpenseReportPage`具現化。</span><span class="sxs-lookup"><span data-stu-id="6c221-287">In this section, you write the code that retrieves the current item that is selected in the list of people on the ExpenseItHome.xaml page, and passes its reference to the constructor of `ExpenseReportPage` during instantiation.</span></span> <span data-ttu-id="6c221-288">`ExpenseReportPage` 會以傳遞的項目設定其資料內容，而這就是 ExpenseReportPage.xaml 中定義的控制項將繫結的項目。</span><span class="sxs-lookup"><span data-stu-id="6c221-288">`ExpenseReportPage` sets its data context with the passed item, which is what the controls defined in ExpenseReportPage.xaml will bind to.</span></span> 
  
1. <span data-ttu-id="6c221-289">開啟 ExpenseReportPage.xaml.vb 或 ExpenseReportPage.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="6c221-289">Open ExpenseReportPage.xaml.vb or ExpenseReportPage.xaml.cs.</span></span> 
  
2. <span data-ttu-id="6c221-290">加入一個可接受物件的建構函式，如此您就可以傳遞選取之人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="6c221-290">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. <span data-ttu-id="6c221-291">開啟 ExpenseItHome.xaml.vb 或 ExpenseItHome.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="6c221-291">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="6c221-292">變更<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式呼叫新的建構函式傳遞所選人員的經費支出報表資料。</span><span class="sxs-lookup"><span data-stu-id="6c221-292">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a><span data-ttu-id="6c221-293">使用資料範本的樣式設定資料</span><span class="sxs-lookup"><span data-stu-id="6c221-293">Styling data with data templates</span></span>  
 <span data-ttu-id="6c221-294">在本節中，您會更新[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]對資料中的每個項目繫結使用的資料範本的清單。</span><span class="sxs-lookup"><span data-stu-id="6c221-294">In this section, you update the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for each item in the data bound lists by using data templates.</span></span> 
  
1. <span data-ttu-id="6c221-295">開啟 ExpenseReportPage.xaml。</span><span class="sxs-lookup"><span data-stu-id="6c221-295">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="6c221-296">繫結內容的 「 名稱 」 和 「 部門 」<xref:System.Windows.Controls.Label>項目以適當的資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="6c221-296">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="6c221-297">如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6c221-297">For more information about data binding, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. <span data-ttu-id="6c221-298">在開啟之後<xref:System.Windows.Controls.Grid>項目，加入下列的資料範本，其中定義經費支出報表資料顯示方式。</span><span class="sxs-lookup"><span data-stu-id="6c221-298">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data.</span></span>  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. <span data-ttu-id="6c221-299">將範本套用至<xref:System.Windows.Controls.DataGrid>資料行，顯示 費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="6c221-299">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span> 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. <span data-ttu-id="6c221-300">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c221-300">Build and run the application.</span></span> 
  
6. <span data-ttu-id="6c221-301">選取 人員，然後按一下**檢視** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6c221-301">Select a person and click the **View** button.</span></span> 
  
 <span data-ttu-id="6c221-302">下圖顯示套用了控制項、配置、樣式、資料繫結和資料範本的 ExpenseIt 應用程式的兩頁頁面。</span><span class="sxs-lookup"><span data-stu-id="6c221-302">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied.</span></span> 
  
 <span data-ttu-id="6c221-303">![ExpenseIt 範例螢幕擷取畫面](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span><span class="sxs-lookup"><span data-stu-id="6c221-303">![ExpenseIt sample screen shots](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="6c221-304">最佳作法</span><span class="sxs-lookup"><span data-stu-id="6c221-304">Best practices</span></span>  
 <span data-ttu-id="6c221-305">這個範例示範 WPF 的特定功能，因此並未遵循應用程式開發的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="6c221-305">This sample demonstrates a specific feature of WPF and, consequently, does not follow application development best practices.</span></span> <span data-ttu-id="6c221-306">完整涵蓋範圍的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]應用程式開發最佳作法，視需要參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="6c221-306">For comprehensive coverage of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and the [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application development best practices, see the following topics as appropriate:</span></span>  
  
-   <span data-ttu-id="6c221-307">協助工具： [協助工具最佳作法](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span><span class="sxs-lookup"><span data-stu-id="6c221-307">Accessibility - [Accessibility Best Practices](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span></span>  
  
-   <span data-ttu-id="6c221-308">安全性-[安全性](../../../../docs/framework/wpf/security-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="6c221-308">Security - [Security](../../../../docs/framework/wpf/security-wpf.md)</span></span>  
  
-   <span data-ttu-id="6c221-309">當地語系化： [WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="6c221-309">Localization - [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span></span>  
  
-   <span data-ttu-id="6c221-310">效能： [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span><span class="sxs-lookup"><span data-stu-id="6c221-310">Performance - [Optimizing WPF Application Performance](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span></span>  
  
## <a name="whats-next"></a><span data-ttu-id="6c221-311">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6c221-311">What's next</span></span>  
 <span data-ttu-id="6c221-312">現在您有一些技術來建立達成[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6c221-312">You now have a number of techniques at your disposal for creating a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] using [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span> <span data-ttu-id="6c221-313">您現在應該有廣泛的了解的資料繫結的基本建置組塊[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="6c221-313">You should now have a broad understanding of the basic building blocks of a data-bound [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application.</span></span> <span data-ttu-id="6c221-314">本主題並不詳盡，但希望您有一些概念，可以自行發掘本主題所述技術之外的可能性。</span><span class="sxs-lookup"><span data-stu-id="6c221-314">This topic is by no means exhaustive, but hopefully you also now have a sense of some of the possibilities you might discover on your own beyond the techniques in this topic.</span></span> 
  
 <span data-ttu-id="6c221-315">如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="6c221-315">For more information about the WPF architecture and programming models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6c221-316">WPF 架構</span><span class="sxs-lookup"><span data-stu-id="6c221-316">WPF Architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [<span data-ttu-id="6c221-317">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="6c221-317">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [<span data-ttu-id="6c221-318">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="6c221-318">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [<span data-ttu-id="6c221-319">版面配置</span><span class="sxs-lookup"><span data-stu-id="6c221-319">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
  
 <span data-ttu-id="6c221-320">如需建立應用程式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="6c221-320">For more information about creating applications, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6c221-321">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="6c221-321">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [<span data-ttu-id="6c221-322">控制項</span><span class="sxs-lookup"><span data-stu-id="6c221-322">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
  
-   [<span data-ttu-id="6c221-323">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="6c221-323">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [<span data-ttu-id="6c221-324">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="6c221-324">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [<span data-ttu-id="6c221-325">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="6c221-325">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a><span data-ttu-id="6c221-326">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c221-326">See also</span></span>  
 [<span data-ttu-id="6c221-327">面板概觀</span><span class="sxs-lookup"><span data-stu-id="6c221-327">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="6c221-328">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="6c221-328">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="6c221-329">建置 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="6c221-329">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="6c221-330">樣式和範本</span><span class="sxs-lookup"><span data-stu-id="6c221-330">Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
