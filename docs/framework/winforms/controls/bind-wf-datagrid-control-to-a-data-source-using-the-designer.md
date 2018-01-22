---
title: "如何：使用設計工具將 Windows Form DataGrid 控制項繫結至資料來源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3913ffe046bb55e31d8be223061af61371a47418
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="f4d01-102">如何：使用設計工具將 Windows Form DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="f4d01-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="f4d01-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="f4d01-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="f4d01-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="f4d01-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="f4d01-105">Windows Form<xref:System.Windows.Forms.DataGrid>控制項特別設計來顯示資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="f4d01-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="f4d01-106">您將控制項繫結在設計階段藉由設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性，或藉由呼叫的執行階段<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="f4d01-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="f4d01-107">雖然您可以顯示來自各種資料來源的資料，但最常見的來源是資料集和資料的檢視。</span><span class="sxs-lookup"><span data-stu-id="f4d01-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="f4d01-108">如果在執行階段可使用資料來源 — 比方說，如果表單包含多個資料集或資料檢視的執行個體，您可以在設計階段格線繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="f4d01-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="f4d01-109">然後，您可以預覽資料方格中的外觀為何。</span><span class="sxs-lookup"><span data-stu-id="f4d01-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="f4d01-110">您也可以在執行階段以程式設計的方式，結合方格。</span><span class="sxs-lookup"><span data-stu-id="f4d01-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="f4d01-111">當您想要設定資料來源，根據您在執行階段取得的資訊，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="f4d01-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="f4d01-112">例如，應用程式可能會讓使用者指定要檢視之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d01-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="f4d01-113">它也是必要的資料來源不在執行階段存在。</span><span class="sxs-lookup"><span data-stu-id="f4d01-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="f4d01-114">這包括資料來源，例如陣列、 集合、 不具類型資料集，以及資料讀取器。</span><span class="sxs-lookup"><span data-stu-id="f4d01-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="f4d01-115">下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="f4d01-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="f4d01-116">設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="f4d01-116">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="f4d01-117">在[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]、<xref:System.Windows.Forms.DataGrid>控制項不是在**工具箱**預設。</span><span class="sxs-lookup"><span data-stu-id="f4d01-117">In [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="f4d01-118">如需將它加入資訊，請參閱[How to： 將項目加入工具箱](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0)。</span><span class="sxs-lookup"><span data-stu-id="f4d01-118">For information about adding it, see [How to: Add Items to the Toolbox](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span> <span data-ttu-id="f4d01-119">此外在[!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)]，您可以使用**資料來源**設計階段資料繫結的視窗。</span><span class="sxs-lookup"><span data-stu-id="f4d01-119">Additionally in [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="f4d01-120">如需詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="f4d01-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4d01-121">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="f4d01-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f4d01-122">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="f4d01-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f4d01-123">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="f4d01-123">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="f4d01-124">若要進行資料繫結 DataGrid 控制項設計工具中的單一資料表</span><span class="sxs-lookup"><span data-stu-id="f4d01-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1.  <span data-ttu-id="f4d01-125">將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>包含您想要繫結至資料項目物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4d01-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="f4d01-126">如果資料來源的資料集，請設定<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性設為要繫結至資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d01-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3.  <span data-ttu-id="f4d01-127">如果資料來源之資料集或資料集資料表為基礎的資料檢視，請將程式碼加入至表單，以填入資料集。</span><span class="sxs-lookup"><span data-stu-id="f4d01-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="f4d01-128">您使用的實際程式碼會取決於資料集從何處取得資料。</span><span class="sxs-lookup"><span data-stu-id="f4d01-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="f4d01-129">如果直接從資料庫填入資料集，您通常會呼叫`Fill`資料配接器，如下列程式碼範例，會填入資料集呼叫的方法`DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="f4d01-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  <span data-ttu-id="f4d01-130">（選擇性）將適當的資料表樣式和資料行樣式加入至方格中。</span><span class="sxs-lookup"><span data-stu-id="f4d01-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="f4d01-131">如果有任何資料表樣式，您會看到資料表，但最少的格式和可見的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="f4d01-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="f4d01-132">若要進行資料繫結 DataGrid 控制項中的資料集設計工具中的多個資料表</span><span class="sxs-lookup"><span data-stu-id="f4d01-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1.  <span data-ttu-id="f4d01-133">將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>包含您想要繫結至資料項目物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4d01-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="f4d01-134">如果資料集包含相關的資料表 （亦即，如果它包含關聯物件），將<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性設為父資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d01-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3.  <span data-ttu-id="f4d01-135">撰寫程式碼以填入資料集。</span><span class="sxs-lookup"><span data-stu-id="f4d01-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d01-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4d01-136">See Also</span></span>  
 [<span data-ttu-id="f4d01-137">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f4d01-137">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="f4d01-138">操作說明：將資料表和資料行新增至 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f4d01-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="f4d01-139">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="f4d01-139">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="f4d01-140">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="f4d01-140">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="f4d01-141">存取 Visual Studio 中的資料</span><span class="sxs-lookup"><span data-stu-id="f4d01-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
