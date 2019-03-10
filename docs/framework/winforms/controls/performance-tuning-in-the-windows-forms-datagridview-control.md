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
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的效能微調
當使用大量的資料，`DataGridView`控制會消耗大量的記憶體額外負荷，除非您小心使用。 在用戶端具有有限的記憶體，您可以避免此額外負荷的一些避免成本高記憶體的功能。 您也可以管理部分或所有資料維護和擷取工作自行使用虛擬模式，以自訂您的案例的記憶體使用量。  
  
## <a name="in-this-section"></a>本節內容  
 [縮放 Windows Forms DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 描述如何使用`DataGridView`控制項使用的大量資料時，可避免不必要的記憶體使用情況和效能的負面影響的方式。  
  
 [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 描述如何使用虛擬模式，以補充或取代標準的資料繫結機制。  
  
 [逐步解說：在 Windows Form DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)  
 描述如何實作多個虛擬模式事件的處理常式。 也會示範如何實作資料列層級復原和使用者編輯的認可。  
  
 [在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 描述如何將資料依需求、 您擁有更多的資料，以顯示可用的用戶端記憶體可以儲存非非常有用。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 提供參考文件<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性。  
  
## <a name="see-also"></a>另請參閱
- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView 控制項的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)
