---
title: DataGridView 控制項案例
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 160d967c6445fb753cb6c73babfb02a734a07e28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742468"
---
# <a name="datagridview-control-scenarios-windows-forms"></a><span data-ttu-id="b0380-102">DataGridView 控制項案例 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="b0380-102">DataGridView Control Scenarios (Windows Forms)</span></span>
<span data-ttu-id="b0380-103">有了 <xref:System.Windows.Forms.DataGridView> 控制項，您就可以從各種資料來源顯示表格式資料。</span><span class="sxs-lookup"><span data-stu-id="b0380-103">With the <xref:System.Windows.Forms.DataGridView> control, you can display tabular data from a variety of data sources.</span></span> <span data-ttu-id="b0380-104">針對簡單的用法，您可以手動填入 <xref:System.Windows.Forms.DataGridView>，並直接透過控制項運算元據。</span><span class="sxs-lookup"><span data-stu-id="b0380-104">For simple uses, you can manually populate a <xref:System.Windows.Forms.DataGridView> and manipulate the data directly through the control.</span></span> <span data-ttu-id="b0380-105">不過，一般而言，您會將資料儲存在外部資料源，並透過 <xref:System.Windows.Forms.BindingSource> 元件將控制項系結至它。</span><span class="sxs-lookup"><span data-stu-id="b0380-105">Typically, however, you will store your data in an external data source and bind the control to it through a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 <span data-ttu-id="b0380-106">本主題描述一些牽涉到 <xref:System.Windows.Forms.DataGridView> 控制項的常見案例。</span><span class="sxs-lookup"><span data-stu-id="b0380-106">This topic describes some of the common scenarios that involve the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a><span data-ttu-id="b0380-107">案例1：顯示少量的資料</span><span class="sxs-lookup"><span data-stu-id="b0380-107">Scenario 1: Displaying Small Amounts of Data</span></span>  
 <span data-ttu-id="b0380-108">您不需要將資料儲存在外部資料源中，就能在 <xref:System.Windows.Forms.DataGridView> 控制項中顯示。</span><span class="sxs-lookup"><span data-stu-id="b0380-108">You do not have to store your data in an external data source to display it in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b0380-109">如果您使用的資料量很少，您可以自行填入控制項，並透過控制項運算元據。</span><span class="sxs-lookup"><span data-stu-id="b0380-109">If you are working with a small amount of data, you can populate the control yourself and manipulate the data through the control.</span></span> <span data-ttu-id="b0380-110">這稱為「*解除*系結模式」。</span><span class="sxs-lookup"><span data-stu-id="b0380-110">This is called *unbound mode*.</span></span> <span data-ttu-id="b0380-111">如需詳細資訊，請參閱[如何：建立未系結的 Windows Forms DataGridView 控制項](how-to-create-an-unbound-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-111">For more information, see [How to: Create an Unbound Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="b0380-112">案例重點</span><span class="sxs-lookup"><span data-stu-id="b0380-112">Scenario Key Points</span></span>  
  
- <span data-ttu-id="b0380-113">在解除系結模式中，您會手動填入控制項。</span><span class="sxs-lookup"><span data-stu-id="b0380-113">In unbound mode, you populate the control manually.</span></span>  
  
- <span data-ttu-id="b0380-114">「解除系結模式」特別適用于少量的唯讀資料。</span><span class="sxs-lookup"><span data-stu-id="b0380-114">Unbound mode is particularly suited for small amounts of read-only data.</span></span>  
  
- <span data-ttu-id="b0380-115">解除系結模式也適用于類似試算表或稀疏的已填入資料表。</span><span class="sxs-lookup"><span data-stu-id="b0380-115">Unbound mode is also suited for spreadsheet-like or sparsely populated tables.</span></span>  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a><span data-ttu-id="b0380-116">案例2：查看和更新儲存在外部資料源中的資料</span><span class="sxs-lookup"><span data-stu-id="b0380-116">Scenario 2: Viewing and Updating Data Stored in an External Data Source</span></span>  
 <span data-ttu-id="b0380-117">您可以使用 <xref:System.Windows.Forms.DataGridView> 控制項做為使用者介面（UI），讓使用者可以透過它存取資料來源中保留的資料，例如資料庫資料表或商務物件的集合。</span><span class="sxs-lookup"><span data-stu-id="b0380-117">You can use the <xref:System.Windows.Forms.DataGridView> control as a user interface (UI) through which users can access data kept in a data source such as a database table or a collection of business objects.</span></span> <span data-ttu-id="b0380-118">如需詳細資訊，請參閱[如何：將資料系結至 Windows Forms DataGridView 控制項](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-118">For more information, see [How to: Bind Data to the Windows Forms DataGridView Control](how-to-bind-data-to-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="b0380-119">案例重點</span><span class="sxs-lookup"><span data-stu-id="b0380-119">Scenario Key Points</span></span>  
  
- <span data-ttu-id="b0380-120">系結模式可讓您連接到資料來源、根據資料來源屬性或資料庫資料行自動產生資料行，以及自動填入控制項。</span><span class="sxs-lookup"><span data-stu-id="b0380-120">Bound mode lets you connect to a data source, automatically generate columns based on the data source properties or database columns, and automatically populate the control.</span></span>  
  
- <span data-ttu-id="b0380-121">系結模式適用于大量使用者與資料的互動。</span><span class="sxs-lookup"><span data-stu-id="b0380-121">Bound mode is suited for heavy user interaction with data.</span></span> <span data-ttu-id="b0380-122">資料可以針對顯示進行格式化，而且使用者指定的資料可以剖析成資料來源所預期的格式。</span><span class="sxs-lookup"><span data-stu-id="b0380-122">Data can be formatted for display, and user-specified data can be parsed into the format expected by the data source.</span></span> <span data-ttu-id="b0380-123">可以偵測到資料輸入格式錯誤和資料庫條件約束錯誤，讓使用者可以收到警告，而且可以更正錯誤的儲存格。</span><span class="sxs-lookup"><span data-stu-id="b0380-123">Data entry formatting errors and database constraint errors can be detected so that users can be warned and erroneous cells can be corrected.</span></span>  
  
- <span data-ttu-id="b0380-124">其他功能（例如資料行排序、凍結和重新排列）可讓使用者以最方便的方式來查看其工作流程的資料。</span><span class="sxs-lookup"><span data-stu-id="b0380-124">Additional functionality such as column sorting, freezing, and reordering enable users to view data in the way most convenient for their workflow.</span></span>  
  
- <span data-ttu-id="b0380-125">剪貼簿支援可讓使用者將資料從您的應用程式複製到其他應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0380-125">Clipboard support enables users to copy data from your application into other applications.</span></span>  
  
## <a name="scenario-3-advanced-data"></a><span data-ttu-id="b0380-126">案例3： Advanced Data</span><span class="sxs-lookup"><span data-stu-id="b0380-126">Scenario 3: Advanced Data</span></span>  
 <span data-ttu-id="b0380-127">如果您有標準資料系結模型無法解決的特殊需求，您可以藉由執行*虛擬模式*來管理控制項與資料之間的互動。</span><span class="sxs-lookup"><span data-stu-id="b0380-127">If you have special needs that the standard data binding model does not address, you can manage the interaction between the control and your data by implementing *virtual mode*.</span></span> <span data-ttu-id="b0380-128">執行虛擬模式表示執行一或多個事件處理常式，可讓控制項要求資料格的相關資訊（如需要資訊）。</span><span class="sxs-lookup"><span data-stu-id="b0380-128">Implementing virtual mode means implementing one or more event handlers that let the control request information about cells as the information is needed.</span></span>  
  
 <span data-ttu-id="b0380-129">例如，如果您使用大量資料，您可能會想要執行虛擬模式以確保最佳的效率。</span><span class="sxs-lookup"><span data-stu-id="b0380-129">For example, if you work with large amounts of data, you may want to implement virtual mode to ensure optimal efficiency.</span></span> <span data-ttu-id="b0380-130">虛擬模式也很適合用來維護您所顯示的未系結資料行值，以及從另一個資料來源中取出的資料行。</span><span class="sxs-lookup"><span data-stu-id="b0380-130">Virtual mode is also useful for maintaining the values of unbound columns that you display along with columns retrieved from another data source.</span></span>  
  
 <span data-ttu-id="b0380-131">如需虛擬模式的詳細資訊，請參閱[逐步解說：在 Windows Forms DataGridView 控制項中執行虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-131">For more information about virtual mode, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="b0380-132">案例重點</span><span class="sxs-lookup"><span data-stu-id="b0380-132">Scenario Key Points</span></span>  
  
- <span data-ttu-id="b0380-133">當您需要微調效能時，虛擬模式適合用來顯示非常大量的資料。</span><span class="sxs-lookup"><span data-stu-id="b0380-133">Virtual mode is suited for displaying very large amounts of data when you need to fine-tune performance.</span></span>  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a><span data-ttu-id="b0380-134">案例4：自動調整資料列和資料行的大小</span><span class="sxs-lookup"><span data-stu-id="b0380-134">Scenario 4: Automatically Resizing Rows and Columns</span></span>  
 <span data-ttu-id="b0380-135">當您顯示定期更新的資料時，您可以自動調整資料列和資料行的大小，以確保所有內容都是可見的。</span><span class="sxs-lookup"><span data-stu-id="b0380-135">When you display data that is regularly updated, you can automatically resize rows and columns to ensure that all content is visible.</span></span> <span data-ttu-id="b0380-136"><xref:System.Windows.Forms.DataGridView> 控制項提供數個選項，可讓您啟用或停用手動調整大小、在特定時間以程式設計方式調整大小，或在內容變更時自動調整大小。</span><span class="sxs-lookup"><span data-stu-id="b0380-136">The <xref:System.Windows.Forms.DataGridView> control provides several options that let you enable or disable manual resizing, resize programmatically at specific times, or resize automatically whenever content changes.</span></span> <span data-ttu-id="b0380-137">如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的調整大小選項](sizing-options-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-137">For more information, see [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="b0380-138">案例重點</span><span class="sxs-lookup"><span data-stu-id="b0380-138">Scenario Key Points</span></span>  
  
- <span data-ttu-id="b0380-139">手動調整大小可讓使用者調整儲存格的高度和寬度。</span><span class="sxs-lookup"><span data-stu-id="b0380-139">Manual resizing enables users to adjust cell heights and widths.</span></span>  
  
- <span data-ttu-id="b0380-140">自動調整大小可讓您維護資料格大小，讓資料格內容永遠不會被裁剪。</span><span class="sxs-lookup"><span data-stu-id="b0380-140">Automatic resizing enables you to maintain cell sizes so that cell content is never clipped.</span></span>  
  
- <span data-ttu-id="b0380-141">以程式設計方式調整大小，可讓您在特定時間調整儲存格的大小，以避免連續自動調整的效能損失。</span><span class="sxs-lookup"><span data-stu-id="b0380-141">Programmatic resizing enables you to resize cells at specific times to avoid the performance penalty of continuous automatic resizing.</span></span>  
  
## <a name="scenario-5-simple-customization"></a><span data-ttu-id="b0380-142">案例5：簡單的自訂</span><span class="sxs-lookup"><span data-stu-id="b0380-142">Scenario 5: Simple Customization</span></span>  
 <span data-ttu-id="b0380-143"><xref:System.Windows.Forms.DataGridView> 控制項提供許多方式，讓您改變其基本外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="b0380-143">The <xref:System.Windows.Forms.DataGridView> control provides many ways for you to alter its basic appearance and behavior.</span></span> <span data-ttu-id="b0380-144">如需詳細資訊，請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-144">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="b0380-145">案例重點</span><span class="sxs-lookup"><span data-stu-id="b0380-145">Scenario Key Points</span></span>  
  
- <span data-ttu-id="b0380-146"><xref:System.Windows.Forms.DataGridViewCellStyle> 物件可讓您在多個層級，以及針對控制項的個別元素，提供色彩、字型、格式和位置資訊。</span><span class="sxs-lookup"><span data-stu-id="b0380-146"><xref:System.Windows.Forms.DataGridViewCellStyle> objects let you provide color, font, formatting, and positioning information at multiple levels and for individual elements of the control.</span></span>  
  
- <span data-ttu-id="b0380-147">儲存格樣式可以透過多個元素進行分層和共用，讓您重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0380-147">Cell styles can be layered and shared by multiple elements, letting you reuse code.</span></span>  
  
## <a name="scenario-6-advanced-customization"></a><span data-ttu-id="b0380-148">案例6： Advanced 自訂</span><span class="sxs-lookup"><span data-stu-id="b0380-148">Scenario 6: Advanced Customization</span></span>  
 <span data-ttu-id="b0380-149"><xref:System.Windows.Forms.DataGridView> 控制項提供許多方式，讓您自訂其外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="b0380-149">The <xref:System.Windows.Forms.DataGridView> control provides many ways for you to customize its appearance and behavior.</span></span>  
  
### <a name="scenario-key-points"></a><span data-ttu-id="b0380-150">案例重點</span><span class="sxs-lookup"><span data-stu-id="b0380-150">Scenario Key Points</span></span>  
  
- <span data-ttu-id="b0380-151">您可以提供自己的儲存格繪製程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0380-151">You can provide your own cell painting code.</span></span> <span data-ttu-id="b0380-152">如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項中自訂儲存格的外觀](customize-the-appearance-of-cells-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-152">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](customize-the-appearance-of-cells-in-the-datagrid.md).</span></span>  
  
- <span data-ttu-id="b0380-153">您可以提供自己的資料列繪製。</span><span class="sxs-lookup"><span data-stu-id="b0380-153">You can provide your own row painting.</span></span> <span data-ttu-id="b0380-154">例如，如果要建立的資料列具有跨越多個資料行的內容，這就很有用。</span><span class="sxs-lookup"><span data-stu-id="b0380-154">This is useful, for example, to create rows with content that spans multiple columns.</span></span> <span data-ttu-id="b0380-155">如需詳細資訊，請參閱[如何：在 Windows Forms DataGridView 控制項中自訂資料列的外觀](customize-the-appearance-of-rows-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-155">For more information, see [How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control](customize-the-appearance-of-rows-in-the-datagrid.md).</span></span>  
  
- <span data-ttu-id="b0380-156">您可以執行自己的儲存格和資料行類別，以自訂資料格外觀。</span><span class="sxs-lookup"><span data-stu-id="b0380-156">You can implement your own cell and column classes to customize cell appearance.</span></span> <span data-ttu-id="b0380-157">如需詳細資訊，請參閱[如何：藉由擴充其行為和外觀，自訂 Windows Forms DataGridView 控制項中的儲存格和資料行](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-157">For more information, see [How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).</span></span>  
  
- <span data-ttu-id="b0380-158">除了內建資料行類型所提供的控制項外，您還可以將自己的儲存格和資料行類別實作為裝載控制項。</span><span class="sxs-lookup"><span data-stu-id="b0380-158">You can implement your own cell and column classes to host controls other than the ones provided by the built-in column types.</span></span> <span data-ttu-id="b0380-159">如需詳細資訊，請參閱[如何： Windows Forms DataGridView 儲存格中的主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。</span><span class="sxs-lookup"><span data-stu-id="b0380-159">For more information, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0380-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0380-160">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b0380-161">DataGridView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b0380-161">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
