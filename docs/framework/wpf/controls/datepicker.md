---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 555bf31b27ba233ffa54438077984b02b5e3084a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161329"
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker>控制項可讓使用者輸入到文字欄位，或使用下拉式清單選取日期<xref:System.Windows.Controls.Calendar>控制項。  
  
 下圖顯示<xref:System.Windows.Controls.DatePicker>。  
  
 ![DatePicker 控制項](./media/ndp-datepicker.png "NDP_DatePicker")  
DatePicker 控制項  
  
 許多<xref:System.Windows.Controls.DatePicker>控制項的屬性是用於管理內建<xref:System.Windows.Controls.Calendar>，和用於對等的屬性，在相同函式<xref:System.Windows.Controls.Calendar>。 特別的是， <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>，以及<xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType>屬性的功能和其<xref:System.Windows.Controls.Calendar>對應項目。 如需詳細資訊，請參閱<xref:System.Windows.Controls.Calendar>。  
  
 使用者可以直接在文字欄位中，它會設定輸入日期<xref:System.Windows.Controls.DatePicker.Text%2A>屬性。 如果<xref:System.Windows.Controls.DatePicker>無法將輸入的字串轉換成有效的日期，<xref:System.Windows.Controls.DatePicker.DateValidationError>就會引發事件。 根據預設，這會導致例外狀況，但事件處理常式<xref:System.Windows.Controls.DatePicker.DateValidationError>可以設定<xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A>屬性設`false`並避免引發例外狀況。  
  
## <a name="see-also"></a>另請參閱

- [控制項](index.md)
- [樣式設定和範本化](styling-and-templating.md)
