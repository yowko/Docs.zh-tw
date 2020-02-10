---
title: 逐步解說：繫結至混合應用程式中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 0d1e66a1277e6a04d2f49ac91691160f70fb56e4
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095069"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="4d259-102">逐步解說：繫結至混合應用程式中的資料</span><span class="sxs-lookup"><span data-stu-id="4d259-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>

<span data-ttu-id="4d259-103">將資料來源系結至控制項，對於提供使用者存取基礎資料（不論是使用 Windows Forms 還是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]）而言，是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="4d259-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using Windows Forms or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="4d259-104">本逐步解說會示範如何在包含 Windows Forms 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項的混合式應用程式中使用資料系結。</span><span class="sxs-lookup"><span data-stu-id="4d259-104">This walkthrough shows how you can use data binding in hybrid applications that include both Windows Forms and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>

<span data-ttu-id="4d259-105">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="4d259-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="4d259-106">建立專案。</span><span class="sxs-lookup"><span data-stu-id="4d259-106">Creating the project.</span></span>

- <span data-ttu-id="4d259-107">定義資料範本。</span><span class="sxs-lookup"><span data-stu-id="4d259-107">Defining the data template.</span></span>

- <span data-ttu-id="4d259-108">指定表單版面配置。</span><span class="sxs-lookup"><span data-stu-id="4d259-108">Specifying the form layout.</span></span>

- <span data-ttu-id="4d259-109">指定資料繫結。</span><span class="sxs-lookup"><span data-stu-id="4d259-109">Specifying data bindings.</span></span>

- <span data-ttu-id="4d259-110">使用交互操作來顯示資料。</span><span class="sxs-lookup"><span data-stu-id="4d259-110">Displaying data by using interoperation.</span></span>

- <span data-ttu-id="4d259-111">將資料來源新增至專案。</span><span class="sxs-lookup"><span data-stu-id="4d259-111">Adding the data source to the project.</span></span>

- <span data-ttu-id="4d259-112">繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="4d259-112">Binding to the data source.</span></span>

<span data-ttu-id="4d259-113">如需本逐步解說中所述工作的完整程式代碼清單，請參閱[混合式應用程式中的資料](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFWithWFAndDatabinding)系結範例。</span><span class="sxs-lookup"><span data-stu-id="4d259-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFWithWFAndDatabinding).</span></span>

<span data-ttu-id="4d259-114">完成後，您就會了解混合應用程式中的資料繫結功能。</span><span class="sxs-lookup"><span data-stu-id="4d259-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d259-115">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4d259-115">Prerequisites</span></span>

<span data-ttu-id="4d259-116">您需要下列元件才能完成這個逐步解說：</span><span class="sxs-lookup"><span data-stu-id="4d259-116">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="4d259-117">Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="4d259-117">Visual Studio.</span></span>

- <span data-ttu-id="4d259-118">在 Microsoft SQL Server 上執行之 Northwind 範例資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="4d259-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="4d259-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="4d259-119">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="4d259-120">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="4d259-120">To create and set up the project</span></span>

1. <span data-ttu-id="4d259-121">建立名為 `WPFWithWFAndDatabinding`的 WPF 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="4d259-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>

2. <span data-ttu-id="4d259-122">在 [方案總管] 中，加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="4d259-122">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="4d259-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="4d259-123">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="4d259-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="4d259-124">System.Windows.Forms</span></span>

3. <span data-ttu-id="4d259-125">在 WPF 設計工具中開啟 Mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="4d259-125">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="4d259-126">在 <xref:System.Windows.Window> 元素中，新增下列 Windows Forms 命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="4d259-126">In the <xref:System.Windows.Window> element, add the following Windows Forms namespaces mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="4d259-127">藉由指派 <xref:System.Windows.FrameworkElement.Name%2A> 屬性來命名預設的 <xref:System.Windows.Controls.Grid> 元素 `mainGrid`。</span><span class="sxs-lookup"><span data-stu-id="4d259-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a><span data-ttu-id="4d259-128">定義資料範本</span><span class="sxs-lookup"><span data-stu-id="4d259-128">Defining the Data Template</span></span>

<span data-ttu-id="4d259-129">客戶的主要清單會顯示在 [<xref:System.Windows.Controls.ListBox>] 控制項中。</span><span class="sxs-lookup"><span data-stu-id="4d259-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="4d259-130">下列程式碼範例會定義名為 `ListItemsTemplate` 的 <xref:System.Windows.DataTemplate> 物件，以控制 <xref:System.Windows.Controls.ListBox> 控制項的視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4d259-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="4d259-131">這個 <xref:System.Windows.DataTemplate> 會指派給 <xref:System.Windows.Controls.ListBox> 控制項的 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4d259-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>

