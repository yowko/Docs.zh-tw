---
title: LINQ to XML 資料系結範例
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920934"
---
# <a name="linq-to-xml-data-binding-sample"></a><span data-ttu-id="0dc07-102">LINQ to XML 資料系結範例</span><span class="sxs-lookup"><span data-stu-id="0dc07-102">LINQ to XML data binding sample</span></span>

<span data-ttu-id="0dc07-103">本文描述 LinqToXmlDataBinding 範例，這是將使用者介面元件系結至內嵌 XML 資料來源的 Windows Presentation Foundation （WPF）應用程式。</span><span class="sxs-lookup"><span data-stu-id="0dc07-103">This article describes the LinqToXmlDataBinding sample, a Windows Presentation Foundation (WPF) app that binds user interface components to an embedded XML data source.</span></span>

## <a name="overview"></a><span data-ttu-id="0dc07-104">總覽</span><span class="sxs-lookup"><span data-stu-id="0dc07-104">Overview</span></span>

<span data-ttu-id="0dc07-105">LinqToXmlDataBinding 範例是包含C#和 XAML 原始程式檔的 WINDOWS PRESENTATION FOUNDATION （WPF）應用程式。</span><span class="sxs-lookup"><span data-stu-id="0dc07-105">The LinqToXmlDataBinding sample is a Windows Presentation Foundation (WPF) app that contains C# and XAML source files.</span></span> <span data-ttu-id="0dc07-106">內嵌的 XML 檔會定義書籍的清單。</span><span class="sxs-lookup"><span data-stu-id="0dc07-106">An embedded XML document defines a list of books.</span></span> <span data-ttu-id="0dc07-107">應用程式可讓使用者查看、新增、刪除和編輯書籍專案。</span><span class="sxs-lookup"><span data-stu-id="0dc07-107">The app enables the user to view, add, delete, and edit the book entries.</span></span>

<span data-ttu-id="0dc07-108">有兩個主要來源檔案：</span><span class="sxs-lookup"><span data-stu-id="0dc07-108">There are two primary source files:</span></span>

- <span data-ttu-id="0dc07-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) 包含適用於主視窗之使用者介面 (UI) 的 XAML 宣告程式碼。</span><span class="sxs-lookup"><span data-stu-id="0dc07-109">[L2DBForm.xaml](l2dbform-xaml-source-code.md) contains the XAML declaration code for the user interface (UI) of the main window.</span></span> <span data-ttu-id="0dc07-110">它也包含一個視窗資源區段，其中定義了書籍清單的資料提供者和內嵌的 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="0dc07-110">It also contains a window resource section that defines a data provider and an embedded XML document for the book listings.</span></span>

- <span data-ttu-id="0dc07-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) 包含與 UI 建立關聯的初始化與事件處理方法。</span><span class="sxs-lookup"><span data-stu-id="0dc07-111">[L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contains the initialization and event-handling methods associated with the UI.</span></span>

<span data-ttu-id="0dc07-112">主視窗分為下列四個 UI 垂直區段：</span><span class="sxs-lookup"><span data-stu-id="0dc07-112">The main window is divided into the following four vertical UI sections:</span></span>

- <span data-ttu-id="0dc07-113">**XML**：顯示內嵌書籍清單的 XML 原始檔。</span><span class="sxs-lookup"><span data-stu-id="0dc07-113">**XML** displays the raw XML source of the embedded book listing.</span></span>

- <span data-ttu-id="0dc07-114">**書籍清單**：將書籍項目顯示為標準文字，並讓使用者選取和刪除個別的項目。</span><span class="sxs-lookup"><span data-stu-id="0dc07-114">**Book List** displays the book entries as standard text and enables the user to select and delete individual entries.</span></span>

- <span data-ttu-id="0dc07-115">**編輯選取的書籍**：可讓使用者編輯與目前所選之書籍項目相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="0dc07-115">**Edit Selected Book** enables the user to edit the values associated with the currently selected book entry.</span></span>

- <span data-ttu-id="0dc07-116">**加入新的書籍**：可根據使用者輸入的值，建立新的書籍項目。</span><span class="sxs-lookup"><span data-stu-id="0dc07-116">**Add New Book** enables the creation of a new book entry based on values entered by the user.</span></span>

## <a name="run-the-sample"></a><span data-ttu-id="0dc07-117">執行範例</span><span class="sxs-lookup"><span data-stu-id="0dc07-117">Run the sample</span></span>

<span data-ttu-id="0dc07-118">本節說明如何在 Visual Studio 中建立和建立 LinqToXmlDataBinding 專案，以及如何執行產生的 LinqToXmlDataBinding Windows Presentation Foundation （WPF）應用程式。</span><span class="sxs-lookup"><span data-stu-id="0dc07-118">This section shows how to create and build the LinqToXmlDataBinding project in Visual Studio, and how to run the resulting LinqToXmlDataBinding Windows Presentation Foundation (WPF) app.</span></span>

