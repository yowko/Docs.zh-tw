---
title: 在 DataGridView 控制項中顯示資料
description: 瞭解如何使用 Windows Forms DataGridView 控制項，以顯示來自各種外部資料源的資料。
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: a0f3e6627290521b8c10477c31459f1486e79162
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174571"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6d316-103">在 Windows Form DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="6d316-103">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6d316-104">`DataGridView`控制項是用來顯示各種不同外部資料源的資料。</span><span class="sxs-lookup"><span data-stu-id="6d316-104">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="6d316-105">或者，您也可以將資料列和資料行新增至控制項，並以手動方式填入資料。</span><span class="sxs-lookup"><span data-stu-id="6d316-105">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="6d316-106">當您將控制項系結至資料來源時，您可以根據資料來源的架構自動產生資料行。</span><span class="sxs-lookup"><span data-stu-id="6d316-106">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="6d316-107">如果這些資料行看起來不像您想要的，您可以隱藏、移除或重新排列它們。</span><span class="sxs-lookup"><span data-stu-id="6d316-107">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="6d316-108">您也可以加入未系結的資料行，以顯示不是來自資料來源的補充資料。</span><span class="sxs-lookup"><span data-stu-id="6d316-108">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="6d316-109">此外，您可以使用標準 (格式（例如貨幣格式) ）來顯示資料，也可以自訂顯示格式來呈現您的資料，不過您需要 (例如變更負數的背景色彩，或以) 的對應影像取代字串值。</span><span class="sxs-lookup"><span data-stu-id="6d316-109">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6d316-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="6d316-110">In This Section</span></span>  
 [<span data-ttu-id="6d316-111">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="6d316-111">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6d316-112">描述以資料填入控制項的選項。</span><span class="sxs-lookup"><span data-stu-id="6d316-112">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="6d316-113">Windows Form DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="6d316-113">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6d316-114">說明格式化儲存格顯示值的選項。</span><span class="sxs-lookup"><span data-stu-id="6d316-114">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="6d316-115">逐步解說：建立未繫結的 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="6d316-115">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6d316-116">說明如何以手動方式將資料填入控制項。</span><span class="sxs-lookup"><span data-stu-id="6d316-116">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="6d316-117">如何：將資料繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="6d316-117">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6d316-118">描述如何藉由將資料系結至 `BindingSource` 包含從資料庫提取之資訊的來填入控制項。</span><span class="sxs-lookup"><span data-stu-id="6d316-118">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="6d316-119">如何：在資料繫結 Windows Form DataGridView 控制項中自動產生資料行</span><span class="sxs-lookup"><span data-stu-id="6d316-119">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="6d316-120">描述如何根據系結的資料來源自動產生資料行。</span><span class="sxs-lookup"><span data-stu-id="6d316-120">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="6d316-121">如何：移除 Windows Form DataGridView 控制項中自動產生的資料行</span><span class="sxs-lookup"><span data-stu-id="6d316-121">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="6d316-122">描述如何隱藏或刪除從系結資料來源自動產生的資料行。</span><span class="sxs-lookup"><span data-stu-id="6d316-122">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="6d316-123">如何：變更 Windows Form DataGridView 控制項資料行的順序</span><span class="sxs-lookup"><span data-stu-id="6d316-123">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6d316-124">描述如何重新排列從系結資料來源自動產生的資料行。</span><span class="sxs-lookup"><span data-stu-id="6d316-124">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="6d316-125">操作說明：將未繫結的資料行加入至已資料繫結的 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="6d316-125">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="6d316-126">描述如何藉由顯示其他未系結的資料行，來補充系結資料來源中的資料。</span><span class="sxs-lookup"><span data-stu-id="6d316-126">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="6d316-127">如何：將物件繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="6d316-127">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="6d316-128">描述如何將控制項系結至任意物件的集合，讓每個物件顯示在它自己的資料列中。</span><span class="sxs-lookup"><span data-stu-id="6d316-128">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="6d316-129">如何：存取物件繫結至 Windows Forms DataGridView 資料列</span><span class="sxs-lookup"><span data-stu-id="6d316-129">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="6d316-130">描述如何抓取系結至控制項之特定資料列的物件。</span><span class="sxs-lookup"><span data-stu-id="6d316-130">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="6d316-131">逐步解說：使用兩個 Windows Form DataGridView 控制項建立主要/詳細表單</span><span class="sxs-lookup"><span data-stu-id="6d316-131">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="6d316-132">描述如何顯示兩個相關資料庫資料表中的資料，讓一個控制項中顯示的值相依 `DataGridView` 于另一個控制項中目前選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="6d316-132">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="6d316-133">如何：自訂 Windows Form DataGridView 控制項中的資料格式</span><span class="sxs-lookup"><span data-stu-id="6d316-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6d316-134">描述如何處理 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> 事件，以根據其值來變更儲存格的外觀。</span><span class="sxs-lookup"><span data-stu-id="6d316-134">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6d316-135">參考</span><span class="sxs-lookup"><span data-stu-id="6d316-135">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="6d316-136">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="6d316-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="6d316-137">提供屬性的參考檔 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6d316-137">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="6d316-138">提供 <xref:System.Windows.Forms.BindingSource> 元件的參考文件。</span><span class="sxs-lookup"><span data-stu-id="6d316-138">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6d316-139">相關章節</span><span class="sxs-lookup"><span data-stu-id="6d316-139">Related Sections</span></span>  
 [<span data-ttu-id="6d316-140">Windows Form DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="6d316-140">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6d316-141">提供主題描述如何變更使用者加入和修改控制項資料的方式。</span><span class="sxs-lookup"><span data-stu-id="6d316-141">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d316-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d316-142">See also</span></span>

- [<span data-ttu-id="6d316-143">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="6d316-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="6d316-144">Windows Form DataGridView 控制項中的資料行類型</span><span class="sxs-lookup"><span data-stu-id="6d316-144">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
