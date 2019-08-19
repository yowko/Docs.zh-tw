---
title: 作法：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源
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
ms.openlocfilehash: de8b8d16f45221fbafe9f61ca634f144d8f6f6ae
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040004"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="49680-102">作法：使用設計工具將 Windows Forms DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="49680-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
>  <span data-ttu-id="49680-103">          <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="49680-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="49680-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="49680-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="49680-105">Windows Forms <xref:System.Windows.Forms.DataGrid>控制項是特別設計來顯示資料來源中的資訊。</span><span class="sxs-lookup"><span data-stu-id="49680-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="49680-106">在設計階段, 您可以藉由設定<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性, 或在<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>執行時間呼叫方法來系結控制項。</span><span class="sxs-lookup"><span data-stu-id="49680-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="49680-107">雖然您可以顯示來自各種資料來源的資料, 但最常見的來源是資料集和資料檢視。</span><span class="sxs-lookup"><span data-stu-id="49680-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>

 <span data-ttu-id="49680-108">如果資料來源在設計階段可用 (例如, 如果表單包含資料集或資料檢視的實例), 您可以在設計階段將方格系結至資料來源。</span><span class="sxs-lookup"><span data-stu-id="49680-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="49680-109">接著, 您可以在方格中預覽資料的樣子。</span><span class="sxs-lookup"><span data-stu-id="49680-109">You can then preview what the data will look like in the grid.</span></span>

 <span data-ttu-id="49680-110">您也可以在執行時間以程式設計方式系結方格。</span><span class="sxs-lookup"><span data-stu-id="49680-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="49680-111">當您想要根據您在執行時間取得的資訊來設定資料來源時, 這會很有用。</span><span class="sxs-lookup"><span data-stu-id="49680-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="49680-112">例如, 應用程式可能會讓使用者指定要查看的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="49680-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="49680-113">在設計階段, 資料來源不存在的情況下也是必要的。</span><span class="sxs-lookup"><span data-stu-id="49680-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="49680-114">這包括資料來源, 例如陣列、集合、不具類型的資料集和資料讀取器。</span><span class="sxs-lookup"><span data-stu-id="49680-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>

 <span data-ttu-id="49680-115">下列程式需要具有包含<xref:System.Windows.Forms.DataGrid>控制項之表單的**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="49680-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="49680-116">如需設定這類專案的相關資訊, [請參閱如何:建立 Windows Forms 應用程式專案](/visualstudio/ide/step-1-create-a-windows-forms-application-project) , [以及如何:將控制項新增至](how-to-add-controls-to-windows-forms.md)Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="49680-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="49680-117">在 Visual Studio 2005 中, <xref:System.Windows.Forms.DataGrid>控制項預設不會在 [**工具箱**] 中。</span><span class="sxs-lookup"><span data-stu-id="49680-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="49680-118">如需新增它的相關資訊[, 請參閱如何:將專案加入 [工具箱](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))]。</span><span class="sxs-lookup"><span data-stu-id="49680-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="49680-119">此外, 在 Visual Studio 2005 中, 您可以使用 [**資料來源**] 視窗進行設計階段資料系結。</span><span class="sxs-lookup"><span data-stu-id="49680-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="49680-120">如需詳細資訊, 請參閱[將控制項系結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="49680-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="49680-121">若要將 DataGrid 控制項資料系結至設計工具中的單一資料表</span><span class="sxs-lookup"><span data-stu-id="49680-121">To data-bind the DataGrid control to a single table in the designer</span></span>

1. <span data-ttu-id="49680-122">將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性設定為包含您要系結之資料項目的物件。</span><span class="sxs-lookup"><span data-stu-id="49680-122">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="49680-123">如果資料來源是資料集, 請將<xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性設定為要系結之資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="49680-123">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>

3. <span data-ttu-id="49680-124">如果資料來源是資料集或根據資料集資料表的資料檢視, 請將程式碼加入至表單, 以填滿資料集。</span><span class="sxs-lookup"><span data-stu-id="49680-124">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>

     <span data-ttu-id="49680-125">您所使用的確切程式碼取決於資料集取得資料的位置。</span><span class="sxs-lookup"><span data-stu-id="49680-125">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="49680-126">如果直接從資料庫填入資料集, 您通常會呼叫`Fill`資料介面卡的方法, 如下列程式碼範例所示, 它會填入名`DsCategories1`為的資料集:</span><span class="sxs-lookup"><span data-stu-id="49680-126">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. <span data-ttu-id="49680-127">選擇性在方格中加入適當的資料表樣式和資料行樣式。</span><span class="sxs-lookup"><span data-stu-id="49680-127">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>

     <span data-ttu-id="49680-128">如果沒有資料表樣式, 您會看到資料表, 但最小的格式和所有資料行都是可見的。</span><span class="sxs-lookup"><span data-stu-id="49680-128">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="49680-129">若要將 DataGrid 控制項資料系結至設計工具中資料集內的多個資料表</span><span class="sxs-lookup"><span data-stu-id="49680-129">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>

1. <span data-ttu-id="49680-130">將控制項的<xref:System.Windows.Forms.DataGrid.DataSource%2A>屬性設定為包含您要系結之資料項目的物件。</span><span class="sxs-lookup"><span data-stu-id="49680-130">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="49680-131">如果資料集包含相關的資料表 (亦即, 如果它包含關聯性物件), 請<xref:System.Windows.Forms.DataGrid.DataMember%2A>將屬性設定為父資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="49680-131">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>

3. <span data-ttu-id="49680-132">撰寫程式碼以填滿資料集。</span><span class="sxs-lookup"><span data-stu-id="49680-132">Write code to fill the dataset.</span></span>

## <a name="see-also"></a><span data-ttu-id="49680-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49680-133">See also</span></span>

- [<span data-ttu-id="49680-134">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="49680-134">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="49680-135">如何：將資料表和資料行加入至 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="49680-135">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="49680-136">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="49680-136">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="49680-137">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="49680-137">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="49680-138">存取 Visual Studio 中的資料</span><span class="sxs-lookup"><span data-stu-id="49680-138">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
