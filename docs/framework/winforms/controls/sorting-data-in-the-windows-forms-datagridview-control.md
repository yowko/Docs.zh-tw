---
title: 在 Windows Form DataGridView 控制項中排序資料
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 606ffc7bd6136b775adaaaa79cf5042cf1e2dd70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012143"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>在 Windows Form DataGridView 控制項中排序資料

根據預設，使用者可以排序資料<xref:System.Windows.Forms.DataGridView>控制項依序按一下 文字 方塊中的資料行的標頭 （或按 F3 時文字 方塊中資料格著重於.NET Framework 4.7.2 和更新版本）。 您可以修改<xref:System.Windows.Forms.DataGridViewColumn.SortMode>特定的資料行，讓使用者得有意義，若要這樣做時，由其他資料行類型排序的屬性。 您也以程式設計的方式排序資料，依任何資料行，或多個資料行。

## <a name="in-this-section"></a>本節內容

[Windows Forms DataGridView 控制項中的資料行排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
描述在控制項中排序資料的選項。

[如何：設定 Windows Form DataGridView 控制項中的資料行排序模式](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
描述如何讓使用者不是預設可排序的資料欄來排序。

[如何：自訂 Windows Form DataGridView 控制項中排序](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
說明如何以程式設計的方式排序資料以及如何自訂所使用的排序<xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType>事件或實作<xref:System.Collections.IComparer>介面。

## <a name="reference"></a>參考資料

<xref:System.Windows.Forms.DataGridView>  
提供 <xref:System.Windows.Forms.DataGridView> 控制項的參考文件。  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
提供參考文件<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
提供參考文件<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>屬性。

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
提供參考文件<xref:System.Windows.Forms.DataGridViewColumnSortMode>列舉型別。

## <a name="see-also"></a>另請參閱

- [DataGridView 控制項](datagridview-control-windows-forms.md)
- [Windows Forms DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
