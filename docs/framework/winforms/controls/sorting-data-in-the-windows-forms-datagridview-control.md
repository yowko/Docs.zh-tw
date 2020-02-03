---
title: 排序 DataGridView 控制項中的資料
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742941"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>排序 Windows Forms DataGridView 控制項中的資料

根據預設，使用者可以按一下文字方塊資料行的標頭來排序 <xref:System.Windows.Forms.DataGridView> 控制項中的資料（或在文字方塊儲存格著重于 .NET Framework 4.7.2 和更新版本時按 F3）。 您可以修改特定資料行的 <xref:System.Windows.Forms.DataGridViewColumn.SortMode> 屬性，以允許使用者在執行這項操作時，依其他資料行類型排序。 您也可以用程式設計方式，依據任何資料行或多個資料行來排序資料。

## <a name="in-this-section"></a>本節內容

[Windows Forms DataGridView 控制項中的資料行排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
描述在控制項中排序資料的選項。

[操作說明：設定 Windows Forms DataGridView 控制項中的資料行排序模式](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
描述如何讓使用者依預設不可排序的資料行排序。

[操作說明：自訂 Windows Forms DataGridView 控制項中的排序](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
描述如何以程式設計方式排序資料，以及如何使用 <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> 事件或藉由執行 <xref:System.Collections.IComparer> 介面來自訂排序。

## <a name="reference"></a>參考

<xref:System.Windows.Forms.DataGridView>  
提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
提供 <xref:System.Windows.Forms.DataGridView.Sort%2A> 方法的參考檔。

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
提供 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 屬性的參考檔。

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
提供 <xref:System.Windows.Forms.DataGridViewColumnSortMode> 列舉的參考檔。

## <a name="see-also"></a>另請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
