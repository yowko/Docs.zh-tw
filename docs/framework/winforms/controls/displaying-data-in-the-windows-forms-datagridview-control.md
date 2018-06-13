---
title: 在 Windows Form DataGridView 控制項中顯示資料
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: 06df9bbcb1e8b1b53d061dbd219a25378a311072
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529424"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="96448-102">在 Windows Form DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="96448-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="96448-103">`DataGridView`控制項用來顯示來自各種外部資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="96448-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="96448-104">或者，您可以將資料列和資料行加入至控制項，並手動填入資料。</span><span class="sxs-lookup"><span data-stu-id="96448-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="96448-105">當您將控制項繫結至資料來源時，您可以產生會自動根據資料來源的結構描述的資料行。</span><span class="sxs-lookup"><span data-stu-id="96448-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="96448-106">如果沒有出現這些資料行，就如同您想要您可以隱藏、 移除或重新排列它們。</span><span class="sxs-lookup"><span data-stu-id="96448-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="96448-107">您也可以加入未繫結的資料行，顯示不是來自資料來源的補充資料。</span><span class="sxs-lookup"><span data-stu-id="96448-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="96448-108">此外，您可以顯示資料，可使用標準格式 （例如貨幣格式），或者您可以自訂顯示格式來呈現您的資料，但是您必須 （例如變更背景色彩為負數，或取代字串值以對應的影像）。</span><span class="sxs-lookup"><span data-stu-id="96448-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96448-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="96448-109">In This Section</span></span>  
 [<span data-ttu-id="96448-110">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="96448-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96448-111">描述用來填入的控制項資料的選項。</span><span class="sxs-lookup"><span data-stu-id="96448-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="96448-112">Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="96448-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96448-113">描述用來格式化儲存格顯示值的選項。</span><span class="sxs-lookup"><span data-stu-id="96448-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="96448-114">逐步解說：建立未繫結的 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="96448-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96448-115">描述如何以手動方式填入資料控制項。</span><span class="sxs-lookup"><span data-stu-id="96448-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="96448-116">操作說明：將資料繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="96448-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96448-117">描述如何將繫結至來填入資料控制項`BindingSource`，其中包含從資料庫提取資訊。</span><span class="sxs-lookup"><span data-stu-id="96448-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="96448-118">操作說明：在資料繫結 Windows Forms DataGridView 控制項中自動產生資料行</span><span class="sxs-lookup"><span data-stu-id="96448-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="96448-119">描述如何自動產生的繫結的資料來源為基礎的資料行。</span><span class="sxs-lookup"><span data-stu-id="96448-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="96448-120">操作說明：移除 Windows Forms DataGridView 控制項中自動產生的資料行</span><span class="sxs-lookup"><span data-stu-id="96448-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="96448-121">描述如何隱藏或刪除自動產生繫結的資料來源的資料行。</span><span class="sxs-lookup"><span data-stu-id="96448-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="96448-122">操作說明：變更 Windows Forms DataGridView 控制項資料行的順序</span><span class="sxs-lookup"><span data-stu-id="96448-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96448-123">描述如何從繫結的資料來源自動產生的資料行重新排列。</span><span class="sxs-lookup"><span data-stu-id="96448-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="96448-124">操作說明：將未繫結的資料行加入至已資料繫結的 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="96448-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="96448-125">描述如何顯示其他、 未繫結的資料行，以補充繫結的資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="96448-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="96448-126">操作說明：將物件繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="96448-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="96448-127">描述如何將控制項繫結到任意物件的集合，使它自己的資料列中顯示每個物件。</span><span class="sxs-lookup"><span data-stu-id="96448-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="96448-128">操作說明：存取物件繫結至 Windows Forms DataGridView 資料列</span><span class="sxs-lookup"><span data-stu-id="96448-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="96448-129">描述如何擷取繫結至控制項的特定資料列的物件。</span><span class="sxs-lookup"><span data-stu-id="96448-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="96448-130">逐步解說：使用兩個 Windows Forms DataGridView 控制項建立主從式表單</span><span class="sxs-lookup"><span data-stu-id="96448-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="96448-131">描述如何顯示兩個相關的資料庫資料表的資料，讓其中一個值`DataGridView`控制項依存於另一個控制項中目前選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="96448-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="96448-132">操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="96448-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96448-133">描述如何處理<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件來變更取決於其值的儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="96448-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="96448-134">參考資料</span><span class="sxs-lookup"><span data-stu-id="96448-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="96448-135">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="96448-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="96448-136">提供參考文件<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="96448-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="96448-137">提供 <xref:System.Windows.Forms.BindingSource> 元件的參考文件。</span><span class="sxs-lookup"><span data-stu-id="96448-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="96448-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="96448-138">Related Sections</span></span>  
 [<span data-ttu-id="96448-139">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="96448-139">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="96448-140">提供主題描述如何變更使用者加入和修改控制項資料的方式。</span><span class="sxs-lookup"><span data-stu-id="96448-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96448-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96448-141">See Also</span></span>  
 [<span data-ttu-id="96448-142">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="96448-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="96448-143">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="96448-143">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
