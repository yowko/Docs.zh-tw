---
title: 將資料網格控制綁定到資料來源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182248"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="761da-102">如何：將 Windows Form DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="761da-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="761da-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="761da-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="761da-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="761da-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="761da-105">Windows 表單<xref:System.Windows.Forms.DataGrid>控制項專為顯示資料來源中的資訊而設計。</span><span class="sxs-lookup"><span data-stu-id="761da-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="761da-106">通過調用<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法在運行時繫結控制項。</span><span class="sxs-lookup"><span data-stu-id="761da-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="761da-107">儘管可以顯示來自各種資料來源的資料，但最典型的來源是資料集和資料檢視。</span><span class="sxs-lookup"><span data-stu-id="761da-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="761da-108">以程式設計方式綁定 DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="761da-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="761da-109">編寫代碼以填充資料集。</span><span class="sxs-lookup"><span data-stu-id="761da-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="761da-110">如果資料來源是基於資料集表的資料集或資料檢視，請向表單添加代碼以填充資料集。</span><span class="sxs-lookup"><span data-stu-id="761da-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="761da-111">您使用的確切代碼取決於資料集獲取資料的位置。</span><span class="sxs-lookup"><span data-stu-id="761da-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="761da-112">如果資料集直接從資料庫填充，則通常調用資料配接器`Fill`的方法，如以下示例所示，該方法填充名為 的`DsCategories1`資料集：</span><span class="sxs-lookup"><span data-stu-id="761da-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="761da-113">如果資料集是從 XML Web 服務填充的，則通常在代碼中創建服務的實例，然後調用其方法之一來返回資料集。</span><span class="sxs-lookup"><span data-stu-id="761da-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="761da-114">然後，將 XML Web 服務中的資料集合併到本地資料集中。</span><span class="sxs-lookup"><span data-stu-id="761da-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="761da-115">下面的示例演示如何創建名為`CategoriesService`的 XML Web 服務的實例， 調用其`GetCategories`方法，並將生成的資料集合併到稱為`DsCategories1`：</span><span class="sxs-lookup"><span data-stu-id="761da-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. <span data-ttu-id="761da-116">調用控制項<xref:System.Windows.Forms.DataGrid><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>的方法，傳遞資料來源和資料成員。</span><span class="sxs-lookup"><span data-stu-id="761da-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="761da-117">如果不需要顯式傳遞資料成員，則傳遞一個空字串。</span><span class="sxs-lookup"><span data-stu-id="761da-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="761da-118">如果首次綁定網格，則可以設置控制項和<xref:System.Windows.Forms.DataGrid.DataSource%2A><xref:System.Windows.Forms.DataGrid.DataMember%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="761da-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="761da-119">但是，在設置這些屬性後，無法重置這些屬性。</span><span class="sxs-lookup"><span data-stu-id="761da-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="761da-120">因此，建議您始終使用 方法<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>。</span><span class="sxs-lookup"><span data-stu-id="761da-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="761da-121">下面的示例演示如何在稱為`DsCustomers1`： 的資料集中以程式設計方式綁定到客戶表：</span><span class="sxs-lookup"><span data-stu-id="761da-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="761da-122">如果"客戶"表是資料集中的唯一表，則可以以這種方式綁定網格：</span><span class="sxs-lookup"><span data-stu-id="761da-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="761da-123">（可選）將適當的表樣式和列樣式添加到網格中。</span><span class="sxs-lookup"><span data-stu-id="761da-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="761da-124">如果沒有表樣式，您將看到該表，但格式最小且所有列可見。</span><span class="sxs-lookup"><span data-stu-id="761da-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761da-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="761da-125">See also</span></span>

- [<span data-ttu-id="761da-126">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="761da-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="761da-127">如何：將資料表和資料行加入至 Windows Form DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="761da-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="761da-128">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="761da-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="761da-129">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="761da-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
