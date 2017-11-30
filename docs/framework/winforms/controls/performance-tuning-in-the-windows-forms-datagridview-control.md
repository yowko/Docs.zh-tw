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
ms.openlocfilehash: 452c55d38a896ec96e0992a4b9826f08dc4caa0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的效能微調
當使用大量的資料，`DataGridView`控制會消耗大量的記憶體中負擔，除非您小心使用。 在用戶端具有有限的記憶體，您可以避免此額外負荷的某些避免有大量記憶體的功能。 您也可以管理部分或所有資料維護和擷取工作自己使用的虛擬模式也可以自訂用於您案例的記憶體使用量。  
  
## <a name="in-this-section"></a>本章節內容  
 [縮放 Windows Forms DataGridView 控制項的最佳作法](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 描述如何使用`DataGridView`控制項中的方式可使用大量的資料時，避免不必要的記憶體使用量和效能的負面影響。  
  
 [Windows Forms DataGridView 控制項中的虛擬模式](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 描述如何使用虛擬模式，以補充或取代標準的資料繫結機制。  
  
 [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 描述如何實作多個虛擬模式事件處理常式。 也會示範如何實作資料列層級復原，並認可為使用者編輯作業。  
  
 [在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 描述如何載入在需要時，您有更多資料才能顯示可用的用戶端記憶體可以儲存的資料。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 提供參考文件<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>屬性。  
  
## <a name="see-also"></a>另請參閱  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Windows Forms DataGridView 控制項的資料顯示模式](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
