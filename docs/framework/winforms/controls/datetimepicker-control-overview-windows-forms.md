---
title: DateTimePicker 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
ms.openlocfilehash: 63271dd91116c1f68d426f3ed5aa710644ded928
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746935"
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.DateTimePicker> 控制項可讓使用者從日期或時間清單中選取單一專案。 用來表示日期時，它會出現在兩個部分：含有文字表示之日期的下拉式清單，以及當您按一下清單旁邊的向下箭號時，所顯示的方格。 方格看起來就像 <xref:System.Windows.Forms.MonthCalendar> 控制項，可以用來選取多個日期。 如需 <xref:System.Windows.Forms.MonthCalendar> 控制項的詳細資訊，請參閱[MonthCalendar 控制項總覽](monthcalendar-control-overview-windows-forms.md)。  
  
## <a name="key-properties"></a>索引鍵內容  
 如果您希望 <xref:System.Windows.Forms.DateTimePicker> 顯示為用於挑選或編輯時間（而不是日期）的控制項，請將 <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> 屬性設定為 `true`，並將 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設為 [<xref:System.Windows.Forms.DateTimePickerFormat.Time>]。 如需詳細資訊，請參閱[如何：使用 DateTimePicker 控制項顯示時間](how-to-display-time-with-the-datetimepicker-control.md)。  
  
 當 [<xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A>] 屬性設定為 [`true`] 時，控制項中選取的日期旁邊會顯示覆選框。 若核取此核取方塊，則會更新選取的日期時間值。 當核取方塊是空的時，值會顯示為無法使用。  
  
 控制項的 <xref:System.Windows.Forms.DateTimePicker.MaxDate%2A> 和 <xref:System.Windows.Forms.DateTimePicker.MinDate%2A> 屬性會決定日期和時間的範圍。 <xref:System.Windows.Forms.DateTimePicker.Value%2A> 屬性包含控制項設定的目前日期和時間。 如需詳細資訊，請參閱[如何：使用 Windows Forms DateTimePicker 控制項來設定和傳回日期](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)。 這些值可以用四種格式顯示，由 <xref:System.Windows.Forms.DateTimePicker.Format%2A> 屬性設定： <xref:System.Windows.Forms.DateTimePickerFormat.Long>、<xref:System.Windows.Forms.DateTimePickerFormat.Short>、<xref:System.Windows.Forms.DateTimePickerFormat.Time>或 <xref:System.Windows.Forms.DateTimePickerFormat.Custom>。 如果選取了自訂格式，您必須將 <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> 屬性設定為適當的字串。 如需詳細資訊，請參閱[如何：使用 Windows Forms DateTimePicker 控制項，以自訂格式顯示日期](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)。  
  
## <a name="see-also"></a>請參閱

- [操作說明：使用 Windows Forms DateTimePicker 控制項顯示自訂格式的日期](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)
- [操作說明：使用 Windows Forms DateTimePicker 控制項設定和傳回日期](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
