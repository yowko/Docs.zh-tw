---
title: 在 Visual Studio 2019 中建立您的第一個 WPF 應用程式-.NET Framework
titleSuffix: ''
description: 開發 Windows Presentation Foundation （WPF）桌面應用程式，其中包含大部分 WPF 應用程式通用的元素。
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: c9af988bcf291325b11df4fd22827b47090c0b48
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853883"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="d3735-103">教學課程：在 Visual Studio 2019 中建立您的第一個 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="d3735-103">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="d3735-104">本文說明如何開發 Windows Presentation Foundation （WPF）桌面應用程式，其中包含大部分 WPF 應用程式通用的專案： Extensible Application Markup Language （XAML）標記、程式碼後置、應用程式定義、控制項、版面配置、資料系結和樣式。</span><span class="sxs-lookup"><span data-stu-id="d3735-104">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="d3735-105">若要開發應用程式，您將使用 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d3735-105">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="d3735-106">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="d3735-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d3735-107">建立 WPF 專案。</span><span class="sxs-lookup"><span data-stu-id="d3735-107">Create a WPF project.</span></span>
> - <span data-ttu-id="d3735-108">使用 XAML 來設計應用程式的使用者介面（UI）的外觀。</span><span class="sxs-lookup"><span data-stu-id="d3735-108">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="d3735-109">撰寫程式碼來建立應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="d3735-109">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="d3735-110">建立應用程式定義來管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3735-110">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="d3735-111">新增控制項，並建立配置來撰寫應用程式 UI。</span><span class="sxs-lookup"><span data-stu-id="d3735-111">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="d3735-112">建立應用程式 UI 中一致外觀的樣式。</span><span class="sxs-lookup"><span data-stu-id="d3735-112">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="d3735-113">將 UI 系結至資料，以從資料填入 UI，以及保持資料和 UI 同步。</span><span class="sxs-lookup"><span data-stu-id="d3735-113">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="d3735-114">在本教學課程結束時，您將會建立獨立的 Windows 應用程式，讓使用者可以查看所選人員的費用報表。</span><span class="sxs-lookup"><span data-stu-id="d3735-114">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="d3735-115">應用程式是由數個以瀏覽器樣式視窗主控的 WPF 頁面所組成。</span><span class="sxs-lookup"><span data-stu-id="d3735-115">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="d3735-116">本教學課程中使用的範例程式碼可在[教學課程 WPF 應用程式範例程式碼](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)中取得 Visual Basic 和 c #。</span><span class="sxs-lookup"><span data-stu-id="d3735-116">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="d3735-117">您可以使用此頁面頂端的 [語言選取器]，切換 c # 和 Visual Basic 之間範例程式碼的程式碼語言。</span><span class="sxs-lookup"><span data-stu-id="d3735-117">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3735-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="d3735-118">Prerequisites</span></span>

