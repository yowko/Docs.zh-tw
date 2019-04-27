---
title: DataGridView 控制項架構 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 892168ec282fbf168c43515e0718fe5486a345a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011610"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="7825e-102">DataGridView 控制項架構 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="7825e-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="7825e-103"><xref:System.Windows.Forms.DataGridView>控制項以及與其相關的類別都是設計成有彈性、 可擴充的系統，來顯示和編輯表格式資料。</span><span class="sxs-lookup"><span data-stu-id="7825e-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="7825e-104">這些類別包含在<xref:System.Windows.Forms?displayProperty=nameWithType>命名空間，而且它們所有以"DataGridView"前置詞命名。</span><span class="sxs-lookup"><span data-stu-id="7825e-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="7825e-105">架構項目</span><span class="sxs-lookup"><span data-stu-id="7825e-105">Architecture Elements</span></span>  
 <span data-ttu-id="7825e-106">主要<xref:System.Windows.Forms.DataGridView>附屬類別衍生自<xref:System.Windows.Forms.DataGridViewElement>。</span><span class="sxs-lookup"><span data-stu-id="7825e-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="7825e-107">下列物件模型說明<xref:System.Windows.Forms.DataGridViewElement>繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="7825e-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![顯示 DataGridViewElement 物件模型階層架構的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="7825e-109"><xref:System.Windows.Forms.DataGridViewElement>類別提供的參考至父代<xref:System.Windows.Forms.DataGridView>控制項，並具有<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性，其中包含值，表示從值的組合<xref:System.Windows.Forms.DataGridViewElementStates>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="7825e-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="7825e-110">下列各節說明<xref:System.Windows.Forms.DataGridView>附屬類別中更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7825e-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="7825e-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="7825e-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="7825e-112"><xref:System.Windows.Forms.DataGridViewElementStates>列舉型別包含下列值：</span><span class="sxs-lookup"><span data-stu-id="7825e-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="7825e-113">這個列舉型別的值可以結合這些位元的邏輯運算子，因此<xref:System.Windows.Forms.DataGridViewElement.State%2A>屬性可以用來表示多個狀態一次。</span><span class="sxs-lookup"><span data-stu-id="7825e-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="7825e-114">例如，<xref:System.Windows.Forms.DataGridViewElement>可以同時<xref:System.Windows.Forms.DataGridViewElementStates.Frozen>， <xref:System.Windows.Forms.DataGridViewElementStates.Selected>，和<xref:System.Windows.Forms.DataGridViewElementStates.Visible>。</span><span class="sxs-lookup"><span data-stu-id="7825e-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="7825e-115">儲存格和群組列</span><span class="sxs-lookup"><span data-stu-id="7825e-115">Cells and Bands</span></span>  
 <span data-ttu-id="7825e-116"><xref:System.Windows.Forms.DataGridView>控制項包含兩個基本類型的物件： 資料格和群組列。</span><span class="sxs-lookup"><span data-stu-id="7825e-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="7825e-117">所有資料格衍生自<xref:System.Windows.Forms.DataGridViewCell>基底類別。</span><span class="sxs-lookup"><span data-stu-id="7825e-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="7825e-118">這兩種帶狀<xref:System.Windows.Forms.DataGridViewColumn>並<xref:System.Windows.Forms.DataGridViewRow>，都是衍生自<xref:System.Windows.Forms.DataGridViewBand>基底類別。</span><span class="sxs-lookup"><span data-stu-id="7825e-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="7825e-119"><xref:System.Windows.Forms.DataGridView>控制項互通的數個類別，但是最常遇到<xref:System.Windows.Forms.DataGridViewCell>， <xref:System.Windows.Forms.DataGridViewColumn>，和<xref:System.Windows.Forms.DataGridViewRow>。</span><span class="sxs-lookup"><span data-stu-id="7825e-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="7825e-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="7825e-120">DataGridViewCell</span></span>  
 <span data-ttu-id="7825e-121">儲存格是互動的基本單位<xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="7825e-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="7825e-122">顯示為置中對齊資料格，並輸入資料通常會執行到的資料格。</span><span class="sxs-lookup"><span data-stu-id="7825e-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="7825e-123">您可以使用來存取資料格<xref:System.Windows.Forms.DataGridViewRow.Cells%2A>的集合<xref:System.Windows.Forms.DataGridViewRow>類別，而您可以使用存取選取的資料格<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>的集合<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="7825e-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="7825e-124">下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewCell>繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="7825e-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![顯示 DataGridViewCell 物件模型階層架構的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="7825e-126"><xref:System.Windows.Forms.DataGridViewCell>型別是抽象的基底類別，從其中衍生所有的資料格類型。</span><span class="sxs-lookup"><span data-stu-id="7825e-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="7825e-127"><xref:System.Windows.Forms.DataGridViewCell> 和其衍生型別不是 Windows Forms 控制項，而某些主機的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="7825e-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="7825e-128">裝載的控制項通常會處理任何支援的資料格的編輯功能。</span><span class="sxs-lookup"><span data-stu-id="7825e-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="7825e-129"><xref:System.Windows.Forms.DataGridViewCell> Windows Form 控制項，物件相同的方式控制自己的外觀和繪製功能。</span><span class="sxs-lookup"><span data-stu-id="7825e-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="7825e-130">相反地，<xref:System.Windows.Forms.DataGridView>負責的外觀及其<xref:System.Windows.Forms.DataGridViewCell>物件。</span><span class="sxs-lookup"><span data-stu-id="7825e-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="7825e-131">您可以大幅影響的外觀和行為的資料格與互動<xref:System.Windows.Forms.DataGridView>控制項的屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="7825e-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="7825e-132">當您有特殊需求的功能，自訂<xref:System.Windows.Forms.DataGridView>控制項，您可以實作自己的類別衍生自<xref:System.Windows.Forms.DataGridViewCell>或其中一個子類別。</span><span class="sxs-lookup"><span data-stu-id="7825e-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="7825e-133">下列清單顯示衍生自的類別<xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="7825e-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   <span data-ttu-id="7825e-134">您的自訂儲存格型別</span><span class="sxs-lookup"><span data-stu-id="7825e-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="7825e-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="7825e-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="7825e-136">結構描述<xref:System.Windows.Forms.DataGridView>控制的連接的資料存放區以表示<xref:System.Windows.Forms.DataGridView>控制項的資料行。</span><span class="sxs-lookup"><span data-stu-id="7825e-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="7825e-137">您可以存取<xref:System.Windows.Forms.DataGridView>控制項的資料行使用<xref:System.Windows.Forms.DataGridView.Columns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="7825e-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="7825e-138">您可以使用來存取所選資料行<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="7825e-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="7825e-139">下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewColumn>繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="7825e-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![顯示 DataGridViewColumn 物件模型階層架構的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="7825e-141">某些索引鍵的資料格類型有對應的資料行類型。</span><span class="sxs-lookup"><span data-stu-id="7825e-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="7825e-142">這些衍生自<xref:System.Windows.Forms.DataGridViewColumn>基底類別。</span><span class="sxs-lookup"><span data-stu-id="7825e-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="7825e-143">下列清單顯示衍生自的類別<xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="7825e-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="7825e-144">您的自訂資料行類型</span><span class="sxs-lookup"><span data-stu-id="7825e-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="7825e-145">DataGridView 編輯控制項</span><span class="sxs-lookup"><span data-stu-id="7825e-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="7825e-146">通常支援進階的編輯功能的資料格會使用裝載的控制項是衍生自 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="7825e-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="7825e-147">這些控制項也會實作<xref:System.Windows.Forms.IDataGridViewEditingControl>介面。</span><span class="sxs-lookup"><span data-stu-id="7825e-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="7825e-148">下列物件模型會說明這些控制項的用法。</span><span class="sxs-lookup"><span data-stu-id="7825e-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![此圖表顯示 DataGridView 編輯控制項物件模型階層架構。](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="7825e-150">下列的編輯控制項所提供的<xref:System.Windows.Forms.DataGridView>控制項：</span><span class="sxs-lookup"><span data-stu-id="7825e-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="7825e-151">如需建立自己的編輯控制項的資訊，請參閱[How to:Windows Forms DataGridView 儲存格主控制項](how-to-host-controls-in-windows-forms-datagridview-cells.md)。</span><span class="sxs-lookup"><span data-stu-id="7825e-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="7825e-152">下表說明資料格類型、 資料行類型，以及編輯控制項之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7825e-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="7825e-153">資料格類型</span><span class="sxs-lookup"><span data-stu-id="7825e-153">Cell type</span></span>|<span data-ttu-id="7825e-154">裝載的控制項</span><span class="sxs-lookup"><span data-stu-id="7825e-154">Hosted control</span></span>|<span data-ttu-id="7825e-155">資料行類型</span><span class="sxs-lookup"><span data-stu-id="7825e-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="7825e-156">N/A</span><span class="sxs-lookup"><span data-stu-id="7825e-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="7825e-157">N/A</span><span class="sxs-lookup"><span data-stu-id="7825e-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="7825e-158">N/A</span><span class="sxs-lookup"><span data-stu-id="7825e-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="7825e-159">N/A</span><span class="sxs-lookup"><span data-stu-id="7825e-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="7825e-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="7825e-160">DataGridViewRow</span></span>  
 <span data-ttu-id="7825e-161"><xref:System.Windows.Forms.DataGridViewRow>類別會顯示記錄的資料欄位從資料存放區複製到其中<xref:System.Windows.Forms.DataGridView>控制項所附加的。</span><span class="sxs-lookup"><span data-stu-id="7825e-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="7825e-162">您可以存取<xref:System.Windows.Forms.DataGridView>控制項的資料列，使用<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="7825e-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="7825e-163">您可以使用來存取選取的資料列<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="7825e-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="7825e-164">下列物件模型說明這種使用方式，以及顯示<xref:System.Windows.Forms.DataGridViewRow>繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="7825e-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![顯示 DataGridViewRow 物件模型階層架構的圖表。](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="7825e-166">您可以衍生自己的型別，從<xref:System.Windows.Forms.DataGridViewRow>類別，雖然這通常不是必要的。</span><span class="sxs-lookup"><span data-stu-id="7825e-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="7825e-167"><xref:System.Windows.Forms.DataGridView>控制項有數個資料列相關的事件和自訂的行為的屬性其<xref:System.Windows.Forms.DataGridViewRow>物件。</span><span class="sxs-lookup"><span data-stu-id="7825e-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="7825e-168">如果您啟用<xref:System.Windows.Forms.DataGridView>控制項的<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>屬性，加入新資料列的特殊資料列會顯示為最後一個資料列。</span><span class="sxs-lookup"><span data-stu-id="7825e-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="7825e-169">此資料列屬於<xref:System.Windows.Forms.DataGridView.Rows%2A>集合，但它有可能需要注意的特殊功能。</span><span class="sxs-lookup"><span data-stu-id="7825e-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="7825e-170">如需詳細資訊，請參閱 <<c0> [ 使用 Windows Form DataGridView 控制項中的新資料錄的資料列](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="7825e-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7825e-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7825e-171">See also</span></span>

- [<span data-ttu-id="7825e-172">DataGridView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="7825e-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="7825e-173">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="7825e-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7825e-174">使用 Windows Forms DataGridView 控制項中用於新增記錄的資料列</span><span class="sxs-lookup"><span data-stu-id="7825e-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
