---
title: HOW TO：Windows Form DataGridView 控制項中實作虛擬模式，以在 Just-in-time 資料載入
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
ms.openlocfilehash: 174d09cc11a37c01c901afac1ab194bb33c6f7c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622542"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d51f2-102">HOW TO：Windows Form DataGridView 控制項中實作虛擬模式，以在 Just-in-time 資料載入</span><span class="sxs-lookup"><span data-stu-id="d51f2-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d51f2-103">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 控制項中的虛擬模式，其中的資料快取只會在需要時才從伺服器載入資料。</span><span class="sxs-lookup"><span data-stu-id="d51f2-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="d51f2-104">此範例中會詳細說明[以 Just-In-Time 資料載入 Windows Forms DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="d51f2-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d51f2-105">範例</span><span class="sxs-lookup"><span data-stu-id="d51f2-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d51f2-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d51f2-106">Compiling the Code</span></span>  
 <span data-ttu-id="d51f2-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d51f2-107">This example requires:</span></span>  
  
-   <span data-ttu-id="d51f2-108">System、System.Data、System.Xml 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d51f2-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="d51f2-109">已安裝 Northwind SQL Server 範例資料庫之伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="d51f2-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
 <span data-ttu-id="d51f2-110">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="d51f2-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d51f2-111">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d51f2-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="d51f2-112">另請參閱[How to:編譯並執行完整的 Windows Form 程式碼範例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="d51f2-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d51f2-113">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="d51f2-113">.NET Framework Security</span></span>  
 <span data-ttu-id="d51f2-114">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="d51f2-114">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="d51f2-115">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="d51f2-115">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="d51f2-116">如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="d51f2-116">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51f2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d51f2-117">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [<span data-ttu-id="d51f2-118">在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="d51f2-118">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="d51f2-119">Windows Forms DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="d51f2-119">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d51f2-120">Windows Forms DataGridView 控制項中的虛擬模式</span><span class="sxs-lookup"><span data-stu-id="d51f2-120">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)
