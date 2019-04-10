---
title: HOW TO：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源
ms.date: 03/30/2017
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
ms.openlocfilehash: fe54c650e1d19f36d681053c7da47e12527c5827
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320882"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="653a0-102">HOW TO：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="653a0-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="653a0-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="653a0-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="653a0-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="653a0-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="653a0-105">Windows Form<xref:System.Windows.Forms.DataGrid>控制項專為顯示從資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="653a0-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="653a0-106">您將控制項繫結在設計階段藉由設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>並<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性，或藉由呼叫的執行階段<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="653a0-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="653a0-107">雖然您可以顯示來自各種資料來源的資料，但最常見的來源是資料集] 和 [資料檢視。</span><span class="sxs-lookup"><span data-stu-id="653a0-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="653a0-108">如果在設計階段所使用資料來源，比方說，如果表單包含資料集或資料檢視的執行個體，您可以在設計階段方格繫結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="653a0-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="653a0-109">然後，您可以預覽資料方格中如下。</span><span class="sxs-lookup"><span data-stu-id="653a0-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="653a0-110">您也可以繫結方格以程式設計的方式，在執行階段。</span><span class="sxs-lookup"><span data-stu-id="653a0-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="653a0-111">當您想要設定資料來源，根據您在執行階段取得的資訊時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="653a0-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="653a0-112">例如，應用程式可能會讓使用者指定要檢視之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="653a0-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="653a0-113">它也是必要的資料來源不在執行階段存在的情況。</span><span class="sxs-lookup"><span data-stu-id="653a0-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="653a0-114">這包括資料來源，例如陣列、 集合、 不具類型的資料集，以及資料讀取器。</span><span class="sxs-lookup"><span data-stu-id="653a0-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="653a0-115">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.DataGrid>控制項。</span><span class="sxs-lookup"><span data-stu-id="653a0-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="653a0-116">如需這類專案的設定資訊，請參閱[How to:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[How to:將控制項新增至 Windows Forms](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="653a0-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="653a0-117">在 Visual Studio 2005 裡<xref:System.Windows.Forms.DataGrid>控制項不是處於**工具箱**預設。</span><span class="sxs-lookup"><span data-stu-id="653a0-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="653a0-118">如需將它加入資訊，請參閱[How to:將項目加入至工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="653a0-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="653a0-119">此外在 Visual Studio 2005 中，您可以使用**Zdroje dat**設計階段資料繫結的視窗。</span><span class="sxs-lookup"><span data-stu-id="653a0-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="653a0-120">如需詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="653a0-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="653a0-121">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="653a0-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="653a0-122">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="653a0-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="653a0-123">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="653a0-123">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="653a0-124">以資料繫結 DataGrid 控制項至設計工具中的單一資料表</span><span class="sxs-lookup"><span data-stu-id="653a0-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1. <span data-ttu-id="653a0-125">將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>包含您想要繫結至的資料項目物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="653a0-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2. <span data-ttu-id="653a0-126">如果資料來源的資料集，請設定<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性繫結至資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="653a0-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3. <span data-ttu-id="653a0-127">如果資料來源之資料集或資料集資料表為基礎的資料檢視，請將程式碼加入表單，以填入資料集。</span><span class="sxs-lookup"><span data-stu-id="653a0-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="653a0-128">您使用的確切程式碼取決於資料集從何處取得資料。</span><span class="sxs-lookup"><span data-stu-id="653a0-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="653a0-129">如果直接從資料庫填入資料集，您通常會呼叫`Fill`方法的資料配接器，如下列程式碼範例中，會填入資料集所示`DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="653a0-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4. <span data-ttu-id="653a0-130">（選擇性）將適當的資料表樣式和資料行樣式加入方格中。</span><span class="sxs-lookup"><span data-stu-id="653a0-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="653a0-131">如果不有任何資料表樣式，您會看到資料表，但搭配最少的格式與可見的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="653a0-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="653a0-132">若要進行資料繫結 DataGrid 控制項中的資料集設計工具中的多個資料表</span><span class="sxs-lookup"><span data-stu-id="653a0-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1. <span data-ttu-id="653a0-133">將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>包含您想要繫結至的資料項目物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="653a0-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2. <span data-ttu-id="653a0-134">如果資料集包含相關的資料表 （也就是如果它包含的關聯性物件），將<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性設為父資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="653a0-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3. <span data-ttu-id="653a0-135">撰寫程式碼以填入資料集。</span><span class="sxs-lookup"><span data-stu-id="653a0-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653a0-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="653a0-136">See also</span></span>

- [<span data-ttu-id="653a0-137">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="653a0-137">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="653a0-138">HOW TO：將資料表和資料行新增至 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="653a0-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="653a0-139">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="653a0-139">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="653a0-140">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="653a0-140">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="653a0-141">在 Visual Studio 中存取資料</span><span class="sxs-lookup"><span data-stu-id="653a0-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
