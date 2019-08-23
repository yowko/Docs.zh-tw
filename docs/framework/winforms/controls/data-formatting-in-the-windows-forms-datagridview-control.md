---
title: Windows Form DataGridView 控制項中的資料格式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 5966f16238999655d6072c1127e5bf16aefde5e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969178"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項中的資料格式
控制項<xref:System.Windows.Forms.DataGridView>會在資料格值與父資料行所顯示的資料類型之間提供自動轉換。 文字方塊資料行, 例如, 顯示日期、時間、數位和列舉值的字串標記法, 並將使用者輸入的字串值轉換成資料存放區所需的類型。  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>使用 DataGridViewCellStyle 類別進行格式設定  
 <xref:System.Windows.Forms.DataGridView> 控制項會<xref:System.Windows.Forms.DataGridViewCellStyle>透過類別提供儲存格值的基本資料格式。 您可以使用<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>屬性, 利用[格式化](../../../standard/base-types/formatting-types.md)型別中所述的格式規範來格式化目前預設文化特性的日期、時間、數位和列舉值。 您也可以使用<xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>屬性, 針對特定文化特性來格式化這些值。 指定的格式會用於顯示資料, 以及剖析使用者以指定格式輸入的資料。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>類別會針對自動換行、文字對齊以及 null 資料庫值的自訂顯示, 提供額外的格式屬性。 如需詳細資訊，請參閱[如何：格式化 Windows Forms DataGridView 控制項](how-to-format-data-in-the-windows-forms-datagridview-control.md)中的資料。  
  
## <a name="formatting-with-the-cellformatting-event"></a>使用 CellFormatting 事件格式化  
 如果基本格式不符合您的需求, 您可以在<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件的處理常式中提供自訂的資料格式。 傳遞<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>至處理常式的會具有<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>一開始包含儲存格值的屬性。 一般來說, 此值會自動轉換成顯示類型。 若要自行轉換值, 請將<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>屬性設定為顯示類型的值。  
  
> [!NOTE]
> 如果格式字串對儲存格有效, 除非您<xref:System.Windows.Forms.ConvertEventArgs.Value%2A> <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A>將屬性設定為`true`, 否則會覆寫屬性值的變更。  
  
 當<xref:System.Windows.Forms.DataGridView.CellFormatting>您想要根據值來設定<xref:System.Windows.Forms.DataGridViewCellStyle>個別資料格的屬性時, 此事件也很有用。 如需詳細資訊，請參閱[如何：自訂 Windows Forms DataGridView 控制項](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)中的資料格式。  
  
 如果使用者指定值的預設剖析不符合您的需求, 您可以處理<xref:System.Windows.Forms.DataGridView.CellParsing> <xref:System.Windows.Forms.DataGridView>控制項的事件, 以提供自訂剖析。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [如何：格式化 Windows Forms DataGridView 控制項中的資料](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [如何：自訂 Windows Forms DataGridView 控制項中的資料格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
