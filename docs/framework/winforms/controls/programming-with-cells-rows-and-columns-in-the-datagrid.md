---
title: 在 Windows Form DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], elements
- columns [Windows Forms], data grids
- cells [Windows Forms], data grids
- DataGridView control [Windows Forms], programming with grid elements
- rows [Windows Forms], data grids
ms.assetid: 0d76f7e4-4149-42c6-9118-bb37d6669dc5
ms.openlocfilehash: 085fcd0114742e787c8cbcaabf89a354b0e3e830
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144621"
---
# <a name="programming-with-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fad1e-102">在 Windows Form DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="fad1e-102">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fad1e-103">本節提供示範各種牽涉到資料格、 資料列和資料行物件的程式設計工作的主題。</span><span class="sxs-lookup"><span data-stu-id="fad1e-103">This section provides topics that demonstrate various programming tasks involving cell, row, and column objects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fad1e-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="fad1e-104">In This Section</span></span>  
 [<span data-ttu-id="fad1e-105">HOW TO：將工具提示新增至 Windows Forms DataGridView 控制項的個別儲存格</span><span class="sxs-lookup"><span data-stu-id="fad1e-105">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>](add-tooltips-to-individual-cells-in-a-wf-datagridview-control.md)  
 <span data-ttu-id="fad1e-106">描述如何處理<xref:System.Windows.Forms.DataGridView.CellFormatting>事件來提供不同的工具提示的個別資料格。</span><span class="sxs-lookup"><span data-stu-id="fad1e-106">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting> event to provide different ToolTips for individual cells.</span></span>  
  
 [<span data-ttu-id="fad1e-107">HOW TO：根據 Windows Forms DataGridView 控制項儲存格的變更執行自訂動作</span><span class="sxs-lookup"><span data-stu-id="fad1e-107">How to: Perform a Custom Action Based on Changes in a Cell of a Windows Forms DataGridView Control</span></span>](perform-a-custom-action-based-on-changes-in-a-cell-of-a-datagrid.md)  
 <span data-ttu-id="fad1e-108">描述如何處理<xref:System.Windows.Forms.DataGridView.CellValueChanged>和<xref:System.Windows.Forms.DataGridView.CellStateChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="fad1e-108">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellValueChanged> and <xref:System.Windows.Forms.DataGridView.CellStateChanged> events.</span></span>  
  
 [<span data-ttu-id="fad1e-109">HOW TO：管理 Windows Forms DataGridView 控制項中的寬線</span><span class="sxs-lookup"><span data-stu-id="fad1e-109">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>](how-to-manipulate-bands-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="fad1e-110">描述如何使用類型的物件進行程式設計<xref:System.Windows.Forms.DataGridViewBand>，這是資料列和資料行的基底類型。</span><span class="sxs-lookup"><span data-stu-id="fad1e-110">Describes how to program with objects of type <xref:System.Windows.Forms.DataGridViewBand>, which is the base type for rows and columns.</span></span>  
  
 [<span data-ttu-id="fad1e-111">HOW TO：管理 Windows Forms DataGridView 控制項中的資料列</span><span class="sxs-lookup"><span data-stu-id="fad1e-111">How to: Manipulate Rows in the Windows Forms DataGridView Control</span></span>](how-to-manipulate-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="fad1e-112">描述如何使用類型的物件進行程式設計`DataGridViewRow`。</span><span class="sxs-lookup"><span data-stu-id="fad1e-112">Describes how to program with objects of type `DataGridViewRow`.</span></span>  
  
 [<span data-ttu-id="fad1e-113">HOW TO：管理 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="fad1e-113">How to: Manipulate Columns in the Windows Forms DataGridView Control</span></span>](how-to-manipulate-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="fad1e-114">描述如何使用類型的物件進行程式設計`DataGridViewColumn`。</span><span class="sxs-lookup"><span data-stu-id="fad1e-114">Describes how to program with objects of type `DataGridViewColumn`.</span></span>  
  
 [<span data-ttu-id="fad1e-115">HOW TO：使用 Windows Forms DataGridView 控制項中的影像資料行</span><span class="sxs-lookup"><span data-stu-id="fad1e-115">How to: Work with Image Columns in the Windows Forms DataGridView Control</span></span>](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="fad1e-116">描述如何使用程式設計`DataGridViewImageColumn`類別。</span><span class="sxs-lookup"><span data-stu-id="fad1e-116">Describes how to program with the `DataGridViewImageColumn` class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fad1e-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="fad1e-117">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="fad1e-118">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="fad1e-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="fad1e-119">提供參考文件<xref:System.Windows.Forms.DataGridViewCell>類別。</span><span class="sxs-lookup"><span data-stu-id="fad1e-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="fad1e-120">提供參考文件<xref:System.Windows.Forms.DataGridViewRow>類別。</span><span class="sxs-lookup"><span data-stu-id="fad1e-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="fad1e-121">提供參考文件<xref:System.Windows.Forms.DataGridViewColumn>類別。</span><span class="sxs-lookup"><span data-stu-id="fad1e-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fad1e-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="fad1e-122">Related Sections</span></span>  
 [<span data-ttu-id="fad1e-123">Windows Form DataGridView 控制項中的基本資料行、資料列和儲存格功能</span><span class="sxs-lookup"><span data-stu-id="fad1e-123">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="fad1e-124">提供描述常用的主題使用的儲存格、 資料列和資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="fad1e-124">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fad1e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fad1e-125">See also</span></span>

- [<span data-ttu-id="fad1e-126">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="fad1e-126">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="fad1e-127">Windows Form DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="fad1e-127">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
