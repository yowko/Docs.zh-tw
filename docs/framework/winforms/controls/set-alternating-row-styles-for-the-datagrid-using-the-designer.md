---
title: 作法：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 1be746d4cce36344e034692a0e2e8e6a9e9320d5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040431"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="075a1-102">作法：使用設計工具設定 Windows Forms DataGridView 控制項的替代資料列樣式</span><span class="sxs-lookup"><span data-stu-id="075a1-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="075a1-103">表格式資料通常會以類似總帳的格式呈現, 其中的替代資料列會有不同的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="075a1-103">Tabular data is often presented in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="075a1-104">這種格式可讓使用者輕鬆地指出每個資料列中有哪些儲存格，特別是具有許多資料行的寬資料表。</span><span class="sxs-lookup"><span data-stu-id="075a1-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>

<span data-ttu-id="075a1-105">利用 <xref:System.Windows.Forms.DataGridView> 控制項，您可以指定替代資料列的完整樣式資訊。</span><span class="sxs-lookup"><span data-stu-id="075a1-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="075a1-106">除了背景色彩以外, 您還可以使用前景色彩和字型等樣式特性來區分替代資料列。</span><span class="sxs-lookup"><span data-stu-id="075a1-106">You can use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span> <span data-ttu-id="075a1-107">如需詳細資訊, 請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="075a1-107">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="075a1-108">下列程式需要具有包含<xref:System.Windows.Forms.DataGridView>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="075a1-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="075a1-109">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="075a1-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="define-styles-for-alternating-rows"></a><span data-ttu-id="075a1-110">定義替代資料列的樣式</span><span class="sxs-lookup"><span data-stu-id="075a1-110">Define styles for alternating rows</span></span>

1. <span data-ttu-id="075a1-111">在設計工具中選取控制項。<xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="075a1-111">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>

2. <span data-ttu-id="075a1-112">在 [**屬性**] 視窗中, 按一下![ <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>屬性旁邊的省略號按鈕 (Visual Studio](./media/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...)。</span><span class="sxs-lookup"><span data-stu-id="075a1-112">In the **Properties** window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> property.</span></span>

3. <span data-ttu-id="075a1-113">在 [ **CellStyle**產生器] 對話方塊中, 藉由設定屬性來定義樣式, 並使用 [**預覽**] 窗格來確認您的選擇。</span><span class="sxs-lookup"><span data-stu-id="075a1-113">In the **CellStyle Builder** dialog box, define the style by setting the properties, and use the **Preview** pane to confirm your choices.</span></span> <span data-ttu-id="075a1-114">您指定的樣式會用於控制項中顯示的每個其他資料列, 從第二個數據列開始。</span><span class="sxs-lookup"><span data-stu-id="075a1-114">The styles you specify are used for every other row displayed in the control, starting with the second one.</span></span>

4. <span data-ttu-id="075a1-115">若要定義其餘資料列的樣式, 請使用<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>屬性重複步驟2和3。</span><span class="sxs-lookup"><span data-stu-id="075a1-115">To define styles for the remaining rows, repeat steps 2 and 3 using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property.</span></span>

    > [!NOTE]
    > <span data-ttu-id="075a1-116">儲存格會使用繼承自多個屬性的樣式來顯示。</span><span class="sxs-lookup"><span data-stu-id="075a1-116">Cells are displayed using styles inherited from multiple properties.</span></span> <span data-ttu-id="075a1-117">如需樣式繼承的詳細資訊, 請參閱[Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="075a1-117">For more information about style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="075a1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="075a1-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="075a1-119">Windows Forms DataGridView 控制項中的儲存格樣式</span><span class="sxs-lookup"><span data-stu-id="075a1-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="075a1-120">Windows Forms DataGridView 控制項中的基本格式化和樣式設定</span><span class="sxs-lookup"><span data-stu-id="075a1-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="075a1-121">使用設計工具搭配 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="075a1-121">Using the Designer with the Windows Forms DataGridView Control</span></span>](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="075a1-122">如何：建立 Windows Forms 應用程式專案</span><span class="sxs-lookup"><span data-stu-id="075a1-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="075a1-123">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="075a1-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
