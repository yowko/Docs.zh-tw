---
title: 在 Visual Studio 2019 - .NET 框架中創建您的第一個 WPF 應用
titleSuffix: ''
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
ms.openlocfilehash: 65b6fe31e86380162e90820c2cf118a9d1b96b4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186591"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="4b994-102">教程：在 Visual Studio 2019 中創建您的第一個 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="4b994-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="4b994-103">本文介紹如何開發 Windows 演示文稿基礎 （WPF） 桌面應用程式，該應用程式包含大多數 WPF 應用程式共有的元素：可擴展的應用程式標記語言 （XAML） 標記、代碼後面、應用程式定義、控制項、佈局、資料繫結和樣式。</span><span class="sxs-lookup"><span data-stu-id="4b994-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="4b994-104">要開發該應用程式，您將使用視覺化工作室。</span><span class="sxs-lookup"><span data-stu-id="4b994-104">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="4b994-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="4b994-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4b994-106">創建 WPF 專案。</span><span class="sxs-lookup"><span data-stu-id="4b994-106">Create a WPF project.</span></span>
> - <span data-ttu-id="4b994-107">使用 XAML 設計應用程式的使用者介面 （UI） 的外觀。</span><span class="sxs-lookup"><span data-stu-id="4b994-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="4b994-108">編寫代碼以生成應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="4b994-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="4b994-109">創建應用程式定義來管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b994-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="4b994-110">添加控制項並創建佈局以組成應用程式 UI。</span><span class="sxs-lookup"><span data-stu-id="4b994-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="4b994-111">在整個應用程式的 UI 中創建一致外觀的樣式。</span><span class="sxs-lookup"><span data-stu-id="4b994-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="4b994-112">將 UI 綁定到資料，以便從資料中填充 UI 並保持資料和 UI 同步。</span><span class="sxs-lookup"><span data-stu-id="4b994-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="4b994-113">在本教程結束時，您將構建一個獨立的 Windows 應用程式，允許使用者查看所選人員的費用報告。</span><span class="sxs-lookup"><span data-stu-id="4b994-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="4b994-114">該應用程式由託管在瀏覽器樣式視窗中的多個 WPF 頁面組成。</span><span class="sxs-lookup"><span data-stu-id="4b994-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="4b994-115">本教程中使用的示例代碼可用於[教程 WPF 應用示例代碼](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)中的 Visual Basic 和 C#。</span><span class="sxs-lookup"><span data-stu-id="4b994-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="4b994-116">您可以使用此頁面頂部的語言選擇器在 C# 和 Visual Basic 之間切換示例代碼的代碼語言。</span><span class="sxs-lookup"><span data-stu-id="4b994-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b994-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="4b994-117">Prerequisites</span></span>

