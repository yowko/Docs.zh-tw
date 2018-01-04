---
title: "逐步解說：繫結至混合應用程式中的資料"
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
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3afc0d2eabb7554d64a40863b182a6edefe169f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="a32d8-102">逐步解說：繫結至混合應用程式中的資料</span><span class="sxs-lookup"><span data-stu-id="a32d8-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>
<span data-ttu-id="a32d8-103">不論您使用資料來源繫結至控制項是不可或缺的使用者提供存取基礎資料，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]或[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a32d8-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="a32d8-104">本逐步解說示範如何使用資料繫結，包括兩者的混合式應用程式中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="a32d8-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>  
  
 <span data-ttu-id="a32d8-105">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="a32d8-105">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a32d8-106">建立專案。</span><span class="sxs-lookup"><span data-stu-id="a32d8-106">Creating the project.</span></span>  
  
-   <span data-ttu-id="a32d8-107">定義資料範本。</span><span class="sxs-lookup"><span data-stu-id="a32d8-107">Defining the data template.</span></span>  
  
-   <span data-ttu-id="a32d8-108">指定表單版面配置。</span><span class="sxs-lookup"><span data-stu-id="a32d8-108">Specifying the form layout.</span></span>  
  
-   <span data-ttu-id="a32d8-109">指定資料繫結。</span><span class="sxs-lookup"><span data-stu-id="a32d8-109">Specifying data bindings.</span></span>  
  
-   <span data-ttu-id="a32d8-110">使用交互操作來顯示資料。</span><span class="sxs-lookup"><span data-stu-id="a32d8-110">Displaying data by using interoperation.</span></span>  
  
-   <span data-ttu-id="a32d8-111">將資料來源新增至專案。</span><span class="sxs-lookup"><span data-stu-id="a32d8-111">Adding the data source to the project.</span></span>  
  
-   <span data-ttu-id="a32d8-112">繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="a32d8-112">Binding to the data source.</span></span>  
  
 <span data-ttu-id="a32d8-113">在此逐步解說中所述的工作的完整程式碼清單，請參閱[混合式應用程式範例中的資料繫結](http://go.microsoft.com/fwlink/?LinkID=159983)。</span><span class="sxs-lookup"><span data-stu-id="a32d8-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](http://go.microsoft.com/fwlink/?LinkID=159983).</span></span>  
  
 <span data-ttu-id="a32d8-114">完成後，您就會了解混合應用程式中的資料繫結功能。</span><span class="sxs-lookup"><span data-stu-id="a32d8-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a32d8-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="a32d8-115">Prerequisites</span></span>  
 <span data-ttu-id="a32d8-116">您需要下列元件才能完成此逐步解說：</span><span class="sxs-lookup"><span data-stu-id="a32d8-116">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="a32d8-117">.</span><span class="sxs-lookup"><span data-stu-id="a32d8-117">.</span></span>  
  
-   <span data-ttu-id="a32d8-118">Microsoft SQL Server 上執行的 Northwind 範例資料庫的存取。</span><span class="sxs-lookup"><span data-stu-id="a32d8-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="a32d8-119">建立專案</span><span class="sxs-lookup"><span data-stu-id="a32d8-119">Creating the Project</span></span>  
  
#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="a32d8-120">建立並設定專案</span><span class="sxs-lookup"><span data-stu-id="a32d8-120">To create and set up the project</span></span>  
  
1.  <span data-ttu-id="a32d8-121">建立 WPF 應用程式專案，名為`WPFWithWFAndDatabinding`。</span><span class="sxs-lookup"><span data-stu-id="a32d8-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>  
  
2.  <span data-ttu-id="a32d8-122">在 [方案總管] 中，加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="a32d8-122">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="a32d8-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="a32d8-123">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="a32d8-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="a32d8-124">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="a32d8-125">開啟 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a32d8-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="a32d8-126">在<xref:System.Windows.Window>項目，加入下列[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命名空間對應。</span><span class="sxs-lookup"><span data-stu-id="a32d8-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="a32d8-127">命名預設<xref:System.Windows.Controls.Grid>元素`mainGrid`藉由指派<xref:System.Windows.FrameworkElement.Name%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a32d8-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]  
  
## <a name="defining-the-data-template"></a><span data-ttu-id="a32d8-128">定義資料範本</span><span class="sxs-lookup"><span data-stu-id="a32d8-128">Defining the Data Template</span></span>  
 <span data-ttu-id="a32d8-129">客戶的主機清單會顯示在<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a32d8-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="a32d8-130">下列程式碼範例會定義<xref:System.Windows.DataTemplate>名為物件`ListItemsTemplate`控制的視覺化樹狀結構<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a32d8-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="a32d8-131">這<xref:System.Windows.DataTemplate>指派給<xref:System.Windows.Controls.ListBox>控制項的<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="a32d8-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>  
  
#### <a name="to-define-the-data-template"></a><span data-ttu-id="a32d8-132">定義資料範本</span><span class="sxs-lookup"><span data-stu-id="a32d8-132">To define the data template</span></span>  
  
-   <span data-ttu-id="a32d8-133">複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。</span><span class="sxs-lookup"><span data-stu-id="a32d8-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]  
  
## <a name="specifying-the-form-layout"></a><span data-ttu-id="a32d8-134">指定表單版面配置</span><span class="sxs-lookup"><span data-stu-id="a32d8-134">Specifying the Form Layout</span></span>  
 <span data-ttu-id="a32d8-135">表單的版面配置定義具有三個資料列和三個資料行的格線。</span><span class="sxs-lookup"><span data-stu-id="a32d8-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="a32d8-136"><xref:System.Windows.Controls.Label>提供控制項來識別 Customers 資料表中的每個資料行。</span><span class="sxs-lookup"><span data-stu-id="a32d8-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>  
  
#### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="a32d8-137">設定格線版面配置</span><span class="sxs-lookup"><span data-stu-id="a32d8-137">To set up the Grid layout</span></span>  
  
-   <span data-ttu-id="a32d8-138">複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。</span><span class="sxs-lookup"><span data-stu-id="a32d8-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]  
  
#### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="a32d8-139">設定 Label 控制項</span><span class="sxs-lookup"><span data-stu-id="a32d8-139">To set up the Label controls</span></span>  
  
-   <span data-ttu-id="a32d8-140">複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。</span><span class="sxs-lookup"><span data-stu-id="a32d8-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]  
  
## <a name="specifying-data-bindings"></a><span data-ttu-id="a32d8-141">指定資料繫結</span><span class="sxs-lookup"><span data-stu-id="a32d8-141">Specifying Data Bindings</span></span>  
 <span data-ttu-id="a32d8-142">客戶的主機清單會顯示在<xref:System.Windows.Controls.ListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a32d8-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="a32d8-143">附加`ListItemsTemplate`繫結<xref:System.Windows.Controls.TextBlock>控制權傳輸至`ContactName`從資料庫欄位。</span><span class="sxs-lookup"><span data-stu-id="a32d8-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>  
  
 <span data-ttu-id="a32d8-144">每個客戶記錄的詳細資訊會顯示在幾個<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="a32d8-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>  
  
#### <a name="to-specify-data-bindings"></a><span data-ttu-id="a32d8-145">指定資料繫結</span><span class="sxs-lookup"><span data-stu-id="a32d8-145">To specify data bindings</span></span>  
  
-   <span data-ttu-id="a32d8-146">複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。</span><span class="sxs-lookup"><span data-stu-id="a32d8-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     <span data-ttu-id="a32d8-147"><xref:System.Windows.Data.Binding>類別繫結<xref:System.Windows.Controls.TextBox>資料庫中的適當欄位的控制項。</span><span class="sxs-lookup"><span data-stu-id="a32d8-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]  
  
## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="a32d8-148">使用交互操作來顯示資料</span><span class="sxs-lookup"><span data-stu-id="a32d8-148">Displaying Data by Using Interoperation</span></span>  
 <span data-ttu-id="a32d8-149">對應至所選客戶的訂單會顯示在<xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType>控制項，名為`dataGridView1`。</span><span class="sxs-lookup"><span data-stu-id="a32d8-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="a32d8-150">`dataGridView1`控制項繫結至程式碼後置檔案中的資料來源。</span><span class="sxs-lookup"><span data-stu-id="a32d8-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="a32d8-151">A<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項是這個父[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。</span><span class="sxs-lookup"><span data-stu-id="a32d8-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>  
  
#### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="a32d8-152">在 DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="a32d8-152">To display data in the DataGridView control</span></span>  
  
-   <span data-ttu-id="a32d8-153">複製成下列 XAML<xref:System.Windows.Controls.Grid>元素的宣告。</span><span class="sxs-lookup"><span data-stu-id="a32d8-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>  
  
     [!code-xaml[WPFWithWFAndDatabinding#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]  
  
## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="a32d8-154">將資料來源新增至專案</span><span class="sxs-lookup"><span data-stu-id="a32d8-154">Adding the Data Source to the Project</span></span>  
 <span data-ttu-id="a32d8-155">與[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，您可以輕鬆加入資料來源至您的專案。</span><span class="sxs-lookup"><span data-stu-id="a32d8-155">With [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can easily add a data source to your project.</span></span> <span data-ttu-id="a32d8-156">此程序會將強型別的資料集新增至專案。</span><span class="sxs-lookup"><span data-stu-id="a32d8-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="a32d8-157">也會新增數個其他支援類別，例如每個所選擇資料表的資料表配置器。</span><span class="sxs-lookup"><span data-stu-id="a32d8-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="a32d8-158">若要新增資料來源</span><span class="sxs-lookup"><span data-stu-id="a32d8-158">To add the data source</span></span>  
  
1.  <span data-ttu-id="a32d8-159">從**資料**功能表上，選取**加入新資料來源**。</span><span class="sxs-lookup"><span data-stu-id="a32d8-159">From the **Data** menu, select **Add New Data Source**.</span></span>  
  
2.  <span data-ttu-id="a32d8-160">在**資料來源組態精靈**，使用的資料集建立 Northwind 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="a32d8-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="a32d8-161">如需詳細資訊，請參閱[如何： 連接到資料庫中的資料](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)。</span><span class="sxs-lookup"><span data-stu-id="a32d8-161">For more information, see [How to: Connect to Data in a Database](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556).</span></span>  
  
3.  <span data-ttu-id="a32d8-162">當提示您**資料來源組態精靈**，儲存連接字串做為`NorthwindConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="a32d8-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>  
  
4.  <span data-ttu-id="a32d8-163">當提示您選擇您的資料庫物件時時，請選取`Customers`和`Orders`資料表，以及名稱產生的資料集`NorthwindDataSet`。</span><span class="sxs-lookup"><span data-stu-id="a32d8-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>  
  
## <a name="binding-to-the-data-source"></a><span data-ttu-id="a32d8-164">繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="a32d8-164">Binding to the Data Source</span></span>  
 <span data-ttu-id="a32d8-165"><xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>元件應用程式的資料來源提供統一的介面。</span><span class="sxs-lookup"><span data-stu-id="a32d8-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="a32d8-166">繫結至資料來源是在程式碼後置檔案中進行實作。</span><span class="sxs-lookup"><span data-stu-id="a32d8-166">Binding to the data source is implemented in the code-behind file.</span></span>  
  
#### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="a32d8-167">繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="a32d8-167">To bind to the data source</span></span>  
  
1.  <span data-ttu-id="a32d8-168">開啟程式碼後置檔案，命名為 MainWindow.xaml.vb 或 MainWindow.xaml.cs。</span><span class="sxs-lookup"><span data-stu-id="a32d8-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="a32d8-169">下列程式碼複製到`MainWindow`類別定義。</span><span class="sxs-lookup"><span data-stu-id="a32d8-169">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="a32d8-170">此程式碼會宣告<xref:System.Windows.Forms.BindingSource>元件，並連接到資料庫的相關聯的 helper 類別。</span><span class="sxs-lookup"><span data-stu-id="a32d8-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]  
  
3.  <span data-ttu-id="a32d8-171">將下列程式碼複製至建構函式。</span><span class="sxs-lookup"><span data-stu-id="a32d8-171">Copy the following code into the constructor.</span></span>  
  
     <span data-ttu-id="a32d8-172">此程式碼會建立並初始化<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="a32d8-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]  
  
4.  <span data-ttu-id="a32d8-173">開啟 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="a32d8-173">Open MainWindow.xaml.</span></span>  
  
5.  <span data-ttu-id="a32d8-174">在 [設計] 檢視或 [XAML] 檢視中，選取<xref:System.Windows.Window>項目。</span><span class="sxs-lookup"><span data-stu-id="a32d8-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="a32d8-175">在 屬性 視窗中，按一下**事件** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a32d8-175">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="a32d8-176">按兩下<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="a32d8-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="a32d8-177">下列程式碼複製到<xref:System.Windows.FrameworkElement.Loaded>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a32d8-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>  
  
     <span data-ttu-id="a32d8-178">此程式碼指派<xref:System.Windows.Forms.BindingSource>元件做為資料內容並於其中填入`Customers`和`Orders`配接器物件。</span><span class="sxs-lookup"><span data-stu-id="a32d8-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]  
  
9. <span data-ttu-id="a32d8-179">下列程式碼複製到`MainWindow`類別定義。</span><span class="sxs-lookup"><span data-stu-id="a32d8-179">Copy the following code into the `MainWindow` class definition.</span></span>  
  
     <span data-ttu-id="a32d8-180">這個方法會處理<xref:System.Windows.Data.CollectionView.CurrentChanged>事件，並更新資料繫結的目前項目。</span><span class="sxs-lookup"><span data-stu-id="a32d8-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>  
  
     [!code-csharp[WPFWithWFAndDatabinding#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]  
  
10. <span data-ttu-id="a32d8-181">按 F5 鍵建置並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a32d8-181">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a32d8-182">請參閱</span><span class="sxs-lookup"><span data-stu-id="a32d8-182">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="a32d8-183">WPF 設計工具</span><span class="sxs-lookup"><span data-stu-id="a32d8-183">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="a32d8-184">混合式應用程式範例中的繫結的資料</span><span class="sxs-lookup"><span data-stu-id="a32d8-184">Data Binding in Hybrid Applications Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159983)  
 [<span data-ttu-id="a32d8-185">逐步解說：在 WPF 中裝載 Windows Forms 複合控制項</span><span class="sxs-lookup"><span data-stu-id="a32d8-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="a32d8-186">逐步解說：在 Windows Forms 中裝載 WPF 複合控制項</span><span class="sxs-lookup"><span data-stu-id="a32d8-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
