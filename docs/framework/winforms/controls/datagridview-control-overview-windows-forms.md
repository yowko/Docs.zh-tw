---
title: DataGridView 控制項概觀
description: 瞭解如何使用 Windows Forms DataGridView 控制項，從許多不同類型的資料來源顯示和編輯表格式資料。
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
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174610"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="7491c-103">DataGridView 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="7491c-103">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="7491c-104"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="7491c-104">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="7491c-105">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="7491c-105">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="7491c-106">使用 <xref:System.Windows.Forms.DataGridView> 控制項，您可以從許多不同類型的資料來源顯示和編輯表格式資料。</span><span class="sxs-lookup"><span data-stu-id="7491c-106">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="7491c-107">將資料系結至 <xref:System.Windows.Forms.DataGridView> 控制項既簡單又直覺，而且在許多情況下，它就像設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="7491c-107">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="7491c-108">當您系結至包含多個清單或資料表的資料來源時，請將 <xref:System.Windows.Forms.DataGridView.DataMember%2A> 屬性設定為指定要系結之清單或資料表的字串。</span><span class="sxs-lookup"><span data-stu-id="7491c-108">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="7491c-109"><xref:System.Windows.Forms.DataGridView>控制項支援標準 Windows Forms 資料系結模型，因此它會系結至下列清單中所述類別的實例：</span><span class="sxs-lookup"><span data-stu-id="7491c-109">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
- <span data-ttu-id="7491c-110">任何會執行介面的類別 <xref:System.Collections.IList> ，包括一維陣列。</span><span class="sxs-lookup"><span data-stu-id="7491c-110">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
- <span data-ttu-id="7491c-111">任何會執行介面的類別 <xref:System.ComponentModel.IListSource> ，例如 <xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 類別。</span><span class="sxs-lookup"><span data-stu-id="7491c-111">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
- <span data-ttu-id="7491c-112">任何會執行介面的類別 <xref:System.ComponentModel.IBindingList> ，例如 <xref:System.ComponentModel.BindingList%601> 類別。</span><span class="sxs-lookup"><span data-stu-id="7491c-112">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
- <span data-ttu-id="7491c-113">任何會執行介面的類別 <xref:System.ComponentModel.IBindingListView> ，例如 <xref:System.Windows.Forms.BindingSource> 類別。</span><span class="sxs-lookup"><span data-stu-id="7491c-113">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="7491c-114"><xref:System.Windows.Forms.DataGridView>控制項支援將資料系結至這些介面所傳回之物件的公用屬性或介面所傳回的屬性集合 <xref:System.ComponentModel.ICustomTypeDescriptor> （如果在傳回的物件上執行）。</span><span class="sxs-lookup"><span data-stu-id="7491c-114">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="7491c-115">一般來說，您會系結至 <xref:System.Windows.Forms.BindingSource> 元件，並將 <xref:System.Windows.Forms.BindingSource> 元件系結至另一個資料來源，或將它填入商務物件。</span><span class="sxs-lookup"><span data-stu-id="7491c-115">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="7491c-116"><xref:System.Windows.Forms.BindingSource>元件是慣用的資料來源，因為它可以系結至各種不同的資料來源，而且可以自動解決許多資料系結問題。</span><span class="sxs-lookup"><span data-stu-id="7491c-116">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="7491c-117">如需詳細資訊，請參閱[BindingSource Component](bindingsource-component.md)。</span><span class="sxs-lookup"><span data-stu-id="7491c-117">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="7491c-118"><xref:System.Windows.Forms.DataGridView>控制項也可以在*未*系結模式中使用，但不含基礎資料存放區。</span><span class="sxs-lookup"><span data-stu-id="7491c-118">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="7491c-119">如需使用未系結控制項的程式碼範例 <xref:System.Windows.Forms.DataGridView> ，請參閱[逐步解說：建立未系結的 Windows Forms DataGridView 控制項](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="7491c-119">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="7491c-120">此 <xref:System.Windows.Forms.DataGridView> 控制項可高度設定和擴充，並提供許多屬性、方法和事件來自訂其外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="7491c-120">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="7491c-121">當您想要 Windows Forms 應用程式顯示表格式資料時，請考慮在 <xref:System.Windows.Forms.DataGridView> 其他人之前使用控制項 (例如 <xref:System.Windows.Forms.DataGrid>) 。</span><span class="sxs-lookup"><span data-stu-id="7491c-121">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="7491c-122">如果您要顯示唯讀值的小型方格，或如果您要讓使用者編輯含有數百萬筆記錄的資料表，此 <xref:System.Windows.Forms.DataGridView> 控制項將提供您容易程式化、記憶體有效率的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7491c-122">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7491c-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="7491c-123">In This Section</span></span>  
 [<span data-ttu-id="7491c-124">DataGridView 控制項技術摘要</span><span class="sxs-lookup"><span data-stu-id="7491c-124">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="7491c-125">摘要說明 <xref:System.Windows.Forms.DataGridView> 控制項概念和相關類別的使用。</span><span class="sxs-lookup"><span data-stu-id="7491c-125">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="7491c-126">DataGridView 控制項架構</span><span class="sxs-lookup"><span data-stu-id="7491c-126">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="7491c-127">描述控制項的架構 <xref:System.Windows.Forms.DataGridView> ，說明其類型階層和繼承結構。</span><span class="sxs-lookup"><span data-stu-id="7491c-127">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="7491c-128">DataGridView 控制項案例</span><span class="sxs-lookup"><span data-stu-id="7491c-128">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="7491c-129">描述使用控制項的最常見案例 <xref:System.Windows.Forms.DataGridView> 。</span><span class="sxs-lookup"><span data-stu-id="7491c-129">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="7491c-130">DataGridView 控制項程式碼目錄</span><span class="sxs-lookup"><span data-stu-id="7491c-130">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="7491c-131">提供各種工作檔中程式碼範例的連結 <xref:System.Windows.Forms.DataGridView> 。</span><span class="sxs-lookup"><span data-stu-id="7491c-131">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="7491c-132">這些範例是以工作類型分類。</span><span class="sxs-lookup"><span data-stu-id="7491c-132">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7491c-133">相關章節</span><span class="sxs-lookup"><span data-stu-id="7491c-133">Related Sections</span></span>  
 [<span data-ttu-id="7491c-134">Windows Form DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="7491c-134">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7491c-135">討論用來顯示資訊的 Windows Forms 控制項中的資料行類型 <xref:System.Windows.Forms.DataGridView> ，並允許使用者修改或加入資訊。</span><span class="sxs-lookup"><span data-stu-id="7491c-135">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="7491c-136">在 Windows Form DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="7491c-136">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7491c-137">提供主題描述如何以手動方式或從外部資料來源將資料填入控制項。</span><span class="sxs-lookup"><span data-stu-id="7491c-137">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="7491c-138">自訂 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="7491c-138">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7491c-139">提供主題描述自訂繪製 <xref:System.Windows.Forms.DataGridView> 儲存格和資料列，並建立衍生儲存格、資料行和資料列類型。</span><span class="sxs-lookup"><span data-stu-id="7491c-139">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="7491c-140">Windows Form DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="7491c-140">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7491c-141">提供主題描述處理大量資料時，如何有效率地使用控制項來避免發生效能問題。</span><span class="sxs-lookup"><span data-stu-id="7491c-141">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7491c-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7491c-142">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="7491c-143">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="7491c-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="7491c-144">Windows Form DataGridView 控制項的預設功能</span><span class="sxs-lookup"><span data-stu-id="7491c-144">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7491c-145">Windows Forms DataGridView 控制項中的預設鍵盤和滑鼠控制</span><span class="sxs-lookup"><span data-stu-id="7491c-145">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
