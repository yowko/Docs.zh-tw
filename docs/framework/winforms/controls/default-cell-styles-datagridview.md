---
title: 作法：使用設計工具設定 Windows Forms DataGridView 控制項的預設儲存格樣式和資料格式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 53faf31c8dd3be1606c491e95594c4aae5aedf98
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039664"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="41185-102">作法：使用設計工具設定 Windows Forms DataGridView 控制項的預設儲存格樣式和資料格式</span><span class="sxs-lookup"><span data-stu-id="41185-102">How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="41185-103"><xref:System.Windows.Forms.DataGridView>控制項可讓您針對整個控制項、特定資料行、資料列和資料行標頭, 以及替代資料列來建立總帳效果, 指定預設的儲存格樣式和儲存格資料格式。</span><span class="sxs-lookup"><span data-stu-id="41185-103">The <xref:System.Windows.Forms.DataGridView> control lets you specify default cell styles and cell data formats for the entire control, for specific columns, for row and column headers, and for alternating rows to create a ledger effect.</span></span> <span data-ttu-id="41185-104">針對整個控制項所設定的預設樣式, 會由資料行和交替資料列的預設樣式所覆寫。</span><span class="sxs-lookup"><span data-stu-id="41185-104">Default styles set for the entire control are overridden by default styles set for columns and alternating rows.</span></span> <span data-ttu-id="41185-105">此外, 您在程式碼中針對個別資料列和資料格所設定的樣式, 會覆寫預設樣式。</span><span class="sxs-lookup"><span data-stu-id="41185-105">Additionally, styles that you set in code for individual rows and cells override the default styles.</span></span>

<span data-ttu-id="41185-106">如需有關儲存格樣式的詳細資訊, 請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="41185-106">For more information about cell styles, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="41185-107">若要設定替代資料列的樣式[, 請參閱如何:使用設計](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)工具設定 Windows Forms DataGridView 控制項的替代資料列樣式。</span><span class="sxs-lookup"><span data-stu-id="41185-107">To set styles for alternating rows, see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).</span></span>

<span data-ttu-id="41185-108">您也可以使用<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>屬性來設定樣式, 以影響將加入至控制項的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="41185-108">You can also set styles using the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property to affect all rows that will be added to the control.</span></span> <span data-ttu-id="41185-109">如需資料列範本的詳細資訊, [請參閱如何:使用 [資料列] 範本來自訂 Windows Forms DataGridView 控制項](use-the-row-template-to-customize-rows-in-the-datagrid.md)中的資料列。</span><span class="sxs-lookup"><span data-stu-id="41185-109">For more information about the row template, see [How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control](use-the-row-template-to-customize-rows-in-the-datagrid.md).</span></span>

<span data-ttu-id="41185-110">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="41185-110">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="41185-111">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="41185-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="to-set-default-styles-for-all-cells-in-the-control"></a><span data-ttu-id="41185-112">設定控制項中所有儲存格的預設樣式</span><span class="sxs-lookup"><span data-stu-id="41185-112">To set default styles for all cells in the control</span></span>

1. <span data-ttu-id="41185-113">在設計工具中選取控制項。<xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="41185-113">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>

2. <span data-ttu-id="41185-114">在 [**屬性**] 視窗![中, 按一下<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>、 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>或<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>屬性旁邊的省略號按鈕 (Visual Studio 的](./media/visual-studio-ellipsis-button.png)屬性視窗中的省略號按鈕 (...))。</span><span class="sxs-lookup"><span data-stu-id="41185-114">In the **Properties** window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> property.</span></span> <span data-ttu-id="41185-115">[ **CellStyle**產生器] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="41185-115">The **CellStyle Builder** dialog box appears.</span></span>

3. <span data-ttu-id="41185-116">藉由設定屬性來定義樣式, 使用**預覽**窗格來確認您的選擇。</span><span class="sxs-lookup"><span data-stu-id="41185-116">Define the style by setting the properties, using the **Preview** pane to confirm your choices.</span></span>