### <a name="create-the-project"></a><span data-ttu-id="0dc07-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="0dc07-119">Create the project</span></span>

1. <span data-ttu-id="0dc07-120">開啟 Visual Studio，然後建立名為 **LinqToXmlDataBinding** 的 C# **WPF 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0dc07-120">Open Visual Studio and create a C# **WPF App** named **LinqToXmlDataBinding**.</span></span>

   <span data-ttu-id="0dc07-121">專案應該將目標設定為 .NET Framework 3.5 (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="0dc07-121">The project should target the .NET Framework 3.5 (or later).</span></span>

1. <span data-ttu-id="0dc07-122">如果尚未存在，加入下列 .NET 組件的專案參考：</span><span class="sxs-lookup"><span data-stu-id="0dc07-122">If not already present, add project references for the following .NET assemblies:</span></span>

    - <span data-ttu-id="0dc07-123">System.Data</span><span class="sxs-lookup"><span data-stu-id="0dc07-123">System.Data</span></span>
    - <span data-ttu-id="0dc07-124">System.Data.DataSetExtensions</span><span class="sxs-lookup"><span data-stu-id="0dc07-124">System.Data.DataSetExtensions</span></span>
    - <span data-ttu-id="0dc07-125">System.Xml</span><span class="sxs-lookup"><span data-stu-id="0dc07-125">System.Xml</span></span>
    - <span data-ttu-id="0dc07-126">System.Xml</span><span class="sxs-lookup"><span data-stu-id="0dc07-126">System.Xml</span></span>

1. <span data-ttu-id="0dc07-127">按 **Ctrl**+**Shift**+**B** 來建置方案，然後按 **F5** 鍵來執行。</span><span class="sxs-lookup"><span data-stu-id="0dc07-127">Build the solution by pressing **Ctrl**+**Shift**+**B**, then run it by pressing **F5**.</span></span>

   <span data-ttu-id="0dc07-128">專案的編譯應該沒有錯誤，而且應該當做一般 WPF 應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="0dc07-128">The project should compile without errors and run as a generic WPF application.</span></span>

### <a name="add-code"></a><span data-ttu-id="0dc07-129">新增程式碼</span><span class="sxs-lookup"><span data-stu-id="0dc07-129">Add code</span></span>

1. <span data-ttu-id="0dc07-130">在 [方案總管] 中，將原始程式檔 **Window1.xaml** 重新命名為 **L2XDBForm.xaml**。</span><span class="sxs-lookup"><span data-stu-id="0dc07-130">In **Solution Explorer**, rename the source file **Window1.xaml** to **L2XDBForm.xaml**.</span></span>

   <span data-ttu-id="0dc07-131">相依的來源檔案 Window1.xaml.cs 會自動重新命名為 L2XDBForm.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="0dc07-131">The dependent source file Window1.xaml.cs is automatically renamed to L2XDBForm.xaml.cs.</span></span>

1. <span data-ttu-id="0dc07-132">以[l2dbform.xaml 程式碼](l2dbform-xaml-source-code.md)取代**l2xdbform.xaml**檔案中找到的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0dc07-132">Replace the source code found in the file **L2XDBForm.xaml** with the [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="0dc07-133">使用 XAML 原始碼檢視來使用這個檔案。</span><span class="sxs-lookup"><span data-stu-id="0dc07-133">Use the XAML source view to work with this file.</span></span>

1. <span data-ttu-id="0dc07-134">同樣地，使用[L2DBForm.xaml.cs 原始程式碼](l2dbform-xaml-cs-source-code.md)取代**L2XDBForm.xaml.cs**中的來源。</span><span class="sxs-lookup"><span data-stu-id="0dc07-134">Similarly, replace the source in **L2XDBForm.xaml.cs** with the [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

1. <span data-ttu-id="0dc07-135">在檔案**app.xaml**中，將所有出現的字串**Window1.xaml**取代為**l2xdbform.xaml**。</span><span class="sxs-lookup"><span data-stu-id="0dc07-135">In the file **App.xaml**, replace all occurrences of the string **Window1.xaml** with **L2XDBForm.xaml**.</span></span>

1. <span data-ttu-id="0dc07-136">按 **Ctrl**+**Shift**+**B** 來建置方案。</span><span class="sxs-lookup"><span data-stu-id="0dc07-136">Build the solution by pressing **Ctrl**+**Shift**+**B**.</span></span>

### <a name="run-the-app"></a><span data-ttu-id="0dc07-137">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="0dc07-137">Run the app</span></span>

<span data-ttu-id="0dc07-138">LinqToXmlDataBinding 應用程式可讓使用者查看及操作儲存為內嵌 XML 元素的書籍清單。</span><span class="sxs-lookup"><span data-stu-id="0dc07-138">The LinqToXmlDataBinding app enables the user to view and manipulate a list of books that's stored as an embedded XML element.</span></span> <span data-ttu-id="0dc07-139">按**f5** （開始偵錯工具）或**Ctrl**+**F5** （[啟動但不進行偵錯工具]）來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0dc07-139">Run the app by pressing **F5** (Start Debugging) or **Ctrl**+**F5** (Start Without Debugging).</span></span>

<span data-ttu-id="0dc07-140">標題為 [使用 LINQ to XML 進行 WPF 資料繫結] 的程式視窗隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0dc07-140">A program window with the title **WPF Data Binding using LINQ to XML** appears.</span></span>

<span data-ttu-id="0dc07-141">UI 的上方區段會顯示代表書籍清單的原始**XML** 。</span><span class="sxs-lookup"><span data-stu-id="0dc07-141">The top section of the UI displays the raw **XML** that represents the book list.</span></span> <span data-ttu-id="0dc07-142">它會使用 WPF <xref:System.Windows.Controls.TextBlock> 控制項顯示，不會透過滑鼠或鍵盤啟用互動。</span><span class="sxs-lookup"><span data-stu-id="0dc07-142">It is displayed using a WPF <xref:System.Windows.Controls.TextBlock> control, which does not enable interaction through the mouse or keyboard.</span></span>

<span data-ttu-id="0dc07-143">第二個垂直區段標示為 [書籍清單]，會將書籍顯示為純文字排序的清單。</span><span class="sxs-lookup"><span data-stu-id="0dc07-143">The second vertical section, labeled **Book List**, displays the books as a plain text ordered list.</span></span> <span data-ttu-id="0dc07-144">它使用 <xref:System.Windows.Controls.ListBox> 控制項，可透過滑鼠或鍵盤進行選取。</span><span class="sxs-lookup"><span data-stu-id="0dc07-144">It uses a <xref:System.Windows.Controls.ListBox> control that enables selection though the mouse or keyboard.</span></span>

### <a name="add-and-delete-books"></a><span data-ttu-id="0dc07-145">新增和刪除書籍</span><span class="sxs-lookup"><span data-stu-id="0dc07-145">Add and delete books</span></span>

<span data-ttu-id="0dc07-146">若要將新的書籍加入清單中，請在 [ **ID** ] 和 [**值**] 中輸入值，<xref:System.Windows.Controls.TextBox> 控制項的最後一節 [**加入新書籍**]，然後選取 [**新增書籍**]。</span><span class="sxs-lookup"><span data-stu-id="0dc07-146">To add a new book to the list, enter values into the **ID** and **Value** <xref:System.Windows.Controls.TextBox> controls in the last section, **Add New Book**, and then select **Add Book**.</span></span> <span data-ttu-id="0dc07-147">本書會附加至書籍和 XML 清單中的清單。</span><span class="sxs-lookup"><span data-stu-id="0dc07-147">The book is appended to the list in both the book and XML listings.</span></span> <span data-ttu-id="0dc07-148">這個程式不會驗證輸入值。</span><span class="sxs-lookup"><span data-stu-id="0dc07-148">This program does not validate input values.</span></span>

<span data-ttu-id="0dc07-149">若要從清單中刪除現有的書籍，請在 [**書籍清單**] 區段中選取它，然後選取 [**移除選取的書籍**]。</span><span class="sxs-lookup"><span data-stu-id="0dc07-149">To delete an existing book from the list, select it in the **Book List** section, and then select **Remove Selected Book**.</span></span> <span data-ttu-id="0dc07-150">書籍專案會從書籍和原始 XML 來源清單中移除。</span><span class="sxs-lookup"><span data-stu-id="0dc07-150">The book entry is removed from both the book and the raw XML source listings.</span></span>

### <a name="edit-a-book-entry"></a><span data-ttu-id="0dc07-151">編輯書籍專案</span><span class="sxs-lookup"><span data-stu-id="0dc07-151">Edit a book entry</span></span>

1. <span data-ttu-id="0dc07-152">在第二個 [書籍清單] 區段中選取書籍項目。</span><span class="sxs-lookup"><span data-stu-id="0dc07-152">Select the book entry in the second **Book List** section.</span></span>

   <span data-ttu-id="0dc07-153">其目前的值會顯示在 [**編輯選取的書籍**] 區段中。</span><span class="sxs-lookup"><span data-stu-id="0dc07-153">Its current values are displayed in the **Edit Selected Book** section.</span></span>

1. <span data-ttu-id="0dc07-154">使用鍵盤編輯值。</span><span class="sxs-lookup"><span data-stu-id="0dc07-154">Edit the values using the keyboard.</span></span> <span data-ttu-id="0dc07-155">一旦 <xref:System.Windows.Controls.TextBox> 控制項失去焦點，變更就會自動傳播至 XML 來源和書籍清單。</span><span class="sxs-lookup"><span data-stu-id="0dc07-155">As soon as either <xref:System.Windows.Controls.TextBox> control loses focus, changes are automatically propagated to the XML source and book listings.</span></span>
