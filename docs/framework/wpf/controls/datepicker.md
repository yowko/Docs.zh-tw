---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 3e66b2306c11c54db14eb05cc6860257635cc653
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460351"
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker> 控制項可讓使用者在文字欄位中輸入日期，或使用下拉式 <xref:System.Windows.Controls.Calendar> 控制項來選取日期。  
  
 下圖顯示 <xref:System.Windows.Controls.DatePicker>。  
  
 ![DatePicker 控制項](./media/ndp-datepicker.png "NDP_DatePicker")  
DatePicker 控制項  
  
 許多 <xref:System.Windows.Controls.DatePicker> 控制項的屬性都是用來管理其內建 <xref:System.Windows.Controls.Calendar>，而且功能與 <xref:System.Windows.Controls.Calendar>中的對等屬性相同。 特別的是，<xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>和 <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> 屬性的功能與其 <xref:System.Windows.Controls.Calendar> 對應專案相同。 如需詳細資訊，請參閱<xref:System.Windows.Controls.Calendar>。  
  
 使用者可以直接在文字欄位中輸入日期，這會設定 <xref:System.Windows.Controls.DatePicker.Text%2A> 屬性。 如果 <xref:System.Windows.Controls.DatePicker> 無法將輸入的字串轉換成有效的日期，就會引發 <xref:System.Windows.Controls.DatePicker.DateValidationError> 事件。 根據預設，這會造成例外狀況，但 <xref:System.Windows.Controls.DatePicker.DateValidationError> 的事件處理常式可以將 <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> 屬性設定為 `false`，並避免引發例外狀況。  
  
## <a name="see-also"></a>請參閱

- [控制項](index.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
