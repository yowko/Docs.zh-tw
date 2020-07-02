---
title: 格式化 DataGridView 控制項中的資料
description: 瞭解如何使用 Windows Forms DataGridView 控制項的 Datagridviewband.defaultcellstyle 屬性和控制項中的特定資料行來格式化資料格值。
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
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622805"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>如何：格式化 Windows Form DataGridView 控制項中的資料
下列程式示範如何使用控制項的 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 屬性 <xref:System.Windows.Forms.DataGridView> 和控制項中特定資料行的屬性，來顯示資料格值的基本格式。 如需有關 advanced data 格式的詳細資訊，請參閱[如何：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="to-format-currency-and-date-values"></a>若要格式化貨幣和日期值  
  
- 設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 屬性。 下列程式碼範例會使用資料行的屬性來設定特定資料行的格式 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 。 資料行中的值 `UnitPrice` 會以目前的文化特性特定貨幣格式顯示，並以括弧括住負數值。 資料行中的值 `ShipDate` 會以目前的特定文化特性簡短日期格式出現。 如需有關值的詳細資訊 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> ，請參閱[格式化類型](../../../standard/base-types/formatting-types.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>若要自訂 null 資料庫值的顯示  
  
- 設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 屬性。 下列程式碼範例會使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性，在包含等於之值的所有資料格中顯示「沒有專案」 <xref:System.DBNull.Value?displayProperty=nameWithType> 。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>若要在以文字為基礎的資料格中啟用自動換行  
  
- 將的 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 屬性設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 為其中一個 <xref:System.Windows.Forms.DataGridViewTriState> 列舉值。 下列程式碼範例會使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 屬性來設定整個控制項的換行模式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>若要指定 DataGridView 儲存格的文字對齊方式  
  
- 將的 <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> 屬性設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 為其中一個 <xref:System.Windows.Forms.DataGridViewContentAlignment> 列舉值。 下列程式碼範例會使用資料行的屬性來設定特定資料行的對齊方式 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這些範例需要：  
  
- <xref:System.Windows.Forms.DataGridView>名為 `dataGridView1` 的控制項，其中包含名為的資料行 `UnitPrice` 、名為的資料行 `ShipDate` ，以及名為的資料行 `CustomerName` 。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="robust-programming"></a>穩固程式設計  
 為了達到最大的擴充性，您應該 <xref:System.Windows.Forms.DataGridViewCellStyle> 跨多個資料列、資料行或資料格共用物件，而這些資料列使用相同的樣式，而不是分別設定每個元素的樣式屬性。 如需詳細資訊，請參閱 [縮放 Windows Form DataGridView 控制項的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Form DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)
- [如何：自訂 Windows Form DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [格式化類型](../../../standard/base-types/formatting-types.md)
