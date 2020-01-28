---
title: 將 DataGrid 控制項系結至資料來源
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
ms.openlocfilehash: 2634a6bd8ace36bcf7a49120162474a8c04b2b83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746695"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="67db0-102">如何：將 Windows Form DataGrid 控制項繫結至資料來源</span><span class="sxs-lookup"><span data-stu-id="67db0-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="67db0-103"><xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="67db0-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="67db0-104">如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="67db0-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="67db0-105">Windows Forms <xref:System.Windows.Forms.DataGrid> 控制項是特別設計來顯示資料來源中的資訊。</span><span class="sxs-lookup"><span data-stu-id="67db0-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="67db0-106">您可以藉由呼叫 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，在執行時間系結控制項。</span><span class="sxs-lookup"><span data-stu-id="67db0-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="67db0-107">雖然您可以顯示來自各種資料來源的資料，但最常見的來源是資料集和資料檢視。</span><span class="sxs-lookup"><span data-stu-id="67db0-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="67db0-108">若要以程式設計方式將 DataGrid 控制項進行資料系結</span><span class="sxs-lookup"><span data-stu-id="67db0-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="67db0-109">撰寫程式碼以填滿資料集。</span><span class="sxs-lookup"><span data-stu-id="67db0-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="67db0-110">如果資料來源是資料集或根據資料集資料表的資料檢視，請將程式碼加入至表單，以填滿資料集。</span><span class="sxs-lookup"><span data-stu-id="67db0-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="67db0-111">您所使用的確切程式碼取決於資料集取得資料的位置。</span><span class="sxs-lookup"><span data-stu-id="67db0-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="67db0-112">如果直接從資料庫填入資料集，您通常會呼叫資料介面卡的 `Fill` 方法，如下列範例所示，它會填入名為 `DsCategories1`的資料集：</span><span class="sxs-lookup"><span data-stu-id="67db0-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="67db0-113">如果要從 XML Web Service 填入資料集，您通常會在程式碼中建立服務的實例，然後呼叫其中一個方法來傳回資料集。</span><span class="sxs-lookup"><span data-stu-id="67db0-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="67db0-114">接著，您可以將資料集從 XML Web Service 合併到本機資料集。</span><span class="sxs-lookup"><span data-stu-id="67db0-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="67db0-115">下列範例會示範如何建立名為 `CategoriesService`的 XML Web Service 實例、呼叫其 `GetCategories` 方法，並將產生的資料集合併到名為 `DsCategories1`的本機資料集：</span><span class="sxs-lookup"><span data-stu-id="67db0-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="67db0-116">呼叫 <xref:System.Windows.Forms.DataGrid> 控制項的 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法，並將資料來源和資料成員傳遞給它。</span><span class="sxs-lookup"><span data-stu-id="67db0-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="67db0-117">如果您不需要明確地傳遞資料成員，請傳遞空字串。</span><span class="sxs-lookup"><span data-stu-id="67db0-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="67db0-118">如果您是第一次系結方格，則可以設定控制項的 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 和 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="67db0-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="67db0-119">不過，一旦設定這些屬性之後，就無法重設這些屬性。</span><span class="sxs-lookup"><span data-stu-id="67db0-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="67db0-120">因此，建議您一律使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="67db0-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="67db0-121">下列範例顯示如何以程式設計方式系結至名為 `DsCustomers1`之資料集內的 Customers 資料表：</span><span class="sxs-lookup"><span data-stu-id="67db0-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="67db0-122">如果 [Customers] 資料表是資料集中的唯一資料表，您也可以透過這種方式來系結格線：</span><span class="sxs-lookup"><span data-stu-id="67db0-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="67db0-123">選擇性在方格中加入適當的資料表樣式和資料行樣式。</span><span class="sxs-lookup"><span data-stu-id="67db0-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="67db0-124">如果沒有資料表樣式，您會看到資料表，但最小的格式和所有資料行都是可見的。</span><span class="sxs-lookup"><span data-stu-id="67db0-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67db0-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="67db0-125">See also</span></span>

- [<span data-ttu-id="67db0-126">DataGrid 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="67db0-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="67db0-127">如何：將資料表和資料行新增至 Windows Forms DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="67db0-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="67db0-128">DataGrid 控制項</span><span class="sxs-lookup"><span data-stu-id="67db0-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="67db0-129">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="67db0-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
