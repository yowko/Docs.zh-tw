---
title: "DateTimePicker 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DateTimePicker
helpviewer_keywords:
- DateTimePicker control [Windows Forms], about
- date and time picker controls
ms.assetid: 501af106-e9fc-4efc-b9b3-c9d8dcaf8c5c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a97eecc43614c84867e9dbdd527dbebd7dfd426e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="datetimepicker-control-overview-windows-forms"></a>DateTimePicker 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.DateTimePicker>控制項可讓使用者選取單一項目從清單中的日期或時間。 用來代表日期時，它會出現在兩個部分： 以文字和一個方格，其中會顯示當您按一下清單旁邊的向下箭號表示日期的下拉式清單。 方格看起來像<xref:System.Windows.Forms.MonthCalendar>控制項，可用來選取多個日期。 如需有關<xref:System.Windows.Forms.MonthCalendar>控制，請參閱[MonthCalendar 控制項概觀](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md)。  
  
## <a name="key-properties"></a>索引鍵內容  
 如果您想<xref:System.Windows.Forms.DateTimePicker>顯示為挑選，或編輯而不是日期時間的控制項，設定<xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A>屬性`true`和<xref:System.Windows.Forms.DateTimePicker.Format%2A>屬性<xref:System.Windows.Forms.DateTimePickerFormat.Time>。 如需詳細資訊，請參閱[How to： 使用 DateTimePicker 控制項顯示時間](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md)。  
  
 當<xref:System.Windows.Forms.DateTimePicker.ShowCheckBox%2A>屬性設定為`true`，控制項中選取的日期旁會顯示核取方塊。 若勾選此核取方塊，就可以更新選取的日期時間值。 當核取方塊是空的時則此值會出現無法使用。  
  
 控制項的<xref:System.Windows.Forms.DateTimePicker.MaxDate%2A>和<xref:System.Windows.Forms.DateTimePicker.MinDate%2A>屬性會決定日期和時間的範圍。 <xref:System.Windows.Forms.DateTimePicker.Value%2A>屬性包含目前的日期和時間控制項設定。 如需詳細資訊，請參閱[How to： 設定和傳回日期搭配 Windows Form DateTimePicker 控制項](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)。 值可以顯示四種格式，這是由在<xref:System.Windows.Forms.DateTimePicker.Format%2A>屬性： <xref:System.Windows.Forms.DateTimePickerFormat.Long>， <xref:System.Windows.Forms.DateTimePickerFormat.Short>， <xref:System.Windows.Forms.DateTimePickerFormat.Time>，或<xref:System.Windows.Forms.DateTimePickerFormat.Custom>。 如果選取的自訂格式，則您必須設定<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>屬性設為適當的字串。 如需詳細資訊，請參閱[How to： 使用 Windows Form DateTimePicker 控制項的自訂格式來顯示日期](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：使用 Windows Forms DateTimePicker 控制項顯示自訂格式的日期](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)  
 [操作說明：使用 Windows Forms DateTimePicker 控制項設定和傳回日期](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)
