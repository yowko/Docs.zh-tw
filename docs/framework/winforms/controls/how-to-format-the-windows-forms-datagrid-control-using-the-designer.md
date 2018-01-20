---
title: "如何：使用設計工具格式化 Windows Form DataGrid 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b47b0c2353764f5452c2bb3f6ca37af11d6d904c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a><span data-ttu-id="f15fa-102">如何：使用設計工具格式化 Windows Form DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f15fa-102">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="f15fa-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="f15fa-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="f15fa-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f15fa-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="f15fa-105">將不同的色彩套用至各個部分<xref:System.Windows.Forms.DataGrid>控制項可以協助讓您更輕鬆地閱讀及解譯中的資訊。</span><span class="sxs-lookup"><span data-stu-id="f15fa-105">Applying different colors to various parts of a <xref:System.Windows.Forms.DataGrid> control can help to make the information in it easier to read and interpret.</span></span> <span data-ttu-id="f15fa-106">色彩可以套用至資料列和資料行中。</span><span class="sxs-lookup"><span data-stu-id="f15fa-106">Color can be applied to rows and columns.</span></span> <span data-ttu-id="f15fa-107">資料列和資料行也可以隱藏或顯示自行斟酌。</span><span class="sxs-lookup"><span data-stu-id="f15fa-107">Rows and columns can also be hidden or shown at your discretion.</span></span>  
  
 <span data-ttu-id="f15fa-108">有三個基本層面等的格式化<xref:System.Windows.Forms.DataGrid>控制項：</span><span class="sxs-lookup"><span data-stu-id="f15fa-108">There are three basic aspects of formatting the <xref:System.Windows.Forms.DataGrid> control:</span></span>  
  
-   <span data-ttu-id="f15fa-109">您可以設定屬性，以建立資料會顯示為預設樣式。</span><span class="sxs-lookup"><span data-stu-id="f15fa-109">You can set properties to establish a default style in which data is displayed.</span></span>  
  
-   <span data-ttu-id="f15fa-110">從該基底，您可以自訂某些資料表顯示在執行階段的方式。</span><span class="sxs-lookup"><span data-stu-id="f15fa-110">From that base, you can then customize the way certain tables are displayed at run time.</span></span>  
  
