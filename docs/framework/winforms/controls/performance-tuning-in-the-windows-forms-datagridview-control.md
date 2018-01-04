---
title: "Windows Form DataGridView 控制項中的效能微調"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0171bf4fa056de2dd06c2f7e431ea55a8dab1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="db241-102">Windows Form DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="db241-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="db241-103">當使用大量的資料，`DataGridView`控制會消耗大量的記憶體中負擔，除非您小心使用。</span><span class="sxs-lookup"><span data-stu-id="db241-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="db241-104">在用戶端具有有限的記憶體，您可以避免此額外負荷的某些避免有大量記憶體的功能。</span><span class="sxs-lookup"><span data-stu-id="db241-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="db241-105">您也可以管理部分或所有資料維護和擷取工作自己使用的虛擬模式也可以自訂用於您案例的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="db241-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db241-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="db241-106">In This Section</span></span>  
 [<span data-ttu-id="db241-107">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="db241-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="db241-108">描述如何使用`DataGridView`控制項中的方式可使用大量的資料時，避免不必要的記憶體使用量和效能的負面影響。</span><span class="sxs-lookup"><span data-stu-id="db241-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="db241-109">Windows Forms DataGridView 控制項中的虛擬模式</span><span class="sxs-lookup"><span data-stu-id="db241-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="db241-110">描述如何使用虛擬模式，以補充或取代標準的資料繫結機制。</span><span class="sxs-lookup"><span data-stu-id="db241-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="db241-111">逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="db241-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="db241-112">描述如何實作多個虛擬模式事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="db241-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="db241-113">也會示範如何實作資料列層級復原，並認可為使用者編輯作業。</span><span class="sxs-lookup"><span data-stu-id="db241-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="db241-114">在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="db241-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="db241-115">描述如何載入在需要時，您有更多資料才能顯示可用的用戶端記憶體可以儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="db241-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="db241-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="db241-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="db241-117">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="db241-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="db241-118">提供參考文件<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="db241-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db241-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="db241-119">See Also</span></span>  
 [<span data-ttu-id="db241-120">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="db241-120">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="db241-121">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="db241-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