- <span data-ttu-id="d3735-119">已安裝 **.net 桌面開發**工作負載的[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 。</span><span class="sxs-lookup"><span data-stu-id="d3735-119">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="d3735-120">如需安裝最新版本 Visual Studio 的詳細資訊，請參閱[Install Visual Studio](/visualstudio/install/install-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="d3735-120">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="d3735-121">建立應用程式專案</span><span class="sxs-lookup"><span data-stu-id="d3735-121">Create the application project</span></span>

<span data-ttu-id="d3735-122">第一個步驟是建立應用程式基礎結構，其中包含應用程式定義、兩頁和影像。</span><span class="sxs-lookup"><span data-stu-id="d3735-122">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="d3735-123">在 Visual Basic 或 Visual c # 中，建立名為的新 WPF 應用程式專案 **`ExpenseIt`** ：</span><span class="sxs-lookup"><span data-stu-id="d3735-123">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="d3735-124">開啟 Visual Studio，然後選取 [**開始**使用] 功能表底下的 [**建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-124">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="d3735-125">[**建立新專案**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d3735-125">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="d3735-126">在 [**語言**] 下拉式清單中，選取 [ **c #** ] 或 [ **Visual Basic**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-126">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="d3735-127">選取 [ **WPF 應用程式（.NET Framework）** ] 範本，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d3735-127">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![[建立新專案] 對話方塊](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="d3735-129">[**設定您的新專案**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d3735-129">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="d3735-130">輸入專案名稱 **`ExpenseIt`** ，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-130">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![[設定新專案] 對話方塊](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="d3735-132">Visual Studio 會建立專案，並開啟名為**mainwindow.xaml**之預設應用程式視窗的設計工具。</span><span class="sxs-lookup"><span data-stu-id="d3735-132">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="d3735-133">開啟*應用程式 .xaml* （Visual Basic）或*app.xaml* （c #）。</span><span class="sxs-lookup"><span data-stu-id="d3735-133">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="d3735-134">此 XAML 檔案會定義 WPF 應用程式和任何應用程式資源。</span><span class="sxs-lookup"><span data-stu-id="d3735-134">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="d3735-135">您也可以使用這個檔案來指定在應用程式啟動時自動顯示的 UI （在此案例中為*mainwindow.xaml*）。</span><span class="sxs-lookup"><span data-stu-id="d3735-135">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="d3735-136">在 Visual Basic 中，您的 XAML 看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-136">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="d3735-137">和 c # 中的如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-137">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="d3735-138">開啟*mainwindow.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3735-138">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="d3735-139">此 XAML 檔案是應用程式的主視窗，會顯示在頁面中建立的內容。</span><span class="sxs-lookup"><span data-stu-id="d3735-139">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="d3735-140"><xref:System.Windows.Window>類別會定義視窗的屬性，例如其標題、大小或圖示，以及處理事件（例如關閉或隱藏）。</span><span class="sxs-lookup"><span data-stu-id="d3735-140">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="d3735-141">將 <xref:System.Windows.Window> 元素變更為 <xref:System.Windows.Navigation.NavigationWindow> ，如下列 XAML 所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-141">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="d3735-142">此應用程式會根據使用者輸入，流覽至不同的內容。</span><span class="sxs-lookup"><span data-stu-id="d3735-142">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="d3735-143">這就是為什麼主要 <xref:System.Windows.Window> 需要變更為的原因 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-143">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="d3735-144"><xref:System.Windows.Navigation.NavigationWindow>繼承的所有屬性 <xref:System.Windows.Window> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-144"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="d3735-145"><xref:System.Windows.Navigation.NavigationWindow>XAML 檔案中的元素會建立類別的實例 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-145">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="d3735-146">如需詳細資訊，請參閱[導覽總覽](../app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3735-146">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="d3735-147">移除 <xref:System.Windows.Controls.Grid> 標記之間的元素 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-147">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="d3735-148">在專案的 XAML 程式碼中變更下列屬性 <xref:System.Windows.Navigation.NavigationWindow> ：</span><span class="sxs-lookup"><span data-stu-id="d3735-148">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="d3735-149">將 <xref:System.Windows.Window.Title%2A> 屬性設定為 " `ExpenseIt` "。</span><span class="sxs-lookup"><span data-stu-id="d3735-149">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="d3735-150">將 <xref:System.Windows.FrameworkElement.Height%2A> 屬性設定為350圖元。</span><span class="sxs-lookup"><span data-stu-id="d3735-150">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="d3735-151">將 <xref:System.Windows.FrameworkElement.Width%2A> 屬性設定為500圖元。</span><span class="sxs-lookup"><span data-stu-id="d3735-151">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="d3735-152">Visual Basic 的 XAML 看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-152">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="d3735-153">C # 的和如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-153">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="d3735-154">開啟*mainwindow.xaml*或*MainWindow.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="d3735-154">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="d3735-155">這個檔案是程式碼後置檔案，其中包含處理*mainwindow.xaml*中所宣告之事件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d3735-155">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="d3735-156">這個檔案包含 XAML 中定義之視窗的部分類別。</span><span class="sxs-lookup"><span data-stu-id="d3735-156">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="d3735-157">如果您使用的是 c #，請將 `MainWindow` 類別變更為衍生自 <xref:System.Windows.Navigation.NavigationWindow> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-157">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="d3735-158">（在 Visual Basic 中，這會在您以 XAML 變更視窗時自動發生）。您的 c # 程式碼現在看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="d3735-158">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="d3735-159">將檔案新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="d3735-159">Add files to the application</span></span>

<span data-ttu-id="d3735-160">在本節中，您要在應用程式中加入兩頁網頁和一個影像。</span><span class="sxs-lookup"><span data-stu-id="d3735-160">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="d3735-161">將新頁面新增至專案，並將它命名為 *`ExpenseItHome.xaml`* ：</span><span class="sxs-lookup"><span data-stu-id="d3735-161">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="d3735-162">在**方案總管**中，以滑鼠右鍵按一下 **`ExpenseIt`** 專案節點，然後選擇 [**加入**  >  **頁面**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-162">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="d3735-163">在 [**加入新專案**] 對話方塊中，已選取 [**頁面（WPF）** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="d3735-163">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="d3735-164">輸入 [名稱] **`ExpenseItHome`** ，然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-164">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="d3735-165">此頁面是應用程式啟動時所顯示的第一個頁面。</span><span class="sxs-lookup"><span data-stu-id="d3735-165">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="d3735-166">它會顯示要從中選取的人員清單，以顯示的費用報表。</span><span class="sxs-lookup"><span data-stu-id="d3735-166">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="d3735-167">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3735-167">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="d3735-168">將設定 <xref:System.Windows.Controls.Page.Title%2A> 為 " `ExpenseIt - Home` "。</span><span class="sxs-lookup"><span data-stu-id="d3735-168">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="d3735-169">將設定 `DesignHeight` 為350圖元，並將設 `DesignWidth` 為500圖元。</span><span class="sxs-lookup"><span data-stu-id="d3735-169">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="d3735-170">XAML 現在會以下列方式顯示 Visual Basic：</span><span class="sxs-lookup"><span data-stu-id="d3735-170">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="d3735-171">C # 的和如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-171">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="d3735-172">開啟*mainwindow.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3735-172">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="d3735-173">將 <xref:System.Windows.Navigation.NavigationWindow.Source%2A> 屬性加入至專案 <xref:System.Windows.Navigation.NavigationWindow> ，並將其設定為 " `ExpenseItHome.xaml` "。</span><span class="sxs-lookup"><span data-stu-id="d3735-173">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="d3735-174">這 *`ExpenseItHome.xaml`* 會設定為在應用程式啟動時開啟的第一個頁面。</span><span class="sxs-lookup"><span data-stu-id="d3735-174">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="d3735-175">Visual Basic 中的 XAML 範例：</span><span class="sxs-lookup"><span data-stu-id="d3735-175">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="d3735-176">C # 中的和：</span><span class="sxs-lookup"><span data-stu-id="d3735-176">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="d3735-177">您也可以在 [**屬性**] 視窗的 [**其他**] 分類中設定 [**來源**] 屬性。</span><span class="sxs-lookup"><span data-stu-id="d3735-177">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![屬性視窗中的來源屬性](./media/properties-source.png)

1. <span data-ttu-id="d3735-179">將另一個新的 WPF 頁面加入至專案，並將它命名為*expensereportpage.xaml。 xaml*：：</span><span class="sxs-lookup"><span data-stu-id="d3735-179">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="d3735-180">在**方案總管**中，以滑鼠右鍵按一下 **`ExpenseIt`** 專案節點，然後選擇 [**加入**  >  **頁面**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-180">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="d3735-181">在 [**加入新專案**] 對話方塊中，選取 [**頁面（WPF）** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="d3735-181">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="d3735-182">輸入名稱**expensereportpage.xaml**，然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-182">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="d3735-183">此頁面會顯示在頁面上選取之人員的費用報表 **`ExpenseItHome`** 。</span><span class="sxs-lookup"><span data-stu-id="d3735-183">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="d3735-184">開啟*expensereportpage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3735-184">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="d3735-185">將設定 <xref:System.Windows.Controls.Page.Title%2A> 為 " `ExpenseIt - View Expense` "。</span><span class="sxs-lookup"><span data-stu-id="d3735-185">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="d3735-186">將設定 `DesignHeight` 為350圖元，並將設 `DesignWidth` 為500圖元。</span><span class="sxs-lookup"><span data-stu-id="d3735-186">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="d3735-187">*Expensereportpage.xaml*現在在 Visual Basic 中看起來會像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="d3735-187">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="d3735-188">和 c # 中的如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-188">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="d3735-189">開啟*expenseithome.xaml.vb*和*expensereportpage.xaml*，或*ExpenseItHome.xaml.cs*和*ExpenseReportPage.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="d3735-189">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="d3735-190">當您建立新的分頁檔時，Visual Studio 會自動建立其程式*代碼後*置檔案。</span><span class="sxs-lookup"><span data-stu-id="d3735-190">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="d3735-191">這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。</span><span class="sxs-lookup"><span data-stu-id="d3735-191">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="d3735-192">您的程式碼看起來應該如下所示 **`ExpenseItHome`** ：</span><span class="sxs-lookup"><span data-stu-id="d3735-192">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="d3735-193">**Expensereportpage.xaml**的和如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-193">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="d3735-194">將名為*watermark.png*的影像加入至專案。</span><span class="sxs-lookup"><span data-stu-id="d3735-194">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="d3735-195">您可以建立自己的映射、從範例程式碼複製檔案，或從[microsoft/WPF 範例](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)GitHub 存放庫取得。</span><span class="sxs-lookup"><span data-stu-id="d3735-195">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="d3735-196">以滑鼠右鍵按一下專案節點，然後選取 [**加入**  >  **現有專案**]，或按**Shift** + **Alt** + **A**。</span><span class="sxs-lookup"><span data-stu-id="d3735-196">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="d3735-197">在 [**加入現有專案**] 對話方塊中，將檔案篩選器設為 [**所有**檔案] 或 [**影像檔**]，流覽至您要使用的影像檔案，然後選取 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-197">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="d3735-198">建置並執行應用程式</span><span class="sxs-lookup"><span data-stu-id="d3735-198">Build and run the application</span></span>

1. <span data-ttu-id="d3735-199">若要建立並執行應用程式，請按**F5**或從 [**調試**程式] 功能表中選取 [**開始調試**]。</span><span class="sxs-lookup"><span data-stu-id="d3735-199">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="d3735-200">下圖顯示具有下列按鈕的應用程式 <xref:System.Windows.Navigation.NavigationWindow> ：</span><span class="sxs-lookup"><span data-stu-id="d3735-200">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![應用程式建立並執行之後。](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="d3735-202">關閉應用程式以返回 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d3735-202">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="d3735-203">建立版面配置</span><span class="sxs-lookup"><span data-stu-id="d3735-203">Create the layout</span></span>

<span data-ttu-id="d3735-204">版面配置提供排序的方式來放置 UI 元素，並在調整 UI 大小時，管理這些元素的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="d3735-204">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="d3735-205">您通常會建立具有下列其中一個版面配置控制項的版面配置：</span><span class="sxs-lookup"><span data-stu-id="d3735-205">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="d3735-206"><xref:System.Windows.Controls.Canvas>-定義一個區域，您可以在其中使用相對於畫布區域的座標，明確地定位子專案。</span><span class="sxs-lookup"><span data-stu-id="d3735-206"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="d3735-207"><xref:System.Windows.Controls.DockPanel>-定義可讓您以水準或垂直方式排列子專案的區域（相對於彼此）。</span><span class="sxs-lookup"><span data-stu-id="d3735-207"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="d3735-208"><xref:System.Windows.Controls.Grid>-定義包含資料行和資料列的彈性方格區域。</span><span class="sxs-lookup"><span data-stu-id="d3735-208"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="d3735-209"><xref:System.Windows.Controls.StackPanel>-將子項目排列成可水準或垂直方向的單一行。</span><span class="sxs-lookup"><span data-stu-id="d3735-209"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="d3735-210"><xref:System.Windows.Controls.VirtualizingStackPanel>-在以水準或垂直方式導向的單一線條上排列和虛擬化內容。</span><span class="sxs-lookup"><span data-stu-id="d3735-210"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="d3735-211"><xref:System.Windows.Controls.WrapPanel>-從左至右將子專案放在順序位置，將內容細分為包含方塊邊緣的下一行。</span><span class="sxs-lookup"><span data-stu-id="d3735-211"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="d3735-212">後續的順序會依方向屬性的值，從上到下或由右至左進行排序。</span><span class="sxs-lookup"><span data-stu-id="d3735-212">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="d3735-213">這些版面配置控制項都支援其子項目的特定版面配置類型。</span><span class="sxs-lookup"><span data-stu-id="d3735-213">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="d3735-214">`ExpenseIt`頁面可以調整大小，而且每個頁面都有與其他元素一起水準和垂直排列的元素。</span><span class="sxs-lookup"><span data-stu-id="d3735-214">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="d3735-215">在此範例中， <xref:System.Windows.Controls.Grid> 是用來做為應用程式的 layout 元素。</span><span class="sxs-lookup"><span data-stu-id="d3735-215">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="d3735-216">如需元素的詳細資訊 <xref:System.Windows.Controls.Panel> ，請參閱[面板總覽](../controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3735-216">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="d3735-217">如需版面配置的詳細資訊，請參閱[版面](../advanced/layout.md)配置。</span><span class="sxs-lookup"><span data-stu-id="d3735-217">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="d3735-218">在本節中，您會將資料行和資料列定義加入中的，以建立具有三個數據列和10個圖元邊界的單欄資料表 <xref:System.Windows.Controls.Grid> *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3735-218">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="d3735-219">在中 *`ExpenseItHome.xaml`* ，將 <xref:System.Windows.FrameworkElement.Margin%2A> 元素上的屬性設定 <xref:System.Windows.Controls.Grid> 為 "10，0，10，10"，其對應于左、上、右和下邊界：</span><span class="sxs-lookup"><span data-stu-id="d3735-219">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="d3735-220">您也可以在 [**屬性**] 視窗的 [**版面**配置] 分類底下設定**邊界**值：</span><span class="sxs-lookup"><span data-stu-id="d3735-220">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![屬性視窗中的邊界值](./media/properties-margin.png)

2. <span data-ttu-id="d3735-222">在標記之間加入下列 XAML， <xref:System.Windows.Controls.Grid> 以建立資料列和資料行定義：</span><span class="sxs-lookup"><span data-stu-id="d3735-222">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="d3735-223"><xref:System.Windows.Controls.RowDefinition.Height%2A>兩個數據列的會設定為 <xref:System.Windows.GridLength.Auto%2A> ，這表示資料列會根據資料列中的內容進行大小調整。</span><span class="sxs-lookup"><span data-stu-id="d3735-223">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="d3735-224">預設值為 [重設 <xref:System.Windows.Controls.RowDefinition.Height%2A> <xref:System.Windows.GridUnitType.Star> 大小]，表示資料列高度是可用空間的加權比例。</span><span class="sxs-lookup"><span data-stu-id="d3735-224">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="d3735-225">例如，如果兩個數據列都有 <xref:System.Windows.Controls.RowDefinition.Height%2A> "\*" 的，則它們的高度為可用空間的一半。</span><span class="sxs-lookup"><span data-stu-id="d3735-225">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="d3735-226">您 <xref:System.Windows.Controls.Grid> 現在應該包含下列 XAML：</span><span class="sxs-lookup"><span data-stu-id="d3735-226">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="d3735-227">新增控制項</span><span class="sxs-lookup"><span data-stu-id="d3735-227">Add controls</span></span>

<span data-ttu-id="d3735-228">在本節中，您將更新首頁 UI 以顯示人員清單，您可以在其中選取一個人員來顯示其費用報表。</span><span class="sxs-lookup"><span data-stu-id="d3735-228">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="d3735-229">控制項是可讓使用者與您應用程式互動的 UI 物件。</span><span class="sxs-lookup"><span data-stu-id="d3735-229">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="d3735-230">如需詳細資訊，請參閱[控制項](../controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3735-230">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="d3735-231">若要建立此 UI，請將下列專案新增至 *`ExpenseItHome.xaml`* ：</span><span class="sxs-lookup"><span data-stu-id="d3735-231">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="d3735-232"><xref:System.Windows.Controls.ListBox>（適用于人員清單）。</span><span class="sxs-lookup"><span data-stu-id="d3735-232">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="d3735-233"><xref:System.Windows.Controls.Label>（適用于清單標頭）。</span><span class="sxs-lookup"><span data-stu-id="d3735-233">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="d3735-234">A <xref:System.Windows.Controls.Button> （按一下即可查看清單中所選人員的費用報表）。</span><span class="sxs-lookup"><span data-stu-id="d3735-234">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="d3735-235">藉 <xref:System.Windows.Controls.Grid> 由設定附加屬性，每個控制項都會放在的資料列中 <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-235">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="d3735-236">如需附加屬性的詳細資訊，請參閱[附加屬性總覽](../advanced/attached-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3735-236">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="d3735-237">在中 *`ExpenseItHome.xaml`* ，于標記之間的位置新增下列 XAML <xref:System.Windows.Controls.Grid> ：</span><span class="sxs-lookup"><span data-stu-id="d3735-237">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="d3735-238">您也可以將控制項從 [**工具箱**] 視窗拖曳至 [設計] 視窗，然後在 [**屬性**] 視窗中設定其屬性，以建立它們。</span><span class="sxs-lookup"><span data-stu-id="d3735-238">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="d3735-239">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3735-239">Build and run the application.</span></span>

    <span data-ttu-id="d3735-240">下圖顯示您所建立的控制項：</span><span class="sxs-lookup"><span data-stu-id="d3735-240">The following illustration shows the controls you created:</span></span>

![ExpenseIt 範例螢幕擷取畫面，顯示名稱清單](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="d3735-242">新增影像和標題</span><span class="sxs-lookup"><span data-stu-id="d3735-242">Add an image and a title</span></span>

<span data-ttu-id="d3735-243">在本節中，您將使用影像和頁面標題來更新首頁 UI。</span><span class="sxs-lookup"><span data-stu-id="d3735-243">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="d3735-244">在中 *`ExpenseItHome.xaml`* ，將另一個資料行加入至，其 <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> 固定為 <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 圖元：</span><span class="sxs-lookup"><span data-stu-id="d3735-244">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. <span data-ttu-id="d3735-245">將另一個資料列新增至 <xref:System.Windows.Controls.Grid.RowDefinitions%2A> ，總計四個數據列：</span><span class="sxs-lookup"><span data-stu-id="d3735-245">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <span data-ttu-id="d3735-246">將控制項移至第二個數據行，方法是 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 在三個控制項（框線、清單方塊和按鈕）中，將屬性設定為1。</span><span class="sxs-lookup"><span data-stu-id="d3735-246">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="d3735-247">將每個控制項向下移動一個資料列，方法是 <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> 針對三個控制項（框線、清單方塊和按鈕）和 Border 元素的每一個值遞增1。</span><span class="sxs-lookup"><span data-stu-id="d3735-247">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="d3735-248">這三個控制項的 XAML 現在看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3735-248">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="d3735-249">藉 <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> 由在和標記之間的任何位置新增下列 XAML，將屬性設定為*watermark.png*影像檔 `<Grid>` `</Grid>` ：</span><span class="sxs-lookup"><span data-stu-id="d3735-249">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="d3735-250">在專案之前 <xref:System.Windows.Controls.Border> ，加入 <xref:System.Windows.Controls.Label> 具有「查看費用報表」內容的。</span><span class="sxs-lookup"><span data-stu-id="d3735-250">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="d3735-251">此標籤是頁面的標題。</span><span class="sxs-lookup"><span data-stu-id="d3735-251">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="d3735-252">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3735-252">Build and run the application.</span></span>

<span data-ttu-id="d3735-253">下圖顯示您剛新增的結果：</span><span class="sxs-lookup"><span data-stu-id="d3735-253">The following illustration shows the results of what you just added:</span></span>

![ExpenseIt 範例螢幕擷取畫面，其中顯示新的影像背景和頁面標題](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="d3735-255">新增程式碼來處理事件</span><span class="sxs-lookup"><span data-stu-id="d3735-255">Add code to handle events</span></span>

1. <span data-ttu-id="d3735-256">在中 *`ExpenseItHome.xaml`* ，將 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式新增至 <xref:System.Windows.Controls.Button> 元素。</span><span class="sxs-lookup"><span data-stu-id="d3735-256">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="d3735-257">如需詳細資訊，請參閱[如何：建立簡單的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d3735-257">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="d3735-258">開啟 *`ExpenseItHome.xaml.vb`* 或 *`ExpenseItHome.xaml.cs`* 。</span><span class="sxs-lookup"><span data-stu-id="d3735-258">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="d3735-259">將下列程式碼新增至 `ExpenseItHome` 類別，以新增按鈕 click 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d3735-259">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="d3735-260">事件處理常式會開啟 [ **expensereportpage.xaml** ] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d3735-260">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="d3735-261">建立 Expensereportpage.xaml 的 UI</span><span class="sxs-lookup"><span data-stu-id="d3735-261">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="d3735-262">*Expensereportpage.xaml*會顯示在頁面上選取之人員的費用報表 **`ExpenseItHome`** 。</span><span class="sxs-lookup"><span data-stu-id="d3735-262">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="d3735-263">在本節中，您將建立**expensereportpage.xaml**的 UI。</span><span class="sxs-lookup"><span data-stu-id="d3735-263">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="d3735-264">您也會將背景和填滿色彩新增至各種 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="d3735-264">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="d3735-265">開啟*expensereportpage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3735-265">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="d3735-266">在標記之間加入下列 XAML <xref:System.Windows.Controls.Grid> ：</span><span class="sxs-lookup"><span data-stu-id="d3735-266">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="d3735-267">這個 UI 類似于 *`ExpenseItHome.xaml`* ，不同之處在于報表資料會顯示在中 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-267">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="d3735-268">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3735-268">Build and run the application.</span></span>

4. <span data-ttu-id="d3735-269">選取 [ **View** ] \ （編輯 \）按鈕。</span><span class="sxs-lookup"><span data-stu-id="d3735-269">Select the **View** button.</span></span>

    <span data-ttu-id="d3735-270">報表頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d3735-270">The expense report page appears.</span></span> <span data-ttu-id="d3735-271">另請注意，[上一頁] 瀏覽按鈕已啟用。</span><span class="sxs-lookup"><span data-stu-id="d3735-271">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="d3735-272">下圖顯示新增至*expensereportpage.xaml*的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="d3735-272">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseIt 範例螢幕擷取畫面，其中顯示剛剛為 Expensereportpage.xaml 建立的 UI。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="d3735-274">樣式控制項</span><span class="sxs-lookup"><span data-stu-id="d3735-274">Style controls</span></span>

<span data-ttu-id="d3735-275">針對 UI 中相同類型的所有元素，各種元素的外觀通常都相同。</span><span class="sxs-lookup"><span data-stu-id="d3735-275">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="d3735-276">UI 會使用[樣式](../../../desktop-wpf/fundamentals/styles-templates-overview.md)，讓多個元素的外觀可重複使用。</span><span class="sxs-lookup"><span data-stu-id="d3735-276">UI uses [styles](../../../desktop-wpf/fundamentals/styles-templates-overview.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="d3735-277">樣式的重複利用有助於簡化 XAML 的建立和管理。</span><span class="sxs-lookup"><span data-stu-id="d3735-277">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="d3735-278">本節會將先前步驟中定義的個別元素屬性 (Attribute) 取代為樣式。</span><span class="sxs-lookup"><span data-stu-id="d3735-278">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="d3735-279">開啟 app.xaml 或*App.xaml\*\*應用程式*。</span><span class="sxs-lookup"><span data-stu-id="d3735-279">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="d3735-280">在標記之間加入下列 XAML <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="d3735-280">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="d3735-281">這個 XAML 會加入下列樣式：</span><span class="sxs-lookup"><span data-stu-id="d3735-281">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="d3735-282">`headerTextStyle`：格式化頁面標題 <xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="d3735-282">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="d3735-283">`labelStyle`：格式化 <xref:System.Windows.Controls.Label> 控制項。</span><span class="sxs-lookup"><span data-stu-id="d3735-283">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="d3735-284">`columnHeaderStyle`：格式化 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。</span><span class="sxs-lookup"><span data-stu-id="d3735-284">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="d3735-285">`listHeaderStyle`：格式化清單標頭 <xref:System.Windows.Controls.Border> 控制項。</span><span class="sxs-lookup"><span data-stu-id="d3735-285">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="d3735-286">`listHeaderTextStyle`：格式化清單標頭 <xref:System.Windows.Controls.Label> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-286">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="d3735-287">`buttonStyle`：設定的格式 <xref:System.Windows.Controls.Button> `ExpenseItHome.xaml` 。</span><span class="sxs-lookup"><span data-stu-id="d3735-287">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="d3735-288">請注意，樣式是屬性元素的資源和子系 <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-288">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="d3735-289">在這裡，樣式會套用至應用程式中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="d3735-289">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="d3735-290">如需在 .NET 應用程式中使用資源的範例，請參閱[使用應用程式資源](../advanced/how-to-use-application-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="d3735-290">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="d3735-291">在中 *`ExpenseItHome.xaml`* ，以下列 XAML 取代元素之間的所有內容 <xref:System.Windows.Controls.Grid> ：</span><span class="sxs-lookup"><span data-stu-id="d3735-291">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="d3735-292">套用樣式會移除並取代諸如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 這類會定義每個控制項外觀的屬性。</span><span class="sxs-lookup"><span data-stu-id="d3735-292">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="d3735-293">例如，會套用 `headerTextStyle` 至「查看費用報表」 <xref:System.Windows.Controls.Label> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-293">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="d3735-294">開啟*expensereportpage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3735-294">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="d3735-295">以下列 XAML 取代元素之間的所有內容 <xref:System.Windows.Controls.Grid> ：</span><span class="sxs-lookup"><span data-stu-id="d3735-295">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="d3735-296">這個 XAML 會將樣式加入至 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Border> 元素。</span><span class="sxs-lookup"><span data-stu-id="d3735-296">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="d3735-297">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3735-297">Build and run the application.</span></span> <span data-ttu-id="d3735-298">視窗外觀與先前相同。</span><span class="sxs-lookup"><span data-stu-id="d3735-298">The window appearance is the same as previously.</span></span>

    ![使用與上一節相同的外觀，ExpenseIt 範例螢幕擷取畫面。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="d3735-300">關閉應用程式以返回 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d3735-300">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="d3735-301">將資料系結至控制項</span><span class="sxs-lookup"><span data-stu-id="d3735-301">Bind data to a control</span></span>

<span data-ttu-id="d3735-302">在本節中，您將建立系結至各種控制項的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="d3735-302">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="d3735-303">在中 *`ExpenseItHome.xaml`* ，于開啟的專案之後 <xref:System.Windows.Controls.Grid> 加入下列 XAML，以建立 <xref:System.Windows.Data.XmlDataProvider> 包含每個人員之資料的：</span><span class="sxs-lookup"><span data-stu-id="d3735-303">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="d3735-304">資料會建立為 <xref:System.Windows.Controls.Grid> 資源。</span><span class="sxs-lookup"><span data-stu-id="d3735-304">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="d3735-305">一般來說，這項資料會載入為檔案，但為了簡單起見，會以內嵌方式加入資料。</span><span class="sxs-lookup"><span data-stu-id="d3735-305">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="d3735-306">在專案中 `<Grid.Resources>` ，加入下列專案，此專案會 `<xref:System.Windows.DataTemplate>` 定義如何在的專案之後顯示中的資料 <xref:System.Windows.Controls.ListBox> `<XmlDataProvider>` ：</span><span class="sxs-lookup"><span data-stu-id="d3735-306">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="d3735-307">如需資料範本的詳細資訊，請參閱[資料範本化總覽](../data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3735-307">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="d3735-308"><xref:System.Windows.Controls.ListBox>以下列 XAML 取代現有的：</span><span class="sxs-lookup"><span data-stu-id="d3735-308">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="d3735-309">這個 XAML 會將的屬性系結 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> 至資料來源，並套用資料範本做為 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d3735-309">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="d3735-310">將資料連線至控制項</span><span class="sxs-lookup"><span data-stu-id="d3735-310">Connect data to controls</span></span>

<span data-ttu-id="d3735-311">接下來，您將新增程式碼來抓取頁面上所選取的名稱， **`ExpenseItHome`** 並將它傳遞給**expensereportpage.xaml**的函式。</span><span class="sxs-lookup"><span data-stu-id="d3735-311">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="d3735-312">**Expensereportpage.xaml**會使用傳遞的專案來設定其資料內容，這就是*expensereportpage.xaml*中定義的控制項。</span><span class="sxs-lookup"><span data-stu-id="d3735-312">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="d3735-313">開啟*expensereportpage.xaml*或*ExpenseReportPage.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="d3735-313">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="d3735-314">加入一個可接受物件的建構函式，如此您就可以傳遞選取之人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="d3735-314">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="d3735-315">開啟 *`ExpenseItHome.xaml.vb`* 或 *`ExpenseItHome.xaml.cs`* 。</span><span class="sxs-lookup"><span data-stu-id="d3735-315">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="d3735-316">變更 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件處理常式，以呼叫新的函式，以傳遞所選人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="d3735-316">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="d3735-317">使用資料範本的樣式資料</span><span class="sxs-lookup"><span data-stu-id="d3735-317">Style data with data templates</span></span>

<span data-ttu-id="d3735-318">在本節中，您將使用資料範本來更新資料系結清單中每個專案的 UI。</span><span class="sxs-lookup"><span data-stu-id="d3735-318">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="d3735-319">開啟*expensereportpage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3735-319">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="d3735-320">將「名稱」和「部門」元素的內容系結 <xref:System.Windows.Controls.Label> 至適當的資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="d3735-320">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="d3735-321">如需資料系結的詳細資訊，請參閱資料系結[總覽](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3735-321">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="d3735-322">在開啟的專案之後 <xref:System.Windows.Controls.Grid> ，新增下列資料範本，以定義如何顯示費用報表資料：</span><span class="sxs-lookup"><span data-stu-id="d3735-322">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="d3735-323">以元素底下的元素取代， <xref:System.Windows.Controls.DataGridTextColumn> <xref:System.Windows.Controls.DataGridTemplateColumn> <xref:System.Windows.Controls.DataGrid> 並將範本套用至這些專案。</span><span class="sxs-lookup"><span data-stu-id="d3735-323">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="d3735-324">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3735-324">Build and run the application.</span></span>

6. <span data-ttu-id="d3735-325">選取人員，然後選取 [ **View** ] \ （編輯 \）按鈕。</span><span class="sxs-lookup"><span data-stu-id="d3735-325">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="d3735-326">下圖顯示應用程式的兩個頁面 `ExpenseIt` ，其中已套用控制項、配置、樣式、資料系結和資料範本：</span><span class="sxs-lookup"><span data-stu-id="d3735-326">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![應用程式的兩個頁面會顯示 [名稱] 清單和費用報表。](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="d3735-328">這個範例會示範 WPF 的特定功能，並不會遵循安全性、當地語系化和協助工具等專案的所有最佳作法。</span><span class="sxs-lookup"><span data-stu-id="d3735-328">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="d3735-329">如需 WPF 和 .NET 應用程式開發最佳作法的完整涵蓋範圍，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d3735-329">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="d3735-330">協助工具</span><span class="sxs-lookup"><span data-stu-id="d3735-330">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="d3735-331">安全性</span><span class="sxs-lookup"><span data-stu-id="d3735-331">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="d3735-332">WPF 全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="d3735-332">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="d3735-333">WPF 效能</span><span class="sxs-lookup"><span data-stu-id="d3735-333">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="d3735-334">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="d3735-334">Next steps</span></span>

<span data-ttu-id="d3735-335">在本逐步解說中，您已瞭解使用 Windows Presentation Foundation （WPF）來建立 UI 的數種技術。</span><span class="sxs-lookup"><span data-stu-id="d3735-335">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="d3735-336">您現在應該對資料系結 .NET 應用程式的建立區塊有基本瞭解。</span><span class="sxs-lookup"><span data-stu-id="d3735-336">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="d3735-337">如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d3735-337">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="d3735-338">WPF 架構</span><span class="sxs-lookup"><span data-stu-id="d3735-338">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="d3735-339">XAML 總覽（WPF）</span><span class="sxs-lookup"><span data-stu-id="d3735-339">XAML overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="d3735-340">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="d3735-340">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="d3735-341">配置</span><span class="sxs-lookup"><span data-stu-id="d3735-341">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="d3735-342">如需建立應用程式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d3735-342">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="d3735-343">XBOX Video Application Development</span><span class="sxs-lookup"><span data-stu-id="d3735-343">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="d3735-344">控制項</span><span class="sxs-lookup"><span data-stu-id="d3735-344">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="d3735-345">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="d3735-345">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="d3735-346">圖形與多媒體</span><span class="sxs-lookup"><span data-stu-id="d3735-346">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="d3735-347">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="d3735-347">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="d3735-348">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3735-348">See also</span></span>

- [<span data-ttu-id="d3735-349">面板總覽</span><span class="sxs-lookup"><span data-stu-id="d3735-349">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="d3735-350">資料範本化總覽</span><span class="sxs-lookup"><span data-stu-id="d3735-350">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="d3735-351">建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="d3735-351">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="d3735-352">樣式和範本</span><span class="sxs-lookup"><span data-stu-id="d3735-352">Styles and templates</span></span>](../controls/styles-and-templates.md)
