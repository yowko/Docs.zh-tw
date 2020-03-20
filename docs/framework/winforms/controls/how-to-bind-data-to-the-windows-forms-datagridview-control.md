---
title: 將資料繫結到資料網格視圖控制項
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182268"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="59e21-102">如何：將資料繫結到 Windows 表單資料網格視圖控制項</span><span class="sxs-lookup"><span data-stu-id="59e21-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="59e21-103">該<xref:System.Windows.Forms.DataGridView>控制項支援標準 Windows 表單資料繫結模型，因此它可以綁定到各種資料來源。</span><span class="sxs-lookup"><span data-stu-id="59e21-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="59e21-104">通常，您將綁定到管理<xref:System.Windows.Forms.BindingSource>與資料來源交互的 。</span><span class="sxs-lookup"><span data-stu-id="59e21-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="59e21-105">可以是<xref:System.Windows.Forms.BindingSource>任何 Windows 表單資料來源，這為您提供了在選擇或修改資料位置時的巨大靈活性。</span><span class="sxs-lookup"><span data-stu-id="59e21-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="59e21-106">有關<xref:System.Windows.Forms.DataGridView>控制項支援的資料來源的詳細資訊，請參閱[DataGridView 控制項概述](datagridview-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="59e21-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="59e21-107">Visual Studio 廣泛支援與 DataGridView 控制項綁定的資料。</span><span class="sxs-lookup"><span data-stu-id="59e21-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="59e21-108">有關詳細資訊，請參閱[：使用設計器將資料繫結到 Windows 表單 DataGridView 控制項](bind-data-to-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="59e21-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="59e21-109">要將 DataGridView 控制項連接到資料：</span><span class="sxs-lookup"><span data-stu-id="59e21-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="59e21-110">實現一種方法來處理檢索資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="59e21-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="59e21-111">以下代碼示例實現一個`GetData`方法，該方法初始化<xref:System.Data.SqlClient.SqlDataAdapter>了 ， 並使用它來<xref:System.Data.DataTable>填充 。</span><span class="sxs-lookup"><span data-stu-id="59e21-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="59e21-112">然後，它將 綁定<xref:System.Data.DataTable>到<xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="59e21-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="59e21-113">在表單<xref:System.Windows.Forms.Form.Load>的事件處理常式中，將<xref:System.Windows.Forms.DataGridView>控制項綁定到 ，<xref:System.Windows.Forms.BindingSource>並調用`GetData`方法以檢索資料。</span><span class="sxs-lookup"><span data-stu-id="59e21-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="59e21-114">範例</span><span class="sxs-lookup"><span data-stu-id="59e21-114">Example</span></span>

<span data-ttu-id="59e21-115">此完整代碼示例從資料庫中檢索資料以在 Windows 表單中填充 DataGridView 控制項。</span><span class="sxs-lookup"><span data-stu-id="59e21-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="59e21-116">該表單還具有重新載入資料和向資料庫提交更改的按鈕。</span><span class="sxs-lookup"><span data-stu-id="59e21-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="59e21-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="59e21-117">This example requires:</span></span>

- <span data-ttu-id="59e21-118">訪問北風 SQL Server 示例資料庫。</span><span class="sxs-lookup"><span data-stu-id="59e21-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="59e21-119">有關安裝北風示例資料庫的詳細資訊，請參閱[獲取ADO.NET代碼示例的示例資料庫](../../data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="59e21-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="59e21-120">對系統、系統.Windows.表單、系統、資料和系統.Xml 程式集的引用。</span><span class="sxs-lookup"><span data-stu-id="59e21-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="59e21-121">要生成和運行此示例，請將代碼粘貼到新 Windows 表單專案中的*Form1*代碼檔中。</span><span class="sxs-lookup"><span data-stu-id="59e21-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="59e21-122">有關從 C# 或 Visual Basic 命令列生成的資訊，請參閱[使用 csc.exe 的命令列構建](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[命令列中的生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="59e21-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="59e21-123">使用北`connectionString`風 SQL Server 示例資料庫連接的值填充示例中的變數。</span><span class="sxs-lookup"><span data-stu-id="59e21-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="59e21-124">Windows 身份驗證也稱為集成安全，與在連接字串中存儲密碼相比，是連接到資料庫的更安全方法。</span><span class="sxs-lookup"><span data-stu-id="59e21-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="59e21-125">有關連接安全性的詳細資訊，請參閱[保護連接資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="59e21-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="59e21-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59e21-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="59e21-127">在 Windows 表單資料網格視圖控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="59e21-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="59e21-128">保護連接資訊</span><span class="sxs-lookup"><span data-stu-id="59e21-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
