---
ms.openlocfilehash: 06a700a6fcd9c434e5ea8a10031371d13a4d1a4b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721366"
---
### <a name="removed-controls"></a><span data-ttu-id="4377c-101">移除的控制項</span><span class="sxs-lookup"><span data-stu-id="4377c-101">Removed controls</span></span>

<span data-ttu-id="4377c-102">從 .NET Core 3.1 開始，部分 Windows Forms 控制項已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="4377c-102">Starting in .NET Core 3.1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4377c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="4377c-103">Change description</span></span>

<span data-ttu-id="4377c-104">從 .NET Core 3.1 開始，已不再提供各種 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="4377c-104">Starting with .NET Core 3.1, various Windows Forms controls are no longer available.</span></span> <span data-ttu-id="4377c-105">在 .NET Framework 2.0 中引進了更佳設計和支援的取代控制項。</span><span class="sxs-lookup"><span data-stu-id="4377c-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="4377c-106">已淘汰的控制項先前已從設計工具工具箱中移除，但仍可供使用。</span><span class="sxs-lookup"><span data-stu-id="4377c-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span>

<span data-ttu-id="4377c-107">下列類型已無法再使用：</span><span class="sxs-lookup"><span data-stu-id="4377c-107">The following types are no longer available:</span></span>

- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.Menu.MenuItemCollection>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.ToolBar>
- <xref:System.Windows.Forms.ToolBarAppearance>
- <xref:System.Windows.Forms.ToolBarButton>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>
- <xref:System.Windows.Forms.ToolBarButtonStyle>
- <xref:System.Windows.Forms.ToolBarTextAlign>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.DataGridBoolColumn>
- <xref:System.Windows.Forms.DataGridCell>
- <xref:System.Windows.Forms.DataGridColumnStyle>
- <xref:System.Windows.Forms.DataGridLineStyle>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter>
- <xref:System.Windows.Forms.DataGridTableStyle>
- <xref:System.Windows.Forms.DataGridTextBox>
- <xref:System.Windows.Forms.DataGridTextBoxColumn>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.GridTablesFactory>
- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.IDataGridEditingService>
- <xref:System.Windows.Forms.DataGrid.HitTestType>
- <xref:System.Windows.Forms.Design.IMenuEditorService>

#### <a name="version-introduced"></a><span data-ttu-id="4377c-108">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4377c-108">Version introduced</span></span>

<span data-ttu-id="4377c-109">3.1</span><span class="sxs-lookup"><span data-stu-id="4377c-109">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4377c-110">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4377c-110">Recommended action</span></span>

<span data-ttu-id="4377c-111">每個移除的控制項都有建議的取代控制項。</span><span class="sxs-lookup"><span data-stu-id="4377c-111">Each removed control has a recommended replacement control.</span></span> <span data-ttu-id="4377c-112">請參閱下表：</span><span class="sxs-lookup"><span data-stu-id="4377c-112">Refer to the following table:</span></span>

