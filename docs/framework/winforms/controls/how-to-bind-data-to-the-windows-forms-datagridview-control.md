---
title: 將資料系結至 DataGridView 控制項
ms.date: 02/08/2019
description: 瞭解 DataGridView 控制項如何支援標準 Windows Forms 資料系結模型，使其可以系結至各種不同的資料來源。
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904412"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="bf498-103">如何：將資料系結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="bf498-103">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="bf498-104"><xref:System.Windows.Forms.DataGridView>控制項支援標準 Windows Forms 資料系結模型，因此可以系結至各種不同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="bf498-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="bf498-105">通常，您會系結至 <xref:System.Windows.Forms.BindingSource> 管理與資料來源互動的。</span><span class="sxs-lookup"><span data-stu-id="bf498-105">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="bf498-106"><xref:System.Windows.Forms.BindingSource>可以是任何 Windows Forms 的資料來源，讓您在選擇或修改資料的位置時，有很大的彈性。</span><span class="sxs-lookup"><span data-stu-id="bf498-106">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="bf498-107">如需控制項支援之資料來源的詳細資訊 <xref:System.Windows.Forms.DataGridView> ，請參閱[DataGridView 控制項總覽](datagridview-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="bf498-107">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="bf498-108">Visual Studio 對 DataGridView 控制項的資料系結有廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="bf498-108">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="bf498-109">如需詳細資訊，請參閱[如何：使用設計工具將資料系結至 Windows Forms DataGridView 控制項](bind-data-to-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="bf498-109">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="bf498-110">若要將 DataGridView 控制項連接到資料：</span><span class="sxs-lookup"><span data-stu-id="bf498-110">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="bf498-111">執行方法來處理抓取資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bf498-111">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="bf498-112">下列程式碼範例會執行 `GetData` 初始化的方法， <xref:System.Data.SqlClient.SqlDataAdapter> 並使用它來填入 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="bf498-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="bf498-113">然後，它會將系結 <xref:System.Data.DataTable> 至 <xref:System.Windows.Forms.BindingSource> 。</span><span class="sxs-lookup"><span data-stu-id="bf498-113">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="bf498-114">在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中，將控制項系結 <xref:System.Windows.Forms.DataGridView> 至 <xref:System.Windows.Forms.BindingSource> ，並呼叫 `GetData` 方法來取得資料。</span><span class="sxs-lookup"><span data-stu-id="bf498-114">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="bf498-115">範例</span><span class="sxs-lookup"><span data-stu-id="bf498-115">Example</span></span>

<span data-ttu-id="bf498-116">這個完整的程式碼範例會從資料庫抓取資料，以在 Windows form 中填入 DataGridView 控制項。</span><span class="sxs-lookup"><span data-stu-id="bf498-116">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="bf498-117">表單也有按鈕可重載資料，並將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="bf498-117">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="bf498-118">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="bf498-118">This example requires:</span></span>

- <span data-ttu-id="bf498-119">Northwind SQL Server 範例資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="bf498-119">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="bf498-120">如需有關安裝 Northwind 範例資料庫的詳細資訊，請參閱[取得 ADO.NET 程式碼範例的範例資料庫](../../data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="bf498-120">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="bf498-121">系統、System.web、System.web 和 System.Xml 元件的參考。</span><span class="sxs-lookup"><span data-stu-id="bf498-121">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="bf498-122">若要建立並執行此範例，請將程式碼貼入新的 Windows Forms 專案中的*Form1*程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="bf498-122">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="bf498-123">如需從 c # 或 Visual Basic 命令列建立的詳細資訊，請參閱[使用 csc.exe的命令列建立](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列建立](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="bf498-123">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="bf498-124">`connectionString`使用 Northwind SQL Server 範例資料庫連接的值，在範例中填入變數。</span><span class="sxs-lookup"><span data-stu-id="bf498-124">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="bf498-125">Windows 驗證（也稱為整合式安全性）比在連接字串中儲存密碼，是更安全的連接到資料庫的方式。</span><span class="sxs-lookup"><span data-stu-id="bf498-125">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="bf498-126">如需連接安全性的詳細資訊，請參閱[保護連接資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="bf498-126">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bf498-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf498-127">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="bf498-128">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="bf498-128">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bf498-129">保護連接資訊</span><span class="sxs-lookup"><span data-stu-id="bf498-129">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
