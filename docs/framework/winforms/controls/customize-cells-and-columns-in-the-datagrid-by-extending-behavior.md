---
title: 作法：擴充 Windows Forms DataGridView 控制項之儲存格和資料行的行為和外觀，以自訂儲存格和資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 0976a0e07aead1bbaf951c6db8266c5de1a31cd8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929707"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a><span data-ttu-id="07ffe-102">作法：擴充 Windows Forms DataGridView 控制項之儲存格和資料行的行為和外觀，以自訂儲存格和資料行</span><span class="sxs-lookup"><span data-stu-id="07ffe-102">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>
<span data-ttu-id="07ffe-103"><xref:System.Windows.Forms.DataGridView> 控制項提供數種方法使用屬性、事件和附屬類別來自訂其外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="07ffe-103">The <xref:System.Windows.Forms.DataGridView> control provides a number of ways to customize its appearance and behavior using properties, events, and companion classes.</span></span> <span data-ttu-id="07ffe-104">有時候除了這些功能可提供的以外，您可能有對於儲存格的更多需求。</span><span class="sxs-lookup"><span data-stu-id="07ffe-104">Occasionally, you may have requirements for your cells that go beyond what these features can provide.</span></span> <span data-ttu-id="07ffe-105">您可以建立自己的自訂 <xref:System.Windows.Forms.DataGridViewCell> 類別來提供擴充功能。</span><span class="sxs-lookup"><span data-stu-id="07ffe-105">You can create your own custom <xref:System.Windows.Forms.DataGridViewCell> class to provide extended functionality.</span></span>  
  
 <span data-ttu-id="07ffe-106">藉由衍生自 <xref:System.Windows.Forms.DataGridViewCell> 基底類別或其中一個衍生的類別，您可建立自訂的 <xref:System.Windows.Forms.DataGridViewCell> 類別。</span><span class="sxs-lookup"><span data-stu-id="07ffe-106">You create a custom <xref:System.Windows.Forms.DataGridViewCell> class by deriving from the <xref:System.Windows.Forms.DataGridViewCell> base class or one of its derived classes.</span></span> <span data-ttu-id="07ffe-107">雖然您可以在任何類型的資料行中顯示任何類型的儲存格，您通常也會建立自訂的 <xref:System.Windows.Forms.DataGridViewColumn> 類別，專門用於顯示儲存格類型。</span><span class="sxs-lookup"><span data-stu-id="07ffe-107">Although you can display any type of cell in any type of column, you will typically also create a custom <xref:System.Windows.Forms.DataGridViewColumn> class specialized for displaying your cell type.</span></span> <span data-ttu-id="07ffe-108">資料行類別衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 或其衍生類型之一。</span><span class="sxs-lookup"><span data-stu-id="07ffe-108">Column classes derive from <xref:System.Windows.Forms.DataGridViewColumn> or one of its derived types.</span></span>  
  
 <span data-ttu-id="07ffe-109">在下列程式碼範例中，您將建立自訂儲存格類別，稱為 `DataGridViewRolloverCell`，偵測滑鼠何時進入及離開儲存格邊界。</span><span class="sxs-lookup"><span data-stu-id="07ffe-109">In the following code example, you will create a custom cell class called `DataGridViewRolloverCell` that detects when the mouse enters and leaves the cell boundaries.</span></span> <span data-ttu-id="07ffe-110">當滑鼠在儲存格的邊界內時，會繪製內凹矩形。</span><span class="sxs-lookup"><span data-stu-id="07ffe-110">While the mouse is within the cell's bounds, an inset rectangle is drawn.</span></span> <span data-ttu-id="07ffe-111">這個新的類型衍生自 <xref:System.Windows.Forms.DataGridViewTextBoxCell>，在其他方面的行為如同其基底類別。</span><span class="sxs-lookup"><span data-stu-id="07ffe-111">This new type derives from <xref:System.Windows.Forms.DataGridViewTextBoxCell> and behaves in all other respects as its base class.</span></span> <span data-ttu-id="07ffe-112">附屬資料行類別稱為 `DataGridViewRolloverColumn`。</span><span class="sxs-lookup"><span data-stu-id="07ffe-112">The companion column class is called `DataGridViewRolloverColumn`.</span></span>  
  
 <span data-ttu-id="07ffe-113">若要使用這些類別，請建立一個表單，其中包含 <xref:System.Windows.Forms.DataGridView> 控制項，以及加入一個以上的 `DataGridViewRolloverColumn` 物件到 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合，並在控制項填入包含值的資料列。</span><span class="sxs-lookup"><span data-stu-id="07ffe-113">To use these classes, create a form containing a <xref:System.Windows.Forms.DataGridView> control, add one or more `DataGridViewRolloverColumn` objects to the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection, and populate the control with rows containing values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07ffe-114">如果您加入空白資料列，此範例將無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="07ffe-114">This example will not work correctly if you add empty rows.</span></span> <span data-ttu-id="07ffe-115">例如當您藉由設定 <xref:System.Windows.Forms.DataGridView.RowCount%2A> 屬性加入資料列至控制項時，會建立空白資料列。</span><span class="sxs-lookup"><span data-stu-id="07ffe-115">Empty rows are created, for example, when you add rows to the control by setting the <xref:System.Windows.Forms.DataGridView.RowCount%2A> property.</span></span> <span data-ttu-id="07ffe-116">這是因為在此情況下加入的資料列會自動共用，這表示 `DataGridViewRolloverCell` 物件不會具現化，直到您按一下個別的儲存格，因而導致相關的資料列變成非共用的。</span><span class="sxs-lookup"><span data-stu-id="07ffe-116">This is because the rows added in this case are automatically shared, which means that `DataGridViewRolloverCell` objects are not instantiated until you click on individual cells, thereby causing the associated rows to become unshared.</span></span>  
  
 <span data-ttu-id="07ffe-117">因為自訂這種類型的儲存格需要非共用的資料列，所以它並不適用於大型資料集的使用。</span><span class="sxs-lookup"><span data-stu-id="07ffe-117">Because this type of cell customization requires unshared rows, it is not appropriate for use with large data sets.</span></span> <span data-ttu-id="07ffe-118">如需有關資料列共用的詳細資訊, 請參閱[縮放 Windows Forms DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="07ffe-118">For more information about row sharing, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07ffe-119">當您自 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 中衍生時，以及在衍生類別中加入新的屬性時，請務必覆寫 `Clone` 方法，在複製作業期間複製新的屬性。</span><span class="sxs-lookup"><span data-stu-id="07ffe-119">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="07ffe-120">您也應該呼叫基底類別的 `Clone` 方法，以便將基底類別的屬性複製到新的儲存格或資料行。</span><span class="sxs-lookup"><span data-stu-id="07ffe-120">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a><span data-ttu-id="07ffe-121">若要自訂 DataGridView 控制項中的資料格和資料行</span><span class="sxs-lookup"><span data-stu-id="07ffe-121">To customize cells and columns in the DataGridView control</span></span>  
  
1. <span data-ttu-id="07ffe-122">從 <xref:System.Windows.Forms.DataGridViewTextBoxCell> 類型衍生新的儲存格類別，稱為 `DataGridViewRolloverCell`。</span><span class="sxs-lookup"><span data-stu-id="07ffe-122">Derive a new cell class, called `DataGridViewRolloverCell`, from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. <span data-ttu-id="07ffe-123">覆寫 <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> 類別中的 `DataGridViewRolloverCell` 方法。</span><span class="sxs-lookup"><span data-stu-id="07ffe-123">Override the <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> method in the `DataGridViewRolloverCell` class.</span></span> <span data-ttu-id="07ffe-124">在覆寫時，先呼叫基底類別實作，這會處理裝載的文字方塊功能。</span><span class="sxs-lookup"><span data-stu-id="07ffe-124">In the override, first call the base class implementation, which handles the hosted text box functionality.</span></span> <span data-ttu-id="07ffe-125">然後使用控制項的 <xref:System.Windows.Forms.Control.PointToClient%2A> 方法，將游標位置 (以螢幕座標表示) 轉換為 <xref:System.Windows.Forms.DataGridView> 工作區座標。</span><span class="sxs-lookup"><span data-stu-id="07ffe-125">Then use the control's <xref:System.Windows.Forms.Control.PointToClient%2A> method to transform the cursor position (in screen coordinates) to the <xref:System.Windows.Forms.DataGridView> client area's coordinates.</span></span> <span data-ttu-id="07ffe-126">如果滑鼠座標落在儲存格的邊界內，則繪製內凹矩形。</span><span class="sxs-lookup"><span data-stu-id="07ffe-126">If the mouse coordinates fall within the bounds of the cell, draw the inset rectangle.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. <span data-ttu-id="07ffe-127">覆寫 `DataGridViewRolloverCell` 類別中的 <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> 和 <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> 方法，當滑鼠指標進入或離開儲存格時，強制重新繪製儲存格。</span><span class="sxs-lookup"><span data-stu-id="07ffe-127">Override the <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> and <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> methods in the `DataGridViewRolloverCell` class to force cells to repaint themselves when the mouse pointer enters or leaves them.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. <span data-ttu-id="07ffe-128">從 <xref:System.Windows.Forms.DataGridViewColumn> 類型衍生新的類別，稱為 `DataGridViewRolloverCellColumn`。</span><span class="sxs-lookup"><span data-stu-id="07ffe-128">Derive a new class, called `DataGridViewRolloverCellColumn`, from the <xref:System.Windows.Forms.DataGridViewColumn> type.</span></span> <span data-ttu-id="07ffe-129">在建構函式中，指派新的 `DataGridViewRolloverCell` 物件至其 <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="07ffe-129">In the constructor, assign a new `DataGridViewRolloverCell` object to its <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a><span data-ttu-id="07ffe-130">範例</span><span class="sxs-lookup"><span data-stu-id="07ffe-130">Example</span></span>  
 <span data-ttu-id="07ffe-131">完整的程式碼範例包含小型測試表單，會示範自訂儲存格類型的行為。</span><span class="sxs-lookup"><span data-stu-id="07ffe-131">The complete code example includes a small test form that demonstrates the behavior of the custom cell type.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07ffe-132">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="07ffe-132">Compiling the Code</span></span>  
 <span data-ttu-id="07ffe-133">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="07ffe-133">This example requires:</span></span>  
  
- <span data-ttu-id="07ffe-134">System、System.Windows.Forms 和 System.Drawing 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="07ffe-134">References to the System, System.Windows.Forms, and System.Drawing assemblies.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="07ffe-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07ffe-135">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="07ffe-136">自訂 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="07ffe-136">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="07ffe-137">DataGridView 控制項架構</span><span class="sxs-lookup"><span data-stu-id="07ffe-137">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="07ffe-138">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="07ffe-138">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="07ffe-139">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="07ffe-139">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
