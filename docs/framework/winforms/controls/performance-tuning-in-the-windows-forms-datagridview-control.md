---
title: DataGridView 控制項中的效能微調
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 77ad86c4cd606bcf074473c97371ec27bcc5605b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744270"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d554b-102">Windows Form DataGridView 控制項中的效能微調</span><span class="sxs-lookup"><span data-stu-id="d554b-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d554b-103">使用大量資料時，除非您小心使用，否則 `DataGridView` 控制項可能會耗用大量的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d554b-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="d554b-104">在記憶體有限的用戶端上，您可以藉由避免具有高記憶體成本的功能，來避免一些額外負荷。</span><span class="sxs-lookup"><span data-stu-id="d554b-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="d554b-105">您也可以使用虛擬模式自行管理部分或全部的資料維護和抓取工作，以自訂您案例的記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="d554b-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d554b-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d554b-106">In This Section</span></span>  
 [<span data-ttu-id="d554b-107">縮放 Windows Forms DataGridView 控制項的最佳作法</span><span class="sxs-lookup"><span data-stu-id="d554b-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d554b-108">描述如何使用 `DataGridView` 控制項，以避免不必要的記憶體使用量，以及處理大量資料時的效能負面影響。</span><span class="sxs-lookup"><span data-stu-id="d554b-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="d554b-109">Windows Forms DataGridView 控制項中的虛擬模式</span><span class="sxs-lookup"><span data-stu-id="d554b-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d554b-110">描述如何使用虛擬模式來補充或取代標準的資料系結機制。</span><span class="sxs-lookup"><span data-stu-id="d554b-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="d554b-111">逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="d554b-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="d554b-112">描述如何執行數個虛擬模式事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="d554b-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="d554b-113">也會示範如何針對使用者編輯執行資料列層級的回復和認可。</span><span class="sxs-lookup"><span data-stu-id="d554b-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="d554b-114">在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式</span><span class="sxs-lookup"><span data-stu-id="d554b-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="d554b-115">描述如何視需要載入資料，當您要顯示的資料比可儲存的可用用戶端記憶體更多時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="d554b-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d554b-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="d554b-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="d554b-117">提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。</span><span class="sxs-lookup"><span data-stu-id="d554b-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="d554b-118">提供 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性的參考檔。</span><span class="sxs-lookup"><span data-stu-id="d554b-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d554b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="d554b-119">See also</span></span>

- [<span data-ttu-id="d554b-120">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="d554b-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="d554b-121">Windows Forms DataGridView 控制項的資料顯示模式</span><span class="sxs-lookup"><span data-stu-id="d554b-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
