---
title: "日期選擇器樣式和範本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fbe8a3935da2d9aa928467b4c64da455f3b53c5f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker-styles-and-templates"></a>日期選擇器樣式和範本
本主題描述樣式和範本<xref:System.Windows.Controls.DatePicker>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="datepicker-parts"></a>日期選擇器組件  
 下表列出的具名組件<xref:System.Windows.Controls.DatePicker>控制項。  
  
|組件|類型|說明|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|控制項的根目錄。|  
|PART_Button|<xref:System.Windows.Controls.Button>|開啟和關閉按鈕<xref:System.Windows.Controls.Calendar>。|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|文字方塊，可讓您輸入的日期。|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|快顯<xref:System.Windows.Controls.DatePicker>控制項。|  
  
## <a name="datepicker-states"></a>日期選擇器狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.DatePicker>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|<xref:System.Windows.Controls.DatePicker>已停用。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.DatePickerTextBox>控制項。  
  
|組件|類型|說明|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|包含的初始文字中的項目<xref:System.Windows.Controls.DatePicker>。|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|可以包含視覺項目<xref:System.Windows.FrameworkElement>。 文字<xref:System.Windows.Controls.TextBox>會顯示在這個項目。|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.DatePickerTextBox>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>已停用。|  
|MouseOver|CommonStates|滑鼠指標位於<xref:System.Windows.Controls.Primitives.DatePickerTextBox>。|  
|ReadOnly|CommonStates|使用者無法變更中的文字<xref:System.Windows.Controls.Primitives.DatePickerTextBox>。|  
|已取得焦點|FocusStates|控制項已取得焦點。|  
|未取得焦點|FocusStates|控制項未取得焦點。|  
|浮水印|WatermarkStates|控制項會顯示它的初始文字。  <xref:System.Windows.Controls.Primitives.DatePickerTextBox>處於執行狀態，當使用者未輸入文字，或選取日期。|  
|Unwatermarked|WatermarkStates|使用者所輸入的文字放到<xref:System.Windows.Controls.Primitives.DatePickerTextBox>或選取日期<xref:System.Windows.Controls.DatePicker>。|  
|驗證|ValidationStates|此控制項會使用<xref:System.Windows.Controls.Validation>類別和<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`false`。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`具有焦點的控制項。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加屬性`true`有控制項沒有焦點。|  
  
## <a name="datepicker-controltemplate-example"></a>日期選擇器 ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.DatePicker>控制項。  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
