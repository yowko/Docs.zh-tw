---
title: DataGrid 樣式和範本
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: e41fe0eb3cce2561514e472a2034e91eea921c12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="datagrid-styles-and-templates"></a>DataGrid 樣式和範本
本主題描述樣式和範本<xref:System.Windows.Controls.DataGrid>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>來提供獨特的外觀的控制項。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="datagrid-parts"></a>DataGrid 的組件  
 下表列出的具名組件<xref:System.Windows.Controls.DataGrid>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|包含資料行標頭的資料列。|  
  
 當您建立<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.DataGrid>，可能會包含您的範本<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。 (<xref:System.Windows.Controls.ItemsPresenter>會顯示每個項目<xref:System.Windows.Controls.DataGrid>;<xref:System.Windows.Controls.ScrollViewer>可捲動控制項內)。  如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須提供<xref:System.Windows.Controls.ItemsPresenter>名稱`ItemsPresenter`。  
  
 預設範本<xref:System.Windows.Controls.DataGrid>包含<xref:System.Windows.Controls.ScrollViewer>控制項。 如需有關所定義的組件<xref:System.Windows.Controls.ScrollViewer>，請參閱[ScrollViewer 樣式和範本](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md)。  
  
## <a name="datagrid-states"></a>DataGrid 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.DataGrid>控制項。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|已停用|CommonStates|已停用控制項。|  
|InvalidFocused|ValidationStates|控制項無效且已取得焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且未取得焦點。|  
|驗證|ValidationStates|控制項有效。|  
  
## <a name="datagridcell-parts"></a>DataGridCell 組件  
 <xref:System.Windows.Controls.DataGridCell>項目沒有任何已命名的組件。  
  
## <a name="datagridcell-states"></a>DataGridCell 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.DataGridCell>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於資料格。|  
|已取得焦點|FocusStates|資料格具有焦點。|  
|未取得焦點|FocusStates|資料格沒有焦點|  
|目前|CurrentStates|資料格是目前儲存格。|  
|Regular|CurrentStates|資料格不是目前儲存格。|  
|顯示|InteractionStates|儲存格是在顯示模式。|  
|編輯|InteractionStates|儲存格處於編輯模式。|  
|已選取|SelectionStates|選取儲存格。|  
|未選取|SelectionStates|未選取的資料格。|  
|InvalidFocused|ValidationStates|資料格不正確，而且具有焦點。|  
|InvalidUnfocused|ValidationStates|資料格不是有效的而且沒有焦點。|  
|驗證|ValidationStates|資料格是有效的。|  
  
## <a name="datagridrow-parts"></a>Datagridrow 不組件  
 <xref:System.Windows.Controls.DataGridRow>項目沒有任何已命名的組件。  
  
## <a name="datagridrow-states"></a>Datagridrow 不狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.DataGridRow>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於資料列。|  
|MouseOver_Editing|CommonStates|滑鼠指標位於資料列和資料列處於編輯模式。|  
|MouseOver_Selected|CommonStates|滑鼠指標位於資料列，並在選取的資料列。|  
|MouseOver_Unfocused_Editing|CommonStates|滑鼠指標位於資料列、 資料列位於編輯模式，並沒有焦點。|  
|MouseOver_Unfocused_Selected|CommonStates|滑鼠指標位於資料列、 資料列已選取，並沒有焦點。|  
|Normal_AlternatingRow|CommonStates|資料列為交替的資料列。|  
|Normal_Editing|CommonStates|在資料列處於編輯模式。|  
|Normal_Selected|CommonStates|選取的資料列。|  
|Unfocused_Editing|CommonStates|資料列處於編輯模式，而且沒有焦點。|  
|Unfocused_Selected|CommonStates|資料列已選取，而且沒有焦點。|  
|InvalidFocused|ValidationStates|控制項無效且已取得焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且未取得焦點。|  
|驗證|ValidationStates|控制項有效。|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.DataGridRowHeader>項目。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用來調整資料列行首，從頂端的項目。|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用來調整資料列行首，從最下方的項目。|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.DataGridRowHeader>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於資料列。|  
|MouseOver_CurrentRow|CommonStates|滑鼠指標位於資料列和資料列是目前的資料列。|  
|MouseOver_CurrentRow_Selected|CommonStates|滑鼠指標位於資料列，並將資料列是目前並已選取。|  
|MouseOver_EditingRow|CommonStates|滑鼠指標位於資料列和資料列處於編輯模式。|  
|MouseOver_Selected|CommonStates|滑鼠指標位於資料列，並在選取的資料列。|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|滑鼠指標位於資料列，資料列目前並加以選取，而且沒有焦點。|  
|MouseOver_Unfocused_EditingRow|CommonStates|滑鼠指標位於資料列、 資料列位於編輯模式，並沒有焦點。|  
|MouseOver_Unfocused_Selected|CommonStates|滑鼠指標位於資料列、 資料列已選取，並沒有焦點。|  
|Normal_CurrentRow|CommonStates|資料列是目前的資料列。|  
|Normal_CurrentRow_Selected|CommonStates|資料列目前資料列，並已選取。|  
|Normal_EditingRow|CommonStates|在資料列處於編輯模式。|  
|Normal_Selected|CommonStates|選取的資料列。|  
|Unfocused_CurrentRow_Selected|CommonStates|資料列目前資料列、 已選取，而且沒有焦點。|  
|Unfocused_EditingRow|CommonStates|資料列處於編輯模式，而且沒有焦點。|  
|Unfocused_Selected|CommonStates|資料列已選取，而且沒有焦點。|  
|InvalidFocused|ValidationStates|控制項無效且已取得焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且未取得焦點。|  
|驗證|ValidationStates|控制項有效。|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>項目。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|資料行標頭預留位置。|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|InvalidFocused|ValidationStates|資料格不正確，而且具有焦點。|  
|InvalidUnfocused|ValidationStates|資料格不是有效的而且沒有焦點。|  
|驗證|ValidationStates|資料格是有效的。|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>項目。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用來調整資料行行首從左邊的項目。|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用來調整資料行行首從右邊項目。|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標移到控制項上。|  
|按下|CommonStates|已按下控制項。|  
|SortAscending|SortStates|資料行是以遞增順序排序。|  
|SortDescending|SortStates|資料行是以遞減順序排序。|  
|未排序|SortStates|未排序的資料行。|  
|InvalidFocused|ValidationStates|控制項無效且已取得焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且未取得焦點。|  
|驗證|ValidationStates|控制項有效。|  
  
## <a name="datagrid-controltemplate-example"></a>DataGrid ControlTemplate 範例  
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.DataGrid>控制項和其相關聯的類型。  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
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