-   <span data-ttu-id="f15fa-111">最後，您可以修改哪些資料行中的資料格，以及色彩顯示，並顯示的其他格式設定。</span><span class="sxs-lookup"><span data-stu-id="f15fa-111">Finally, you can modify which columns are displayed in the data grid as well as the colors and other formatting that is shown.</span></span>  
  
 <span data-ttu-id="f15fa-112">格式化資料格在初始步驟，您可以設定的屬性<xref:System.Windows.Forms.DataGrid>本身。</span><span class="sxs-lookup"><span data-stu-id="f15fa-112">As an initial step in formatting a data grid, you can set the properties of the <xref:System.Windows.Forms.DataGrid> itself.</span></span> <span data-ttu-id="f15fa-113">這些色彩和格式的選擇會形成從中您可以再進行變更，取決於資料的資料表和顯示的資料行的基底。</span><span class="sxs-lookup"><span data-stu-id="f15fa-113">These color and format choices form a base from which you can then make changes depending on the data tables and columns displayed.</span></span>  
  
 <span data-ttu-id="f15fa-114">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="f15fa-114">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="f15fa-115">設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="f15fa-115">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="f15fa-116">在[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>控制項不是在**工具箱**預設。</span><span class="sxs-lookup"><span data-stu-id="f15fa-116">In [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="f15fa-117">如需詳細資訊，請參閱[How to： 將項目加入工具箱](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)。</span><span class="sxs-lookup"><span data-stu-id="f15fa-117">For more information, see [How to: Add Items to the Toolbox](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f15fa-118">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="f15fa-118">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f15fa-119">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="f15fa-119">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f15fa-120">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="f15fa-120">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a><span data-ttu-id="f15fa-121">若要建立之預設樣式的 DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f15fa-121">To establish a default style for the DataGrid control</span></span>  
  
1.  <span data-ttu-id="f15fa-122">選取 <xref:System.Windows.Forms.DataGrid> 控制項。</span><span class="sxs-lookup"><span data-stu-id="f15fa-122">Select the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
2.  <span data-ttu-id="f15fa-123">在**屬性**視窗中，設定下列屬性，視需要。</span><span class="sxs-lookup"><span data-stu-id="f15fa-123">In the **Properties** window, set the following properties, as appropriate.</span></span>  
  
    |<span data-ttu-id="f15fa-124">屬性</span><span class="sxs-lookup"><span data-stu-id="f15fa-124">Property</span></span>|<span data-ttu-id="f15fa-125">描述</span><span class="sxs-lookup"><span data-stu-id="f15fa-125">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<span data-ttu-id="f15fa-126">`BackColor`屬性定義的方格其偶數資料列的色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-126">The `BackColor` property defines the color of the even-numbered rows of the grid.</span></span> <span data-ttu-id="f15fa-127">當您將<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>為不同的色彩屬性，每個資料列設定為這個新的色彩 （1、 3、 5 和等等的資料列）。</span><span class="sxs-lookup"><span data-stu-id="f15fa-127">When you set the <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> property to a different color, every other row is set to this new color (rows 1, 3, 5, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|<span data-ttu-id="f15fa-128">方格其偶數資料列的背景色彩 （0、 2、 4、 6 和等等的資料列）。</span><span class="sxs-lookup"><span data-stu-id="f15fa-128">The background color of the even-numbered rows of the grid (rows 0, 2, 4, 6, and so on).</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|<span data-ttu-id="f15fa-129">而<xref:System.Windows.Forms.DataGrid.BackColor%2A>和<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>屬性決定在方格中，資料列的色彩<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>屬性會決定外部資料列區域中，才看得見，由上至下，捲動方格時，或者如果只有少數資料列區域的色彩包含在方格中。</span><span class="sxs-lookup"><span data-stu-id="f15fa-129">Whereas the <xref:System.Windows.Forms.DataGrid.BackColor%2A> and <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> properties determines the color of rows in the grid, the <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> property determines the color of the area outside the row area, which is only visible when the grid is scrolled to the bottom, or if only a few rows are contained in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|<span data-ttu-id="f15fa-130">方格的框線樣式，其中<xref:System.Windows.Forms.BorderStyle>列舉值。</span><span class="sxs-lookup"><span data-stu-id="f15fa-130">The grid's border style, one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|<span data-ttu-id="f15fa-131">就會立即顯示方格上方的方格視窗標題的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-131">The background color of the grid's window caption which appears immediately above the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|<span data-ttu-id="f15fa-132">頂端的方格標題的字型。</span><span class="sxs-lookup"><span data-stu-id="f15fa-132">The font of the caption at the top of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|<span data-ttu-id="f15fa-133">方格的視窗標題的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-133">The background color of the grid's window caption.</span></span>|  
    |<xref:System.Windows.Forms.Control.Font%2A>|<span data-ttu-id="f15fa-134">用來在方格中顯示文字的字型。</span><span class="sxs-lookup"><span data-stu-id="f15fa-134">The font used to display the text in the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|<span data-ttu-id="f15fa-135">資料格的資料列中的資料顯示的字型色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-135">The color of the font displayed by the data in the rows of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|<span data-ttu-id="f15fa-136">資料格的格線色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-136">The color of the grid lines of the data grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<span data-ttu-id="f15fa-137">分隔資料格方格，其中線條的樣式<xref:System.Windows.Forms.DataGridLineStyle>列舉值。</span><span class="sxs-lookup"><span data-stu-id="f15fa-137">The style of the lines separating the cells of the grid, one of the <xref:System.Windows.Forms.DataGridLineStyle> enumeration values.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|<span data-ttu-id="f15fa-138">資料列和資料行的標頭的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-138">The background color of row and column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|<span data-ttu-id="f15fa-139">資料行標頭所使用的字型。</span><span class="sxs-lookup"><span data-stu-id="f15fa-139">The font used for the column headers.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|<span data-ttu-id="f15fa-140">會顯示方格的資料行標頭，包括資料行標頭文字和加號 （+） 和減號 （-） 展開和摺疊資料列，當多個相關資料表時，這些圖像的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-140">The foreground color of the grid's column headers, including the column header text and the plus sign (+) and minus sign (-) glyphs that expand and collapse rows when multiple related tables are displayed.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|<span data-ttu-id="f15fa-141">資料格，其中包含子資料表、 關聯性名稱和等等的連結中的所有連結的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-141">The color of text of all the links in the data grid, including links to child tables, the relation name, and so on.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|<span data-ttu-id="f15fa-142">在子資料表中，這會是父資料列的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-142">In a child table, this is the background color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|<span data-ttu-id="f15fa-143">在子資料表中，這會是父資料列的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-143">In a child table, this is the foreground color of the parent rows.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|<span data-ttu-id="f15fa-144">判斷資料表和資料行名稱是否會顯示在父資料列，藉由<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="f15fa-144">Determines whether the table and column names are displayed in the parent row, by means of the <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|<span data-ttu-id="f15fa-145">方格中資料行的預設寬度 (單位為像素)。</span><span class="sxs-lookup"><span data-stu-id="f15fa-145">The default width (in pixels) of columns in the grid.</span></span> <span data-ttu-id="f15fa-146">重設之前設定此屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或是透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f15fa-146">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="f15fa-147">屬性無法設為小於 0。</span><span class="sxs-lookup"><span data-stu-id="f15fa-147">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|<span data-ttu-id="f15fa-148">在方格中的資料列的資料列高度 （以像素為單位）。</span><span class="sxs-lookup"><span data-stu-id="f15fa-148">The row height (in pixels) of rows in the grid.</span></span> <span data-ttu-id="f15fa-149">重設之前設定此屬性<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性 (可能是分開，或是透過<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法)，或屬性會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f15fa-149">Set this property before resetting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties (either separately, or through the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method), or the property will have no effect.</span></span><br /><br /> <span data-ttu-id="f15fa-150">屬性無法設為小於 0。</span><span class="sxs-lookup"><span data-stu-id="f15fa-150">The property cannot be set to a value less than 0.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|<span data-ttu-id="f15fa-151">方格的資料列行首的寬度。</span><span class="sxs-lookup"><span data-stu-id="f15fa-151">The width of the row headers of the grid.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|<span data-ttu-id="f15fa-152">選取的資料列或資料格時，這是背景色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-152">When a row or cell is selected, this is the background color.</span></span>|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|<span data-ttu-id="f15fa-153">選取的資料列或資料格時，這是前景色彩。</span><span class="sxs-lookup"><span data-stu-id="f15fa-153">When a row or cell is selected, this is the foreground color.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="f15fa-154">當您在自訂控制項的色彩時，便可將控制項設為不佳的色彩選擇 （例如，紅色和綠色） 而無法存取。</span><span class="sxs-lookup"><span data-stu-id="f15fa-154">When you are customizing the colors of controls, it is possible to make the control inaccessible due to poor color choice (for example, red and green).</span></span> <span data-ttu-id="f15fa-155">使用上可用的色彩**系統色彩**調色盤，若要避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="f15fa-155">Use the colors available on the **System Colors** palette to avoid this issue.</span></span>  
  
     <span data-ttu-id="f15fa-156">下列程序需要<xref:System.Windows.Forms.DataGrid>控制項繫結至資料表。</span><span class="sxs-lookup"><span data-stu-id="f15fa-156">The following procedure requires a <xref:System.Windows.Forms.DataGrid> control bound to a data table.</span></span> <span data-ttu-id="f15fa-157">如需詳細資訊，請參閱[How to： 將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="f15fa-157">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a><span data-ttu-id="f15fa-158">若要在設計階段設定資料表的資料的資料表和資料行樣式</span><span class="sxs-lookup"><span data-stu-id="f15fa-158">To set the table and column style of a data table at design time</span></span>  
  
1.  <span data-ttu-id="f15fa-159">選取<xref:System.Windows.Forms.DataGrid>控制項在表單上的。</span><span class="sxs-lookup"><span data-stu-id="f15fa-159">Select the <xref:System.Windows.Forms.DataGrid> control on your form.</span></span>  
  
2.  <span data-ttu-id="f15fa-160">在**屬性**視窗中，選取<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性，然後按一下**省略**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f15fa-160">In the **Properties** window, select the <xref:System.Windows.Forms.DataGrid.TableStyles%2A> property and click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button.</span></span>  
  
3.  <span data-ttu-id="f15fa-161">在**DataGridTableStyle 集合編輯器**對話方塊中，按一下 **新增**將資料表樣式加入集合。</span><span class="sxs-lookup"><span data-stu-id="f15fa-161">In the **DataGridTableStyle Collection Editor** dialog box, click **Add** to add a table style to the collection.</span></span>  
  
     <span data-ttu-id="f15fa-162">與**DataGridTableStyle 集合編輯器**、 您可以加入和移除資料表樣式，設定顯示和版面配置屬性，以及設定資料表樣式名稱對應。</span><span class="sxs-lookup"><span data-stu-id="f15fa-162">With the **DataGridTableStyle Collection Editor**, you can add and remove table styles, set display and layout properties, and set the mapping name for the table styles.</span></span>  
  
4.  <span data-ttu-id="f15fa-163">設定<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>屬性設為每個資料表樣式的對應名稱。</span><span class="sxs-lookup"><span data-stu-id="f15fa-163">Set the <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> property to the mapping name for each table style.</span></span>  
  
     <span data-ttu-id="f15fa-164">對應名稱用來指定應該用於哪一個資料表的資料表樣式。</span><span class="sxs-lookup"><span data-stu-id="f15fa-164">The mapping name is used to specify which table style should be used with which table.</span></span>  
  
5.  <span data-ttu-id="f15fa-165">在**DataGridTableStyle 集合編輯器**，選取<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")).</span><span class="sxs-lookup"><span data-stu-id="f15fa-165">In the **DataGridTableStyle Collection Editor**, select the <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> property and click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")).</span></span>  
  
6.  <span data-ttu-id="f15fa-166">在**DataGridColumnStyle 集合編輯器**對話方塊方塊中，為您建立的資料表樣式加入資料行樣式。</span><span class="sxs-lookup"><span data-stu-id="f15fa-166">In the **DataGridColumnStyle Collection Editor** dialog box, add column styles to the table style you created.</span></span>  
  
     <span data-ttu-id="f15fa-167">與**DataGridColumnStyle 集合編輯器**、 您可以加入和移除資料行樣式，設定顯示和版面配置屬性，以及設定對應名稱和資料行的資料格式字串。</span><span class="sxs-lookup"><span data-stu-id="f15fa-167">With the **DataGridColumnStyle Collection Editor**, you can add and remove column styles, set display and layout properties, and set the mapping name and formatting strings for the data columns.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f15fa-168">如需格式化字串的詳細資訊，請參閱[格式化型別](../../../../docs/standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f15fa-168">For more information about formatting strings, see [Formatting Types](../../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15fa-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="f15fa-169">See Also</span></span>  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [<span data-ttu-id="f15fa-170">操作說明：刪除或隱藏 Windows Forms DataGrid 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="f15fa-170">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="f15fa-171">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f15fa-171">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
