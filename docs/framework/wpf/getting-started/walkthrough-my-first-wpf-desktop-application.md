---
title: 在 Visual Studio 中建立 WPF 應用程式
ms.date: 10/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: dbfc40bd1fcc97810ea1397731bd8c232297cbd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922909"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="d3192-102">逐步解說：我的第一個 WPF 傳統型應用程式</span><span class="sxs-lookup"><span data-stu-id="d3192-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="d3192-103">這篇文章會示範如何開發簡單的 Windows Presentation Foundation (WPF) 應用程式，其中包含大部分的 WPF 應用程式通用的項目：Extensible Application Markup Language (XAML) 標記、 程式碼後置、 應用程式定義、 控制項、 版面配置、 資料繫結和樣式。</span><span class="sxs-lookup"><span data-stu-id="d3192-103">This article shows you how to develop a simple Windows Presentation Foundation (WPF) application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span>

<span data-ttu-id="d3192-104">本逐步解說包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d3192-104">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="d3192-105">您可以使用 XAML 來設計應用程式的使用者介面 (UI) 的外觀。</span><span class="sxs-lookup"><span data-stu-id="d3192-105">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="d3192-106">撰寫程式碼來建置應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="d3192-106">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="d3192-107">建立應用程式定義來管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3192-107">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="d3192-108">新增控制項並建立要撰寫應用程式 UI 的配置。</span><span class="sxs-lookup"><span data-stu-id="d3192-108">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="d3192-109">建立一致的外觀，整個應用程式的 UI 的樣式。</span><span class="sxs-lookup"><span data-stu-id="d3192-109">Create styles for a consistent appearance throughout an application's UI.</span></span>

- <span data-ttu-id="d3192-110">將 UI 繫結到資料填入資料的 UI 和保留的資料和同步處理的 UI。</span><span class="sxs-lookup"><span data-stu-id="d3192-110">Bind the UI to data to both populate the UI from data and keep the data and UI synchronized.</span></span>

<span data-ttu-id="d3192-111">本逐步解說結束時，您將會建置一個獨立的 Windows 應用程式，可讓使用者檢視所選取人員經費支出報表。</span><span class="sxs-lookup"><span data-stu-id="d3192-111">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="d3192-112">應用程式是由數個在瀏覽器樣式的視窗中裝載的 WPF 頁面所組成。</span><span class="sxs-lookup"><span data-stu-id="d3192-112">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="d3192-113">用來建立這個逐步解說的範例程式碼是適用於 Visual Basic 和 C#[建置 WPF 應用程式簡介](https://go.microsoft.com/fwlink/?LinkID=160008)。</span><span class="sxs-lookup"><span data-stu-id="d3192-113">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Introduction to Building WPF Applications](https://go.microsoft.com/fwlink/?LinkID=160008).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3192-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="d3192-114">Prerequisites</span></span>

