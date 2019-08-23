---
title: 作法：使用設計工具以 Windows Forms DataGrid 控制項建立主從式清單
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 3962b671176ad158b338889140181834e05bbeee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929716"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a><span data-ttu-id="34964-102">作法：使用設計工具以 Windows Forms DataGrid 控制項建立主從式清單</span><span class="sxs-lookup"><span data-stu-id="34964-102">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="34964-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="34964-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="34964-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="34964-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="34964-105">如果您<xref:System.Data.DataSet>包含一系列相關的資料表, 您可以使用兩<xref:System.Windows.Forms.DataGrid>個控制項, 以主版詳細資料格式顯示資料。</span><span class="sxs-lookup"><span data-stu-id="34964-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master-detail format.</span></span> <span data-ttu-id="34964-106">其中<xref:System.Windows.Forms.DataGrid>一個會被指定為主要方格, 而第二個則指定為詳細資料方格。</span><span class="sxs-lookup"><span data-stu-id="34964-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="34964-107">當您選取 [主要] 清單中的專案時, [詳細資料] 清單中會顯示所有相關的子專案。</span><span class="sxs-lookup"><span data-stu-id="34964-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="34964-108">例如, 如果您<xref:System.Data.DataSet>的包含 customers 資料表和相關的 Orders 資料表, 您會將 customers 資料表指定為主要方格, 而 orders 資料表則是詳細資料方格。</span><span class="sxs-lookup"><span data-stu-id="34964-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="34964-109">從主要方格中選取客戶時, [訂單] 資料表中與該客戶相關聯的所有訂單都會顯示在 [詳細資料] 方格中。</span><span class="sxs-lookup"><span data-stu-id="34964-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>

 <span data-ttu-id="34964-110">下列程式需要**Windows 應用程式**專案 ([  > 檔案] [**新增** > **專案** > ] [ **C#視覺效果**] 或 [ **Visual Basic**  > ] **傳統桌面** >  **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="34964-110">The following procedure requires a **Windows Application** project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

## <a name="to-create-a-master-details-list-in-the-designer"></a><span data-ttu-id="34964-111">若要在設計工具中建立主版詳細資料清單</span><span class="sxs-lookup"><span data-stu-id="34964-111">To create a master-details list in the designer</span></span>

1. <span data-ttu-id="34964-112">將兩<xref:System.Windows.Forms.DataGrid>個控制項新增至表單。</span><span class="sxs-lookup"><span data-stu-id="34964-112">Add two <xref:System.Windows.Forms.DataGrid> controls to the form.</span></span> <span data-ttu-id="34964-113">如需詳細資訊，請參閱[如何：將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="34964-113">For more information, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="34964-114">在 Visual Studio 2005 中, <xref:System.Windows.Forms.DataGrid>控制項預設不會在 [**工具箱**] 中。</span><span class="sxs-lookup"><span data-stu-id="34964-114">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="34964-115">如需詳細資訊，請參閱[如何：將專案加入 [工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))]。</span><span class="sxs-lookup"><span data-stu-id="34964-115">For more information, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span>

    > [!NOTE]
    > <span data-ttu-id="34964-116">下列步驟不適用於 Visual Studio 2005, 其使用設計階段資料系結的 [**資料來源**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="34964-116">The following steps are not applicable to Visual Studio 2005, which uses the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="34964-117">如需詳細資訊, 請參閱[將控制項系結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)和[如何:在 Windows Forms 應用程式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))中顯示相關資料。</span><span class="sxs-lookup"><span data-stu-id="34964-117">For more information, see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) and [How to: Display Related Data in a Windows Forms Application](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).</span></span>

2. <span data-ttu-id="34964-118">將兩個或多個資料表從**伺服器總管**拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="34964-118">Drag two or more tables from **Server Explorer** to the form.</span></span>

3. <span data-ttu-id="34964-119">從 [**資料**] 功能表中, 選取 [**產生資料集**]。</span><span class="sxs-lookup"><span data-stu-id="34964-119">From the **Data** menu, select **Generate DataSet**.</span></span>

4. <span data-ttu-id="34964-120">使用 XML 設計工具設定資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="34964-120">Set the relationships between the tables using the XML Designer.</span></span> <span data-ttu-id="34964-121">如需詳細資訊, 請參閱 < 如何:在 MSDN 上的 XML 架構和資料集內建立一對多關聯性。</span><span class="sxs-lookup"><span data-stu-id="34964-121">For details, see "How to: Create One-to-Many Relationships in XML Schemas and Datasets" on MSDN.</span></span>

5. <span data-ttu-id="34964-122">從 [檔案] 功能表中選取 [**全部儲存**], 以儲存關聯性。</span><span class="sxs-lookup"><span data-stu-id="34964-122">Save the relationships by selecting **Save All** from the **File** menu.</span></span>

6. <span data-ttu-id="34964-123">設定您想要指定主要方格的控制項,如下所示:<xref:System.Windows.Forms.DataGrid></span><span class="sxs-lookup"><span data-stu-id="34964-123">Configure the <xref:System.Windows.Forms.DataGrid> control that you want to designate the master grid, as follows:</span></span>

    1. <span data-ttu-id="34964-124"><xref:System.Data.DataSet>從<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性的下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="34964-124">Select the <xref:System.Data.DataSet> from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataSource%2A> property.</span></span>

    2. <span data-ttu-id="34964-125">從<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性的下拉式清單中選取主資料表 (例如「Customers」)。</span><span class="sxs-lookup"><span data-stu-id="34964-125">Select the master table (for example, "Customers") from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property.</span></span>

7. <span data-ttu-id="34964-126">設定您想要指定詳細資料方格的控制項,如下所示:<xref:System.Windows.Forms.DataGrid></span><span class="sxs-lookup"><span data-stu-id="34964-126">Configure the <xref:System.Windows.Forms.DataGrid> control that you want to designate the details grid, as follows:</span></span>

    1. <span data-ttu-id="34964-127"><xref:System.Data.DataSet>從<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性的下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="34964-127">Select the <xref:System.Data.DataSet> from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataSource%2A> property.</span></span>

    2. <span data-ttu-id="34964-128">從<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性的下拉式清單中, 選取 master 和 detail 資料表之間的關聯性 (例如, "Customers. CustOrd")。</span><span class="sxs-lookup"><span data-stu-id="34964-128">Select the relationship (for example, "Customers.CustOrd") between the master and detail tables from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property.</span></span> <span data-ttu-id="34964-129">若要查看關聯性, 請在下拉式清單中按一下主表旁邊的 **+** 加號 (), 展開節點。</span><span class="sxs-lookup"><span data-stu-id="34964-129">In order to see the relationship, expand the node by clicking on the plus (**+**) sign next to the master table in the drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="34964-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34964-130">See also</span></span>

- [<span data-ttu-id="34964-131">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="34964-131">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="34964-132">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="34964-132">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="34964-133">如何：將 Windows Forms DataGrid 控制項系結至資料來源</span><span class="sxs-lookup"><span data-stu-id="34964-133">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [<span data-ttu-id="34964-134">將控制項繫結至 Visual Studio 中的資料</span><span class="sxs-lookup"><span data-stu-id="34964-134">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
