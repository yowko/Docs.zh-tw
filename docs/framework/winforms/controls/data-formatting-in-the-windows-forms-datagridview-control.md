---
title: Windows Form DataGridView 控制項中的資料格式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: ae1947cf7c3825553837fa5f1ee288114988d28f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料格式
<xref:System.Windows.Forms.DataGridView>控制項提供自動資料格的值與父資料行顯示的資料類型之間轉換。 文字方塊資料行，例如顯示的日期、 時間、 數字和列舉值的字串表示法，並將使用者輸入的字串值轉換為資料存放區所需的類型。  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>格式化與 DataGridViewCellStyle 類別  
 <xref:System.Windows.Forms.DataGridView>控制項提供基本的資料格式的資料格值透過<xref:System.Windows.Forms.DataGridViewCellStyle>類別。 您可以使用<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>屬性來格式化日期、 時間、 數字和列舉值目前使用中所述的格式規範的預設文化特性[格式化型別](../../../../docs/standard/base-types/formatting-types.md)。 您也可以格式化特定文化特性使用的這些值<xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>屬性。 指定的格式用來顯示資料，並剖析使用者輸入中指定的格式的資料。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>類別自動換行、 文字對齊方式，以及資料庫 null 值的自訂顯示提供額外的格式化屬性。 如需詳細資訊，請參閱[如何：格式化 Windows Forms DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="formatting-with-the-cellformatting-event"></a>格式化與 CellFormatting 事件  
 如果基本的格式不符合您的需求，您可以提供自訂中的資料格式的處理常式<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件。 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>傳遞至處理常式具有<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>屬性一開始不包含儲存格的值。 一般來說，這個值會自動轉換為顯示類型。 若要自行轉換值，設定<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>屬性設為顯示類型的值。  
  
> [!NOTE]
>  如果格式字串是作用中的儲存格，它會覆寫您的變更<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>屬性值，除非您將設定<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A>屬性`true`。  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>事件時也很有用您想要設定<xref:System.Windows.Forms.DataGridViewCellStyle>個別資料格的內容會根據它們的值。 如需詳細資訊，請參閱[How to： 在 Windows Form DataGridView 控制項中自訂格式化資料](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
 如果使用者指定值的預設值剖析不符合您的需求，您可以處理<xref:System.Windows.Forms.DataGridView.CellParsing>事件<xref:System.Windows.Forms.DataGridView>控制項來提供自訂剖析。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [操作說明：格式化 Windows Forms DataGridView 控制項中的資料](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [操作說明：自訂 Windows Forms DataGridView 控制項中的資料格式](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
