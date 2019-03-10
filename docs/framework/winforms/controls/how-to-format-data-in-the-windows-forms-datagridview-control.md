---
title: HOW TO：格式資料中的 Windows Forms DataGridView 控制項
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
ms.openlocfilehash: 0699aec73c0a48efe88fc2901ef11c70d6f639d7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721277"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>HOW TO：格式資料中的 Windows Forms DataGridView 控制項
下列程序將示範基本的資料格的值使用的格式<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>屬性<xref:System.Windows.Forms.DataGridView>控制項和控制項中的特定資料行。 如需進階的資料格式資訊，請參閱[How to:自訂 Windows Form DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="to-format-currency-and-date-values"></a>若要將貨幣格式化數值和日期值  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 屬性。 下列程式碼範例會設定使用的特定資料行的格式<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>的資料行的屬性。 中的值`UnitPrice`資料行出現在目前的特定文化特性的貨幣格式，與括號括住的負數值。 中的值`ShipDate`目前文化特性的簡短日期格式顯示資料行。 如需詳細資訊<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>值，請參閱[格式化型別](../../../standard/base-types/formatting-types.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>若要自訂資料庫 null 值的顯示  
  
-   設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 屬性。 下列程式碼範例會使用<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>屬性來顯示 「 沒有項目 」 中所有的資料格包含值等於<xref:System.DBNull.Value?displayProperty=nameWithType>。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>若要啟用自動換行中以文字為基礎的資料格  
  
-   設定<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>的屬性<xref:System.Windows.Forms.DataGridViewCellStyle>的其中一個<xref:System.Windows.Forms.DataGridViewTriState>列舉值。 下列程式碼範例使用<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>屬性來設定整個控制項的自動換行模式。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>若要指定 DataGridView 儲存格中的文字對齊方式  
  
-   設定<xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>的屬性<xref:System.Windows.Forms.DataGridViewCellStyle>的其中一個<xref:System.Windows.Forms.DataGridViewContentAlignment>列舉值。 下列程式碼範例會設定特定的資料行，使用的對齊方式<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>資料行屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這些範例需要：  
  
-   A<xref:System.Windows.Forms.DataGridView>控制項，名為`dataGridView1`，其中包含名為的資料行`UnitPrice`，為的資料行`ShipDate`，和名為資料行`CustomerName`。  
  
-   
  <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="robust-programming"></a>穩固程式設計  
 最大延展性，您應該共用<xref:System.Windows.Forms.DataGridViewCellStyle>跨多個資料列、 資料行或使用相同的樣式，而不是分別設定每個項目之樣式屬性的資料格的物件。 如需詳細資訊，請參閱 <<c0> [ 縮放 Windows Form DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料格式](data-formatting-in-the-windows-forms-datagridview-control.md)
- [如何：自訂 Windows Form DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [格式化類型](../../../standard/base-types/formatting-types.md)
