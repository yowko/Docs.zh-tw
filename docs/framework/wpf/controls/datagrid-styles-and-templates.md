---
title: "DataGrid 樣式和範本 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ControlTemplate [WPF], DataGrid"
  - "DataGrid [WPF], 樣式和範本"
  - "組件 [WPF], DataGrid"
  - "狀態 [WPF], DataGrid"
  - "樣式 [WPF], DataGrid"
  - "範本 [WPF], DataGrid"
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# DataGrid 樣式和範本
本主題說明 <xref:System.Windows.Controls.DataGrid> 控制項的樣式和範本。  您可以修改預設的 <xref:System.Windows.Controls.ControlTemplate>，讓控制項擁有獨特的外觀。  如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## DataGrid 組件  
 下表列出 <xref:System.Windows.Controls.DataGrid> 控制項的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|包含資料行行首的資料列。|  
  
 當您建立 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.Controls.ControlTemplate> 時，您的範本可能在 <xref:System.Windows.Controls.ScrollViewer> 內包含 <xref:System.Windows.Controls.ItemsPresenter> \(<xref:System.Windows.Controls.ItemsPresenter> 會顯示 <xref:System.Windows.Controls.DataGrid> 中的每一個項目，而 <xref:System.Windows.Controls.ScrollViewer> 會啟用控制項內的捲動功能\)。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer> 的直接子系，您必須將 <xref:System.Windows.Controls.ItemsPresenter> 命名為 `ItemsPresenter`。  
  
 <xref:System.Windows.Controls.DataGrid> 的預設範本包含 <xref:System.Windows.Controls.ScrollViewer> 控制項。  如需 <xref:System.Windows.Controls.ScrollViewer> 所定義各組件的詳細資訊，請參閱 [ScrollViewer 樣式和範本](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md)。  
  
## DataGrid 狀態  
 下表列出 <xref:System.Windows.Controls.DataGrid> 控制項的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|Disabled|CommonStates|控制項已停用。|  
|InvalidFocused|ValidationStates|控制項無效，但是有焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且沒有焦點。|  
|Valid|ValidationStates|控制項有效。|  
  
## DataGridCell 組件  
 <xref:System.Windows.Controls.DataGridCell> 項目沒有任何具名組件。  
  
## DataGridCell 狀態  
 下表列出 <xref:System.Windows.Controls.DataGridCell> 項目的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於儲存格上。|  
|Focused|FocusStates|儲存格擁有焦點。|  
|Unfocused|FocusStates|儲存格沒有焦點。|  
|Current|CurrentStates|儲存格是目前的儲存格。|  
|Regular|CurrentStates|儲存格不是目前的儲存格。|  
|Display|InteractionStates|儲存格處於顯示模式。|  
|編輯|InteractionStates|儲存格處於編輯模式。|  
|Selected|SelectionStates|儲存格。|  
|Unselected|SelectionStates|儲存格為未選取。|  
|InvalidFocused|ValidationStates|儲存格無效，但是有焦點。|  
|InvalidUnfocused|ValidationStates|儲存格無效且沒有焦點。|  
|Valid|ValidationStates|儲存格有效。|  
  
## DataGridRow 組件  
 <xref:System.Windows.Controls.DataGridRow> 項目沒有任何具名組件。  
  
## DataGridRow 狀態  
 下表列出 <xref:System.Windows.Controls.DataGridRow> 項目的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於資料列上。|  
|MouseOver\_Editing|CommonStates|滑鼠指標位於資料列上，且資料列處於編輯模式。|  
|MouseOver\_Selected|CommonStates|滑鼠指標位於資料列上，且資料列為已選取。|  
|MouseOver\_Unfocused\_Editing|CommonStates|滑鼠指標位於資料列上，且資料列處於編輯模式，但沒有焦點。|  
|MouseOver\_Unfocused\_Selected|CommonStates|滑鼠指標位於資料列上，且資料列為已選取，但沒有焦點。|  
|Normal\_AlternatingRow|CommonStates|資料列是替代資料列。|  
|Normal\_Editing|CommonStates|資料列處於編輯模式。|  
|Normal\_Selected|CommonStates|資料列為已選取。|  
|Unfocused\_Editing|CommonStates|資料列處於編輯模式，但沒有焦點。|  
|Unfocused\_Selected|CommonStates|資料列為已選取，但沒有焦點。|  
|InvalidFocused|ValidationStates|控制項無效，但是有焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且沒有焦點。|  
|Valid|ValidationStates|控制項有效。|  
  
