---
title: DataGridView 控制項架構
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742536"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="e83fe-102">DataGridView 控制項架構 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="e83fe-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="e83fe-103"><xref:System.Windows.Forms.DataGridView> 控制項和其相關類別的設計，是彈性且可擴充的系統，可用於顯示和編輯表格式資料。</span><span class="sxs-lookup"><span data-stu-id="e83fe-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="e83fe-104">這些類別全都包含在 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間中，而且全都以 "DataGridView" 前置詞命名。</span><span class="sxs-lookup"><span data-stu-id="e83fe-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="e83fe-105">架構項目</span><span class="sxs-lookup"><span data-stu-id="e83fe-105">Architecture Elements</span></span>  
 <span data-ttu-id="e83fe-106">主要 <xref:System.Windows.Forms.DataGridView> 隨附類別衍生自 <xref:System.Windows.Forms.DataGridViewElement>。</span><span class="sxs-lookup"><span data-stu-id="e83fe-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="e83fe-107">下列物件模型說明 <xref:System.Windows.Forms.DataGridViewElement> 繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="e83fe-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![顯示 DataGridViewElement 物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="e83fe-109"><xref:System.Windows.Forms.DataGridViewElement> 類別會提供父 <xref:System.Windows.Forms.DataGridView> 控制項的參考，並具有 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 屬性，它會保存一個值，表示來自 <xref:System.Windows.Forms.DataGridViewElementStates> 列舉的值組合。</span><span class="sxs-lookup"><span data-stu-id="e83fe-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="e83fe-110">下列各節會更詳細地說明 <xref:System.Windows.Forms.DataGridView> 附屬類別。</span><span class="sxs-lookup"><span data-stu-id="e83fe-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="e83fe-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="e83fe-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="e83fe-112"><xref:System.Windows.Forms.DataGridViewElementStates> 列舉包含下列值：</span><span class="sxs-lookup"><span data-stu-id="e83fe-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="e83fe-113">這個列舉的值可以與位邏輯運算子結合，因此 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 屬性可以同時表示一次以上的狀態。</span><span class="sxs-lookup"><span data-stu-id="e83fe-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="e83fe-114">例如，<xref:System.Windows.Forms.DataGridViewElement> 可以同時 <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>、<xref:System.Windows.Forms.DataGridViewElementStates.Selected>和 <xref:System.Windows.Forms.DataGridViewElementStates.Visible>。</span><span class="sxs-lookup"><span data-stu-id="e83fe-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="e83fe-115">資料格和頻帶</span><span class="sxs-lookup"><span data-stu-id="e83fe-115">Cells and Bands</span></span>  
 <span data-ttu-id="e83fe-116"><xref:System.Windows.Forms.DataGridView> 控制項包含兩種基本的物件：資料格和波段。</span><span class="sxs-lookup"><span data-stu-id="e83fe-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="e83fe-117">所有資料格都衍生自 <xref:System.Windows.Forms.DataGridViewCell> 基類。</span><span class="sxs-lookup"><span data-stu-id="e83fe-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="e83fe-118">兩種類型的群組（<xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.DataGridViewRow>）皆衍生自 <xref:System.Windows.Forms.DataGridViewBand> 基類。</span><span class="sxs-lookup"><span data-stu-id="e83fe-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="e83fe-119"><xref:System.Windows.Forms.DataGridView> 控制項與數個類別交互操作，但最常遇到的是 <xref:System.Windows.Forms.DataGridViewCell>、<xref:System.Windows.Forms.DataGridViewColumn>和 <xref:System.Windows.Forms.DataGridViewRow>。</span><span class="sxs-lookup"><span data-stu-id="e83fe-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="e83fe-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="e83fe-120">DataGridViewCell</span></span>  
 <span data-ttu-id="e83fe-121">資料格是 <xref:System.Windows.Forms.DataGridView>的互動基礎單位。</span><span class="sxs-lookup"><span data-stu-id="e83fe-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="e83fe-122">顯示是以儲存格為中心，而資料輸入通常是透過儲存格來執行。</span><span class="sxs-lookup"><span data-stu-id="e83fe-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="e83fe-123">您可以使用 <xref:System.Windows.Forms.DataGridViewRow> 類別的 <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> 集合來存取資料格，而且可以使用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 集合來存取選取的儲存格。</span><span class="sxs-lookup"><span data-stu-id="e83fe-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e83fe-124">下列物件模型說明這種用法，並顯示 <xref:System.Windows.Forms.DataGridViewCell> 繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="e83fe-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![顯示 DataGridViewCell 物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="e83fe-126"><xref:System.Windows.Forms.DataGridViewCell> 類型是抽象基類，所有的資料格類型都會從中衍生。</span><span class="sxs-lookup"><span data-stu-id="e83fe-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="e83fe-127"><xref:System.Windows.Forms.DataGridViewCell> 及其衍生型別不是 Windows Forms 控制項，但是某些主機 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="e83fe-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="e83fe-128">資料格支援的任何編輯功能通常是由裝載的控制項所處理。</span><span class="sxs-lookup"><span data-stu-id="e83fe-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="e83fe-129"><xref:System.Windows.Forms.DataGridViewCell> 物件無法以 Windows Forms 控制項的相同方式來控制自己的外觀和繪製功能。</span><span class="sxs-lookup"><span data-stu-id="e83fe-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="e83fe-130">相反地，<xref:System.Windows.Forms.DataGridView> 會負責其 <xref:System.Windows.Forms.DataGridViewCell> 物件的外觀。</span><span class="sxs-lookup"><span data-stu-id="e83fe-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="e83fe-131">您可以藉由與 <xref:System.Windows.Forms.DataGridView> 控制項的屬性和事件互動，大幅影響資料格的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="e83fe-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="e83fe-132">當您對於超出 <xref:System.Windows.Forms.DataGridView> 控制項功能的自訂有特殊需求時，您可以實作為衍生自 <xref:System.Windows.Forms.DataGridViewCell> 或其其中一個子類別的類別。</span><span class="sxs-lookup"><span data-stu-id="e83fe-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="e83fe-133">下列清單顯示衍生自 <xref:System.Windows.Forms.DataGridViewCell>的類別：</span><span class="sxs-lookup"><span data-stu-id="e83fe-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- <span data-ttu-id="e83fe-134">您的自訂資料格類型</span><span class="sxs-lookup"><span data-stu-id="e83fe-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="e83fe-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="e83fe-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="e83fe-136"><xref:System.Windows.Forms.DataGridView> 控制項之附加資料存放區的架構，會以 <xref:System.Windows.Forms.DataGridView> 控制項的資料行表示。</span><span class="sxs-lookup"><span data-stu-id="e83fe-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="e83fe-137">您可以使用 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合來存取 <xref:System.Windows.Forms.DataGridView> 控制項的資料行。</span><span class="sxs-lookup"><span data-stu-id="e83fe-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="e83fe-138">您可以使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 集合來存取選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="e83fe-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="e83fe-139">下列物件模型說明這種用法，並顯示 <xref:System.Windows.Forms.DataGridViewColumn> 繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="e83fe-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![顯示 DataGridViewColumn 物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="e83fe-141">某些索引鍵資料格類型具有對應的資料行類型。</span><span class="sxs-lookup"><span data-stu-id="e83fe-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="e83fe-142">這些衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 基類。</span><span class="sxs-lookup"><span data-stu-id="e83fe-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="e83fe-143">下列清單顯示衍生自 <xref:System.Windows.Forms.DataGridViewColumn>的類別：</span><span class="sxs-lookup"><span data-stu-id="e83fe-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- <span data-ttu-id="e83fe-144">您的自訂資料行類型</span><span class="sxs-lookup"><span data-stu-id="e83fe-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="e83fe-145">DataGridView 編輯控制項</span><span class="sxs-lookup"><span data-stu-id="e83fe-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="e83fe-146">支援先進編輯功能的儲存格通常會使用衍生自 Windows Forms 控制項的裝載控制項。</span><span class="sxs-lookup"><span data-stu-id="e83fe-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="e83fe-147">這些控制項也會執行 <xref:System.Windows.Forms.IDataGridViewEditingControl> 介面。</span><span class="sxs-lookup"><span data-stu-id="e83fe-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="e83fe-148">下列物件模型說明這些控制項的使用方式。</span><span class="sxs-lookup"><span data-stu-id="e83fe-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![顯示 DataGridView 編輯控制項物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="e83fe-150"><xref:System.Windows.Forms.DataGridView> 控制項提供下列編輯控制項：</span><span class="sxs-lookup"><span data-stu-id="e83fe-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="e83fe-151">如需建立您自己的編輯控制項的詳細資訊，請參閱[如何： Windows Forms DataGridView 儲存格中的主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。</span><span class="sxs-lookup"><span data-stu-id="e83fe-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="e83fe-152">下表說明資料格類型、資料行類型和編輯控制項之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e83fe-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="e83fe-153">資料格類型</span><span class="sxs-lookup"><span data-stu-id="e83fe-153">Cell type</span></span>|<span data-ttu-id="e83fe-154">Hosted 控制項</span><span class="sxs-lookup"><span data-stu-id="e83fe-154">Hosted control</span></span>|<span data-ttu-id="e83fe-155">資料行類型</span><span class="sxs-lookup"><span data-stu-id="e83fe-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="e83fe-156">N/A</span><span class="sxs-lookup"><span data-stu-id="e83fe-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="e83fe-157">N/A</span><span class="sxs-lookup"><span data-stu-id="e83fe-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="e83fe-158">N/A</span><span class="sxs-lookup"><span data-stu-id="e83fe-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="e83fe-159">N/A</span><span class="sxs-lookup"><span data-stu-id="e83fe-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="e83fe-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="e83fe-160">DataGridViewRow</span></span>  
 <span data-ttu-id="e83fe-161"><xref:System.Windows.Forms.DataGridViewRow> 類別會從附加 <xref:System.Windows.Forms.DataGridView> 控制項的資料存放區中，顯示記錄的資料欄位。</span><span class="sxs-lookup"><span data-stu-id="e83fe-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="e83fe-162">您可以使用 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合來存取 <xref:System.Windows.Forms.DataGridView> 控制項的資料列。</span><span class="sxs-lookup"><span data-stu-id="e83fe-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="e83fe-163">您可以使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 集合來存取選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="e83fe-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="e83fe-164">下列物件模型說明這種用法，並顯示 <xref:System.Windows.Forms.DataGridViewRow> 繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="e83fe-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![顯示 DataGridViewRow 物件模型階層的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="e83fe-166">您可以從 <xref:System.Windows.Forms.DataGridViewRow> 類別衍生自己的型別，雖然這通常不是必要的。</span><span class="sxs-lookup"><span data-stu-id="e83fe-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="e83fe-167"><xref:System.Windows.Forms.DataGridView> 控制項有數個與資料列相關的事件和屬性，可自訂其 <xref:System.Windows.Forms.DataGridViewRow> 物件的行為。</span><span class="sxs-lookup"><span data-stu-id="e83fe-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="e83fe-168">如果您啟用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> 屬性，加入新資料列的特殊資料列就會顯示為最後一個資料列。</span><span class="sxs-lookup"><span data-stu-id="e83fe-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="e83fe-169">這個資料列是 <xref:System.Windows.Forms.DataGridView.Rows%2A> 集合的一部分，但它有特殊功能需要您的注意。</span><span class="sxs-lookup"><span data-stu-id="e83fe-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="e83fe-170">如需詳細資訊，請參閱在[Windows Forms DataGridView 控制項中使用資料列做為新記錄](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e83fe-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83fe-171">請參閱</span><span class="sxs-lookup"><span data-stu-id="e83fe-171">See also</span></span>

- [<span data-ttu-id="e83fe-172">DataGridView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e83fe-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="e83fe-173">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="e83fe-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e83fe-174">使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列</span><span class="sxs-lookup"><span data-stu-id="e83fe-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
