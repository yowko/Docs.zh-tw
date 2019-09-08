---
title: 教學課程：在 Visual Studio 2019 中建立您的第一個 WPF 應用程式-.NET Framework
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: vs-dotnet
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8b7f6f3bdbf3adc7c355e88cfe1f569cc0cb76f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799338"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="afdd0-102">教學課程：在 Visual Studio 2019 中建立您的第一個 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="afdd0-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="afdd0-103">本文說明如何開發 Windows Presentation Foundation （WPF）桌面應用程式，其中包含大部分 WPF 應用程式通用的元素：Extensible Application Markup Language （XAML）標記、程式碼後置、應用程式定義、控制項、版面配置、資料系結和樣式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="afdd0-104">若要開發應用程式，您將使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="afdd0-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="afdd0-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="afdd0-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="afdd0-106">建立 WPF 專案。</span><span class="sxs-lookup"><span data-stu-id="afdd0-106">Create a WPF project.</span></span>
> - <span data-ttu-id="afdd0-107">使用 XAML 來設計應用程式的使用者介面（UI）的外觀。</span><span class="sxs-lookup"><span data-stu-id="afdd0-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="afdd0-108">撰寫程式碼來建立應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="afdd0-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="afdd0-109">建立應用程式定義來管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="afdd0-110">新增控制項，並建立配置來撰寫應用程式 UI。</span><span class="sxs-lookup"><span data-stu-id="afdd0-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="afdd0-111">建立應用程式 UI 中一致外觀的樣式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="afdd0-112">將 UI 系結至資料，以從資料填入 UI，以及保持資料和 UI 同步。</span><span class="sxs-lookup"><span data-stu-id="afdd0-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="afdd0-113">在本教學課程結束時，您將會建立獨立的 Windows 應用程式，讓使用者可以查看所選人員的費用報表。</span><span class="sxs-lookup"><span data-stu-id="afdd0-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="afdd0-114">應用程式是由數個以瀏覽器樣式視窗主控的 WPF 頁面所組成。</span><span class="sxs-lookup"><span data-stu-id="afdd0-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="afdd0-115">本教學課程中使用的範例程式碼適用于 Visual Basic 和C# [教學課程 WPF 應用程式範例程式碼](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="afdd0-116">您可以使用此頁面頂端的 [語言選取器C# ]，切換和 Visual Basic 之間的範例程式碼語言。</span><span class="sxs-lookup"><span data-stu-id="afdd0-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="afdd0-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="afdd0-117">Prerequisites</span></span>

