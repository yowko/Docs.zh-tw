---
title: 在 Windows Form DataGridView 控制項中顯示資料
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: d35fd2d17ce8d1b3c4759da1bab2370c450d2fbf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703259"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5af95-102">在 Windows Form DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="5af95-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5af95-103">`DataGridView`控制項用來顯示各種不同的外部資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="5af95-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="5af95-104">或者，您可以將資料列和資料行加入至控制項，並手動填入資料。</span><span class="sxs-lookup"><span data-stu-id="5af95-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="5af95-105">當您將控制項繫結至資料來源時，您可以產生會自動根據資料來源的結構描述的資料行。</span><span class="sxs-lookup"><span data-stu-id="5af95-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="5af95-106">如果只是依您想要時，才不會出現這些資料行，您可以隱藏、 移除或重新排列它們。</span><span class="sxs-lookup"><span data-stu-id="5af95-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="5af95-107">您也可以加入未繫結的資料行，顯示不是來自資料來源的補充資料。</span><span class="sxs-lookup"><span data-stu-id="5af95-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="5af95-108">此外，您可以顯示資料，可使用標準格式 （例如貨幣格式），或者您可以自訂顯示格式來呈現您的資料，但您需要 （例如變更背景色彩為負數，或取代字串值與對應的映像）。</span><span class="sxs-lookup"><span data-stu-id="5af95-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5af95-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="5af95-109">In This Section</span></span>  
 [<span data-ttu-id="5af95-110">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="5af95-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5af95-111">描述用來填入控制項資料的選項。</span><span class="sxs-lookup"><span data-stu-id="5af95-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="5af95-112">Windows Forms DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="5af95-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5af95-113">描述用於格式化儲存格顯示值的選項。</span><span class="sxs-lookup"><span data-stu-id="5af95-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="5af95-114">逐步解說：建立未繫結的 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5af95-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5af95-115">描述如何手動填入資料控制項。</span><span class="sxs-lookup"><span data-stu-id="5af95-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="5af95-116">如何：將資料繫結至 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5af95-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5af95-117">描述如何填入控制項資料繫結至`BindingSource`，其中包含從資料庫提取的資訊。</span><span class="sxs-lookup"><span data-stu-id="5af95-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="5af95-118">如何：自動產生資料繫結 Windows Form DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="5af95-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="5af95-119">說明如何自動產生繫結的資料來源為基礎的資料行。</span><span class="sxs-lookup"><span data-stu-id="5af95-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="5af95-120">如何：移除 Windows Form DataGridView 控制項中的自動產生資料行</span><span class="sxs-lookup"><span data-stu-id="5af95-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="5af95-121">描述如何隱藏或刪除自動產生繫結的資料來源的資料行。</span><span class="sxs-lookup"><span data-stu-id="5af95-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="5af95-122">如何：變更 Windows Form DataGridView 控制項中的資料行的順序</span><span class="sxs-lookup"><span data-stu-id="5af95-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5af95-123">描述如何重新整理從繫結的資料來源自動產生的資料行。</span><span class="sxs-lookup"><span data-stu-id="5af95-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="5af95-124">如何：未繫結的資料行加入資料繫結 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5af95-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="5af95-125">描述如何顯示其他、 未繫結的資料行來補充繫結的資料來源的資料。</span><span class="sxs-lookup"><span data-stu-id="5af95-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="5af95-126">如何：將物件繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5af95-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="5af95-127">描述如何將控制項繫結至任意物件的集合，以便在它自己的資料列中顯示每個物件。</span><span class="sxs-lookup"><span data-stu-id="5af95-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="5af95-128">如何：存取物件的繫結至 Windows Forms DataGridView 資料列</span><span class="sxs-lookup"><span data-stu-id="5af95-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="5af95-129">描述如何擷取繫結至控制項的特定資料列的物件。</span><span class="sxs-lookup"><span data-stu-id="5af95-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="5af95-130">逐步解說：建立主版/詳細表單使用兩個 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5af95-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="5af95-131">描述如何顯示來自兩個相關的資料庫資料表的資料，讓一個所示的值`DataGridView`控制相依於另一個控制項中目前選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="5af95-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="5af95-132">如何：自訂 Windows Form DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="5af95-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5af95-133">描述如何處理<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件來變更取決於其值的儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="5af95-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5af95-134">參考資料</span><span class="sxs-lookup"><span data-stu-id="5af95-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="5af95-135">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="5af95-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="5af95-136">提供參考文件<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="5af95-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="5af95-137">提供 <xref:System.Windows.Forms.BindingSource> 元件的參考文件。</span><span class="sxs-lookup"><span data-stu-id="5af95-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5af95-138">相關章節</span><span class="sxs-lookup"><span data-stu-id="5af95-138">Related Sections</span></span>  
 [<span data-ttu-id="5af95-139">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="5af95-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5af95-140">提供主題描述如何變更使用者加入和修改控制項資料的方式。</span><span class="sxs-lookup"><span data-stu-id="5af95-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af95-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5af95-141">See also</span></span>
- [<span data-ttu-id="5af95-142">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="5af95-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="5af95-143">Windows Forms DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="5af95-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
