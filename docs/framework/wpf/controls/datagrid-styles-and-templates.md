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
ms.openlocfilehash: dacc1222958ab05971c9681d33a0c431b72d0531
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912284"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid 樣式和範本
本主題描述的樣式和範本<xref:System.Windows.Controls.DataGrid>控制項。 您可以修改預設<xref:System.Windows.Controls.ControlTemplate>，讓控制項的獨特的外觀。 如需詳細資訊，請參閱[透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)。  
  
## <a name="datagrid-parts"></a>DataGrid 的組件  
 下表列出的具名組件<xref:System.Windows.Controls.DataGrid>控制項。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|包含資料行行首的資料列。|  
  
 當您建立<xref:System.Windows.Controls.ControlTemplate>for <xref:System.Windows.Controls.DataGrid>，您的範本可能會包含<xref:System.Windows.Controls.ItemsPresenter>內<xref:System.Windows.Controls.ScrollViewer>。 (<xref:System.Windows.Controls.ItemsPresenter>會顯示在每個項目<xref:System.Windows.Controls.DataGrid>;<xref:System.Windows.Controls.ScrollViewer>可在控制項內捲動)。  如果<xref:System.Windows.Controls.ItemsPresenter>不是直接子系<xref:System.Windows.Controls.ScrollViewer>，您必須給予<xref:System.Windows.Controls.ItemsPresenter>名稱， `ItemsPresenter`。  
  
 預設樣板<xref:System.Windows.Controls.DataGrid>包含<xref:System.Windows.Controls.ScrollViewer>控制項。 如需有關所定義的組件<xref:System.Windows.Controls.ScrollViewer>，請參閱 < [ScrollViewer 樣式和範本](scrollviewer-styles-and-templates.md)。  
  
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
 <xref:System.Windows.Controls.DataGridCell>元素並沒有任何具名組件。  
  
## <a name="datagridcell-states"></a>DataGridCell 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.DataGridCell>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於儲存格。|  
|已取得焦點|FocusStates|儲存格具有焦點。|  
|未取得焦點|FocusStates|儲存格未取得焦點|  
|目前|CurrentStates|儲存格位於目前的儲存格。|  
|Regular|CurrentStates|資料格不是目前的儲存格。|  
|顯示|InteractionStates|資料格是在顯示模式。|  
|編輯|InteractionStates|儲存格處於編輯模式。|  
|已選取|SelectionStates|選取儲存格。|  
|未選取|SelectionStates|未選取的資料格。|  
|InvalidFocused|ValidationStates|儲存格不是有效，且焦點時。|  
|InvalidUnfocused|ValidationStates|儲存格不是有效，而且沒有焦點。|  
|驗證|ValidationStates|儲存格是有效的。|  
  
## <a name="datagridrow-parts"></a>DataGridRow 組件  
 <xref:System.Windows.Controls.DataGridRow>元素並沒有任何具名組件。  
  
## <a name="datagridrow-states"></a>DataGridRow 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.DataGridRow>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於資料列。|  
|MouseOver_Editing|CommonStates|滑鼠指標位於資料列和資料列處於編輯模式。|  
|MouseOver_Selected|CommonStates|滑鼠指標位於資料列，並在選取的資料列。|  
|MouseOver_Unfocused_Editing|CommonStates|滑鼠指標位於資料列、 資料列中編輯模式，而且沒有焦點。|  
|MouseOver_Unfocused_Selected|CommonStates|滑鼠指標位於資料列、 資料列已選取，而且沒有焦點。|  
|Normal_AlternatingRow|CommonStates|資料列為替代資料列。|  
|Normal_Editing|CommonStates|資料列處於編輯模式。|  
|Normal_Selected|CommonStates|選取資料列。|  
|Unfocused_Editing|CommonStates|資料列處於編輯模式，而且沒有焦點。|  
|Unfocused_Selected|CommonStates|資料列已選取，而且沒有焦點。|  
|InvalidFocused|ValidationStates|控制項無效且已取得焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且未取得焦點。|  
|驗證|ValidationStates|控制項有效。|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.DataGridRowHeader>項目。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用來調整大小，從頂端資料列標頭的項目。|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用來調整大小資料列標頭從下方的項目。|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader 狀態  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.DataGridRowHeader>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|一般|CommonStates|預設狀態。|  
|MouseOver|CommonStates|滑鼠指標位於資料列。|  
|MouseOver_CurrentRow|CommonStates|滑鼠指標位於資料列和資料列是目前的資料列。|  
|MouseOver_CurrentRow_Selected|CommonStates|滑鼠指標位於資料列，並將資料列是目前和已選取。|  
|MouseOver_EditingRow|CommonStates|滑鼠指標位於資料列和資料列處於編輯模式。|  
|MouseOver_Selected|CommonStates|滑鼠指標位於資料列，並在選取的資料列。|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|滑鼠指標位於資料列，透過的資料列目前並加以選取，以及未取得焦點。|  
|MouseOver_Unfocused_EditingRow|CommonStates|滑鼠指標位於資料列、 資料列中編輯模式，而且沒有焦點。|  
|MouseOver_Unfocused_Selected|CommonStates|滑鼠指標位於資料列、 資料列已選取，而且沒有焦點。|  
|Normal_CurrentRow|CommonStates|資料列是目前的資料列。|  
|Normal_CurrentRow_Selected|CommonStates|資料列目前的資料列，並選取。|  
|Normal_EditingRow|CommonStates|資料列處於編輯模式。|  
|Normal_Selected|CommonStates|選取資料列。|  
|Unfocused_CurrentRow_Selected|CommonStates|資料列是目前資料列已選取，未取得焦點。|  
|Unfocused_EditingRow|CommonStates|資料列處於編輯模式，而且沒有焦點。|  
|Unfocused_Selected|CommonStates|資料列已選取，而且沒有焦點。|  
|InvalidFocused|ValidationStates|控制項無效且已取得焦點。|  
|InvalidUnfocused|ValidationStates|控制項無效且未取得焦點。|  
|驗證|ValidationStates|控制項有效。|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>項目。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|資料行標頭的預留位置。|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter States  
 下表列出的視覺狀態<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>項目。  
  
|VisualState 名稱|VisualStateGroup 名稱|描述|  
|-|-|-|  
|InvalidFocused|ValidationStates|儲存格不是有效，且焦點時。|  
|InvalidUnfocused|ValidationStates|儲存格不是有效，而且沒有焦點。|  
|驗證|ValidationStates|儲存格是有效的。|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader 組件  
 下表列出的具名組件<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>項目。  
  
|組件|類型|描述|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用來調整資料行行首，從左邊的項目。|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用來調整大小資料行標頭的右邊的項目。|  
  
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
 下列範例示範如何定義<xref:System.Windows.Controls.ControlTemplate>針對<xref:System.Windows.Controls.DataGrid>控制項和其相關聯的類型。  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 上述範例使用下列一或多項資源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 如需完整的範例，請參閱[使用 ControlTemplate 設定樣式範例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控制項的樣式和範本](control-styles-and-templates.md)
- [控制項自訂](control-customization.md)
- [樣式設定和範本化](styling-and-templating.md)
- [透過建立 ControlTemplate 自訂現有控制項的外觀](customizing-the-appearance-of-an-existing-control.md)
