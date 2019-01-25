---
title: HOW TO：驗證 Windows Form DataGridView 控制項中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: e8cfd8d67444cb41e5d56ae23457648a05514d28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609547"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="19dd2-102">HOW TO：驗證 Windows Form DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="19dd2-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="19dd2-103">下列程式碼範例示範如何驗證使用者輸入 <xref:System.Windows.Forms.DataGridView> 控制項的資料。</span><span class="sxs-lookup"><span data-stu-id="19dd2-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="19dd2-104">在此範例中，會填入來自 Northwind 範例資料庫 `Customers` 資料表的資料列到 <xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="19dd2-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="19dd2-105">當使用者編輯 `CompanyName` 資料行中的儲存格時，會檢查是否為空白以測試其值的有效性。</span><span class="sxs-lookup"><span data-stu-id="19dd2-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="19dd2-106">如果 <xref:System.Windows.Forms.DataGridView.CellValidating> 事件的事件處理常式發現此值為空字串，則直到使用者輸入非空白字串之前，<xref:System.Windows.Forms.DataGridView> 會讓使用者不能離開儲存格。</span><span class="sxs-lookup"><span data-stu-id="19dd2-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="19dd2-107">如需這個程式碼範例的完整說明，請參閱[逐步解說：驗證資料，在 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="19dd2-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19dd2-108">範例</span><span class="sxs-lookup"><span data-stu-id="19dd2-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="19dd2-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="19dd2-109">Compiling the Code</span></span>  
 <span data-ttu-id="19dd2-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="19dd2-110">This example requires:</span></span>  
  
-   <span data-ttu-id="19dd2-111">System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。 </span><span class="sxs-lookup"><span data-stu-id="19dd2-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="19dd2-112">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="19dd2-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="19dd2-113">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="19dd2-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="19dd2-114">另請參閱[How to:編譯並執行完整的 Windows Form 程式碼範例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="19dd2-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="19dd2-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="19dd2-115">.NET Framework Security</span></span>  
 <span data-ttu-id="19dd2-116">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="19dd2-116">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="19dd2-117">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="19dd2-117">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="19dd2-118">如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="19dd2-118">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19dd2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19dd2-119">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="19dd2-120">逐步解說：驗證 Windows Form DataGridView 控制項中的資料</span><span class="sxs-lookup"><span data-stu-id="19dd2-120">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="19dd2-121">Windows Forms DataGridView 控制項中的資料輸入</span><span class="sxs-lookup"><span data-stu-id="19dd2-121">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="19dd2-122">逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="19dd2-122">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="19dd2-123">保護連線資訊</span><span class="sxs-lookup"><span data-stu-id="19dd2-123">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
