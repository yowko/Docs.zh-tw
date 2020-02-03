---
title: DataGridView 控制項中的資料格式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: a041bcc5e1b65afb3123f1f42e0f1b5a479b5764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743991"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料格式
[<xref:System.Windows.Forms.DataGridView>] 控制項提供資料格值與父欄位顯示之資料類型之間的自動轉換。 文字方塊資料行，例如，顯示日期、時間、數位和列舉值的字串標記法，並將使用者輸入的字串值轉換成資料存放區所需的類型。  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>使用 DataGridViewCellStyle 類別進行格式設定  
 <xref:System.Windows.Forms.DataGridView> 控制項會透過 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別，提供儲存格值的基本資料格式。 您可以使用 [<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>] 屬性，利用[格式化類型](../../../standard/base-types/formatting-types.md)中所述的格式規範來格式化目前預設文化特性的日期、時間、數位和列舉值。 您也可以使用 <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> 屬性，針對特定文化特性來格式化這些值。 指定的格式會用於顯示資料，以及剖析使用者以指定格式輸入的資料。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> 類別會針對自動換行、文字對齊以及 null 資料庫值的自訂顯示，提供額外的格式屬性。 如需詳細資訊，請參閱[如何：格式化 Windows Forms DataGridView 控制項中的資料](how-to-format-data-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="formatting-with-the-cellformatting-event"></a>使用 CellFormatting 事件格式化  
 如果基本格式不符合您的需求，您可以在 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> 事件的處理常式中提供自訂的資料格式。 傳遞至處理常式的 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> 具有 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> 屬性，其一開始會包含儲存格的值。 一般來說，此值會自動轉換成顯示類型。 若要自行轉換值，請將 [<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>] 屬性設定為 [顯示類型] 的值。  
  
> [!NOTE]
> 如果格式字串適用于資料格，則會覆寫 <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> 屬性值的變更，除非您將 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> 屬性設定為 [`true`]。  
  
 當您想要根據個別資料格的值來設定 <xref:System.Windows.Forms.DataGridViewCellStyle> 屬性時，<xref:System.Windows.Forms.DataGridView.CellFormatting> 事件也很有用。 如需詳細資訊，請參閱[如何：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
 如果使用者指定值的預設剖析不符合您的需求，您可以處理 <xref:System.Windows.Forms.DataGridView> 控制項的 <xref:System.Windows.Forms.DataGridView.CellParsing> 事件，以提供自訂剖析。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [操作說明：格式化 Windows Forms DataGridView 控制項中的資料](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