- <span data-ttu-id="4b994-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)安裝 **.NET 桌面開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="4b994-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="4b994-119">有關安裝最新版本的視覺化工作室的詳細資訊，請參閱[安裝視覺化工作室](/visualstudio/install/install-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="4b994-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="4b994-120">創建應用程式專案</span><span class="sxs-lookup"><span data-stu-id="4b994-120">Create the application project</span></span>

<span data-ttu-id="4b994-121">第一步是創建應用程式基礎結構，其中包括應用程式定義、兩頁和一個映射。</span><span class="sxs-lookup"><span data-stu-id="4b994-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="4b994-122">在名為**`ExpenseIt`**"可視基本"或"視覺化 C#的視覺化 C# 中創建新的 WPF 應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="4b994-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="4b994-123">打開視覺化工作室，在"**開始"** 功能表下選擇 **"創建新專案**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="4b994-124">將打開"**創建新專案**"對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b994-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="4b994-125">在 **"語言**"下拉清單中，選擇**C#** 或**視覺化基本**。</span><span class="sxs-lookup"><span data-stu-id="4b994-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="4b994-126">選擇**WPF 應用 （.NET 框架）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![創建新專案對話方塊](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="4b994-128">將打開"**配置新專案**"對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b994-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="4b994-129">輸入專案名稱**`ExpenseIt`**，然後選擇 **"創建**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![配置新專案對話方塊](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="4b994-131">Visual Studio 創建專案並打開名為**MainWindow.xaml**的預設應用程式視窗的設計器。</span><span class="sxs-lookup"><span data-stu-id="4b994-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="4b994-132">打開*應用程式.xaml（* 視覺基本）或*App.xaml* （C#）。</span><span class="sxs-lookup"><span data-stu-id="4b994-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="4b994-133">此 XAML 檔定義 WPF 應用程式和任何應用程式資源。</span><span class="sxs-lookup"><span data-stu-id="4b994-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="4b994-134">您還可以使用此檔指定 UI，在本例中*為 MainWindow.xaml，* 在應用程式啟動時自動顯示。</span><span class="sxs-lookup"><span data-stu-id="4b994-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="4b994-135">您的 XAML 在視覺化基礎知識中應如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b994-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="4b994-136">和以下 C#：</span><span class="sxs-lookup"><span data-stu-id="4b994-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="4b994-137">打開*主視窗.xaml*。</span><span class="sxs-lookup"><span data-stu-id="4b994-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="4b994-138">此 XAML 檔是應用程式的主視窗，並顯示在頁面中創建的內容。</span><span class="sxs-lookup"><span data-stu-id="4b994-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="4b994-139">類<xref:System.Windows.Window>定義視窗的屬性，如其標題、大小或圖示，並處理事件，如關閉或隱藏。</span><span class="sxs-lookup"><span data-stu-id="4b994-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="4b994-140">將<xref:System.Windows.Window>元素更改為 ，<xref:System.Windows.Navigation.NavigationWindow>如以下 XAML 所示：</span><span class="sxs-lookup"><span data-stu-id="4b994-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="4b994-141">此應用根據使用者輸入導航到不同的內容。</span><span class="sxs-lookup"><span data-stu-id="4b994-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="4b994-142">這就是為什麼需要將主要<xref:System.Windows.Window>需要更改為 。 <xref:System.Windows.Navigation.NavigationWindow></span><span class="sxs-lookup"><span data-stu-id="4b994-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="4b994-143"><xref:System.Windows.Navigation.NavigationWindow>繼承<xref:System.Windows.Window>的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="4b994-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="4b994-144">XAML<xref:System.Windows.Navigation.NavigationWindow>檔中的元素創建類的<xref:System.Windows.Navigation.NavigationWindow>實例。</span><span class="sxs-lookup"><span data-stu-id="4b994-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="4b994-145">有關詳細資訊，請參閱[導航概述](../app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4b994-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="4b994-146">從<xref:System.Windows.Navigation.NavigationWindow>標記<xref:System.Windows.Controls.Grid>之間刪除元素。</span><span class="sxs-lookup"><span data-stu-id="4b994-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="4b994-147">更改<xref:System.Windows.Navigation.NavigationWindow>元素的 XAML 代碼中的以下屬性：</span><span class="sxs-lookup"><span data-stu-id="4b994-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="4b994-148">將<xref:System.Windows.Window.Title%2A>屬性設置為""。`ExpenseIt`</span><span class="sxs-lookup"><span data-stu-id="4b994-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="4b994-149">將<xref:System.Windows.FrameworkElement.Height%2A>屬性設置為 350 圖元。</span><span class="sxs-lookup"><span data-stu-id="4b994-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="4b994-150">將<xref:System.Windows.FrameworkElement.Width%2A>屬性設置為 500 圖元。</span><span class="sxs-lookup"><span data-stu-id="4b994-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="4b994-151">對於視覺化基本版，您的 XAML 應如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b994-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="4b994-152">與以下 C# 類似：</span><span class="sxs-lookup"><span data-stu-id="4b994-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="4b994-153">打開*主視窗.xaml.vb*或*MainWindow.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="4b994-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="4b994-154">此檔是一個代碼背後的檔，其中包含用於處理*MainWindow.xaml*中聲明的事件的代碼。</span><span class="sxs-lookup"><span data-stu-id="4b994-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="4b994-155">這個檔案包含 XAML 中定義之視窗的部分類別。</span><span class="sxs-lookup"><span data-stu-id="4b994-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="4b994-156">如果使用 C#，則更改從 派生`MainWindow`的<xref:System.Windows.Navigation.NavigationWindow>類。</span><span class="sxs-lookup"><span data-stu-id="4b994-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="4b994-157">（在視覺化基本版中，當您在 XAML 中更改視窗時，會自動發生這種情況。您的 C# 代碼現在應如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b994-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="4b994-158">將檔添加到應用程式</span><span class="sxs-lookup"><span data-stu-id="4b994-158">Add files to the application</span></span>

<span data-ttu-id="4b994-159">在本節中，您要在應用程式中加入兩頁網頁和一個影像。</span><span class="sxs-lookup"><span data-stu-id="4b994-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="4b994-160">向專案添加新頁面，並命名為*`ExpenseItHome.xaml`*：</span><span class="sxs-lookup"><span data-stu-id="4b994-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="4b994-161">在**解決方案資源管理器\*\*\*\*`ExpenseIt`** 中，按右鍵專案節點並選擇 **"添加** > **頁面**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="4b994-162">在"**添加新專案"** 對話方塊中，已選擇**頁面 （WPF）** 範本。</span><span class="sxs-lookup"><span data-stu-id="4b994-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="4b994-163">輸入名稱**`ExpenseItHome`**，然後選擇 **"添加**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="4b994-164">此頁是應用程式啟動時顯示的第一頁。</span><span class="sxs-lookup"><span data-stu-id="4b994-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="4b994-165">它將顯示要從中選擇的人員清單，以顯示其支出報表。</span><span class="sxs-lookup"><span data-stu-id="4b994-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="4b994-166">打開*`ExpenseItHome.xaml`*。</span><span class="sxs-lookup"><span data-stu-id="4b994-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="4b994-167">將<xref:System.Windows.Controls.Page.Title%2A>設置為""。`ExpenseIt - Home`</span><span class="sxs-lookup"><span data-stu-id="4b994-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="4b994-168">將`DesignHeight`設置為 350 圖元，`DesignWidth`將 設置為 500 圖元。</span><span class="sxs-lookup"><span data-stu-id="4b994-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="4b994-169">XAML 現在顯示如下視覺基礎：</span><span class="sxs-lookup"><span data-stu-id="4b994-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="4b994-170">與以下 C# 類似：</span><span class="sxs-lookup"><span data-stu-id="4b994-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="4b994-171">打開*主視窗.xaml*。</span><span class="sxs-lookup"><span data-stu-id="4b994-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="4b994-172">將屬性<xref:System.Windows.Navigation.NavigationWindow.Source%2A>添加到元素並將其<xref:System.Windows.Navigation.NavigationWindow>設置為""。`ExpenseItHome.xaml`</span><span class="sxs-lookup"><span data-stu-id="4b994-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="4b994-173">這將集*`ExpenseItHome.xaml`* 為應用程式啟動時打開的第一頁。</span><span class="sxs-lookup"><span data-stu-id="4b994-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="4b994-174">視覺化基礎知識中的 XAML 示例：</span><span class="sxs-lookup"><span data-stu-id="4b994-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="4b994-175">在 C# 中：</span><span class="sxs-lookup"><span data-stu-id="4b994-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="4b994-176">您還可以在 **"屬性"** 視窗的 **"雜項**"類別中設置 **"源**"屬性。</span><span class="sxs-lookup"><span data-stu-id="4b994-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![屬性視窗中的源屬性](./media/properties-source.png)

1. <span data-ttu-id="4b994-178">向專案添加另一個新 WPF 頁面，並將其命名為 *"費用報告頁.xaml：：*</span><span class="sxs-lookup"><span data-stu-id="4b994-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="4b994-179">在**解決方案資源管理器\*\*\*\*`ExpenseIt`** 中，按右鍵專案節點並選擇 **"添加** > **頁面**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="4b994-180">在"**添加新專案"** 對話方塊中，選擇**頁面 （WPF）** 範本。</span><span class="sxs-lookup"><span data-stu-id="4b994-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="4b994-181">輸入名稱 **"支出報告頁**"，然後選擇 **"添加**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="4b994-182">此頁將顯示**`ExpenseItHome`** 頁面上所選人員的費用報表。</span><span class="sxs-lookup"><span data-stu-id="4b994-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="4b994-183">打開*費用報告頁.xaml*。</span><span class="sxs-lookup"><span data-stu-id="4b994-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="4b994-184">將<xref:System.Windows.Controls.Page.Title%2A>設置為""。`ExpenseIt - View Expense`</span><span class="sxs-lookup"><span data-stu-id="4b994-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="4b994-185">將`DesignHeight`設置為 350 圖元，`DesignWidth`將 設置為 500 圖元。</span><span class="sxs-lookup"><span data-stu-id="4b994-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="4b994-186">*支出報告頁.xaml*現在在視覺化基礎知識中如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b994-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="4b994-187">和以下 C#：</span><span class="sxs-lookup"><span data-stu-id="4b994-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="4b994-188">打開*費用它Home.xaml.vb*和*費用報告頁.xaml.vb，* 或*ExpenseItHome.xaml.cs*和*ExpenseReportPage.xaml.cs。*</span><span class="sxs-lookup"><span data-stu-id="4b994-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="4b994-189">創建新的 Page 檔時，Visual Studio 會自動創建其*代碼背後的*檔。</span><span class="sxs-lookup"><span data-stu-id="4b994-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="4b994-190">這些程式碼後置檔案會處理用於回應使用者輸入的邏輯。</span><span class="sxs-lookup"><span data-stu-id="4b994-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="4b994-191">對於 ： 的代碼應如下所示**`ExpenseItHome`**：</span><span class="sxs-lookup"><span data-stu-id="4b994-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="4b994-192">和下面的**費用報告頁**：</span><span class="sxs-lookup"><span data-stu-id="4b994-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="4b994-193">向專案添加名為*浮水印.png*的圖像。</span><span class="sxs-lookup"><span data-stu-id="4b994-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="4b994-194">您可以創建自己的映射、從示例代碼複製檔或從[Microsoft/WPF-示例](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)GitHub 存儲庫獲取該檔。</span><span class="sxs-lookup"><span data-stu-id="4b994-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="4b994-195">按右鍵專案節點並選擇"**添加** > **現有專案**"，或按 **"移動**+**Alt**+**A**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="4b994-196">在"**添加現有專案"** 對話方塊中，將檔篩選器設置為 **"所有檔**"或 **"影像檔**"，流覽到要使用的影像檔，然後選擇"**添加**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="4b994-197">建置並執行應用程式</span><span class="sxs-lookup"><span data-stu-id="4b994-197">Build and run the application</span></span>

1. <span data-ttu-id="4b994-198">要生成和運行應用程式，請按**F5**或從**調試**功能表中選擇 **"開始調試**"。</span><span class="sxs-lookup"><span data-stu-id="4b994-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="4b994-199">下圖顯示了帶有<xref:System.Windows.Navigation.NavigationWindow>按鈕的應用程式：</span><span class="sxs-lookup"><span data-stu-id="4b994-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![生成並運行應用程式後。](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="4b994-201">關閉應用程式以返回到視覺化工作室。</span><span class="sxs-lookup"><span data-stu-id="4b994-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="4b994-202">創建佈局</span><span class="sxs-lookup"><span data-stu-id="4b994-202">Create the layout</span></span>

<span data-ttu-id="4b994-203">佈局提供了放置 UI 元素的有序方式，並在調整 UI 大小時管理這些元素的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="4b994-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="4b994-204">您通常會建立具有下列其中一個版面配置控制項的版面配置：</span><span class="sxs-lookup"><span data-stu-id="4b994-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="4b994-205"><xref:System.Windows.Controls.Canvas>- 定義一個區域，您可以在其中使用與"畫布"區域相關的座標顯式定位子項目。</span><span class="sxs-lookup"><span data-stu-id="4b994-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="4b994-206"><xref:System.Windows.Controls.DockPanel>- 定義一個區域，您可以在其中水準或垂直排列子項目，彼此相對。</span><span class="sxs-lookup"><span data-stu-id="4b994-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="4b994-207"><xref:System.Windows.Controls.Grid>- 定義由列和行組成的靈活網格區域。</span><span class="sxs-lookup"><span data-stu-id="4b994-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="4b994-208"><xref:System.Windows.Controls.StackPanel>- 將子項目排列成一條可以水準或垂直方向的直線。</span><span class="sxs-lookup"><span data-stu-id="4b994-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="4b994-209"><xref:System.Windows.Controls.VirtualizingStackPanel>- 在水準或垂直方向的一條線上排列和虛擬化內容。</span><span class="sxs-lookup"><span data-stu-id="4b994-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="4b994-210"><xref:System.Windows.Controls.WrapPanel>- 將子項目從左向右定位在順序位置，將內容分解到包含框邊緣的下一行。</span><span class="sxs-lookup"><span data-stu-id="4b994-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="4b994-211">後續排序按順序從上到下或從右向左進行，具體取決於方向屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4b994-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="4b994-212">每個佈局控制項都支援其子項目的特定類型的佈局。</span><span class="sxs-lookup"><span data-stu-id="4b994-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="4b994-213">`ExpenseIt`頁面可以調整大小，並且每個頁面都有與其他元素一起水準和垂直排列的元素。</span><span class="sxs-lookup"><span data-stu-id="4b994-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="4b994-214">在此示例中，<xref:System.Windows.Controls.Grid>用作應用程式的佈局元素。</span><span class="sxs-lookup"><span data-stu-id="4b994-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="4b994-215">有關<xref:System.Windows.Controls.Panel>元素的詳細資訊，請參閱[面板概述](../controls/panels-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4b994-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="4b994-216">有關佈局的詳細資訊，請參閱[佈局](../advanced/layout.md)。</span><span class="sxs-lookup"><span data-stu-id="4b994-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="4b994-217">在本節中，通過將列和行定義添加到 in，<xref:System.Windows.Controls.Grid>*`ExpenseItHome.xaml`* 可以創建包含三行和 10 圖元邊距的單清單。</span><span class="sxs-lookup"><span data-stu-id="4b994-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="4b994-218">在*`ExpenseItHome.xaml`* 中，<xref:System.Windows.FrameworkElement.Margin%2A>將元素的屬性<xref:System.Windows.Controls.Grid>設置為"10，0，10，10"，對應于左、上、右和下邊距：</span><span class="sxs-lookup"><span data-stu-id="4b994-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="4b994-219">您還可以在"**屬性**"視窗中的 **"佈局"** 類別下設置 **"邊距**"值：</span><span class="sxs-lookup"><span data-stu-id="4b994-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![屬性視窗中的邊距值](./media/properties-margin.png)

2. <span data-ttu-id="4b994-221">在<xref:System.Windows.Controls.Grid>標記之間添加以下 XAML 以創建行和列定義：</span><span class="sxs-lookup"><span data-stu-id="4b994-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="4b994-222">兩<xref:System.Windows.Controls.RowDefinition.Height%2A>行的 設置為<xref:System.Windows.GridLength.Auto%2A>，這意味著行的大小基於行中的內容。</span><span class="sxs-lookup"><span data-stu-id="4b994-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="4b994-223">預設值<xref:System.Windows.Controls.RowDefinition.Height%2A>為<xref:System.Windows.GridUnitType.Star>大小調整，這意味著行高度是可用空間的加權比例。</span><span class="sxs-lookup"><span data-stu-id="4b994-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="4b994-224">例如，如果兩行各有一個<xref:System.Windows.Controls.RowDefinition.Height%2A>"\*"，則它們每個行的高度是可用空間的一半。</span><span class="sxs-lookup"><span data-stu-id="4b994-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="4b994-225">您<xref:System.Windows.Controls.Grid>現在應該包含以下 XAML：</span><span class="sxs-lookup"><span data-stu-id="4b994-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="4b994-226">新增控制項</span><span class="sxs-lookup"><span data-stu-id="4b994-226">Add controls</span></span>

<span data-ttu-id="4b994-227">在本節中，您將更新主頁 UI 以顯示人員清單，其中選擇一個人來顯示其支出報表。</span><span class="sxs-lookup"><span data-stu-id="4b994-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="4b994-228">控制項是可讓使用者與您應用程式互動的 UI 物件。</span><span class="sxs-lookup"><span data-stu-id="4b994-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="4b994-229">有關詳細資訊，請參閱[控制項](../controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4b994-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="4b994-230">要創建此 UI，您將將以下元素添加到*`ExpenseItHome.xaml`*：</span><span class="sxs-lookup"><span data-stu-id="4b994-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="4b994-231">A（<xref:System.Windows.Controls.ListBox>用於人員清單）。</span><span class="sxs-lookup"><span data-stu-id="4b994-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="4b994-232">A（<xref:System.Windows.Controls.Label>對於清單標頭）。</span><span class="sxs-lookup"><span data-stu-id="4b994-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="4b994-233">（<xref:System.Windows.Controls.Button>按一下以查看清單中所選人員的支出報表）。</span><span class="sxs-lookup"><span data-stu-id="4b994-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="4b994-234">通過設置附加屬性，將每個控制項放置在<xref:System.Windows.Controls.Grid>的一<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>行中。</span><span class="sxs-lookup"><span data-stu-id="4b994-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="4b994-235">有關附加屬性的詳細資訊，請參閱[附加屬性概述](../advanced/attached-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4b994-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="4b994-236">在*`ExpenseItHome.xaml`* 中，在<xref:System.Windows.Controls.Grid>標記之間添加以下 XAML：</span><span class="sxs-lookup"><span data-stu-id="4b994-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="4b994-237">還可以通過將控制項從 **"工具箱"** 視窗拖動到設計視窗，然後在 **"屬性"** 視窗中設置其屬性來創建控制項。</span><span class="sxs-lookup"><span data-stu-id="4b994-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="4b994-238">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b994-238">Build and run the application.</span></span>

    <span data-ttu-id="4b994-239">下圖顯示了您創建的控制項：</span><span class="sxs-lookup"><span data-stu-id="4b994-239">The following illustration shows the controls you created:</span></span>

![支出它示例螢幕截圖顯示名稱清單](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="4b994-241">添加圖像和標題</span><span class="sxs-lookup"><span data-stu-id="4b994-241">Add an image and a title</span></span>

<span data-ttu-id="4b994-242">在本節中，您將使用圖像和頁面標題更新主頁 UI。</span><span class="sxs-lookup"><span data-stu-id="4b994-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="4b994-243">在*`ExpenseItHome.xaml`* 中，將另一<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>列添加到固定<xref:System.Windows.Controls.ColumnDefinition.Width%2A>為 230 圖元的 列：</span><span class="sxs-lookup"><span data-stu-id="4b994-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="4b994-244">向 添加<xref:System.Windows.Controls.Grid.RowDefinitions%2A>另一行，共四行：</span><span class="sxs-lookup"><span data-stu-id="4b994-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="4b994-245">通過將<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>屬性設置為三個控制項（邊框、ListBox 和 Button）中每個控制項中的 1，將控制項移動到第二列。</span><span class="sxs-lookup"><span data-stu-id="4b994-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="4b994-246">將每個控制項向下移動一行，將<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>三個控制項（邊框、ListBox 和 Button）和"邊框"元素的值分別增加 1。</span><span class="sxs-lookup"><span data-stu-id="4b994-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="4b994-247">三個控制項的 XAML 現在如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b994-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="4b994-248">通過將以下<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>XAML 添加到 和`<Grid>``</Grid>`標記之間的任意位置，將屬性設置為*浮水印.png*影像檔：</span><span class="sxs-lookup"><span data-stu-id="4b994-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="4b994-249">在元素<xref:System.Windows.Controls.Border>之前，添加包含<xref:System.Windows.Controls.Label>內容"查看支出報表"的 。</span><span class="sxs-lookup"><span data-stu-id="4b994-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="4b994-250">此標籤是頁面的標題。</span><span class="sxs-lookup"><span data-stu-id="4b994-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="4b994-251">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b994-251">Build and run the application.</span></span>

<span data-ttu-id="4b994-252">下圖顯示了您剛剛添加的內容的結果：</span><span class="sxs-lookup"><span data-stu-id="4b994-252">The following illustration shows the results of what you just added:</span></span>

![費用它示例螢幕截圖，顯示新的圖像背景和頁面標題](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="4b994-254">添加代碼以處理事件</span><span class="sxs-lookup"><span data-stu-id="4b994-254">Add code to handle events</span></span>

1. <span data-ttu-id="4b994-255">在*`ExpenseItHome.xaml`* 中，<xref:System.Windows.Controls.Primitives.ButtonBase.Click>向<xref:System.Windows.Controls.Button>元素添加事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4b994-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="4b994-256">有關詳細資訊，請參閱[操作：創建一個簡單的事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="4b994-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="4b994-257">打開*`ExpenseItHome.xaml.vb`* 或*`ExpenseItHome.xaml.cs`*。</span><span class="sxs-lookup"><span data-stu-id="4b994-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="4b994-258">將以下代碼添加到類以`ExpenseItHome`添加按鈕按一下事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4b994-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="4b994-259">事件處理常式將打開 **"支出報告頁"** 頁。</span><span class="sxs-lookup"><span data-stu-id="4b994-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="4b994-260">為支出報表頁創建 UI</span><span class="sxs-lookup"><span data-stu-id="4b994-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="4b994-261">*支出報告Page.xaml*顯示**`ExpenseItHome`** 頁面上所選人員的費用報表。</span><span class="sxs-lookup"><span data-stu-id="4b994-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="4b994-262">在本節中，您將為**支出報表頁**創建 UI。</span><span class="sxs-lookup"><span data-stu-id="4b994-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="4b994-263">您還將向各種 UI 元素添加背景和填充顏色。</span><span class="sxs-lookup"><span data-stu-id="4b994-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="4b994-264">打開*費用報告頁.xaml*。</span><span class="sxs-lookup"><span data-stu-id="4b994-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="4b994-265">在<xref:System.Windows.Controls.Grid>標記之間添加以下 XAML：</span><span class="sxs-lookup"><span data-stu-id="4b994-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="4b994-266">此 UI 與*`ExpenseItHome.xaml`* 類似，但報表資料顯示在 中<xref:System.Windows.Controls.DataGrid>。</span><span class="sxs-lookup"><span data-stu-id="4b994-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="4b994-267">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b994-267">Build and run the application.</span></span>

4. <span data-ttu-id="4b994-268">選擇 **"查看**"按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b994-268">Select the **View** button.</span></span>

    <span data-ttu-id="4b994-269">報表頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="4b994-269">The expense report page appears.</span></span> <span data-ttu-id="4b994-270">另請注意，後退導覽按鈕已啟用。</span><span class="sxs-lookup"><span data-stu-id="4b994-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="4b994-271">下圖顯示了添加到*支出報表Page.xaml*的 UI 元素。</span><span class="sxs-lookup"><span data-stu-id="4b994-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![支出它示例螢幕截圖，顯示剛剛為支出報告頁創建的 UI。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="4b994-273">樣式控制項</span><span class="sxs-lookup"><span data-stu-id="4b994-273">Style controls</span></span>

<span data-ttu-id="4b994-274">對於 UI 中相同類型的所有元素，各種元素的外觀通常相同。</span><span class="sxs-lookup"><span data-stu-id="4b994-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="4b994-275">UI 使用[樣式](../controls/styling-and-templating.md)使外觀可跨多個元素重用。</span><span class="sxs-lookup"><span data-stu-id="4b994-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="4b994-276">樣式的再使用性有助於簡化 XAML 的創建和管理。</span><span class="sxs-lookup"><span data-stu-id="4b994-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="4b994-277">本節會將先前步驟中定義的個別元素屬性 (Attribute) 取代為樣式。</span><span class="sxs-lookup"><span data-stu-id="4b994-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="4b994-278">打開*應用程式.xaml*或*App.xaml*。</span><span class="sxs-lookup"><span data-stu-id="4b994-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="4b994-279">在<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>標記之間添加以下 XAML：</span><span class="sxs-lookup"><span data-stu-id="4b994-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="4b994-280">這個 XAML 會加入下列樣式：</span><span class="sxs-lookup"><span data-stu-id="4b994-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="4b994-281">`headerTextStyle`：格式化頁面標題 <xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="4b994-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="4b994-282">`labelStyle`：格式化 <xref:System.Windows.Controls.Label> 控制項。</span><span class="sxs-lookup"><span data-stu-id="4b994-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="4b994-283">`columnHeaderStyle`：格式化 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>。</span><span class="sxs-lookup"><span data-stu-id="4b994-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="4b994-284">`listHeaderStyle`：格式化清單標頭 <xref:System.Windows.Controls.Border> 控制項。</span><span class="sxs-lookup"><span data-stu-id="4b994-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="4b994-285">`listHeaderTextStyle`：格式化清單標頭<xref:System.Windows.Controls.Label>。</span><span class="sxs-lookup"><span data-stu-id="4b994-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="4b994-286">`buttonStyle`：格式化<xref:System.Windows.Controls.Button>on `ExpenseItHome.xaml`。</span><span class="sxs-lookup"><span data-stu-id="4b994-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="4b994-287">請注意，樣式是屬性元素的資源和子項目<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4b994-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="4b994-288">在這裡，樣式會套用至應用程式中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="4b994-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="4b994-289">有關在 .NET 應用中使用資源的示例，請參閱[使用應用程式資源](../advanced/how-to-use-application-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="4b994-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="4b994-290">在*`ExpenseItHome.xaml`* 中，將<xref:System.Windows.Controls.Grid>元素之間的所有內容替換為以下 XAML：</span><span class="sxs-lookup"><span data-stu-id="4b994-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="4b994-291">套用樣式會移除並取代諸如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 這類會定義每個控制項外觀的屬性。</span><span class="sxs-lookup"><span data-stu-id="4b994-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="4b994-292">例如，`headerTextStyle`應用於"查看費用報表"。 <xref:System.Windows.Controls.Label></span><span class="sxs-lookup"><span data-stu-id="4b994-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="4b994-293">打開*費用報告頁.xaml*。</span><span class="sxs-lookup"><span data-stu-id="4b994-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="4b994-294">將<xref:System.Windows.Controls.Grid>元素之間的所有內容替換為以下 XAML：</span><span class="sxs-lookup"><span data-stu-id="4b994-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="4b994-295">此 XAML 向<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.Border>元素添加樣式。</span><span class="sxs-lookup"><span data-stu-id="4b994-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="4b994-296">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b994-296">Build and run the application.</span></span> <span data-ttu-id="4b994-297">視窗外觀與以前相同。</span><span class="sxs-lookup"><span data-stu-id="4b994-297">The window appearance is the same as previously.</span></span>

    ![支出它示例螢幕截圖的外觀與上一節相同。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="4b994-299">關閉應用程式以返回到視覺化工作室。</span><span class="sxs-lookup"><span data-stu-id="4b994-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="4b994-300">將資料繫結到控制項</span><span class="sxs-lookup"><span data-stu-id="4b994-300">Bind data to a control</span></span>

<span data-ttu-id="4b994-301">在本節中，您將創建綁定到各種控制項的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="4b994-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="4b994-302">在*`ExpenseItHome.xaml`* 打開<xref:System.Windows.Controls.Grid>元素之後，添加以下 XAML 以創建包含每個人<xref:System.Windows.Data.XmlDataProvider>資料的 a：</span><span class="sxs-lookup"><span data-stu-id="4b994-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="4b994-303">資料作為<xref:System.Windows.Controls.Grid>資源創建。</span><span class="sxs-lookup"><span data-stu-id="4b994-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="4b994-304">通常，此資料將作為檔載入，但為了簡單起見，資料將內聯添加。</span><span class="sxs-lookup"><span data-stu-id="4b994-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="4b994-305">在`<Grid.Resources>`元素中，添加以下`<xref:System.Windows.DataTemplate>`元素，該元素定義如何在<xref:System.Windows.Controls.ListBox>`<XmlDataProvider>`元素之後在 中顯示資料：</span><span class="sxs-lookup"><span data-stu-id="4b994-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="4b994-306">有關資料範本的詳細資訊，請參閱[資料範本概述](../data/data-templating-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4b994-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="4b994-307">將現有<xref:System.Windows.Controls.ListBox>替換為以下 XAML：</span><span class="sxs-lookup"><span data-stu-id="4b994-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="4b994-308">此 XAML 將<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的屬性<xref:System.Windows.Controls.ListBox>綁定到資料來源，並將資料範本應用為 。 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A></span><span class="sxs-lookup"><span data-stu-id="4b994-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="4b994-309">將資料連線到控制項</span><span class="sxs-lookup"><span data-stu-id="4b994-309">Connect data to controls</span></span>

<span data-ttu-id="4b994-310">接下來，您將添加代碼來檢索**`ExpenseItHome`** 頁面上選擇的名稱，並將其傳遞給**費用報表頁的**建構函式。</span><span class="sxs-lookup"><span data-stu-id="4b994-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="4b994-311">**支出報告頁**將其資料上下文與傳遞的項設置，這是*支出報告頁.xaml*中定義的控制項綁定到的。</span><span class="sxs-lookup"><span data-stu-id="4b994-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="4b994-312">打開*費用報告頁.xaml.vb*或*ExpenseReportPage.xaml.cs*。</span><span class="sxs-lookup"><span data-stu-id="4b994-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="4b994-313">加入一個可接受物件的建構函式，如此您就可以傳遞選取之人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="4b994-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="4b994-314">打開*`ExpenseItHome.xaml.vb`* 或*`ExpenseItHome.xaml.cs`*。</span><span class="sxs-lookup"><span data-stu-id="4b994-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="4b994-315">更改<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式以調用新的建構函式，傳遞所選人員的費用報表資料。</span><span class="sxs-lookup"><span data-stu-id="4b994-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="4b994-316">使用資料範本對資料進行樣式設置資料</span><span class="sxs-lookup"><span data-stu-id="4b994-316">Style data with data templates</span></span>

<span data-ttu-id="4b994-317">在本節中，您將使用資料繫結清單中的每個專案更新 UI。</span><span class="sxs-lookup"><span data-stu-id="4b994-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="4b994-318">打開*費用報告頁.xaml*。</span><span class="sxs-lookup"><span data-stu-id="4b994-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="4b994-319">將"名稱"和"部門"<xref:System.Windows.Controls.Label>元素的內容綁定到相應的資料來源屬性。</span><span class="sxs-lookup"><span data-stu-id="4b994-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="4b994-320">有關資料繫結的詳細資訊，請參閱[資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4b994-320">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="4b994-321">在打開<xref:System.Windows.Controls.Grid>元素之後，添加以下資料範本，這些範本定義如何顯示支出報表資料：</span><span class="sxs-lookup"><span data-stu-id="4b994-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="4b994-322">將<xref:System.Windows.Controls.DataGridTextColumn>元素替換為元素<xref:System.Windows.Controls.DataGridTemplateColumn>，<xref:System.Windows.Controls.DataGrid>並將範本應用於它們。</span><span class="sxs-lookup"><span data-stu-id="4b994-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="4b994-323">建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4b994-323">Build and run the application.</span></span>

6. <span data-ttu-id="4b994-324">選擇人員，然後選擇 **"查看**"按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b994-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="4b994-325">下圖顯示了應用控制項、佈局、樣式`ExpenseIt`、資料繫結和資料範本的應用程式兩頁：</span><span class="sxs-lookup"><span data-stu-id="4b994-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![顯示名稱清單和支出報表的應用兩個頁面。](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="4b994-327">此示例演示了 WPF 的特定功能，並且不遵循安全、當地語系化和可訪問性等所有最佳實踐。</span><span class="sxs-lookup"><span data-stu-id="4b994-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="4b994-328">有關 WPF 和 .NET 應用開發最佳實踐的全面覆蓋，請參閱以下主題：</span><span class="sxs-lookup"><span data-stu-id="4b994-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="4b994-329">協助工具</span><span class="sxs-lookup"><span data-stu-id="4b994-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="4b994-330">安全性</span><span class="sxs-lookup"><span data-stu-id="4b994-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="4b994-331">WPF 全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="4b994-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="4b994-332">WPF 性能</span><span class="sxs-lookup"><span data-stu-id="4b994-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="4b994-333">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4b994-333">Next steps</span></span>

<span data-ttu-id="4b994-334">在本演練中，您學習了使用 Windows 演示文稿基礎 （WPF） 創建 UI 的多種技術。</span><span class="sxs-lookup"><span data-stu-id="4b994-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="4b994-335">現在，您應該對資料繫結 .NET 應用的構建基塊有基本的瞭解。</span><span class="sxs-lookup"><span data-stu-id="4b994-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="4b994-336">如需 WPF 架構和程式設計模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="4b994-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="4b994-337">WPF 架構</span><span class="sxs-lookup"><span data-stu-id="4b994-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="4b994-338">XAML 概述 （WPF）</span><span class="sxs-lookup"><span data-stu-id="4b994-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="4b994-339">依賴項屬性概述</span><span class="sxs-lookup"><span data-stu-id="4b994-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="4b994-340">版面配置</span><span class="sxs-lookup"><span data-stu-id="4b994-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="4b994-341">如需建立應用程式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="4b994-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="4b994-342">應用程式開發</span><span class="sxs-lookup"><span data-stu-id="4b994-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="4b994-343">控制</span><span class="sxs-lookup"><span data-stu-id="4b994-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="4b994-344">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="4b994-344">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4b994-345">圖形與多媒體</span><span class="sxs-lookup"><span data-stu-id="4b994-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="4b994-346">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="4b994-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="4b994-347">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b994-347">See also</span></span>

- [<span data-ttu-id="4b994-348">面板概述</span><span class="sxs-lookup"><span data-stu-id="4b994-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="4b994-349">資料範本概述</span><span class="sxs-lookup"><span data-stu-id="4b994-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="4b994-350">構建 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="4b994-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="4b994-351">樣式和範本</span><span class="sxs-lookup"><span data-stu-id="4b994-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