- <span data-ttu-id="afdd0-118">已安裝 **.net 桌面開發**工作負載的[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 。</span><span class="sxs-lookup"><span data-stu-id="afdd0-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="afdd0-119">如需安裝最新版本 Visual Studio 的詳細資訊，請參閱[Install Visual Studio](/visualstudio/install/install-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="afdd0-120">建立應用程式專案</span><span class="sxs-lookup"><span data-stu-id="afdd0-120">Create the application project</span></span>

<span data-ttu-id="afdd0-121">第一個步驟是建立應用程式基礎結構，其中包含應用程式定義、兩頁和影像。</span><span class="sxs-lookup"><span data-stu-id="afdd0-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="afdd0-122">在 Visual Basic 或 Visual C# 中名為建立新的 WPF 應用程式專案 **`ExpenseIt`** :</span><span class="sxs-lookup"><span data-stu-id="afdd0-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="afdd0-123">開啟 Visual Studio，然後選取 [**開始**使用] 功能表底下的 [**建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="afdd0-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="afdd0-124">[**建立新專案**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="afdd0-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="afdd0-125">在 **語言** 下拉式清單中**C#** ，選取或**Visual Basic**。</span><span class="sxs-lookup"><span data-stu-id="afdd0-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="afdd0-126">選取 [ **WPF 應用程式（.NET Framework）** ] 範本，然後選取 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="afdd0-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![[建立新專案] 對話方塊](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="afdd0-128">[**設定您的新專案**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="afdd0-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="afdd0-129">輸入專案名稱 **`ExpenseIt`** ，然後選取**建立**。</span><span class="sxs-lookup"><span data-stu-id="afdd0-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![[設定新專案] 對話方塊](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="afdd0-131">Visual Studio 會建立專案，並開啟名為**mainwindow.xaml**之預設應用程式視窗的設計工具。</span><span class="sxs-lookup"><span data-stu-id="afdd0-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="afdd0-132">開啟*應用程式 .xaml* （Visual Basic）或*app.xaml* （C#）。</span><span class="sxs-lookup"><span data-stu-id="afdd0-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="afdd0-133">此 XAML 檔案會定義 WPF 應用程式和任何應用程式資源。</span><span class="sxs-lookup"><span data-stu-id="afdd0-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="afdd0-134">您也可以使用這個檔案來指定在應用程式啟動時自動顯示的 UI （在此案例中為*mainwindow.xaml*）。</span><span class="sxs-lookup"><span data-stu-id="afdd0-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="afdd0-135">在 Visual Basic 中，您的 XAML 看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="afdd0-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="afdd0-136">和如下所示C#：</span><span class="sxs-lookup"><span data-stu-id="afdd0-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="afdd0-137">開啟*mainwindow.xaml*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="afdd0-138">此 XAML 檔案是應用程式的主視窗，會顯示在頁面中建立的內容。</span><span class="sxs-lookup"><span data-stu-id="afdd0-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="afdd0-139"><xref:System.Windows.Window>類別會定義視窗的屬性，例如其標題、大小或圖示，以及處理事件（例如關閉或隱藏）。</span><span class="sxs-lookup"><span data-stu-id="afdd0-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="afdd0-140">將元素變更<xref:System.Windows.Navigation.NavigationWindow>為，如下列 XAML 所示： <xref:System.Windows.Window></span><span class="sxs-lookup"><span data-stu-id="afdd0-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="afdd0-141">此應用程式會根據使用者輸入，流覽至不同的內容。</span><span class="sxs-lookup"><span data-stu-id="afdd0-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="afdd0-142">這就是為什麼主要<xref:System.Windows.Window>需要變更為的<xref:System.Windows.Navigation.NavigationWindow>原因。</span><span class="sxs-lookup"><span data-stu-id="afdd0-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="afdd0-143"><xref:System.Windows.Navigation.NavigationWindow>繼承的所有屬性<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="afdd0-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="afdd0-144">XAML <xref:System.Windows.Navigation.NavigationWindow>檔案中的元素會建立<xref:System.Windows.Navigation.NavigationWindow>類別的實例。</span><span class="sxs-lookup"><span data-stu-id="afdd0-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="afdd0-145">如需詳細資訊，請參閱[導覽總覽](../app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="afdd0-146">移除<xref:System.Windows.Controls.Grid> 標記<xref:System.Windows.Navigation.NavigationWindow>之間的元素。</span><span class="sxs-lookup"><span data-stu-id="afdd0-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="afdd0-147">在專案的 XAML 程式<xref:System.Windows.Navigation.NavigationWindow>代碼中變更下列屬性：</span><span class="sxs-lookup"><span data-stu-id="afdd0-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="afdd0-148">將屬性設定為 "`ExpenseIt`"。 <xref:System.Windows.Window.Title%2A></span><span class="sxs-lookup"><span data-stu-id="afdd0-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="afdd0-149"><xref:System.Windows.FrameworkElement.Height%2A>將屬性設定為350圖元。</span><span class="sxs-lookup"><span data-stu-id="afdd0-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="afdd0-150"><xref:System.Windows.FrameworkElement.Width%2A>將屬性設定為500圖元。</span><span class="sxs-lookup"><span data-stu-id="afdd0-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="afdd0-151">Visual Basic 的 XAML 看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="afdd0-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="afdd0-152">和如下所示C#：</span><span class="sxs-lookup"><span data-stu-id="afdd0-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="afdd0-153">開啟*mainwindow.xaml*或*MainWindow.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="afdd0-154">這個檔案是程式碼後置檔案，其中包含處理*mainwindow.xaml*中所宣告之事件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="afdd0-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="afdd0-155">這個檔案包含 XAML 中定義之視窗的部分類別。</span><span class="sxs-lookup"><span data-stu-id="afdd0-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="afdd0-156">如果您使用C#的`MainWindow`是，請將類別變更為<xref:System.Windows.Navigation.NavigationWindow>衍生自。</span><span class="sxs-lookup"><span data-stu-id="afdd0-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="afdd0-157">（在 Visual Basic 中，這會在您以 XAML 變更視窗時自動發生）。您C#的程式碼現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="afdd0-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="afdd0-158">將檔案新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="afdd0-158">Add files to the application</span></span>

<span data-ttu-id="afdd0-159">在本節中，您要在應用程式中加入兩頁網頁和一個影像。</span><span class="sxs-lookup"><span data-stu-id="afdd0-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="afdd0-160">將新頁面加入至專案，並將它命名 *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="afdd0-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="afdd0-161">在 [**方案總管] 中**，以滑鼠右鍵按一下 **`ExpenseIt`** 專案節點，然後選擇**新增** > **頁面**。</span><span class="sxs-lookup"><span data-stu-id="afdd0-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="afdd0-162">在 [**加入新專案**] 對話方塊中，已選取 [**頁面（WPF）** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="afdd0-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="afdd0-163">輸入名稱 **`ExpenseItHome`** ，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="afdd0-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="afdd0-164">此頁面是應用程式啟動時所顯示的第一個頁面。</span><span class="sxs-lookup"><span data-stu-id="afdd0-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="afdd0-165">它會顯示要從中選取的人員清單，以顯示的費用報表。</span><span class="sxs-lookup"><span data-stu-id="afdd0-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="afdd0-166">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="afdd0-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="afdd0-167">將設定`ExpenseIt - Home`為 ""。 <xref:System.Windows.Controls.Page.Title%2A></span><span class="sxs-lookup"><span data-stu-id="afdd0-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="afdd0-168">`DesignWidth`將設定`DesignHeight`為350圖元，並將設為500圖元。</span><span class="sxs-lookup"><span data-stu-id="afdd0-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="afdd0-169">XAML 現在會以下列方式顯示 Visual Basic：</span><span class="sxs-lookup"><span data-stu-id="afdd0-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="afdd0-170">和如下所示C#：</span><span class="sxs-lookup"><span data-stu-id="afdd0-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="afdd0-171">開啟*mainwindow.xaml*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="afdd0-172">將屬性加入<xref:System.Windows.Navigation.NavigationWindow>至專案，並將其設定為`ExpenseItHome.xaml`""。 <xref:System.Windows.Navigation.NavigationWindow.Source%2A></span><span class="sxs-lookup"><span data-stu-id="afdd0-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="afdd0-173">這會設定 *`ExpenseItHome.xaml`* 是第一頁開啟 應用程式啟動時。</span><span class="sxs-lookup"><span data-stu-id="afdd0-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="afdd0-174">Visual Basic 中的 XAML 範例：</span><span class="sxs-lookup"><span data-stu-id="afdd0-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="afdd0-175">在 C#:</span><span class="sxs-lookup"><span data-stu-id="afdd0-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="afdd0-176">您也可以在 [**屬性**] 視窗的 [**其他**] 分類中設定 [**來源**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="afdd0-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![屬性視窗中的來源屬性](./media/properties-source.png)

1. <span data-ttu-id="afdd0-178">將另一個新的 WPF 頁面加入至專案，並將它命名為*expensereportpage.xaml。 xaml*：：</span><span class="sxs-lookup"><span data-stu-id="afdd0-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="afdd0-179">在 [**方案總管] 中**，以滑鼠右鍵按一下 **`ExpenseIt`** 專案節點，然後選擇**新增** > **頁面**。</span><span class="sxs-lookup"><span data-stu-id="afdd0-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="afdd0-180">在 [**加入新專案**] 對話方塊中，選取 [**頁面（WPF）** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="afdd0-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="afdd0-181">輸入名稱**expensereportpage.xaml**，然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="afdd0-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="afdd0-182">此頁面會顯示在所選取之人員的費用報表 **`ExpenseItHome`** 頁面。</span><span class="sxs-lookup"><span data-stu-id="afdd0-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="afdd0-183">開啟 *ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="afdd0-184">將設定`ExpenseIt - View Expense`為 ""。 <xref:System.Windows.Controls.Page.Title%2A></span><span class="sxs-lookup"><span data-stu-id="afdd0-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="afdd0-185">`DesignWidth`將設定`DesignHeight`為350圖元，並將設為500圖元。</span><span class="sxs-lookup"><span data-stu-id="afdd0-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span> 

    <span data-ttu-id="afdd0-186">*Expensereportpage.xaml*現在在 Visual Basic 中看起來會像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="afdd0-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="afdd0-187">和如下所示C#：</span><span class="sxs-lookup"><span data-stu-id="afdd0-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="afdd0-188">開啟*expenseithome.xaml.vb*和*expensereportpage.xaml*，或*ExpenseItHome.xaml.cs*和*ExpenseReportPage.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="afdd0-189">當您建立新的分頁檔時，Visual Studio 會自動建立其程式*代碼後*置檔案。</span><span class="sxs-lookup"><span data-stu-id="afdd0-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="afdd0-190">這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。</span><span class="sxs-lookup"><span data-stu-id="afdd0-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="afdd0-191">您的程式碼應該看起來如下所示 **`ExpenseItHome`** :</span><span class="sxs-lookup"><span data-stu-id="afdd0-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="afdd0-192">**Expensereportpage.xaml**的和如下所示：</span><span class="sxs-lookup"><span data-stu-id="afdd0-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="afdd0-193">將名為 [*浮水印 .png* ] 的影像加入至專案。</span><span class="sxs-lookup"><span data-stu-id="afdd0-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="afdd0-194">您可以建立自己的映射、從範例程式碼複製檔案，或從[microsoft/WPF 範例](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)GitHub 存放庫取得。</span><span class="sxs-lookup"><span data-stu-id="afdd0-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="afdd0-195">以滑鼠右鍵按一下專案節點，然後選取 [**加入** > **現有專案**]，或按**Shift** + **Alt** + **A**。</span><span class="sxs-lookup"><span data-stu-id="afdd0-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="afdd0-196">在 [**加入現有專案**] 對話方塊中，將檔案篩選器設為 [**所有**檔案] 或 [**影像檔**]，流覽至您要使用的影像檔案，然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="afdd0-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="afdd0-197">建立和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="afdd0-197">Build and run the application</span></span>

1. <span data-ttu-id="afdd0-198">若要建立並執行應用程式，請按**F5**或從 [**調試**程式] 功能表中選取 [**開始調試**]。</span><span class="sxs-lookup"><span data-stu-id="afdd0-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="afdd0-199">下圖顯示具有<xref:System.Windows.Navigation.NavigationWindow>下列按鈕的應用程式：</span><span class="sxs-lookup"><span data-stu-id="afdd0-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![應用程式建立並執行之後。](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="afdd0-201">關閉應用程式以返回 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="afdd0-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="afdd0-202">建立版面配置</span><span class="sxs-lookup"><span data-stu-id="afdd0-202">Create the layout</span></span>

<span data-ttu-id="afdd0-203">版面配置提供排序的方式來放置 UI 元素，並在調整 UI 大小時，管理這些元素的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="afdd0-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="afdd0-204">您通常會建立具有下列其中一個版面配置控制項的版面配置：</span><span class="sxs-lookup"><span data-stu-id="afdd0-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="afdd0-205"><xref:System.Windows.Controls.Canvas>-定義一個區域，您可以在其中使用相對於畫布區域的座標，明確地定位子專案。</span><span class="sxs-lookup"><span data-stu-id="afdd0-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="afdd0-206"><xref:System.Windows.Controls.DockPanel>-定義可讓您以水準或垂直方式排列子專案的區域（相對於彼此）。</span><span class="sxs-lookup"><span data-stu-id="afdd0-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="afdd0-207"><xref:System.Windows.Controls.Grid>-定義包含資料行和資料列的彈性方格區域。</span><span class="sxs-lookup"><span data-stu-id="afdd0-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="afdd0-208"><xref:System.Windows.Controls.StackPanel>-將子項目排列成可水準或垂直方向的單一行。</span><span class="sxs-lookup"><span data-stu-id="afdd0-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="afdd0-209"><xref:System.Windows.Controls.VirtualizingStackPanel>-在以水準或垂直方式導向的單一線條上排列和虛擬化內容。</span><span class="sxs-lookup"><span data-stu-id="afdd0-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="afdd0-210"><xref:System.Windows.Controls.WrapPanel>-從左至右將子專案放在順序位置，將內容細分為包含方塊邊緣的下一行。</span><span class="sxs-lookup"><span data-stu-id="afdd0-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="afdd0-211">後續的順序會依方向屬性的值，從上到下或由右至左進行排序。</span><span class="sxs-lookup"><span data-stu-id="afdd0-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="afdd0-212">這些版面配置控制項都支援其子項目的特定版面配置類型。</span><span class="sxs-lookup"><span data-stu-id="afdd0-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="afdd0-213">`ExpenseIt`頁面可以調整大小，而且每個頁面都有與其他元素一起水準和垂直排列的元素。</span><span class="sxs-lookup"><span data-stu-id="afdd0-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="afdd0-214">在此範例中， <xref:System.Windows.Controls.Grid>是用來做為應用程式的 layout 元素。</span><span class="sxs-lookup"><span data-stu-id="afdd0-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="afdd0-215">如需<xref:System.Windows.Controls.Panel>元素的詳細資訊，請參閱[面板總覽](../controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="afdd0-216">如需版面配置的詳細資訊，請參閱[版面](../advanced/layout.md)配置。</span><span class="sxs-lookup"><span data-stu-id="afdd0-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="afdd0-217">在本節中，您建立單欄資料表具有三個資料列和 10 個像素邊界藉由新增資料行和資料列定義，以<xref:System.Windows.Controls.Grid>中 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="afdd0-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="afdd0-218">在 *`ExpenseItHome.xaml`* 中，將<xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Grid>元素上的屬性設定為 "10，0，10，10"，其對應于左、上、右和下邊界：</span><span class="sxs-lookup"><span data-stu-id="afdd0-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="afdd0-219">您也可以在 [**屬性**] 視窗的 [**版面**配置] 分類底下設定**邊界**值：</span><span class="sxs-lookup"><span data-stu-id="afdd0-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![屬性視窗中的邊界值](./media/properties-margin.png)

2. <span data-ttu-id="afdd0-221">在<xref:System.Windows.Controls.Grid>標記之間加入下列 XAML，以建立資料列和資料行定義：</span><span class="sxs-lookup"><span data-stu-id="afdd0-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="afdd0-222">兩個數據列的會設定<xref:System.Windows.GridLength.Auto%2A>為，這表示資料列會根據資料列中的內容進行大小調整。 <xref:System.Windows.Controls.RowDefinition.Height%2A></span><span class="sxs-lookup"><span data-stu-id="afdd0-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="afdd0-223">預設值<xref:System.Windows.Controls.RowDefinition.Height%2A>為<xref:System.Windows.GridUnitType.Star> [調整大小]，表示資料列高度是可用空間的加權比例。</span><span class="sxs-lookup"><span data-stu-id="afdd0-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="afdd0-224">例如，如果兩個數據列都<xref:System.Windows.Controls.RowDefinition.Height%2A>有 "\*" 的，則它們的高度為可用空間的一半。</span><span class="sxs-lookup"><span data-stu-id="afdd0-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="afdd0-225">您<xref:System.Windows.Controls.Grid>現在應該包含下列 XAML：</span><span class="sxs-lookup"><span data-stu-id="afdd0-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="afdd0-226">加入控制項</span><span class="sxs-lookup"><span data-stu-id="afdd0-226">Add controls</span></span>

<span data-ttu-id="afdd0-227">在本節中，您將更新首頁 UI 以顯示人員清單，您可以在其中選取一個人員來顯示其費用報表。</span><span class="sxs-lookup"><span data-stu-id="afdd0-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="afdd0-228">控制項是可讓使用者與您應用程式互動的 UI 物件。</span><span class="sxs-lookup"><span data-stu-id="afdd0-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="afdd0-229">如需詳細資訊，請參閱 [控制項](../controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="afdd0-230">若要建立此 UI，您會新增下列項目，來 *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="afdd0-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="afdd0-231"><xref:System.Windows.Controls.ListBox> （適用于人員清單）。</span><span class="sxs-lookup"><span data-stu-id="afdd0-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="afdd0-232"><xref:System.Windows.Controls.Label> （適用于清單標頭）。</span><span class="sxs-lookup"><span data-stu-id="afdd0-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="afdd0-233">A <xref:System.Windows.Controls.Button> （按一下即可查看清單中所選人員的費用報表）。</span><span class="sxs-lookup"><span data-stu-id="afdd0-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="afdd0-234">藉<xref:System.Windows.Controls.Grid> 由<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>設定附加屬性，每個控制項都會放在的資料列中。</span><span class="sxs-lookup"><span data-stu-id="afdd0-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="afdd0-235">如需附加屬性的詳細資訊，請參閱[附加屬性總覽](../advanced/attached-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="afdd0-236">在 *`ExpenseItHome.xaml`* 中，于<xref:System.Windows.Controls.Grid>標記之間的位置新增下列 XAML：</span><span class="sxs-lookup"><span data-stu-id="afdd0-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="afdd0-237">您也可以將控制項從 [**工具箱**] 視窗拖曳至 [設計] 視窗，然後在 [**屬性**] 視窗中設定其屬性，以建立它們。</span><span class="sxs-lookup"><span data-stu-id="afdd0-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="afdd0-238">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-238">Build and run the application.</span></span>

    <span data-ttu-id="afdd0-239">下圖顯示您所建立的控制項：</span><span class="sxs-lookup"><span data-stu-id="afdd0-239">The following illustration shows the controls you created:</span></span>

![ExpenseIt 範例螢幕擷取畫面，顯示名稱清單](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="afdd0-241">新增影像和標題</span><span class="sxs-lookup"><span data-stu-id="afdd0-241">Add an image and a title</span></span>

<span data-ttu-id="afdd0-242">在本節中，您將使用影像和頁面標題來更新首頁 UI。</span><span class="sxs-lookup"><span data-stu-id="afdd0-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="afdd0-243">在 *`ExpenseItHome.xaml`* 中，將另一個資料<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>行加入至<xref:System.Windows.Controls.ColumnDefinition.Width%2A> ，其固定為230圖元：</span><span class="sxs-lookup"><span data-stu-id="afdd0-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="afdd0-244">將另一個資料列<xref:System.Windows.Controls.Grid.RowDefinitions%2A>新增至，總計四個數據列：</span><span class="sxs-lookup"><span data-stu-id="afdd0-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="afdd0-245">將控制項移至第二個數據行， <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>方法是在三個控制項（框線、清單方塊和按鈕）中，將屬性設定為1。</span><span class="sxs-lookup"><span data-stu-id="afdd0-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="afdd0-246">將每個控制項向下移動一個資料<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>列，方法是針對三個控制項（框線、清單方塊和按鈕）和 Border 元素的每一個值遞增1。</span><span class="sxs-lookup"><span data-stu-id="afdd0-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="afdd0-247">這三個控制項的 XAML 現在看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="afdd0-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="afdd0-248">藉由在`<Grid>`和標記`</Grid>`之間的任何位置新增下列 XAML，將 屬性設定為浮水印.png圖像<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>檔：</span><span class="sxs-lookup"><span data-stu-id="afdd0-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="afdd0-249">在專案之前， <xref:System.Windows.Controls.Label>加入具有「查看費用報表」內容的。 <xref:System.Windows.Controls.Border></span><span class="sxs-lookup"><span data-stu-id="afdd0-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="afdd0-250">此標籤是頁面的標題。</span><span class="sxs-lookup"><span data-stu-id="afdd0-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="afdd0-251">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-251">Build and run the application.</span></span>

<span data-ttu-id="afdd0-252">下圖顯示您剛新增的結果：</span><span class="sxs-lookup"><span data-stu-id="afdd0-252">The following illustration shows the results of what you just added:</span></span>

![ExpenseIt 範例螢幕擷取畫面，其中顯示新的影像背景和頁面標題](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="afdd0-254">新增程式碼來處理事件</span><span class="sxs-lookup"><span data-stu-id="afdd0-254">Add code to handle events</span></span>

1. <span data-ttu-id="afdd0-255">在 *`ExpenseItHome.xaml`* 中， <xref:System.Windows.Controls.Primitives.ButtonBase.Click>將事件處理常式新增<xref:System.Windows.Controls.Button>至元素。</span><span class="sxs-lookup"><span data-stu-id="afdd0-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="afdd0-256">如需詳細資訊，請參閱[如何：建立簡單的事件處理](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))程式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="afdd0-257">開啟 *`ExpenseItHome.xaml.vb`* 或是 *`ExpenseItHome.xaml.cs`* 。</span><span class="sxs-lookup"><span data-stu-id="afdd0-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="afdd0-258">將下列程式碼新增至`ExpenseItHome`類別，以新增按鈕 click 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="afdd0-259">事件處理常式會開啟 [ **expensereportpage.xaml** ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="afdd0-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="afdd0-260">建立 Expensereportpage.xaml 的 UI</span><span class="sxs-lookup"><span data-stu-id="afdd0-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="afdd0-261">*ExpenseReportPage.xaml*上選取的人員顯示的經費支出報表 **`ExpenseItHome`** 頁面。</span><span class="sxs-lookup"><span data-stu-id="afdd0-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="afdd0-262">在本節中，您將建立**expensereportpage.xaml**的 UI。</span><span class="sxs-lookup"><span data-stu-id="afdd0-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="afdd0-263">您也會將背景和填滿色彩新增至各種 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="afdd0-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="afdd0-264">開啟 *ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="afdd0-265">在<xref:System.Windows.Controls.Grid>標記之間加入下列 XAML：</span><span class="sxs-lookup"><span data-stu-id="afdd0-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="afdd0-266">此 UI 很類似 *`ExpenseItHome.xaml`* ，但報表資料會顯示在<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="afdd0-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="afdd0-267">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-267">Build and run the application.</span></span>

4. <span data-ttu-id="afdd0-268">選取 [ **View** ] \ （編輯 \）按鈕。</span><span class="sxs-lookup"><span data-stu-id="afdd0-268">Select the **View** button.</span></span>

    <span data-ttu-id="afdd0-269">報表頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="afdd0-269">The expense report page appears.</span></span> <span data-ttu-id="afdd0-270">另請注意，[上一頁] 瀏覽按鈕已啟用。</span><span class="sxs-lookup"><span data-stu-id="afdd0-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="afdd0-271">下圖顯示新增至*expensereportpage.xaml*的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="afdd0-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseIt 範例螢幕擷取畫面，其中顯示剛剛為 Expensereportpage.xaml 建立的 UI。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="afdd0-273">樣式控制項</span><span class="sxs-lookup"><span data-stu-id="afdd0-273">Style controls</span></span>

<span data-ttu-id="afdd0-274">針對 UI 中相同類型的所有元素，各種元素的外觀通常都相同。</span><span class="sxs-lookup"><span data-stu-id="afdd0-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="afdd0-275">UI 會使用[樣式](../controls/styling-and-templating.md)，讓多個元素的外觀可重複使用。</span><span class="sxs-lookup"><span data-stu-id="afdd0-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="afdd0-276">樣式的重複利用有助於簡化 XAML 的建立和管理。</span><span class="sxs-lookup"><span data-stu-id="afdd0-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="afdd0-277">本節會將先前步驟中定義的個別元素屬性 (Attribute) 取代為樣式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="afdd0-278">開啟 app.xaml 或*App.xaml* *應用程式*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="afdd0-279">在<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>標記之間加入下列 XAML：</span><span class="sxs-lookup"><span data-stu-id="afdd0-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="afdd0-280">這個 XAML 會加入下列樣式：</span><span class="sxs-lookup"><span data-stu-id="afdd0-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="afdd0-281">`headerTextStyle`：設定頁面標題<xref:System.Windows.Controls.Label>的格式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="afdd0-282">`labelStyle`：設定控制項的<xref:System.Windows.Controls.Label>格式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="afdd0-283">`columnHeaderStyle`：以格式化<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。</span><span class="sxs-lookup"><span data-stu-id="afdd0-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="afdd0-284">`listHeaderStyle`：格式化清單標頭<xref:System.Windows.Controls.Border>控制項。</span><span class="sxs-lookup"><span data-stu-id="afdd0-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="afdd0-285">`listHeaderTextStyle`：以格式化清單標頭<xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="afdd0-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="afdd0-286">`buttonStyle`：要格式化的<xref:System.Windows.Controls.Button>。 `ExpenseItHome.xaml`</span><span class="sxs-lookup"><span data-stu-id="afdd0-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="afdd0-287">請注意，樣式是<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>屬性元素的資源和子系。</span><span class="sxs-lookup"><span data-stu-id="afdd0-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="afdd0-288">在這裡，樣式會套用至應用程式中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="afdd0-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="afdd0-289">如需在 .NET 應用程式中使用資源的範例，請參閱[使用應用程式資源](../advanced/how-to-use-application-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="afdd0-290">在 *`ExpenseItHome.xaml`* 中，以下列 XAML <xref:System.Windows.Controls.Grid>取代元素之間的所有內容：</span><span class="sxs-lookup"><span data-stu-id="afdd0-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="afdd0-291">套用樣式會移除並取代諸如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 這類會定義每個控制項外觀的屬性。</span><span class="sxs-lookup"><span data-stu-id="afdd0-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="afdd0-292">例如， `headerTextStyle`會套用至「查看費用<xref:System.Windows.Controls.Label>報表」。</span><span class="sxs-lookup"><span data-stu-id="afdd0-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="afdd0-293">開啟 *ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="afdd0-294">以下列 XAML 取代<xref:System.Windows.Controls.Grid>元素之間的所有內容：</span><span class="sxs-lookup"><span data-stu-id="afdd0-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="afdd0-295">這個 XAML 會將樣式加入<xref:System.Windows.Controls.Label>至<xref:System.Windows.Controls.Border>和元素。</span><span class="sxs-lookup"><span data-stu-id="afdd0-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="afdd0-296">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-296">Build and run the application.</span></span> <span data-ttu-id="afdd0-297">視窗外觀與先前相同。</span><span class="sxs-lookup"><span data-stu-id="afdd0-297">The window appearance is the same as previously.</span></span>

    ![使用與上一節相同的外觀，ExpenseIt 範例螢幕擷取畫面。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="afdd0-299">關閉應用程式以返回 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="afdd0-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="afdd0-300">將資料系結至控制項</span><span class="sxs-lookup"><span data-stu-id="afdd0-300">Bind data to a control</span></span>

<span data-ttu-id="afdd0-301">在本節中，您將建立系結至各種控制項的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="afdd0-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="afdd0-302">中 *`ExpenseItHome.xaml`* ，在開啟之後<xref:System.Windows.Controls.Grid>項目，加入下列 XAML 來建立<xref:System.Windows.Data.XmlDataProvider>包含的每個人資料：</span><span class="sxs-lookup"><span data-stu-id="afdd0-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="afdd0-303">資料會建立為<xref:System.Windows.Controls.Grid>資源。</span><span class="sxs-lookup"><span data-stu-id="afdd0-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="afdd0-304">一般來說，這項資料會載入為檔案，但為了簡單起見，會以內嵌方式加入資料。</span><span class="sxs-lookup"><span data-stu-id="afdd0-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="afdd0-305">在專案中，加入下列`<xref:System.Windows.DataTemplate>`專案，此專案會定義如何`<XmlDataProvider>`在的專案之後<xref:System.Windows.Controls.ListBox>顯示中的資料： `<Grid.Resources>`</span><span class="sxs-lookup"><span data-stu-id="afdd0-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="afdd0-306">如需資料範本的詳細資訊，請參閱[資料範本化總覽](../data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="afdd0-307">以下列 XAML <xref:System.Windows.Controls.ListBox>取代現有的：</span><span class="sxs-lookup"><span data-stu-id="afdd0-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="afdd0-308">這個 XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>會將的屬性<xref:System.Windows.Controls.ListBox>系結至資料來源，並套用資料範本做為<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。</span><span class="sxs-lookup"><span data-stu-id="afdd0-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="afdd0-309">將資料連線至控制項</span><span class="sxs-lookup"><span data-stu-id="afdd0-309">Connect data to controls</span></span>

<span data-ttu-id="afdd0-310">接下來，您要在其中加入程式碼，以擷取名稱上選取 **`ExpenseItHome`** 頁面上，並將它傳遞給建構函式**ExpenseReportPage**。</span><span class="sxs-lookup"><span data-stu-id="afdd0-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="afdd0-311">**Expensereportpage.xaml**會使用傳遞的專案來設定其資料內容，這就是*expensereportpage.xaml*中定義的控制項。</span><span class="sxs-lookup"><span data-stu-id="afdd0-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="afdd0-312">開啟 *ExpenseReportPage.xaml.vb* 或 *ExpenseReportPage.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="afdd0-313">加入一個可接受物件的建構函式，如此您就可以傳遞選取之人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="afdd0-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="afdd0-314">開啟 *`ExpenseItHome.xaml.vb`* 或是 *`ExpenseItHome.xaml.cs`* 。</span><span class="sxs-lookup"><span data-stu-id="afdd0-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="afdd0-315"><xref:System.Windows.Controls.Primitives.ButtonBase.Click>變更事件處理常式，以呼叫新的函式，以傳遞所選人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="afdd0-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="afdd0-316">使用資料範本的樣式資料</span><span class="sxs-lookup"><span data-stu-id="afdd0-316">Style data with data templates</span></span>

<span data-ttu-id="afdd0-317">在本節中，您將使用資料範本來更新資料系結清單中每個專案的 UI。</span><span class="sxs-lookup"><span data-stu-id="afdd0-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="afdd0-318">開啟 *ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="afdd0-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="afdd0-319">將「名稱」和「部門<xref:System.Windows.Controls.Label> 」元素的內容系結至適當的資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="afdd0-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="afdd0-320">如需資料系結的詳細資訊，請參閱資料系結[總覽](../data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd0-320">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="afdd0-321">在開啟<xref:System.Windows.Controls.Grid>的專案之後，新增下列資料範本，以定義如何顯示費用報表資料：</span><span class="sxs-lookup"><span data-stu-id="afdd0-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="afdd0-322">以元素底下的<xref:System.Windows.Controls.DataGridTemplateColumn> 元素取代，並將範本套用至這些專案。<xref:System.Windows.Controls.DataGridTextColumn> <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="afdd0-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="afdd0-323">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="afdd0-323">Build and run the application.</span></span>

6. <span data-ttu-id="afdd0-324">選取人員，然後選取 [ **View** ] \ （編輯 \）按鈕。</span><span class="sxs-lookup"><span data-stu-id="afdd0-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="afdd0-325">下圖顯示`ExpenseIt`應用程式的兩個頁面，其中已套用控制項、配置、樣式、資料系結和資料範本：</span><span class="sxs-lookup"><span data-stu-id="afdd0-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![應用程式的兩個頁面會顯示 [名稱] 清單和費用報表。](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="afdd0-327">這個範例會示範 WPF 的特定功能，並不會遵循安全性、當地語系化和協助工具等專案的所有最佳作法。</span><span class="sxs-lookup"><span data-stu-id="afdd0-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="afdd0-328">如需 WPF 和 .NET 應用程式開發最佳作法的完整涵蓋範圍，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="afdd0-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="afdd0-329">協助工具選項</span><span class="sxs-lookup"><span data-stu-id="afdd0-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="afdd0-330">Security</span><span class="sxs-lookup"><span data-stu-id="afdd0-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="afdd0-331">WPF 全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="afdd0-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="afdd0-332">WPF 效能</span><span class="sxs-lookup"><span data-stu-id="afdd0-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="afdd0-333">後續步驟</span><span class="sxs-lookup"><span data-stu-id="afdd0-333">Next steps</span></span>

<span data-ttu-id="afdd0-334">在本逐步解說中，您已瞭解使用 Windows Presentation Foundation （WPF）來建立 UI 的數種技術。</span><span class="sxs-lookup"><span data-stu-id="afdd0-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="afdd0-335">您現在應該對資料系結 .NET 應用程式的建立區塊有基本瞭解。</span><span class="sxs-lookup"><span data-stu-id="afdd0-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="afdd0-336">如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="afdd0-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="afdd0-337">WPF 架構</span><span class="sxs-lookup"><span data-stu-id="afdd0-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="afdd0-338">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="afdd0-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="afdd0-339">相依性屬性總覽</span><span class="sxs-lookup"><span data-stu-id="afdd0-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="afdd0-340">版面配置</span><span class="sxs-lookup"><span data-stu-id="afdd0-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="afdd0-341">如需建立應用程式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="afdd0-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="afdd0-342">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="afdd0-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="afdd0-343">控制項</span><span class="sxs-lookup"><span data-stu-id="afdd0-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="afdd0-344">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="afdd0-344">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="afdd0-345">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="afdd0-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="afdd0-346">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="afdd0-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="afdd0-347">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afdd0-347">See also</span></span>

- [<span data-ttu-id="afdd0-348">面板總覽</span><span class="sxs-lookup"><span data-stu-id="afdd0-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="afdd0-349">資料範本化總覽</span><span class="sxs-lookup"><span data-stu-id="afdd0-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="afdd0-350">建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="afdd0-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="afdd0-351">樣式和範本</span><span class="sxs-lookup"><span data-stu-id="afdd0-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