> [!NOTE]
> <span data-ttu-id="41185-117">如果啟用視覺化樣式, 則目前的主題會自動將資料列和<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>資料行標頭 (除外) 樣式化, 以覆<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>寫<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>和屬性值。</span><span class="sxs-lookup"><span data-stu-id="41185-117">If visual styles are enabled, the row and column headers (except for the <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) are automatically styled by the current theme, overriding the <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> property values.</span></span>
>
> <span data-ttu-id="41185-118">您可以使用設計工具來設定多<xref:System.Windows.Forms.DataGridView>個所選控制項的儲存格樣式, 但只有在它們的值與您要修改的儲存格樣式屬性相同時。</span><span class="sxs-lookup"><span data-stu-id="41185-118">You can set cell styles for multiple selected <xref:System.Windows.Forms.DataGridView> controls using the designer, but only if they have identical values for the cell style property you want to modify.</span></span> <span data-ttu-id="41185-119">如果該屬性的任何儲存格樣式不同, [ **CellStyle**產生器] 對話方塊的 [**屬性**] 視窗就會是空白。</span><span class="sxs-lookup"><span data-stu-id="41185-119">If any cell styles differ for that property, the **Properties** windows of the **CellStyle Builder** dialog box will be blank.</span></span>

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a><span data-ttu-id="41185-120">若要設定個別資料行中儲存格的預設樣式</span><span class="sxs-lookup"><span data-stu-id="41185-120">To set default styles for cells in individual columns</span></span>

1. <span data-ttu-id="41185-121">以滑鼠右鍵按一下<xref:System.Windows.Forms.DataGridView>設計工具中的控制項, 然後選擇 [**編輯資料行**]。</span><span class="sxs-lookup"><span data-stu-id="41185-121">Right-click the <xref:System.Windows.Forms.DataGridView> control in the designer and choose **Edit Columns**.</span></span>

2. <span data-ttu-id="41185-122">從 [選取的資料**行**] 清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="41185-122">Select a column from the **Selected Columns** list.</span></span>

3. <span data-ttu-id="41185-123">在 資料**行屬性**] 方格中, 按一下![ <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>屬性旁邊的省略號按鈕 ([Visual Studio 的](./media/visual-studio-ellipsis-button.png)屬性視窗中的省略號按鈕 (...))。</span><span class="sxs-lookup"><span data-stu-id="41185-123">In the **Column Properties** grid, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="41185-124">[ **CellStyle**產生器] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="41185-124">The **CellStyle Builder** dialog box appears.</span></span>

4. <span data-ttu-id="41185-125">藉由設定屬性來定義樣式, 使用**預覽**窗格來確認您的選擇。</span><span class="sxs-lookup"><span data-stu-id="41185-125">Define the style by setting the properties, using the **Preview** pane to confirm your choices.</span></span>

### <a name="to-format-data-in-cells"></a><span data-ttu-id="41185-126">格式化儲存格中的資料</span><span class="sxs-lookup"><span data-stu-id="41185-126">To format data in cells</span></span>

1. <span data-ttu-id="41185-127">使用上述其中一個程式, 顯示與預設儲存格樣式屬性相關的 [ **CellStyle**產生器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="41185-127">Use one of the preceding procedures to display a **CellStyle Builder** dialog box related to a default cell style property.</span></span>

2. <span data-ttu-id="41185-128">在 [ **CellStyle**產生器] 對話方塊中, 按一下![ <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>屬性旁邊的省略號按鈕 (Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...)。</span><span class="sxs-lookup"><span data-stu-id="41185-128">In the **CellStyle Builder** dialog box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property.</span></span> <span data-ttu-id="41185-129">[**格式字串**] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="41185-129">The **Format String** dialog box appears.</span></span>

3. <span data-ttu-id="41185-130">選取格式類型, 然後使用 [**範例**] 方塊來確認您的選擇, 以修改類型的詳細資料 (例如要顯示的小數位數)。</span><span class="sxs-lookup"><span data-stu-id="41185-130">Select a format type, then modify the details of the type (such as the number of decimal places to display), using the **Sample** box to confirm your choices.</span></span>

4. <span data-ttu-id="41185-131">如果您要將<xref:System.Windows.Forms.DataGridView>控制項系結至可能包含 null 值的資料來源, 請在 [ **null 值**] 文字方塊中填入。</span><span class="sxs-lookup"><span data-stu-id="41185-131">If you are binding the <xref:System.Windows.Forms.DataGridView> control to a data source that is likely to contain null values, fill in the **Null Value** text box.</span></span> <span data-ttu-id="41185-132">當資料格值等於 null 參考 (`Nothing` Visual Basic) 或<xref:System.DBNull.Value?displayProperty=nameWithType>時, 就會顯示此值。</span><span class="sxs-lookup"><span data-stu-id="41185-132">This value is displayed when the cell value is equal to a null reference (`Nothing` in Visual Basic) or <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>

## <a name="see-also"></a><span data-ttu-id="41185-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41185-133">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [<span data-ttu-id="41185-134">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="41185-134">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="41185-135">如何：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="41185-135">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [<span data-ttu-id="41185-136">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="41185-136">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="41185-137">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="41185-137">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
