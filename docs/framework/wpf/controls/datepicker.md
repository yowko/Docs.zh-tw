---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd2a1755ae076369661b2c9a7a2b744961cdb129
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker>控制項可讓使用者選取日期，可能輸入到文字欄位，或使用下拉式清單<xref:System.Windows.Controls.Calendar>控制項。  
  
 下圖顯示<xref:System.Windows.Controls.DatePicker>。  
  
 ![DatePicker 控制項](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")  
日期選擇器控制項  
  
 許多<xref:System.Windows.Controls.DatePicker>控制項的屬性是用於管理內建的<xref:System.Windows.Controls.Calendar>，以及相同 function 中的相等屬性<xref:System.Windows.Controls.Calendar>。 特別是， <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>， <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>，和<xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType>屬性函式和其<xref:System.Windows.Controls.Calendar>對應項目。 如需詳細資訊，請參閱<xref:System.Windows.Controls.Calendar>。  
  
 使用者可以直接在文字欄位中，設定輸入日期<xref:System.Windows.Controls.DatePicker.Text%2A>屬性。 如果<xref:System.Windows.Controls.DatePicker>無法將輸入的字串轉換成有效的日期，<xref:System.Windows.Controls.DatePicker.DateValidationError>會引發事件。 根據預設，這會導致例外狀況，但事件處理常式<xref:System.Windows.Controls.DatePicker.DateValidationError>可以設定<xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A>屬性`false`並防止所引發的例外狀況。  
  
## <a name="see-also"></a>請參閱  
 [控制項](../../../../docs/framework/wpf/controls/index.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