- <span data-ttu-id="d3192-115">Visual Studio 2017 或更新版本</span><span class="sxs-lookup"><span data-stu-id="d3192-115">Visual Studio 2017 or later</span></span>

   <span data-ttu-id="d3192-116">如需有關如何安裝最新版的 Visual Studio 的詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio](/visualstudio/install/install-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="d3192-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="d3192-117">建立應用程式專案</span><span class="sxs-lookup"><span data-stu-id="d3192-117">Create the application project</span></span>

<span data-ttu-id="d3192-118">第一個步驟是建立應用程式基礎結構，包括應用程式定義、 兩個頁面，以及映像。</span><span class="sxs-lookup"><span data-stu-id="d3192-118">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="d3192-119">在 Visual Basic 或 Visual C# 中名為建立新的 WPF 應用程式專案 **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="d3192-119">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="d3192-120">開啟 Visual Studio，然後選取**檔案** > **新增** > **專案**。</span><span class="sxs-lookup"><span data-stu-id="d3192-120">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="d3192-121">**新的專案** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d3192-121">The **New Project** dialog opens.</span></span>

   2. <span data-ttu-id="d3192-122">底下**已安裝**分類中，展開**視覺化C#** 或**Visual Basic**節點，，然後選取**Windows 桌面**。</span><span class="sxs-lookup"><span data-stu-id="d3192-122">Under the **Installed** category, expand either the **Visual C#** or **Visual Basic** node, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="d3192-123">選取  **WPF 應用程式 (.NET Framework)** 範本。</span><span class="sxs-lookup"><span data-stu-id="d3192-123">Select the **WPF App (.NET Framework)** template.</span></span> <span data-ttu-id="d3192-124">輸入名稱 **`ExpenseIt`** ，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="d3192-124">Enter the name **`ExpenseIt`** and then select **OK**.</span></span>

      ![與所選的 WPF 應用程式的 [新增專案] 對話方塊](./media/new-project-dialog.png)

      <span data-ttu-id="d3192-126">Visual Studio 會建立專案並開啟名為預設應用程式視窗的設計工具**MainWindow.xaml**。</span><span class="sxs-lookup"><span data-stu-id="d3192-126">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d3192-127">本逐步解說使用<xref:System.Windows.Controls.DataGrid>可在.NET Framework 4 及更新版本的控制項。</span><span class="sxs-lookup"><span data-stu-id="d3192-127">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4 and later.</span></span> <span data-ttu-id="d3192-128">為確定您的專案目標.NET Framework 4 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="d3192-128">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="d3192-129">如需詳細資訊，請參閱[如何：以一個 .NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。</span><span class="sxs-lookup"><span data-stu-id="d3192-129">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

2. <span data-ttu-id="d3192-130">開啟*Application.xaml* (Visual Basic) 或*App.xaml* (C#)。</span><span class="sxs-lookup"><span data-stu-id="d3192-130">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="d3192-131">此 XAML 檔案定義 WPF 應用程式和任何應用程式資源。</span><span class="sxs-lookup"><span data-stu-id="d3192-131">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="d3192-132">您也使用此檔案來指定 UI 會自動顯示時，應用程式啟動;在此情況下， *MainWindow.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-132">You also use this file to specify the UI that automatically shows when the application starts; in this case, *MainWindow.xaml*.</span></span>

    <span data-ttu-id="d3192-133">在 Visual Basic 中，您的 XAML 應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="d3192-133">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="d3192-134">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3192-134">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="d3192-135">開啟*MainWindow.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-135">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="d3192-136">此 XAML 檔案是您的應用程式的主視窗，並顯示在頁面中建立的內容。</span><span class="sxs-lookup"><span data-stu-id="d3192-136">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="d3192-137"><xref:System.Windows.Window>類別定義的屬性視窗中，例如其標題、 大小或圖示，並處理例如關閉或隱藏的事件。</span><span class="sxs-lookup"><span data-stu-id="d3192-137">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="d3192-138">變更<xref:System.Windows.Window>項目<xref:System.Windows.Navigation.NavigationWindow>，如下列 XAML 所示：</span><span class="sxs-lookup"><span data-stu-id="d3192-138">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="d3192-139">此應用程式瀏覽至不同的內容，根據使用者輸入而定。</span><span class="sxs-lookup"><span data-stu-id="d3192-139">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="d3192-140">這就是為什麼主要<xref:System.Windows.Window>變更為需要<xref:System.Windows.Navigation.NavigationWindow>。</span><span class="sxs-lookup"><span data-stu-id="d3192-140">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="d3192-141"><xref:System.Windows.Navigation.NavigationWindow> 繼承的所有屬性<xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="d3192-141"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="d3192-142"><xref:System.Windows.Navigation.NavigationWindow> XAML 檔案中的項目建立的執行個體<xref:System.Windows.Navigation.NavigationWindow>類別。</span><span class="sxs-lookup"><span data-stu-id="d3192-142">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="d3192-143">如需詳細資訊，請參閱 <<c0> [ 巡覽概觀](../app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3192-143">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="d3192-144">在變更下列屬性<xref:System.Windows.Navigation.NavigationWindow>項目：</span><span class="sxs-lookup"><span data-stu-id="d3192-144">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="d3192-145">設定<xref:System.Windows.Window.Title%2A>屬性，以 「`ExpenseIt`"。</span><span class="sxs-lookup"><span data-stu-id="d3192-145">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="d3192-146">設定<xref:System.Windows.FrameworkElement.Width%2A>為 500 像素的屬性。</span><span class="sxs-lookup"><span data-stu-id="d3192-146">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    - <span data-ttu-id="d3192-147">設定<xref:System.Windows.FrameworkElement.Height%2A>350 像素為單位的屬性。</span><span class="sxs-lookup"><span data-stu-id="d3192-147">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="d3192-148">移除<xref:System.Windows.Controls.Grid>之間的項目<xref:System.Windows.Navigation.NavigationWindow>標記。</span><span class="sxs-lookup"><span data-stu-id="d3192-148">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

    <span data-ttu-id="d3192-149">在 Visual Basic 中，您的 XAML 應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="d3192-149">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="d3192-150">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3192-150">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. <span data-ttu-id="d3192-151">開啟*MainWindow.xaml.vb*或是*MainWindow.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="d3192-151">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="d3192-152">這個檔案是包含程式碼來處理中所宣告事件的程式碼後置檔案*MainWindow.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-152">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="d3192-153">這個檔案包含 XAML 中定義之視窗的部分類別。</span><span class="sxs-lookup"><span data-stu-id="d3192-153">This file contains a partial class for the window defined in XAML.</span></span>

7. <span data-ttu-id="d3192-154">如果您使用的 C#，變更`MainWindow`類別來衍生自<xref:System.Windows.Navigation.NavigationWindow>。</span><span class="sxs-lookup"><span data-stu-id="d3192-154">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="d3192-155">（在 Visual Basic 中，這會自動變更 XAML 中的視窗。）</span><span class="sxs-lookup"><span data-stu-id="d3192-155">(In Visual Basic, this happens automatically when you change the window in XAML.)</span></span>

   <span data-ttu-id="d3192-156">您的程式碼看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="d3192-156">Your code should look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > <span data-ttu-id="d3192-157">您可以切換之間 C# 和 Visual Basic 中的範例程式碼的程式碼語言**語言**這篇文章的右上方的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d3192-157">You can toggle the code language of the sample code between C# and Visual Basic in the **Language** drop-down on the upper right side of this article.</span></span>

## <a name="add-files-to-the-application"></a><span data-ttu-id="d3192-158">將檔案新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="d3192-158">Add files to the application</span></span>

<span data-ttu-id="d3192-159">在本節中，您要在應用程式中加入兩頁網頁和一個影像。</span><span class="sxs-lookup"><span data-stu-id="d3192-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="d3192-160">將新的 WPF 頁面新增至專案，並將它命名 *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="d3192-160">Add a new WPF page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="d3192-161">在 [**方案總管] 中**，以滑鼠右鍵按一下 **`ExpenseIt`** 專案節點，然後選擇**新增** > **頁面**。</span><span class="sxs-lookup"><span data-stu-id="d3192-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="d3192-162">在 [**加入新項目**] 對話方塊中，**頁面 (WPF)** 已選取範本。</span><span class="sxs-lookup"><span data-stu-id="d3192-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="d3192-163">輸入名稱 **`ExpenseItHome`** ，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="d3192-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="d3192-164">此頁面是應用程式啟動時顯示的第一頁。</span><span class="sxs-lookup"><span data-stu-id="d3192-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="d3192-165">它會顯示一份可供選取，以顯示其費用報表的人員。</span><span class="sxs-lookup"><span data-stu-id="d3192-165">It will show a list of people to select from, to show an expense report for.</span></span>

2. <span data-ttu-id="d3192-166">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-166">Open *`ExpenseItHome.xaml`*.</span></span>

3. <span data-ttu-id="d3192-167">設定<xref:System.Windows.Controls.Page.Title%2A>到 「`ExpenseIt - Home`"。</span><span class="sxs-lookup"><span data-stu-id="d3192-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

    <span data-ttu-id="d3192-168">在 Visual Basic 中，您的 XAML 應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="d3192-168">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="d3192-169">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3192-169">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. <span data-ttu-id="d3192-170">開啟*MainWindow.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-170">Open *MainWindow.xaml*.</span></span>

5. <span data-ttu-id="d3192-171">設定<xref:System.Windows.Navigation.NavigationWindow.Source%2A>上的屬性<xref:System.Windows.Navigation.NavigationWindow>到 「`ExpenseItHome.xaml`"。</span><span class="sxs-lookup"><span data-stu-id="d3192-171">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="d3192-172">這會設定 *`ExpenseItHome.xaml`* 是第一頁開啟 應用程式啟動時。</span><span class="sxs-lookup"><span data-stu-id="d3192-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> <span data-ttu-id="d3192-173">在 Visual Basic 中，您的 XAML 應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="d3192-173">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="d3192-174">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3192-174">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="d3192-175">您也可以設定**來源**中的屬性**其他**分類**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="d3192-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![在 [屬性] 視窗中的 [來源] 屬性](./media/properties-source.png)

6. <span data-ttu-id="d3192-177">將另一個新的 WPF 頁面新增至專案，並將它命名*ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="d3192-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="d3192-178">在 [**方案總管] 中**，以滑鼠右鍵按一下 **`ExpenseIt`** 專案節點，然後選擇**新增** > **頁面**。</span><span class="sxs-lookup"><span data-stu-id="d3192-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="d3192-179">在 [**加入新項目**] 對話方塊中，**頁面 (WPF)** 已選取範本。</span><span class="sxs-lookup"><span data-stu-id="d3192-179">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="d3192-180">輸入名稱**ExpenseReportPage**，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="d3192-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="d3192-181">此頁面會顯示在所選取之人員的費用報表 **`ExpenseItHome`** 頁面。</span><span class="sxs-lookup"><span data-stu-id="d3192-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

7. <span data-ttu-id="d3192-182">開啟 *ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-182">Open *ExpenseReportPage.xaml*.</span></span>

8. <span data-ttu-id="d3192-183">設定<xref:System.Windows.Controls.Page.Title%2A>到 「`ExpenseIt - View Expense`"。</span><span class="sxs-lookup"><span data-stu-id="d3192-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

    <span data-ttu-id="d3192-184">在 Visual Basic 中，您的 XAML 應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="d3192-184">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="d3192-185">或在 C# 中如下所示：</span><span class="sxs-lookup"><span data-stu-id="d3192-185">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. <span data-ttu-id="d3192-186">開啟*ExpenseItHome.xaml.vb*並*ExpenseReportPage.xaml.vb*，或*ExpenseItHome.xaml.cs*並*ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="d3192-186">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="d3192-187">當您建立新的分頁檔時，Visual Studio 會自動建立*程式碼後置*檔案。</span><span class="sxs-lookup"><span data-stu-id="d3192-187">When you create a new Page file, Visual Studio automatically creates a *code-behind* file.</span></span> <span data-ttu-id="d3192-188">這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。</span><span class="sxs-lookup"><span data-stu-id="d3192-188">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="d3192-189">您的程式碼應該看起來像這樣的 **`ExpenseItHome`** :</span><span class="sxs-lookup"><span data-stu-id="d3192-189">Your code should look like this for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="d3192-190">與此項目，例如**ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="d3192-190">And like this for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. <span data-ttu-id="d3192-191">加入名為影像*watermark.png*至專案。</span><span class="sxs-lookup"><span data-stu-id="d3192-191">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="d3192-192">您可以建立自己的映像、 將檔案複製範例程式碼，或取得它[此處](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/./media/watermark.png)。</span><span class="sxs-lookup"><span data-stu-id="d3192-192">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/./media/watermark.png).</span></span>

    1. <span data-ttu-id="d3192-193">以滑鼠右鍵按一下專案節點，然後選取**新增** > **現有項目**，或按**Shift**+**Alt**+ **A**。</span><span class="sxs-lookup"><span data-stu-id="d3192-193">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="d3192-194">在 **加入現有項目** 對話方塊中，瀏覽至您想要使用此項目，然後選取 映像檔案**新增**。</span><span class="sxs-lookup"><span data-stu-id="d3192-194">In the **Add Existing Item** dialog, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="d3192-195">建立和執行應用程式</span><span class="sxs-lookup"><span data-stu-id="d3192-195">Build and run the application</span></span>

1. <span data-ttu-id="d3192-196">若要建置並執行應用程式，請按**F5**或選取**開始偵錯**從**偵錯**功能表。</span><span class="sxs-lookup"><span data-stu-id="d3192-196">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="d3192-197">下圖顯示應用程式與<xref:System.Windows.Navigation.NavigationWindow>按鈕：</span><span class="sxs-lookup"><span data-stu-id="d3192-197">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![ExpenseIt 範例螢幕擷取畫面](./media/gettingstartedfigure1.png)

2. <span data-ttu-id="d3192-199">關閉應用程式，若要返回 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d3192-199">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="d3192-200">建立版面配置</span><span class="sxs-lookup"><span data-stu-id="d3192-200">Create the layout</span></span>

<span data-ttu-id="d3192-201">版面配置會按照順序放置 UI 項目，並也會管理的大小和位置，這些元件的 UI 調整大小時。</span><span class="sxs-lookup"><span data-stu-id="d3192-201">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="d3192-202">您通常會建立具有下列其中一個版面配置控制項的版面配置：</span><span class="sxs-lookup"><span data-stu-id="d3192-202">You typically create a layout with one of the following layout controls:</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

<span data-ttu-id="d3192-203">這些版面配置控制項都支援其子元素的特殊版面配置類型。</span><span class="sxs-lookup"><span data-stu-id="d3192-203">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="d3192-204">`ExpenseIt` 頁面可以調整大小，以及每個頁面都有會水平和垂直排列沿著其他元素的元素。</span><span class="sxs-lookup"><span data-stu-id="d3192-204">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="d3192-205">因此，<xref:System.Windows.Controls.Grid>為應用程式的理想的版面配置項目。</span><span class="sxs-lookup"><span data-stu-id="d3192-205">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="d3192-206">如需詳細資訊<xref:System.Windows.Controls.Panel>項目，請參閱[面板概觀](../controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3192-206">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="d3192-207">如需有關配置的詳細資訊，請參閱[版面配置](../advanced/layout.md)。</span><span class="sxs-lookup"><span data-stu-id="d3192-207">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="d3192-208">在區段中，您建立單欄資料表具有三個資料列和 10 個像素邊界添加資料行和資料列的定義，以便<xref:System.Windows.Controls.Grid>中 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-208">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="d3192-209">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-209">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="d3192-210">設定<xref:System.Windows.FrameworkElement.Margin%2A>屬性上的<xref:System.Windows.Controls.Grid>"10,0,10,10 」，其對應到左、 上、 右和下邊界的項目：</span><span class="sxs-lookup"><span data-stu-id="d3192-210">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="d3192-211">您也可以設定**邊界**中的值**屬性**視窗下方**配置**類別：</span><span class="sxs-lookup"><span data-stu-id="d3192-211">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![在 [屬性] 視窗中的邊界值](./media/properties-margin.png)

3. <span data-ttu-id="d3192-213">加入下列 XAML 之間<xref:System.Windows.Controls.Grid>標籤來建立的資料列和資料行定義：</span><span class="sxs-lookup"><span data-stu-id="d3192-213">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="d3192-214"><xref:System.Windows.Controls.RowDefinition.Height%2A>兩個資料列設<xref:System.Windows.GridLength.Auto%2A>，這表示資料列的大小調整為基礎的資料列中的內容。</span><span class="sxs-lookup"><span data-stu-id="d3192-214">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="d3192-215">預設值<xref:System.Windows.Controls.RowDefinition.Height%2A>是<xref:System.Windows.GridUnitType.Star>調整大小，這表示資料列高度的可用空間的加權的比例。</span><span class="sxs-lookup"><span data-stu-id="d3192-215">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="d3192-216">例如，如果兩個資料列有<xref:System.Windows.Controls.RowDefinition.Height%2A>的 「 \* 」，它們都各自具有的高度都是可用空間的一半。</span><span class="sxs-lookup"><span data-stu-id="d3192-216">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="d3192-217">您<xref:System.Windows.Controls.Grid>現在看起來應該像下列 XAML:</span><span class="sxs-lookup"><span data-stu-id="d3192-217">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="d3192-218">加入控制項</span><span class="sxs-lookup"><span data-stu-id="d3192-218">Add controls</span></span>

<span data-ttu-id="d3192-219">在本節中，您會更新 UI，讓使用者可以從選取以顯示費用報表的人員清單中的 [首頁] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d3192-219">In this section, you'll update the home page UI to show a list of people that a user can select from to show the expense report for.</span></span> <span data-ttu-id="d3192-220">控制項是可讓使用者與您應用程式互動的 UI 物件。</span><span class="sxs-lookup"><span data-stu-id="d3192-220">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="d3192-221">如需詳細資訊，請參閱 [控制項](../controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3192-221">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="d3192-222">若要建立此 UI，您會新增下列項目，來 *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="d3192-222">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="d3192-223"><xref:System.Windows.Controls.ListBox> （適用於的人員清單）。</span><span class="sxs-lookup"><span data-stu-id="d3192-223"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="d3192-224"><xref:System.Windows.Controls.Label> （適用於清單標頭）。</span><span class="sxs-lookup"><span data-stu-id="d3192-224"><xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="d3192-225"><xref:System.Windows.Controls.Button> （可以按一下清單中選取的人員檢視費用報表）。</span><span class="sxs-lookup"><span data-stu-id="d3192-225"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="d3192-226">每個控制項都會在資料列<xref:System.Windows.Controls.Grid>藉由設定<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>附加屬性。</span><span class="sxs-lookup"><span data-stu-id="d3192-226">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="d3192-227">如需有關附加屬性的詳細資訊，請參閱[附加屬性概觀](../advanced/attached-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3192-227">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="d3192-228">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-228">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="d3192-229">加入下列 XAML 某處之間<xref:System.Windows.Controls.Grid>標記：</span><span class="sxs-lookup"><span data-stu-id="d3192-229">Add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="d3192-230">您也可以從建立控制項**工具箱**視窗拖曳至 [設計] 視窗和中，然後設定其屬性**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="d3192-230">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

3. <span data-ttu-id="d3192-231">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3192-231">Build and run the application.</span></span>

<span data-ttu-id="d3192-232">下圖將顯示您剛才建立的控制項：</span><span class="sxs-lookup"><span data-stu-id="d3192-232">The following illustration shows the controls you just created:</span></span>

![ExpenseIt 範例螢幕擷取畫面](./media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="d3192-234">新增影像和標題</span><span class="sxs-lookup"><span data-stu-id="d3192-234">Add an image and a title</span></span>

<span data-ttu-id="d3192-235">在本節中，您將使用影像和網頁標題更新在首頁 UI。</span><span class="sxs-lookup"><span data-stu-id="d3192-235">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="d3192-236">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-236">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="d3192-237">新增另一個資料行<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>具有固定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>230 像素的：</span><span class="sxs-lookup"><span data-stu-id="d3192-237">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. <span data-ttu-id="d3192-238">新增另一個資料列<xref:System.Windows.Controls.Grid.RowDefinitions%2A>，總共四個資料列：</span><span class="sxs-lookup"><span data-stu-id="d3192-238">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. <span data-ttu-id="d3192-239">將控制項移到第二個資料行中，藉由設定<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>屬性設為 1，在每個三個控制項 （框線、 清單方塊中和按鈕）。</span><span class="sxs-lookup"><span data-stu-id="d3192-239">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

5. <span data-ttu-id="d3192-240">下移資料列中的每個控制項，遞增其<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>值加 1。</span><span class="sxs-lookup"><span data-stu-id="d3192-240">Move each control down a row, by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1.</span></span>

   <span data-ttu-id="d3192-241">三個控制項的 XAML 現在看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="d3192-241">The XAML for the three controls now looks like this:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. <span data-ttu-id="d3192-242">設定<xref:System.Windows.Controls.Panel.Background%2A>的<xref:System.Windows.Controls.Grid>要*watermark.png*映像檔案中的，新增下列 XAML 某處之間`<Grid>`和`</Grid>`標記：</span><span class="sxs-lookup"><span data-stu-id="d3192-242">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the *watermark.png* image file, by adding the following XAML somewhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. <span data-ttu-id="d3192-243">再<xref:System.Windows.Controls.Border>項目，新增<xref:System.Windows.Controls.Label>以"View Expense Report"的內容。</span><span class="sxs-lookup"><span data-stu-id="d3192-243">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="d3192-244">這是頁面的標題。</span><span class="sxs-lookup"><span data-stu-id="d3192-244">This is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. <span data-ttu-id="d3192-245">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3192-245">Build and run the application.</span></span>

<span data-ttu-id="d3192-246">下圖顯示您剛才加入的結果：</span><span class="sxs-lookup"><span data-stu-id="d3192-246">The following illustration shows the results of what you just added:</span></span>

![ExpenseIt 範例螢幕擷取畫面](./media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="d3192-248">加入程式碼來處理事件</span><span class="sxs-lookup"><span data-stu-id="d3192-248">Add code to handle events</span></span>

1. <span data-ttu-id="d3192-249">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-249">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="d3192-250">新增<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式來<xref:System.Windows.Controls.Button>項目。</span><span class="sxs-lookup"><span data-stu-id="d3192-250">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="d3192-251">如需詳細資訊，請參閱[如何：建立簡單的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d3192-251">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. <span data-ttu-id="d3192-252">開啟 *`ExpenseItHome.xaml.vb`* 或是 *`ExpenseItHome.xaml.cs`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-252">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="d3192-253">將下列程式碼加入`ExpenseItHome`類別加入的按鈕 click 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d3192-253">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="d3192-254">事件處理常式會開啟**ExpenseReportPage**頁面。</span><span class="sxs-lookup"><span data-stu-id="d3192-254">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="d3192-255">建立 ExpenseReportPage 的 UI</span><span class="sxs-lookup"><span data-stu-id="d3192-255">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="d3192-256">*ExpenseReportPage.xaml*上選取的人員顯示的經費支出報表 **`ExpenseItHome`** 頁面。</span><span class="sxs-lookup"><span data-stu-id="d3192-256">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="d3192-257">在本節中，您將建立的 UI **ExpenseReportPage**。</span><span class="sxs-lookup"><span data-stu-id="d3192-257">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="d3192-258">您也將新增的背景和填滿色彩，以各種不同的 UI 項目。</span><span class="sxs-lookup"><span data-stu-id="d3192-258">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="d3192-259">開啟 *ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-259">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="d3192-260">加入下列 XAML 之間<xref:System.Windows.Controls.Grid>標記：</span><span class="sxs-lookup"><span data-stu-id="d3192-260">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="d3192-261">此 UI 很類似 *`ExpenseItHome.xaml`* ，但報表資料會顯示在<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="d3192-261">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="d3192-262">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3192-262">Build and run the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d3192-263">如果您收到錯誤指出<xref:System.Windows.Controls.DataGrid>找不到或不存在，請確定您的專案目標.NET Framework 4 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="d3192-263">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="d3192-264">如需詳細資訊，請參閱[如何：以一個 .NET Framework 版本為目標](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)。</span><span class="sxs-lookup"><span data-stu-id="d3192-264">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

4. <span data-ttu-id="d3192-265">選取 [**檢視**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d3192-265">Select the **View** button.</span></span>

    <span data-ttu-id="d3192-266">報表頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d3192-266">The expense report page appears.</span></span> <span data-ttu-id="d3192-267">也請注意，會啟用 [向後巡覽] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d3192-267">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="d3192-268">下圖顯示加入至 UI 項目*ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-268">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseIt 範例螢幕擷取畫面](./media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="d3192-270">樣式控制項</span><span class="sxs-lookup"><span data-stu-id="d3192-270">Style controls</span></span>

<span data-ttu-id="d3192-271">各種元素外觀通常是相同的 UI 中相同類型的所有項目。</span><span class="sxs-lookup"><span data-stu-id="d3192-271">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="d3192-272">使用 UI[樣式](../controls/styling-and-templating.md)讓跨多個元素的可重複使用外觀。</span><span class="sxs-lookup"><span data-stu-id="d3192-272">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="d3192-273">樣式的重複使用性有助於簡化 XAML 建立與管理。</span><span class="sxs-lookup"><span data-stu-id="d3192-273">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="d3192-274">本節會將先前步驟中定義的個別元素屬性 (Attribute) 取代為樣式。</span><span class="sxs-lookup"><span data-stu-id="d3192-274">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="d3192-275">開啟*Application.xaml*或是*App.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-275">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="d3192-276">加入下列 XAML 之間<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>標記：</span><span class="sxs-lookup"><span data-stu-id="d3192-276">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="d3192-277">這個 XAML 會加入下列樣式：</span><span class="sxs-lookup"><span data-stu-id="d3192-277">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="d3192-278">`headerTextStyle`：若要格式化頁面標題<xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="d3192-278">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="d3192-279">`labelStyle`：若要格式化<xref:System.Windows.Controls.Label>控制項。</span><span class="sxs-lookup"><span data-stu-id="d3192-279">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="d3192-280">`columnHeaderStyle`：若要格式化<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。</span><span class="sxs-lookup"><span data-stu-id="d3192-280">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="d3192-281">`listHeaderStyle`：若要格式化清單標頭<xref:System.Windows.Controls.Border>控制項。</span><span class="sxs-lookup"><span data-stu-id="d3192-281">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="d3192-282">`listHeaderTextStyle`：若要格式化清單標頭<xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="d3192-282">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="d3192-283">`buttonStyle`：若要格式化<xref:System.Windows.Controls.Button>上`ExpenseItHome.xaml`。</span><span class="sxs-lookup"><span data-stu-id="d3192-283">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="d3192-284">請注意，樣式是資源和子系<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>屬性項目。</span><span class="sxs-lookup"><span data-stu-id="d3192-284">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="d3192-285">在這裡，樣式會套用至應用程式中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="d3192-285">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="d3192-286">如需在.NET Framework 應用程式中使用資源的範例，請參閱[使用應用程式資源](../advanced/how-to-use-application-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="d3192-286">For an example of using resources in a .NET Framework application, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="d3192-287">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-287">Open *`ExpenseItHome.xaml`*.</span></span>

4. <span data-ttu-id="d3192-288">取代之間的所有內容<xref:System.Windows.Controls.Grid>具有下列的 XAML 項目：</span><span class="sxs-lookup"><span data-stu-id="d3192-288">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="d3192-289">套用樣式會移除並取代諸如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 這類會定義每個控制項外觀的屬性。</span><span class="sxs-lookup"><span data-stu-id="d3192-289">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="d3192-290">例如，`headerTextStyle`套用至"View Expense Report" <xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="d3192-290">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

5. <span data-ttu-id="d3192-291">開啟 *ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-291">Open *ExpenseReportPage.xaml*.</span></span>

6. <span data-ttu-id="d3192-292">取代之間的所有內容<xref:System.Windows.Controls.Grid>具有下列的 XAML 項目：</span><span class="sxs-lookup"><span data-stu-id="d3192-292">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="d3192-293">這樣會將樣式加入 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Border> 項目。</span><span class="sxs-lookup"><span data-stu-id="d3192-293">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="d3192-294">將資料繫結至控制項</span><span class="sxs-lookup"><span data-stu-id="d3192-294">Bind data to a control</span></span>

<span data-ttu-id="d3192-295">在本節中，您將建立 XML 資料繫結至不同的控制項。</span><span class="sxs-lookup"><span data-stu-id="d3192-295">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="d3192-296">開啟 *`ExpenseItHome.xaml`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-296">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="d3192-297">在開啟之後<xref:System.Windows.Controls.Grid>項目，加入下列 XAML 來建立<xref:System.Windows.Data.XmlDataProvider>包含的每個人資料：</span><span class="sxs-lookup"><span data-stu-id="d3192-297">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#21](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="d3192-298">資料會建立為<xref:System.Windows.Controls.Grid>資源。</span><span class="sxs-lookup"><span data-stu-id="d3192-298">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="d3192-299">這通常會載入為檔案，但為求簡化會內嵌資料。</span><span class="sxs-lookup"><span data-stu-id="d3192-299">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span>

3. <span data-ttu-id="d3192-300">內`<Grid.Resources>`項目，新增下列<xref:System.Windows.DataTemplate>，其定義如何顯示資料的<xref:System.Windows.Controls.ListBox>:</span><span class="sxs-lookup"><span data-stu-id="d3192-300">Within the `<Grid.Resources>` element, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>:</span></span>

    [!code-xaml[ExpenseIt#21](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="d3192-301">如需有關資料範本的詳細資訊，請參閱[資料範本化概觀](../data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3192-301">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

4. <span data-ttu-id="d3192-302">取代現有<xref:System.Windows.Controls.ListBox>與下列 XAML:</span><span class="sxs-lookup"><span data-stu-id="d3192-302">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="d3192-303">此 XAML 會將繫結<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的屬性<xref:System.Windows.Controls.ListBox>資料來源，並套用資料範本，做為<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>。</span><span class="sxs-lookup"><span data-stu-id="d3192-303">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="d3192-304">連接至控制項的資料</span><span class="sxs-lookup"><span data-stu-id="d3192-304">Connect data to controls</span></span>

<span data-ttu-id="d3192-305">接下來，您要在其中加入程式碼，以擷取名稱上選取 **`ExpenseItHome`** 頁面上，並將它傳遞給建構函式**ExpenseReportPage**。</span><span class="sxs-lookup"><span data-stu-id="d3192-305">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="d3192-306">**ExpenseReportPage**設定其資料內容，與傳遞的項目，它是由控制項的定義中*ExpenseReportPage.xaml*繫結至。</span><span class="sxs-lookup"><span data-stu-id="d3192-306">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="d3192-307">開啟 *ExpenseReportPage.xaml.vb* 或 *ExpenseReportPage.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="d3192-307">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="d3192-308">加入一個可接受物件的建構函式，如此您就可以傳遞選取之人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="d3192-308">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="d3192-309">開啟 *`ExpenseItHome.xaml.vb`* 或是 *`ExpenseItHome.xaml.cs`* 。</span><span class="sxs-lookup"><span data-stu-id="d3192-309">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="d3192-310">變更<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式呼叫新的建構函式傳遞所選人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="d3192-310">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="d3192-311">樣式的資料，使用資料範本</span><span class="sxs-lookup"><span data-stu-id="d3192-311">Style data with data templates</span></span>

<span data-ttu-id="d3192-312">在本節中，您將使用資料範本更新的 UI 資料繫結清單中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="d3192-312">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="d3192-313">開啟 *ExpenseReportPage.xaml*。</span><span class="sxs-lookup"><span data-stu-id="d3192-313">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="d3192-314">「 名稱 」 和 「 部門 」 的內容繫結<xref:System.Windows.Controls.Label>項目至適當的資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="d3192-314">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="d3192-315">如需有關資料繫結的詳細資訊，請參閱 <<c0> [ 資料繫結概觀](../data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d3192-315">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="d3192-316">在開啟之後<xref:System.Windows.Controls.Grid>項目，新增下列資料範本，定義顯示費用報表資料的方式：</span><span class="sxs-lookup"><span data-stu-id="d3192-316">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="d3192-317">取代<xref:System.Windows.Controls.DataGridTextColumn>項目<xref:System.Windows.Controls.DataGridTemplateColumn>下方<xref:System.Windows.Controls.DataGrid>項目並將範本套用至它們。</span><span class="sxs-lookup"><span data-stu-id="d3192-317">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="d3192-318">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d3192-318">Build and run the application.</span></span>

6. <span data-ttu-id="d3192-319">選取 人員，然後選取**檢視** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d3192-319">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="d3192-320">下圖顯示的兩個頁面`ExpenseIt`應用程式與控制項、 版面配置、 樣式、 資料繫結及套用資料範本：</span><span class="sxs-lookup"><span data-stu-id="d3192-320">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![ExpenseIt 範例螢幕擷取畫面](./media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="d3192-322">此範例示範 WPF 的特定功能，並不是採用像是安全性、 當地語系化和協助工具的所有最佳作法。</span><span class="sxs-lookup"><span data-stu-id="d3192-322">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="d3192-323">如的 WPF 和.NET Framework 應用程式開發的最佳做法的完整涵蓋範圍，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d3192-323">For comprehensive coverage of WPF and the .NET Framework application development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="d3192-324">協助工具選項</span><span class="sxs-lookup"><span data-stu-id="d3192-324">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="d3192-325">安全性</span><span class="sxs-lookup"><span data-stu-id="d3192-325">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="d3192-326">WPF 全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="d3192-326">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="d3192-327">WPF 效能</span><span class="sxs-lookup"><span data-stu-id="d3192-327">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="d3192-328">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d3192-328">Next steps</span></span>

<span data-ttu-id="d3192-329">在本逐步解說，您學到一些技巧可以用於建立使用 Windows Presentation Foundation (WPF) UI 的內容。</span><span class="sxs-lookup"><span data-stu-id="d3192-329">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="d3192-330">您現在應該有基本的了解資料繫結的.NET Framework 應用程式的建置組塊。</span><span class="sxs-lookup"><span data-stu-id="d3192-330">You should now have a basic understanding of the building blocks of a data-bound, .NET Framework application.</span></span> <span data-ttu-id="d3192-331">如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d3192-331">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="d3192-332">WPF 架構</span><span class="sxs-lookup"><span data-stu-id="d3192-332">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="d3192-333">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="d3192-333">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="d3192-334">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="d3192-334">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="d3192-335">版面配置</span><span class="sxs-lookup"><span data-stu-id="d3192-335">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="d3192-336">如需建立應用程式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="d3192-336">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="d3192-337">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="d3192-337">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="d3192-338">控制項</span><span class="sxs-lookup"><span data-stu-id="d3192-338">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="d3192-339">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="d3192-339">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="d3192-340">圖形和多媒體</span><span class="sxs-lookup"><span data-stu-id="d3192-340">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="d3192-341">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="d3192-341">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="d3192-342">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3192-342">See also</span></span>

- [<span data-ttu-id="d3192-343">面板概觀</span><span class="sxs-lookup"><span data-stu-id="d3192-343">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="d3192-344">資料範本化概觀</span><span class="sxs-lookup"><span data-stu-id="d3192-344">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="d3192-345">建置 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="d3192-345">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="d3192-346">樣式和範本</span><span class="sxs-lookup"><span data-stu-id="d3192-346">Styles and templates</span></span>](../controls/styles-and-templates.md)