### <a name="to-define-the-data-template"></a><span data-ttu-id="4d259-132">定義資料範本</span><span class="sxs-lookup"><span data-stu-id="4d259-132">To define the data template</span></span>

- <span data-ttu-id="4d259-133">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素的宣告中。</span><span class="sxs-lookup"><span data-stu-id="4d259-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a><span data-ttu-id="4d259-134">指定表單版面配置</span><span class="sxs-lookup"><span data-stu-id="4d259-134">Specifying the Form Layout</span></span>

<span data-ttu-id="4d259-135">表單的版面配置定義具有三個資料列和三個資料行的格線。</span><span class="sxs-lookup"><span data-stu-id="4d259-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="4d259-136">系統會提供 <xref:System.Windows.Controls.Label> 控制項，以識別 Customers 資料表中的每個資料行。</span><span class="sxs-lookup"><span data-stu-id="4d259-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>

### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="4d259-137">設定格線版面配置</span><span class="sxs-lookup"><span data-stu-id="4d259-137">To set up the Grid layout</span></span>

- <span data-ttu-id="4d259-138">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素的宣告中。</span><span class="sxs-lookup"><span data-stu-id="4d259-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="4d259-139">設定 Label 控制項</span><span class="sxs-lookup"><span data-stu-id="4d259-139">To set up the Label controls</span></span>

- <span data-ttu-id="4d259-140">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素的宣告中。</span><span class="sxs-lookup"><span data-stu-id="4d259-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a><span data-ttu-id="4d259-141">指定資料繫結</span><span class="sxs-lookup"><span data-stu-id="4d259-141">Specifying Data Bindings</span></span>

<span data-ttu-id="4d259-142">客戶的主要清單會顯示在 [<xref:System.Windows.Controls.ListBox>] 控制項中。</span><span class="sxs-lookup"><span data-stu-id="4d259-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="4d259-143">附加的 `ListItemsTemplate` 會將 <xref:System.Windows.Controls.TextBlock> 控制項系結至資料庫中的 `ContactName` 欄位。</span><span class="sxs-lookup"><span data-stu-id="4d259-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>

<span data-ttu-id="4d259-144">每筆客戶記錄的詳細資料會顯示在數個 <xref:System.Windows.Controls.TextBox> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="4d259-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>

### <a name="to-specify-data-bindings"></a><span data-ttu-id="4d259-145">指定資料繫結</span><span class="sxs-lookup"><span data-stu-id="4d259-145">To specify data bindings</span></span>

- <span data-ttu-id="4d259-146">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素的宣告中。</span><span class="sxs-lookup"><span data-stu-id="4d259-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     <span data-ttu-id="4d259-147"><xref:System.Windows.Data.Binding> 類別會將 <xref:System.Windows.Controls.TextBox> 控制項系結至資料庫中的適當欄位。</span><span class="sxs-lookup"><span data-stu-id="4d259-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="4d259-148">使用交互操作來顯示資料</span><span class="sxs-lookup"><span data-stu-id="4d259-148">Displaying Data by Using Interoperation</span></span>

<span data-ttu-id="4d259-149">對應至所選客戶的訂單會顯示在名為 `dataGridView1`的 <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="4d259-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="4d259-150">`dataGridView1` 控制項系結至程式碼後置檔案中的資料來源。</span><span class="sxs-lookup"><span data-stu-id="4d259-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="4d259-151"><xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項是這個 Windows Forms 控制項的父系。</span><span class="sxs-lookup"><span data-stu-id="4d259-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this Windows Forms control.</span></span>

### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="4d259-152">在 DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="4d259-152">To display data in the DataGridView control</span></span>

- <span data-ttu-id="4d259-153">將下列 XAML 複製到 <xref:System.Windows.Controls.Grid> 元素的宣告中。</span><span class="sxs-lookup"><span data-stu-id="4d259-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="4d259-154">將資料來源新增至專案</span><span class="sxs-lookup"><span data-stu-id="4d259-154">Adding the Data Source to the Project</span></span>