| <span data-ttu-id="4377c-113">已移除控制項（API）</span><span class="sxs-lookup"><span data-stu-id="4377c-113">Removed control (API)</span></span> | <span data-ttu-id="4377c-114">建議取代</span><span class="sxs-lookup"><span data-stu-id="4377c-114">Recommended replacement</span></span> | <span data-ttu-id="4377c-115">已移除的相關聯 Api</span><span class="sxs-lookup"><span data-stu-id="4377c-115">Associated APIs that are removed</span></span> |
|-|-|-|
| <span data-ttu-id="4377c-116">DataGrid</span><span class="sxs-lookup"><span data-stu-id="4377c-116">DataGrid</span></span> | <span data-ttu-id="4377c-117">DataGridView</span><span class="sxs-lookup"><span data-stu-id="4377c-117">DataGridView</span></span> | <span data-ttu-id="4377c-118">DataGridCell、DataGridRow、DataGridTableCollection、DataGridColumnCollection、DataGridTableStyle、System.windows.forms.datagridcolumnstyle>、DataGridLineStyle、DataGridParentRowsLabel、DataGridParentRowsLabelStyle、DataGridBoolColumn、DataGridTextBox、System.windows.forms.gridcolumnstylescollection>、system.windows.forms.gridtablestylescollection>、HitTestType</span><span class="sxs-lookup"><span data-stu-id="4377c-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span></span> |
| <span data-ttu-id="4377c-119">ToolBar</span><span class="sxs-lookup"><span data-stu-id="4377c-119">ToolBar</span></span> | <span data-ttu-id="4377c-120">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4377c-120">ToolStrip</span></span> | <span data-ttu-id="4377c-121">System.windows.forms.toolbar.appearance</span><span class="sxs-lookup"><span data-stu-id="4377c-121">ToolBarAppearance</span></span> |
| <span data-ttu-id="4377c-122">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="4377c-122">ToolBarButton</span></span> | <span data-ttu-id="4377c-123">ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="4377c-123">ToolStripButton</span></span> | <span data-ttu-id="4377c-124">System.windows.forms.toolbarbuttonclickeventargs>、ToolBarButtonClickEventHandler、ToolBarButtonStyle、ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="4377c-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span></span>|
| <span data-ttu-id="4377c-125">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4377c-125">ContextMenu</span></span> | <span data-ttu-id="4377c-126">ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="4377c-126">ContextMenuStrip</span></span> | |
| <span data-ttu-id="4377c-127">功能表</span><span class="sxs-lookup"><span data-stu-id="4377c-127">Menu</span></span> | <span data-ttu-id="4377c-128">ToolStripDropDown、ToolStripDropDownMenu</span><span class="sxs-lookup"><span data-stu-id="4377c-128">ToolStripDropDown, ToolStripDropDownMenu</span></span> | <span data-ttu-id="4377c-129">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="4377c-129">MenuItemCollection</span></span> |
| <span data-ttu-id="4377c-130">MainMenu</span><span class="sxs-lookup"><span data-stu-id="4377c-130">MainMenu</span></span> | <span data-ttu-id="4377c-131">MenuStrip</span><span class="sxs-lookup"><span data-stu-id="4377c-131">MenuStrip</span></span> | |
| <span data-ttu-id="4377c-132">MenuItem</span><span class="sxs-lookup"><span data-stu-id="4377c-132">MenuItem</span></span> | <span data-ttu-id="4377c-133">ToolStripMenuItem</span><span class="sxs-lookup"><span data-stu-id="4377c-133">ToolStripMenuItem</span></span> | |

#### <a name="category"></a><span data-ttu-id="4377c-134">類別</span><span class="sxs-lookup"><span data-stu-id="4377c-134">Category</span></span>

<span data-ttu-id="4377c-135">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4377c-135">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4377c-136">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4377c-136">Affected APIs</span></span>

- <xref:System.Windows.Forms.Menu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Menu.MenuItemCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MainMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ContextMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MenuItem?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarAppearance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarTextAlign?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridBoolColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridCell?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridColumnStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridLineStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTableStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBox?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBoxColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridColumnStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTablesFactory?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTableStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.IDataGridEditingService?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid.HitTestType?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Design.IMenuEditorService?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.Menu`
- `T:System.Windows.Forms.Menu.MenuItemCollection`
- `T:System.Windows.Forms.MainMenu`
- `T:System.Windows.Forms.ContextMenu`
- `T:System.Windows.Forms.MenuItem`
- `T:System.Windows.Forms.ToolBar`
- `T:System.Windows.Forms.ToolBarAppearance`
- `T:System.Windows.Forms.ToolBarButton`
- `T:System.Windows.Forms.ToolBar.ToolBarButtonCollection`
- `T:System.Windows.Forms.ToolBarButtonClickEventArgs`
- `T:System.Windows.Forms.ToolBarButtonStyle`
- `T:System.Windows.Forms.ToolBarTextAlign`
- `T:System.Windows.Forms.DataGrid`
- `T:System.Windows.Forms.DataGridBoolColumn`
- `T:System.Windows.Forms.DataGridCell`
- `T:System.Windows.Forms.DataGridColumnStyle`
- `T:System.Windows.Forms.DataGridLineStyle`
- `T:System.Windows.Forms.DataGridParentRowsLabelStyle`
- `T:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter`
- `T:System.Windows.Forms.DataGridTableStyle`
- `T:System.Windows.Forms.DataGridTextBox`
- `T:System.Windows.Forms.DataGridTextBoxColumn`
- `T:System.Windows.Forms.GridColumnStylesCollection`
- `T:System.Windows.Forms.GridTablesFactory`
- `T:System.Windows.Forms.GridTableStylesCollection`
- `T:System.Windows.Forms.IDataGridEditingService`
- `T:System.Windows.Forms.DataGrid.HitTestType`
- `T:System.Windows.Forms.Design.IMenuEditorService`

-->
