---
title: DataGridView 控制項案例 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 7350b0da19650b99bcfd456f93e994492a56d7e3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648099"
---
# <a name="datagridview-control-scenarios-windows-forms"></a><span data-ttu-id="6a6de-102">DataGridView 控制項案例 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="6a6de-102">DataGridView Control Scenarios (Windows Forms)</span></span>
<span data-ttu-id="6a6de-103">使用<xref:System.Windows.Forms.DataGridView>控制項，您可以顯示各種資料來源的表格式資料。</span><span class="sxs-lookup"><span data-stu-id="6a6de-103">With the <xref:System.Windows.Forms.DataGridView> control, you can display tabular data from a variety of data sources.</span></span> <span data-ttu-id="6a6de-104">如需簡單的用法，您可以手動填入<xref:System.Windows.Forms.DataGridView>和操作直接透過控制項的資料。</span><span class="sxs-lookup"><span data-stu-id="6a6de-104">For simple uses, you can manually populate a <xref:System.Windows.Forms.DataGridView> and manipulate the data directly through the control.</span></span> <span data-ttu-id="6a6de-105">一般而言，不過，您會將資料儲存在外部資料來源並將控制項繫結至其透過<xref:System.Windows.Forms.BindingSource>元件。</span><span class="sxs-lookup"><span data-stu-id="6a6de-105">Typically, however, you will store your data in an external data source and bind the control to it through a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="6a6de-106">本主題描述一些常見案例涉及<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="6a6de-106">This topic describes some of the common scenarios that involve the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a><span data-ttu-id="6a6de-107">案例 1:顯示少量的資料</span><span class="sxs-lookup"><span data-stu-id="6a6de-107">Scenario 1: Displaying Small Amounts of Data</span></span>  
 <span data-ttu-id="6a6de-108">您不必將資料儲存在外部資料來源將它顯示在<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="6a6de-108">You do not have to store your data in an external data source to display it in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="6a6de-109">如果您正在使用少量的資料，您可以自行填入控制項，並管理透過控制項的資料。</span><span class="sxs-lookup"><span data-stu-id="6a6de-109">If you are working with a small amount of data, you can populate the control yourself and manipulate the data through the control.</span></span> <span data-ttu-id="6a6de-110">這就叫做*režim bez vazby*。</span><span class="sxs-lookup"><span data-stu-id="6a6de-110">This is called *unbound mode*.</span></span> <span data-ttu-id="6a6de-111">如需詳細資訊，請參閱[如何：建立未繫結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-111">For more information, see [How to: Create an Unbound Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="6a6de-112">案例重點</span><span class="sxs-lookup"><span data-stu-id="6a6de-112">Scenario Key Points</span></span>  
  
- <span data-ttu-id="6a6de-113">在未繫結模式中，您可以手動填入控制項。</span><span class="sxs-lookup"><span data-stu-id="6a6de-113">In unbound mode, you populate the control manually.</span></span>  
  
- <span data-ttu-id="6a6de-114">未繫結的模式是特別適用於少量的唯讀資料。</span><span class="sxs-lookup"><span data-stu-id="6a6de-114">Unbound mode is particularly suited for small amounts of read-only data.</span></span>  
  
- <span data-ttu-id="6a6de-115">未繫結的模式也適用於類似試算表或稀疏填入的資料表。</span><span class="sxs-lookup"><span data-stu-id="6a6de-115">Unbound mode is also suited for spreadsheet-like or sparsely populated tables.</span></span>  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a><span data-ttu-id="6a6de-116">案例 2:檢視和更新儲存在外部資料來源中的資料</span><span class="sxs-lookup"><span data-stu-id="6a6de-116">Scenario 2: Viewing and Updating Data Stored in an External Data Source</span></span>  
 <span data-ttu-id="6a6de-117">您可以使用<xref:System.Windows.Forms.DataGridView>做為使用者介面 (UI) 控制哪些使用者可以透過存取保留在資料來源，例如資料庫資料表或商務物件的集合中的資料。</span><span class="sxs-lookup"><span data-stu-id="6a6de-117">You can use the <xref:System.Windows.Forms.DataGridView> control as a user interface (UI) through which users can access data kept in a data source such as a database table or a collection of business objects.</span></span> <span data-ttu-id="6a6de-118">如需詳細資訊，請參閱[如何：資料繫結至 Windows Form DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-118">For more information, see [How to: Bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="6a6de-119">案例重點</span><span class="sxs-lookup"><span data-stu-id="6a6de-119">Scenario Key Points</span></span>  
  
- <span data-ttu-id="6a6de-120">繫結的模式可讓您連接到資料來源、 自動產生資料行是根據資料來源屬性或資料庫資料行，以及自動填入控制項。</span><span class="sxs-lookup"><span data-stu-id="6a6de-120">Bound mode lets you connect to a data source, automatically generate columns based on the data source properties or database columns, and automatically populate the control.</span></span>  
  
- <span data-ttu-id="6a6de-121">繫結的模式很適合大量的使用者與資料互動。</span><span class="sxs-lookup"><span data-stu-id="6a6de-121">Bound mode is suited for heavy user interaction with data.</span></span> <span data-ttu-id="6a6de-122">可以格式化資料以供顯示，以及使用者指定的資料可以剖析成資料來源所預期的格式。</span><span class="sxs-lookup"><span data-stu-id="6a6de-122">Data can be formatted for display, and user-specified data can be parsed into the format expected by the data source.</span></span> <span data-ttu-id="6a6de-123">可以偵測格式錯誤和資料庫條件約束錯誤的資料項目，以便可以警告使用者，且可以更正錯誤的儲存格。</span><span class="sxs-lookup"><span data-stu-id="6a6de-123">Data entry formatting errors and database constraint errors can be detected so that users can be warned and erroneous cells can be corrected.</span></span>  
  
- <span data-ttu-id="6a6de-124">其他功能，例如資料行排序，凍結和重新調整順序可以讓使用者在其工作流程最簡便的方式檢視資料。</span><span class="sxs-lookup"><span data-stu-id="6a6de-124">Additional functionality such as column sorting, freezing, and reordering enable users to view data in the way most convenient for their workflow.</span></span>  
  
- <span data-ttu-id="6a6de-125">剪貼簿支援可讓使用者將資料複製到其他應用程式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a6de-125">Clipboard support enables users to copy data from your application into other applications.</span></span>  
  
## <a name="scenario-3-advanced-data"></a><span data-ttu-id="6a6de-126">案例 3:進階的資料</span><span class="sxs-lookup"><span data-stu-id="6a6de-126">Scenario 3: Advanced Data</span></span>  
 <span data-ttu-id="6a6de-127">如果您有標準資料繫結模型不能解決的特殊需求，您可以藉由實作來管理控制項和您的資料之間的互動*虛擬模式*。</span><span class="sxs-lookup"><span data-stu-id="6a6de-127">If you have special needs that the standard data binding model does not address, you can manage the interaction between the control and your data by implementing *virtual mode*.</span></span> <span data-ttu-id="6a6de-128">需要實作虛擬模式表示實作一或多個事件處理常式，可讓控制項要求的相關資訊的儲存格的資訊。</span><span class="sxs-lookup"><span data-stu-id="6a6de-128">Implementing virtual mode means implementing one or more event handlers that let the control request information about cells as the information is needed.</span></span>  
  
 <span data-ttu-id="6a6de-129">例如，如果您使用大量資料時，您可能想要實作虛擬模式，以確保最佳的效率。</span><span class="sxs-lookup"><span data-stu-id="6a6de-129">For example, if you work with large amounts of data, you may want to implement virtual mode to ensure optimal efficiency.</span></span> <span data-ttu-id="6a6de-130">虛擬模式也適合用於維護，以及從另一個資料來源擷取的資料行顯示未繫結資料行的值。</span><span class="sxs-lookup"><span data-stu-id="6a6de-130">Virtual mode is also useful for maintaining the values of unbound columns that you display along with columns retrieved from another data source.</span></span>  
  
 <span data-ttu-id="6a6de-131">如需有關虛擬模式的詳細資訊，請參閱[逐步解說：實作虛擬模式中的 Windows Form DataGridView 控制項](implementing-virtual-mode-wf-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-131">For more information about virtual mode, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="6a6de-132">案例重點</span><span class="sxs-lookup"><span data-stu-id="6a6de-132">Scenario Key Points</span></span>  
  
- <span data-ttu-id="6a6de-133">虛擬模式很適合您要微調效能時，顯示非常大量的資料。</span><span class="sxs-lookup"><span data-stu-id="6a6de-133">Virtual mode is suited for displaying very large amounts of data when you need to fine-tune performance.</span></span>  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a><span data-ttu-id="6a6de-134">案例 4:自動調整資料列和資料行的大小</span><span class="sxs-lookup"><span data-stu-id="6a6de-134">Scenario 4: Automatically Resizing Rows and Columns</span></span>  
 <span data-ttu-id="6a6de-135">當您顯示會定期更新的資料時，您可以自動調整資料列和資料行以確保所有內容都是可見。</span><span class="sxs-lookup"><span data-stu-id="6a6de-135">When you display data that is regularly updated, you can automatically resize rows and columns to ensure that all content is visible.</span></span> <span data-ttu-id="6a6de-136"><xref:System.Windows.Forms.DataGridView>控制項提供數個選項，可讓您啟用或停用手動調整大小、 調整大小以程式設計方式在特定時間，或調整大小自動每當內容變更。</span><span class="sxs-lookup"><span data-stu-id="6a6de-136">The <xref:System.Windows.Forms.DataGridView> control provides several options that let you enable or disable manual resizing, resize programmatically at specific times, or resize automatically whenever content changes.</span></span> <span data-ttu-id="6a6de-137">如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-137">For more information, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="6a6de-138">案例重點</span><span class="sxs-lookup"><span data-stu-id="6a6de-138">Scenario Key Points</span></span>  
  
- <span data-ttu-id="6a6de-139">手動調整大小，可讓使用者調整儲存格的高度和寬度。</span><span class="sxs-lookup"><span data-stu-id="6a6de-139">Manual resizing enables users to adjust cell heights and widths.</span></span>  
  
- <span data-ttu-id="6a6de-140">自動調整大小，可讓您維護儲存格的大小，以便儲存格內容永遠不會被裁剪。</span><span class="sxs-lookup"><span data-stu-id="6a6de-140">Automatic resizing enables you to maintain cell sizes so that cell content is never clipped.</span></span>  
  
- <span data-ttu-id="6a6de-141">以程式設計方式調整大小，可讓您調整儲存格大小以避免連續的自動調整大小的效能負面影響的特定時間。</span><span class="sxs-lookup"><span data-stu-id="6a6de-141">Programmatic resizing enables you to resize cells at specific times to avoid the performance penalty of continuous automatic resizing.</span></span>  
  
## <a name="scenario-5-simple-customization"></a><span data-ttu-id="6a6de-142">案例 5:簡單的自訂</span><span class="sxs-lookup"><span data-stu-id="6a6de-142">Scenario 5: Simple Customization</span></span>  
 <span data-ttu-id="6a6de-143"><xref:System.Windows.Forms.DataGridView>控制項提供許多方式來改變其基本外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="6a6de-143">The <xref:System.Windows.Forms.DataGridView> control provides many ways for you to alter its basic appearance and behavior.</span></span> <span data-ttu-id="6a6de-144">如需詳細資訊，請參閱 < [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-144">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="6a6de-145">案例重點</span><span class="sxs-lookup"><span data-stu-id="6a6de-145">Scenario Key Points</span></span>  
  
- <span data-ttu-id="6a6de-146"><xref:System.Windows.Forms.DataGridViewCellStyle> 物件可讓您提供色彩、 字型、 格式和多個層級和個別的項目控制項的位置資訊。</span><span class="sxs-lookup"><span data-stu-id="6a6de-146"><xref:System.Windows.Forms.DataGridViewCellStyle> objects let you provide color, font, formatting, and positioning information at multiple levels and for individual elements of the control.</span></span>  
  
- <span data-ttu-id="6a6de-147">儲存格樣式可以分層和共用的多個項目，可讓您重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a6de-147">Cell styles can be layered and shared by multiple elements, letting you reuse code.</span></span>  
  
## <a name="scenario-6-advanced-customization"></a><span data-ttu-id="6a6de-148">案例 6:進階的自訂</span><span class="sxs-lookup"><span data-stu-id="6a6de-148">Scenario 6: Advanced Customization</span></span>  
 <span data-ttu-id="6a6de-149"><xref:System.Windows.Forms.DataGridView>控制項提供許多的方式，供您自訂其外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="6a6de-149">The <xref:System.Windows.Forms.DataGridView> control provides many ways for you to customize its appearance and behavior.</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="6a6de-150">案例重點</span><span class="sxs-lookup"><span data-stu-id="6a6de-150">Scenario Key Points</span></span>  
  
- <span data-ttu-id="6a6de-151">您可以提供自己的儲存格的繪製程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a6de-151">You can provide your own cell painting code.</span></span> <span data-ttu-id="6a6de-152">如需詳細資訊，請參閱[如何：自訂 Windows Form DataGridView 控制項中的儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-152">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md).</span></span>  
  
- <span data-ttu-id="6a6de-153">您可以提供您自己的資料列繪製。</span><span class="sxs-lookup"><span data-stu-id="6a6de-153">You can provide your own row painting.</span></span> <span data-ttu-id="6a6de-154">這是很有用，例如，具有跨越多個資料行的內容中建立資料列。</span><span class="sxs-lookup"><span data-stu-id="6a6de-154">This is useful, for example, to create rows with content that spans multiple columns.</span></span> <span data-ttu-id="6a6de-155">如需詳細資訊，請參閱[如何：自訂 Windows Form DataGridView 控制項中的資料列的外觀](customize-the-appearance-of-rows-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-155">For more information, see [How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control](customize-the-appearance-of-rows-in-the-datagrid.md).</span></span>  
  
- <span data-ttu-id="6a6de-156">您可以實作您自己的儲存格和資料行的類別，以自訂儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="6a6de-156">You can implement your own cell and column classes to customize cell appearance.</span></span> <span data-ttu-id="6a6de-157">如需詳細資訊，請參閱[如何：自訂資料格資料行中的 Windows Form DataGridView 控制項和擴充其行為和外觀](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-157">For more information, see [How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).</span></span>  
  
- <span data-ttu-id="6a6de-158">您可以實作您自己的儲存格和資料行的類別，來提供的內建的資料行類型以外的主控制項。</span><span class="sxs-lookup"><span data-stu-id="6a6de-158">You can implement your own cell and column classes to host controls other than the ones provided by the built-in column types.</span></span> <span data-ttu-id="6a6de-159">如需詳細資訊，請參閱[如何：Windows Forms DataGridView 儲存格主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。</span><span class="sxs-lookup"><span data-stu-id="6a6de-159">For more information, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6de-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a6de-160">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="6a6de-161">DataGridView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="6a6de-161">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
