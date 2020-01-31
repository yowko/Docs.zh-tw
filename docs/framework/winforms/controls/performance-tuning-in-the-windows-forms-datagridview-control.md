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
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的效能微調
使用大量資料時，除非您小心使用，否則 `DataGridView` 控制項可能會耗用大量的記憶體。 在記憶體有限的用戶端上，您可以藉由避免具有高記憶體成本的功能，來避免一些額外負荷。 您也可以使用虛擬模式自行管理部分或全部的資料維護和抓取工作，以自訂您案例的記憶體使用量。  
  
## <a name="in-this-section"></a>本章節內容  
 [縮放 Windows Forms DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 描述如何使用 `DataGridView` 控制項，以避免不必要的記憶體使用量，以及處理大量資料時的效能負面影響。  
  
 [Windows Forms DataGridView 控制項中的虛擬模式](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 描述如何使用虛擬模式來補充或取代標準的資料系結機制。  
  
 [逐步解說：在 Windows Forms DataGridView 控制項中實作虛擬模式](implementing-virtual-mode-wf-datagridview-control.md)  
 描述如何執行數個虛擬模式事件的處理常式。 也會示範如何針對使用者編輯執行資料列層級的回復和認可。  
  
 [在 Windows Forms DataGridView 控制項中以 Just-In-Time 資料載入方式實作虛擬模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 描述如何視需要載入資料，當您要顯示的資料比可儲存的可用用戶端記憶體更多時，這會很有用。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.DataGridView>  
 提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 提供 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> 屬性的參考檔。  
  
## <a name="see-also"></a>請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView 控制項的資料顯示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)