<span data-ttu-id="4d259-155">有了 Visual Studio，您就可以輕鬆地將資料來源加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="4d259-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="4d259-156">此程序會將強型別的資料集新增至專案。</span><span class="sxs-lookup"><span data-stu-id="4d259-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="4d259-157">也會新增數個其他支援類別，例如每個所選擇資料表的資料表配置器。</span><span class="sxs-lookup"><span data-stu-id="4d259-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="4d259-158">若要新增資料來源</span><span class="sxs-lookup"><span data-stu-id="4d259-158">To add the data source</span></span>

1. <span data-ttu-id="4d259-159">從 [**資料**] 功能表中，選取 [**加入新的資料來源**]。</span><span class="sxs-lookup"><span data-stu-id="4d259-159">From the **Data** menu, select **Add New Data Source**.</span></span>

2. <span data-ttu-id="4d259-160">在 [**資料來源設定向導]** 中，使用資料集建立與 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="4d259-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="4d259-161">如需詳細資訊，請參閱 [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="4d259-161">For more information, see [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span></span>

3. <span data-ttu-id="4d259-162">當**資料來源設定向導**提示您時，請將連接字串儲存為 `NorthwindConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="4d259-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>

4. <span data-ttu-id="4d259-163">當系統提示您選擇資料庫物件時，請選取 `Customers` 並 `Orders` 資料表，並將產生的資料集命名 `NorthwindDataSet`。</span><span class="sxs-lookup"><span data-stu-id="4d259-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>

## <a name="binding-to-the-data-source"></a><span data-ttu-id="4d259-164">繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="4d259-164">Binding to the Data Source</span></span>

<span data-ttu-id="4d259-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> 元件會為應用程式的資料來源提供統一的介面。</span><span class="sxs-lookup"><span data-stu-id="4d259-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="4d259-166">繫結至資料來源是在程式碼後置檔案中進行實作。</span><span class="sxs-lookup"><span data-stu-id="4d259-166">Binding to the data source is implemented in the code-behind file.</span></span>

### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="4d259-167">繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="4d259-167">To bind to the data source</span></span>

1. <span data-ttu-id="4d259-168">開啟程式碼後置檔案，命名為 MainWindow.xaml.vb 或 MainWindow.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="4d259-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="4d259-169">將下列程式碼複製到 `MainWindow` 類別定義中。</span><span class="sxs-lookup"><span data-stu-id="4d259-169">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="4d259-170">此程式碼會宣告連接至資料庫的 <xref:System.Windows.Forms.BindingSource> 元件和相關聯的 helper 類別。</span><span class="sxs-lookup"><span data-stu-id="4d259-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. <span data-ttu-id="4d259-171">將下列程式碼複製至建構函式。</span><span class="sxs-lookup"><span data-stu-id="4d259-171">Copy the following code into the constructor.</span></span>

     <span data-ttu-id="4d259-172">此程式碼會建立並初始化 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="4d259-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. <span data-ttu-id="4d259-173">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="4d259-173">Open MainWindow.xaml.</span></span>

5. <span data-ttu-id="4d259-174">在設計檢視或 XAML 視圖中，選取 [<xref:System.Windows.Window>] 元素。</span><span class="sxs-lookup"><span data-stu-id="4d259-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="4d259-175">在 屬性視窗中，按一下 **事件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="4d259-175">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="4d259-176">按兩下 [<xref:System.Windows.FrameworkElement.Loaded>] 事件。</span><span class="sxs-lookup"><span data-stu-id="4d259-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="4d259-177">將下列程式碼複製到 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4d259-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

     <span data-ttu-id="4d259-178">此程式碼會將 <xref:System.Windows.Forms.BindingSource> 元件指派為數據內容，並填入 `Customers` 和 `Orders` 介面卡物件。</span><span class="sxs-lookup"><span data-stu-id="4d259-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. <span data-ttu-id="4d259-179">將下列程式碼複製到 `MainWindow` 類別定義中。</span><span class="sxs-lookup"><span data-stu-id="4d259-179">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="4d259-180">這個方法會處理 <xref:System.Windows.Data.CollectionView.CurrentChanged> 事件，並更新資料系結的目前專案。</span><span class="sxs-lookup"><span data-stu-id="4d259-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. <span data-ttu-id="4d259-181">按 F5 以建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="4d259-181">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d259-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d259-182">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="4d259-183">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="4d259-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="4d259-184">混合式應用程式中的資料系結範例</span><span class="sxs-lookup"><span data-stu-id="4d259-184">Data Binding in Hybrid Applications Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFWithWFAndDatabinding)
- [<span data-ttu-id="4d259-185">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="4d259-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="4d259-186">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="4d259-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
