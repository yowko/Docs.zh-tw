---
title: "如何：將資料繫結至 Windows Forms DataGridView 控制項"
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
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04fee5f753cb4b3786d5ca58f85880f151caf0b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="4f90c-102">如何：將資料繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="4f90c-102">How to: Bind Data to the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4f90c-103"><xref:System.Windows.Forms.DataGridView> 控制項支援標準的 Windows Form 資料繫結模型，因此會繫結至各種資料來源。</span><span class="sxs-lookup"><span data-stu-id="4f90c-103">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to a variety of data sources.</span></span> <span data-ttu-id="4f90c-104">不過，在大部分情況下，您會繫結至 <xref:System.Windows.Forms.BindingSource> 元件，以便管理與資料來源互動的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4f90c-104">In most circumstances, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component which will manage the details of interacting with the data source.</span></span> <span data-ttu-id="4f90c-105"><xref:System.Windows.Forms.BindingSource> 元件可代表任何 Windows Form 資料來源，並可讓您更彈性地選擇或修改資料的位置。</span><span class="sxs-lookup"><span data-stu-id="4f90c-105">The <xref:System.Windows.Forms.BindingSource> component can represent any Windows Forms data source and gives you great flexibility when choosing or modifying the location of your data.</span></span> <span data-ttu-id="4f90c-106">如需有關所支援的資料來源<xref:System.Windows.Forms.DataGridView>控制，請參閱[DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="4f90c-106">For more information about the data sources supported by the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="4f90c-107">在 Visual Studio 中對於本工作有更詳盡的支援。</span><span class="sxs-lookup"><span data-stu-id="4f90c-107">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="4f90c-108">另請參閱[如何：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="4f90c-108">Also see [How to: Bind Data to the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="4f90c-109">程序</span><span class="sxs-lookup"><span data-stu-id="4f90c-109">Procedure</span></span>  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a><span data-ttu-id="4f90c-110">將 DataGridView 控制項連接到資料</span><span class="sxs-lookup"><span data-stu-id="4f90c-110">To connect a DataGridView control to data</span></span>  
  
1.  <span data-ttu-id="4f90c-111">實作一種方法來處理從資料庫中擷取資料的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4f90c-111">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="4f90c-112">下列程式碼範例會實作初始化 <xref:System.Data.SqlClient.SqlDataAdapter> 元件的 `GetData` 方法，並使用它來填入 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="4f90c-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="4f90c-113"><xref:System.Data.DataTable> 會接著繫結至 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="4f90c-113">The <xref:System.Data.DataTable> is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="4f90c-114">請務必將 `connectionString` 變數設定為適用於您資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="4f90c-114">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="4f90c-115">您將需要已安裝 Northwind SQL Server 範例資料庫之伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="4f90c-115">You will need access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  <span data-ttu-id="4f90c-116">在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中，將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至 <xref:System.Windows.Forms.BindingSource> 元件並呼叫 `GetData` 方法，以便從資料庫中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="4f90c-116">In your form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="4f90c-117">範例</span><span class="sxs-lookup"><span data-stu-id="4f90c-117">Example</span></span>  
 <span data-ttu-id="4f90c-118">下列完整的程式碼範例會提供按鈕，以從資料庫重新載入資料，並將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="4f90c-118">The following complete code example provides buttons for reloading data from the database and submitting changes to the database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f90c-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4f90c-119">Compiling the Code</span></span>  
 <span data-ttu-id="4f90c-120">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4f90c-120">This example requires:</span></span>  
  
-   <span data-ttu-id="4f90c-121">System、System.Windows.Forms、System.Data 和 System.XML 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="4f90c-121">References to the System, System.Windows.Forms, System.Data, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="4f90c-122">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="4f90c-122">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4f90c-123">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="4f90c-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="4f90c-124">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="4f90c-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4f90c-125">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="4f90c-125">.NET Framework Security</span></span>  
 <span data-ttu-id="4f90c-126">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="4f90c-126">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="4f90c-127">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="4f90c-127">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="4f90c-128">如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="4f90c-128">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f90c-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f90c-129">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="4f90c-130">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="4f90c-130">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="4f90c-131">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="4f90c-131">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
