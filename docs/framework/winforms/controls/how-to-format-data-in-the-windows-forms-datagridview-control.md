---
title: 格式化 DataGridView 控制項中的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 9ee2869cf4085b5acfdf1f8c440151be506dbe3e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736782"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>如何：格式化 Windows Form DataGridView 控制項中的資料
下列程式示範使用 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 屬性和控制項中特定資料行的資料格值的基本格式。 如需有關 advanced data 格式的詳細資訊，請參閱[如何：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="to-format-currency-and-date-values"></a>若要格式化貨幣和日期值  
  
- 設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 屬性。 下列程式碼範例會使用資料行的 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 屬性來設定特定資料行的格式。 [`UnitPrice`] 資料行中的值會以目前的特定文化特性貨幣格式顯示，並以括弧括住負數值。 [`ShipDate`] 資料行中的值會以目前的特定文化特性簡短日期格式出現。 如需 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 值的詳細資訊，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>若要自訂 null 資料庫值的顯示  
  
- 設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 屬性。 下列程式碼範例會使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性，在包含等於 <xref:System.DBNull.Value?displayProperty=nameWithType>之值的所有資料格中顯示「沒有專案」。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>若要在以文字為基礎的資料格中啟用自動換行  
  
- 將 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.DataGridViewTriState> 的列舉值。 下列程式碼範例會使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性來設定整個控制項的換行模式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>若要指定 DataGridView 儲存格的文字對齊方式  
  
- 將 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> 屬性設定為其中一個 <xref:System.Windows.Forms.DataGridViewContentAlignment> 的列舉值。 下列程式碼範例會使用資料行的 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 屬性來設定特定資料行的對齊方式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這些範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項，其中包含名為 `UnitPrice`的資料行、名為 `ShipDate`的資料行，以及名為 `CustomerName`的資料行。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="robust-programming"></a>最佳化程式設計  
 為了達到最大的擴充性，您應該跨多個資料列、資料行或使用相同樣式的資料格共用 <xref:System.Windows.Forms.DataGridViewCellStyle> 物件，而不是分別設定每個元素的樣式屬性。 如需詳細資訊，請參閱[縮放 Windows Forms DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)
- [操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [格式化類型](../../../standard/base-types/formatting-types.md)
