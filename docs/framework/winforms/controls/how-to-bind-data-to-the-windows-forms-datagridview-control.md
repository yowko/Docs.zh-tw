---
title: 將資料系結至 DataGridView 控制項
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: e2762bf363a469abf8c1e57b851d351c1cb41b62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745084"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="b275e-102">如何：將資料系結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="b275e-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="b275e-103"><xref:System.Windows.Forms.DataGridView> 控制項支援標準的 Windows Forms 資料系結模型，因此它可以系結至各種不同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="b275e-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="b275e-104">通常，您會系結至管理與資料來源互動的 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="b275e-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="b275e-105"><xref:System.Windows.Forms.BindingSource> 可以是任何 Windows Forms 的資料來源，讓您在選擇或修改資料的位置時，有很大的彈性。</span><span class="sxs-lookup"><span data-stu-id="b275e-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="b275e-106">如需 <xref:System.Windows.Forms.DataGridView> 控制項支援之資料來源的詳細資訊，請參閱[DataGridView 控制項總覽](datagridview-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b275e-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="b275e-107">Visual Studio 對 DataGridView 控制項的資料系結有廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="b275e-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="b275e-108">如需詳細資訊，請參閱[如何：使用設計工具將資料系結至 Windows Forms DataGridView 控制項](bind-data-to-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="b275e-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="b275e-109">若要將 DataGridView 控制項連接到資料：</span><span class="sxs-lookup"><span data-stu-id="b275e-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="b275e-110">執行方法來處理抓取資料的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b275e-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="b275e-111">下列程式碼範例會執行初始化 <xref:System.Data.SqlClient.SqlDataAdapter>的 `GetData` 方法，並使用它來填入 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="b275e-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="b275e-112">然後，它會將 <xref:System.Data.DataTable> 系結至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="b275e-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="b275e-113">在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中，將 <xref:System.Windows.Forms.DataGridView> 控制項系結至 <xref:System.Windows.Forms.BindingSource>，並呼叫 `GetData` 方法來取得資料。</span><span class="sxs-lookup"><span data-stu-id="b275e-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="b275e-114">範例</span><span class="sxs-lookup"><span data-stu-id="b275e-114">Example</span></span>

<span data-ttu-id="b275e-115">這個完整的程式碼範例會從資料庫抓取資料，以在 Windows form 中填入 DataGridView 控制項。</span><span class="sxs-lookup"><span data-stu-id="b275e-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="b275e-116">表單也有按鈕可重載資料，並將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="b275e-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="b275e-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b275e-117">This example requires:</span></span> 

- <span data-ttu-id="b275e-118">Northwind SQL Server 範例資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="b275e-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="b275e-119">如需有關安裝 Northwind 範例資料庫的詳細資訊，請參閱[取得 ADO.NET 程式碼範例的範例資料庫](../../data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="b275e-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="b275e-120">系統、System.web、system.webserver、system.string 和 system.string 元件的參考。</span><span class="sxs-lookup"><span data-stu-id="b275e-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="b275e-121">若要建立並執行此範例，請將程式碼貼入新的 Windows Forms 專案中的*Form1*程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="b275e-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="b275e-122">如需從C#或 Visual Basic 命令列建立的詳細資訊，請參閱[使用 csc 建立命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列建立](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="b275e-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="b275e-123">使用 Northwind SQL Server 範例資料庫連接的值填入範例中的 `connectionString` 變數。</span><span class="sxs-lookup"><span data-stu-id="b275e-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="b275e-124">Windows 驗證（也稱為整合式安全性）比在連接字串中儲存密碼，是更安全的連接到資料庫的方式。</span><span class="sxs-lookup"><span data-stu-id="b275e-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="b275e-125">如需連接安全性的詳細資訊，請參閱[保護連接資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="b275e-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b275e-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="b275e-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="b275e-127">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="b275e-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b275e-128">保護連接資訊</span><span class="sxs-lookup"><span data-stu-id="b275e-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