## DataGridRowHeader 組件  
 下表列出 <xref:System.Windows.Controls.Primitives.DataGridRowHeader> 項目的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|項目，用來從頂端調整資料列行首的大小。|  
|PART\_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|項目，用來從底部調整資料列行首的大小。|  
  
## DataGridRowHeader 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.DataGridRowHeader> 項目的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於資料列上。|  
|MouseOver\_CurrentRow|CommonStates|滑鼠指標位於資料列上，且資料列是目前的資料列。|  
|MouseOver\_CurrentRow\_Selected|CommonStates|滑鼠指標位於資料列上，且資料列是目前的資料列並已選取。|  
|MouseOver\_EditingRow|CommonStates|滑鼠指標位於資料列上，且資料列處於編輯模式。|  
|MouseOver\_Selected|CommonStates|滑鼠指標位於資料列上，且資料列為已選取。|  
|MouseOver\_Unfocused\_CurrentRow\_Selected|CommonStates|滑鼠指標位於資料列上，且資料列是目前的資料列並已選取，但沒有焦點。|  
|MouseOver\_Unfocused\_EditingRow|CommonStates|滑鼠指標位於資料列上，且資料列處於編輯模式，但沒有焦點。|  
|MouseOver\_Unfocused\_Selected|CommonStates|滑鼠指標位於資料列上，且資料列為已選取，但沒有焦點。|  
|Normal\_CurrentRow|CommonStates|資料列是目前的資料列。|  
|Normal\_CurrentRow\_Selected|CommonStates|資料列是目前的資料列並已選取。|  
|Normal\_EditingRow|CommonStates|資料列處於編輯模式。|  
|Normal\_Selected|CommonStates|資料列為已選取。|  
|Unfocused\_CurrentRow\_Selected|CommonStates|資料列是目前的資料列並已選取，但沒有焦點。|  
|Unfocused\_EditingRow|CommonStates|資料列處於編輯模式，但沒有焦點。|  
|Unfocused\_Selected|CommonStates|資料列為已選取，但沒有焦點。|  
|InvalidFocused|ValidationStates|控制項無效，但是有焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且沒有焦點。|  
|Valid|ValidationStates|控制項有效。|  
  
## DataGridColumnHeadersPresenter 組件  
 下表列出 <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> 項目的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|資料行行首的預留位置。|  
  
## DataGridColumnHeadersPresenter 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> 項目的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|InvalidFocused|ValidationStates|儲存格無效，但是有焦點。|  
|InvalidUnfocused|ValidationStates|儲存格無效且沒有焦點。|  
|Valid|ValidationStates|儲存格有效。|  
  
## DataGridColumnHeader 組件  
 下表列出 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> 項目的具名組件。  
  
||||  
|-|-|-|  
|組件|型別|描述|  
|PART\_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|項目，用來從左側調整資料行行首的大小。|  
|PART\_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|項目，用來從右側調整資料行行首的大小。|  
  
## DataGridColumnHeader 狀態  
 下表列出 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> 項目的可見狀態。  
  
||||  
|-|-|-|  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|Normal|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於控制項上方。|  
|Pressed|CommonStates|已按下控制項。|  
|SortAscending|SortStates|資料行以遞增方式排序。|  
|SortDescending|SortStates|資料行以遞減方式排序。|  
|Unsorted|SortStates|資料行未排序。|  
|InvalidFocused|ValidationStates|控制項無效，但是有焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且沒有焦點。|  
|Valid|ValidationStates|控制項有效。|  
  
## DataGrid ControlTemplate 範例  
 下列範例顯示如何定義 <xref:System.Windows.Controls.DataGrid> 控制項的 <xref:System.Windows.Controls.ControlTemplate> 及其關聯的型別。  
  
 [!code-xml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 前述範例使用了下列一或多項資源。  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整範例，請參閱          [使用 ControlTemplates 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041) .  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [控制項的樣式和範本](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [控制項自訂](../../../../docs/framework/wpf/controls/control-customization.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)