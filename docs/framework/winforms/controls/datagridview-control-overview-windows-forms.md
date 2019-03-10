---
title: DataGridView 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: d7ff88f877f73382f69874c58392c3374a83c019
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705996"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="266cb-102">DataGridView 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="266cb-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="266cb-103">
  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="266cb-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="266cb-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="266cb-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="266cb-105">使用<xref:System.Windows.Forms.DataGridView>控制項，您可以顯示和編輯多種不同的資料來源的表格式資料。</span><span class="sxs-lookup"><span data-stu-id="266cb-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="266cb-106">若要將資料繫結<xref:System.Windows.Forms.DataGridView>控制項是簡單又直覺，並在許多情況下很簡單，只要設定<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="266cb-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="266cb-107">當您繫結至資料來源包含多個清單或資料表時，設定<xref:System.Windows.Forms.DataGridView.DataMember%2A>屬性設為指定的清單或繫結資料表的字串。</span><span class="sxs-lookup"><span data-stu-id="266cb-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="266cb-108"><xref:System.Windows.Forms.DataGridView>控制項支援標準的 Windows Form 資料繫結模型，因此它會繫結至下列清單所述類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="266cb-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
-   <span data-ttu-id="266cb-109">任何實作類別<xref:System.Collections.IList>介面，包括一維陣列。</span><span class="sxs-lookup"><span data-stu-id="266cb-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="266cb-110">任何實作類別<xref:System.ComponentModel.IListSource>介面，例如<xref:System.Data.DataTable>和<xref:System.Data.DataSet>類別。</span><span class="sxs-lookup"><span data-stu-id="266cb-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
-   <span data-ttu-id="266cb-111">任何實作類別<xref:System.ComponentModel.IBindingList>介面，例如<xref:System.ComponentModel.BindingList%601>類別。</span><span class="sxs-lookup"><span data-stu-id="266cb-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
-   <span data-ttu-id="266cb-112">任何實作類別<xref:System.ComponentModel.IBindingListView>介面，例如<xref:System.Windows.Forms.BindingSource>類別。</span><span class="sxs-lookup"><span data-stu-id="266cb-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="266cb-113"><xref:System.Windows.Forms.DataGridView>控制項支援資料繫結至這些介面所傳回的物件的公用屬性或所傳回的屬性集合<xref:System.ComponentModel.ICustomTypeDescriptor>介面，如果傳回的物件上實作。</span><span class="sxs-lookup"><span data-stu-id="266cb-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="266cb-114">一般而言，您會繫結，來<xref:System.Windows.Forms.BindingSource>元件，並繫結<xref:System.Windows.Forms.BindingSource>元件到另一個資料來源，或商務物件以進行擴展。</span><span class="sxs-lookup"><span data-stu-id="266cb-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="266cb-115"><xref:System.Windows.Forms.BindingSource>元件是慣用的資料來源，因為它可以繫結至各種資料來源，而且可以自動解決許多資料繫結的問題。</span><span class="sxs-lookup"><span data-stu-id="266cb-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="266cb-116">如需詳細資訊，請參閱 < [BindingSource 元件](bindingsource-component.md)。</span><span class="sxs-lookup"><span data-stu-id="266cb-116">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="266cb-117"><xref:System.Windows.Forms.DataGridView>控制項也會用於*未繫結*模式中的，沒有基礎資料存放區。</span><span class="sxs-lookup"><span data-stu-id="266cb-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="266cb-118">使用未繫結的程式碼範例<xref:System.Windows.Forms.DataGridView>控制項，請參閱[逐步解說：建立未繫結的 Windows Form DataGridView 控制項](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="266cb-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="266cb-119"><xref:System.Windows.Forms.DataGridView>控制項是高度可設定和擴充性，並提供許多屬性、 方法和事件，以自訂其外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="266cb-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="266cb-120">當您想要顯示表格式資料，Windows Forms 應用程式時，請考慮使用<xref:System.Windows.Forms.DataGridView>比其他控制項 (例如<xref:System.Windows.Forms.DataGrid>)。</span><span class="sxs-lookup"><span data-stu-id="266cb-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="266cb-121">如果您要顯示的唯讀值的小型格線，或如果您要啟用使用者無法編輯的資料表的數百萬筆記錄，<xref:System.Windows.Forms.DataGridView>控制會提供您隨時可程式化、 記憶體有效率的解決方案。</span><span class="sxs-lookup"><span data-stu-id="266cb-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="266cb-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="266cb-122">In This Section</span></span>  
 [<span data-ttu-id="266cb-123">DataGridView 控制項技術摘要</span><span class="sxs-lookup"><span data-stu-id="266cb-123">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="266cb-124">摘要說明<xref:System.Windows.Forms.DataGridView>控制概念和使用相關的類別。</span><span class="sxs-lookup"><span data-stu-id="266cb-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="266cb-125">DataGridView 控制項架構</span><span class="sxs-lookup"><span data-stu-id="266cb-125">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="266cb-126">描述的架構<xref:System.Windows.Forms.DataGridView>控制項，說明它的型別階層架構和繼承結構。</span><span class="sxs-lookup"><span data-stu-id="266cb-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="266cb-127">DataGridView 控制項案例</span><span class="sxs-lookup"><span data-stu-id="266cb-127">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="266cb-128">描述最常見的案例，在其中<xref:System.Windows.Forms.DataGridView>控制項可用。</span><span class="sxs-lookup"><span data-stu-id="266cb-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="266cb-129">DataGridView 控制項程式碼目錄</span><span class="sxs-lookup"><span data-stu-id="266cb-129">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="266cb-130">提供各種文件中的程式碼範例連結<xref:System.Windows.Forms.DataGridView>工作。</span><span class="sxs-lookup"><span data-stu-id="266cb-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="266cb-131">這些範例是以工作類型分類。</span><span class="sxs-lookup"><span data-stu-id="266cb-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="266cb-132">相關章節</span><span class="sxs-lookup"><span data-stu-id="266cb-132">Related Sections</span></span>  
 [<span data-ttu-id="266cb-133">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="266cb-133">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="266cb-134">討論 Windows Form 中的資料行類型<xref:System.Windows.Forms.DataGridView>用來顯示資訊，並允許使用者修改或新增資訊的控制項。</span><span class="sxs-lookup"><span data-stu-id="266cb-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="266cb-135">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="266cb-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="266cb-136">提供主題描述如何以手動方式或從外部資料來源將資料填入控制項。</span><span class="sxs-lookup"><span data-stu-id="266cb-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="266cb-137">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="266cb-137">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="266cb-138">提供主題描述自訂繪製 <xref:System.Windows.Forms.DataGridView> 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。</span><span class="sxs-lookup"><span data-stu-id="266cb-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="266cb-139">Windows Forms DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="266cb-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="266cb-140">提供主題描述處理大量資料時，如何有效率地使用控制項來避免發生效能問題。</span><span class="sxs-lookup"><span data-stu-id="266cb-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="266cb-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="266cb-141">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="266cb-142">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="266cb-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="266cb-143">Windows Forms DataGridView 控制項的預設功能</span><span class="sxs-lookup"><span data-stu-id="266cb-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="266cb-144">Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠處理</span><span class="sxs-lookup"><span data-stu-id="266cb-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
