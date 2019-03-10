---
title: Windows Form DataGridView 控制項中的效能微調
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: d425488adb8569a48333de4f8c0312143029fbe0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703158"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="03726-102">Windows Form DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="03726-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="03726-103">當使用大量的資料，`DataGridView`控制會消耗大量的記憶體額外負荷，除非您小心使用。</span><span class="sxs-lookup"><span data-stu-id="03726-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="03726-104">在用戶端具有有限的記憶體，您可以避免此額外負荷的一些避免成本高記憶體的功能。</span><span class="sxs-lookup"><span data-stu-id="03726-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="03726-105">您也可以管理部分或所有資料維護和擷取工作自行使用虛擬模式，以自訂您的案例的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="03726-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="03726-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="03726-106">In This Section</span></span>  
 [<span data-ttu-id="03726-107">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="03726-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="03726-108">描述如何使用`DataGridView`控制項使用的大量資料時，可避免不必要的記憶體使用情況和效能的負面影響的方式。</span><span class="sxs-lookup"><span data-stu-id="03726-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="03726-109">Windows Forms DataGridView 控制項中的虛擬模式</span><span class="sxs-lookup"><span data-stu-id="03726-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="03726-110">描述如何使用虛擬模式，以補充或取代標準的資料繫結機制。</span><span class="sxs-lookup"><span data-stu-id="03726-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="03726-111">逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="03726-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="03726-112">描述如何實作多個虛擬模式事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="03726-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="03726-113">也會示範如何實作資料列層級復原和使用者編輯的認可。</span><span class="sxs-lookup"><span data-stu-id="03726-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="03726-114">在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="03726-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="03726-115">描述如何將資料依需求、 您擁有更多的資料，以顯示可用的用戶端記憶體可以儲存非非常有用。</span><span class="sxs-lookup"><span data-stu-id="03726-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="03726-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="03726-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="03726-117">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="03726-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="03726-118">提供參考文件<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="03726-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03726-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03726-119">See also</span></span>
- [<span data-ttu-id="03726-120">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="03726-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="03726-121">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="03726-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
