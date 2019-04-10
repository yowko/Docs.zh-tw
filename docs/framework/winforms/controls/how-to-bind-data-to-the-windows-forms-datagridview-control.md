---
title: HOW TO：將資料繫結至 Windows Form DataGridView 控制項
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e147109a64687177f201ad1e312fab56ea61d604
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160066"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="2dc8f-102">HOW TO：將資料繫結至 Windows Form DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="2dc8f-102">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="2dc8f-103"><xref:System.Windows.Forms.DataGridView>控制項支援標準的 Windows Form 資料繫結模型，因此它可以繫結至各種資料來源。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="2dc8f-104">通常，您將繫結至<xref:System.Windows.Forms.BindingSource>管理與資料來源互動。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-104">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="2dc8f-105"><xref:System.Windows.Forms.BindingSource>可以是任何 Windows Form 資料來源，可讓您更彈性地選擇或修改您的資料位置。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-105">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="2dc8f-106">如需有關資料來源<xref:System.Windows.Forms.DataGridView>控制項支援，請參閱 < [DataGridView 控制項概觀](datagridview-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-106">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="2dc8f-107">Visual Studio 的資料繫結至 DataGridView 控制項中的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-107">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="2dc8f-108">如需詳細資訊，請參閱[如何：資料繫結至 Windows Form DataGridView 控制項中使用設計工具](bind-data-to-the-datagrid-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-108">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="2dc8f-109">若要將 DataGridView 控制項連接至資料：</span><span class="sxs-lookup"><span data-stu-id="2dc8f-109">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="2dc8f-110">實作一個方法來處理擷取資料的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-110">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="2dc8f-111">下列程式碼範例會實作`GetData`方法，初始化<xref:System.Data.SqlClient.SqlDataAdapter>，並使用它來填入<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-111">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="2dc8f-112">它接著會繫結<xref:System.Data.DataTable>至<xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-112">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span> 

2. <span data-ttu-id="2dc8f-113">在表單的<xref:System.Windows.Forms.Form.Load>事件處理常式，繫結<xref:System.Windows.Forms.DataGridView>若要控制<xref:System.Windows.Forms.BindingSource>，並呼叫`GetData`方法來擷取資料。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-113">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="2dc8f-114">範例</span><span class="sxs-lookup"><span data-stu-id="2dc8f-114">Example</span></span>

<span data-ttu-id="2dc8f-115">這個完整的程式碼範例會從資料庫填入在 Windows form DataGridView 控制項擷取資料。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-115">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="2dc8f-116">此表單還有按鈕來重新載入資料，並將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-116">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="2dc8f-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="2dc8f-117">This example requires:</span></span> 

- <span data-ttu-id="2dc8f-118">Northwind SQL Server 範例資料庫的存取。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-118">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="2dc8f-119">如需有關如何安裝 Northwind 範例資料庫的詳細資訊，請參閱 <<c0> [ 取得範例資料庫的 ADO.NET 程式碼範例](../../data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-119">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span> 

- <span data-ttu-id="2dc8f-120">System、 System.Windows.Forms、 System.Data 和 System.Xml 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-120">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="2dc8f-121">若要建置並執行此範例中，貼上程式碼插入*Form1*中新的 Windows Form 專案的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-121">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="2dc8f-122">如需從建置C#或 Visual Basic 命令列，請參閱[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或是[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-122">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="2dc8f-123">填入`connectionString`變數中的範例 Northwind SQL Server 範例資料庫連線的值。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-123">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="2dc8f-124">Windows 驗證，也稱為整合式的安全性，是更安全的方式，來連接到資料庫將會比將密碼儲存在連接字串。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-124">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="2dc8f-125">如需連線安全性的詳細資訊，請參閱[保護連接資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="2dc8f-125">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2dc8f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dc8f-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="2dc8f-127">Windows Form DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="2dc8f-127">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2dc8f-128">保護連接資訊</span><span class="sxs-lookup"><span data-stu-id="2dc8f-128">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
