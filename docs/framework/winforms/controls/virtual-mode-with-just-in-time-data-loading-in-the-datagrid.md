---
title: HOW TO：在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式
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
ms.openlocfilehash: 82a6e7bd1bb112c3341e7aefb4a3722d3c2be056
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592904"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="3668d-102">HOW TO：在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="3668d-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3668d-103">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 控制項中的虛擬模式，其中的資料快取只會在需要時才從伺服器載入資料。</span><span class="sxs-lookup"><span data-stu-id="3668d-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="3668d-104">此範例中會詳細說明[以 Just-In-Time 資料載入 Windows Forms DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)。</span><span class="sxs-lookup"><span data-stu-id="3668d-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3668d-105">範例</span><span class="sxs-lookup"><span data-stu-id="3668d-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3668d-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3668d-106">Compiling the Code</span></span>  
 <span data-ttu-id="3668d-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="3668d-107">This example requires:</span></span>  
  
- <span data-ttu-id="3668d-108">System、System.Data、System.Xml 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3668d-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="3668d-109">已安裝 Northwind SQL Server 範例資料庫之伺服器的存取權。</span><span class="sxs-lookup"><span data-stu-id="3668d-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3668d-110">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="3668d-110">.NET Framework Security</span></span>  
 <span data-ttu-id="3668d-111">在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="3668d-111">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="3668d-112">使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。</span><span class="sxs-lookup"><span data-stu-id="3668d-112">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="3668d-113">如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="3668d-113">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3668d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3668d-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [<span data-ttu-id="3668d-115">在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="3668d-115">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="3668d-116">Windows Forms DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="3668d-116">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="3668d-117">Windows Forms DataGridView 控制項中的虛擬模式</span><span class="sxs-lookup"><span data-stu-id="3668d-117">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)
