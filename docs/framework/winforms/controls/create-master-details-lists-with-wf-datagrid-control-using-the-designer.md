---
title: HOW TO：使用設計工具以 Windows Forms DataGrid 控制項建立主從式清單
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: f586572c850927ffe71566287986e6db6112c689
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961356"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a><span data-ttu-id="f7977-102">HOW TO：使用設計工具以 Windows Forms DataGrid 控制項建立主從式清單</span><span class="sxs-lookup"><span data-stu-id="f7977-102">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="f7977-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="f7977-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="f7977-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f7977-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="f7977-105">如果您<xref:System.Data.DataSet>包含一系列相關的資料表，您可以使用兩個<xref:System.Windows.Forms.DataGrid>主版詳細資料的格式顯示資料的控制項。</span><span class="sxs-lookup"><span data-stu-id="f7977-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master-detail format.</span></span> <span data-ttu-id="f7977-106">一個<xref:System.Windows.Forms.DataGrid>指定為主要方格中，與第二個指定為詳細資料方格。</span><span class="sxs-lookup"><span data-stu-id="f7977-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="f7977-107">當您選取的主機清單中的項目時，所有相關的子系項目會顯示在詳細資料清單。</span><span class="sxs-lookup"><span data-stu-id="f7977-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="f7977-108">比方說，如果您<xref:System.Data.DataSet>包含 Customers 資料表和相關的 Orders 資料表中，您會指定為主要格線的 [客戶] 資料表和 Orders 資料表詳細資料方格。</span><span class="sxs-lookup"><span data-stu-id="f7977-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="f7977-109">主要方格中選取客戶時，詳細資料方格中就會顯示所有相關聯的 Orders 資料表中與該客戶的訂單。</span><span class="sxs-lookup"><span data-stu-id="f7977-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
 <span data-ttu-id="f7977-110">下列程序需要**Windows 應用程式**專案 (**檔案** > **新增** > **專案** >  **Visual C#** 或是**Visual Basic** > **傳統桌面** > **Windows Form應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="f7977-110">The following procedure requires a **Windows Application** project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7977-111">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="f7977-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f7977-112">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="f7977-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f7977-113">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="f7977-113">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a><span data-ttu-id="f7977-114">若要在設計工具中建立主版詳細資料清單</span><span class="sxs-lookup"><span data-stu-id="f7977-114">To create a master-details list in the designer</span></span>  
  
1. <span data-ttu-id="f7977-115">新增兩個<xref:System.Windows.Forms.DataGrid>控制項加入表單。</span><span class="sxs-lookup"><span data-stu-id="f7977-115">Add two <xref:System.Windows.Forms.DataGrid> controls to the form.</span></span> <span data-ttu-id="f7977-116">如需詳細資訊，請參閱[如何：將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="f7977-116">For more information, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="f7977-117">在 Visual Studio 2005 裡<xref:System.Windows.Forms.DataGrid>控制項不是處於**工具箱**預設。</span><span class="sxs-lookup"><span data-stu-id="f7977-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="f7977-118">如需詳細資訊，請參閱[如何：將項目加入至工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f7977-118">For more information, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7977-119">下列步驟並不適用於 Visual Studio 2005，它會使用**Zdroje dat**設計階段資料繫結的視窗。</span><span class="sxs-lookup"><span data-stu-id="f7977-119">The following steps are not applicable to Visual Studio 2005, which uses the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="f7977-120">如需詳細資訊，請參閱 <<c0> [ 控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)和[How to:資料在 Windows Forms 應用程式中顯示相關](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="f7977-120">For more information, see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) and [How to: Display Related Data in a Windows Forms Application](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).</span></span>  
  
2. <span data-ttu-id="f7977-121">將兩個或多個資料表，從**伺服器總管**至表單。</span><span class="sxs-lookup"><span data-stu-id="f7977-121">Drag two or more tables from **Server Explorer** to the form.</span></span>  
  
3. <span data-ttu-id="f7977-122">從**資料**功能表上，選取**產生的資料集**。</span><span class="sxs-lookup"><span data-stu-id="f7977-122">From the **Data** menu, select **Generate DataSet**.</span></span>  
  
4. <span data-ttu-id="f7977-123">設定使用 XML 設計工具的資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="f7977-123">Set the relationships between the tables using the XML Designer.</span></span> <span data-ttu-id="f7977-124">如需詳細資訊，請參閱 「 如何：建立 XML 結構描述與資料集中的一對多關聯性"MSDN 上。</span><span class="sxs-lookup"><span data-stu-id="f7977-124">For details, see "How to: Create One-to-Many Relationships in XML Schemas and Datasets" on MSDN.</span></span>  
  
5. <span data-ttu-id="f7977-125">儲存選取的關聯性**全部儲存**從**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="f7977-125">Save the relationships by selecting **Save All** from the **File** menu.</span></span>  
  
6. <span data-ttu-id="f7977-126">設定<xref:System.Windows.Forms.DataGrid>控制您想要指定主版方格中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f7977-126">Configure the <xref:System.Windows.Forms.DataGrid> control that you want to designate the master grid, as follows:</span></span>  
  
    1. <span data-ttu-id="f7977-127">選取 <xref:System.Data.DataSet>從下拉式清單中<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f7977-127">Select the <xref:System.Data.DataSet> from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataSource%2A> property.</span></span>  
  
    2. <span data-ttu-id="f7977-128">從下拉式清單中選取主要資料表中 （例如，「 客戶 」）<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f7977-128">Select the master table (for example, "Customers") from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property.</span></span>  
  
7. <span data-ttu-id="f7977-129">設定<xref:System.Windows.Forms.DataGrid>控制您想要指定詳細資料方格中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f7977-129">Configure the <xref:System.Windows.Forms.DataGrid> control that you want to designate the details grid, as follows:</span></span>  
  
    1. <span data-ttu-id="f7977-130">選取 <xref:System.Data.DataSet>從下拉式清單中<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f7977-130">Select the <xref:System.Data.DataSet> from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataSource%2A> property.</span></span>  
  
    2. <span data-ttu-id="f7977-131">選取 master] 和 [詳細資料的資料表，從下拉式清單中之間的關聯性 (例如，"Customers.CustOrd 」)<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f7977-131">Select the relationship (for example, "Customers.CustOrd") between the master and detail tables from the drop-down list in the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property.</span></span> <span data-ttu-id="f7977-132">若要查看的關聯性，請按一下加號展開的節點 (**+**) 旁邊下拉式清單中的主資料表。</span><span class="sxs-lookup"><span data-stu-id="f7977-132">In order to see the relationship, expand the node by clicking on the plus (**+**) sign next to the master table in the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7977-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7977-133">See also</span></span>

- [<span data-ttu-id="f7977-134">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f7977-134">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="f7977-135">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f7977-135">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="f7977-136">如何：將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="f7977-136">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [<span data-ttu-id="f7977-137">將控制項繫結至 Visual Studio 中的資料</span><span class="sxs-lookup"><span data-stu-id="f7977-137">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
