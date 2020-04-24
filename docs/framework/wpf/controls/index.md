---
title: 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 2aab0fc8adaf17a8e9820a6269a740ef09540cda
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646478"
---
# <a name="controls"></a>控制項
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]附帶許多常用的 UI 元件,這些元件用於幾乎每個 Windows 應用程式<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Label>,<xref:System.Windows.Controls.TextBox>例如<xref:System.Windows.Controls.Menu><xref:System.Windows.Controls.ListBox>、 與 。 在過去，這些物件是稱為控制項。 雖然[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]SDK 繼續使用術語「控件」來鬆散地表示表示應用程式中可見物件的任何類,但請務必注意,類<xref:System.Windows.Controls.Control>不需要從 類繼承來具有可見狀態。 從類繼承的<xref:System.Windows.Controls.Control>類別包含<xref:System.Windows.Controls.ControlTemplate>, 它允許控制項的消費者從根本上改變控制件的外觀,而無需創建新的子類。  這個主題討論如何在<xref:System.Windows.Controls.Control>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中常用控制項(從類別繼承的控制項和未從類繼承的控制件)  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>建立控制項的執行個體  
 可以使用 任一[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或代碼向應用程式添加控制項。  下列範例示範如何建立一個要求使用者輸入其名字和姓氏的簡單應用程式。  本示例在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中 創建六個控制項:兩個標籤、兩個文字框和兩個按鈕。 您可以用類似的方式建立所有控制項。  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 下列範例會以程式碼建立相同的應用程式。 為簡潔起見,從樣本中排除了<xref:System.Windows.Controls.Grid>的`grid1`創建。 `grid1`具有與上例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]所示相同的列和行定義。  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>變更控制項的外觀  
 變更控制項的外觀以符合您應用程式的外觀及操作，是很常見的做法。 您可以根據想要達成的目的，執行下列其中一項操作來變更控制項的外觀：  
  
- 變更控制項的屬性值。  
  
- 為控制項<xref:System.Windows.Style>建立 。  
  
- <xref:System.Windows.Controls.ControlTemplate>為控制項創建新控制項。  
  
### <a name="changing-a-controls-property-value"></a>變更控制項的屬性值  
 許多控制檔具有允許您變更控制檔顯示方式的屬性,例如<xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> 。 您可以在和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]代碼中設置值屬性。 下面的範例在<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Control.FontSize%2A><xref:System.Windows.Controls.Control.FontWeight%2A><xref:System.Windows.Controls.Button>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中設置、 屬性。  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 下列範例會以程式碼設定相同的屬性。  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>為控制項建立樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]以建立 ,可以大規模指定控制項的外觀,而不是設定應用程式中每個實體的屬性<xref:System.Windows.Style>。 下面的範例建立<xref:System.Windows.Style>套用應用程式中每個<xref:System.Windows.Controls.Button>應用程式的 。 <xref:System.Windows.Style>定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]通常在<xref:System.Windows.ResourceDictionary>中<xref:System.Windows.FrameworkElement.Resources%2A>定義,如<xref:System.Windows.FrameworkElement>的屬性。  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 還可以通過將鍵分配給樣式並在控件`Style`的屬性中指定該鍵,僅將樣式應用於特定類型的特定控制項。  有關樣式的詳細資訊,請參閱[樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)化。  
  
### <a name="creating-a-controltemplate"></a>建立 ControlTemplate  
 允許您<xref:System.Windows.Style>一次在多個控制項上設置屬性,但有時您可能希望自定義<xref:System.Windows.Controls.Control>的外觀,超出透過創建可以執行<xref:System.Windows.Style>的內容。 從類繼承的<xref:System.Windows.Controls.Control>類別,<xref:System.Windows.Controls.ControlTemplate>它定義<xref:System.Windows.Controls.Control>的結構和外觀。 的屬性<xref:System.Windows.Controls.Control.Template%2A><xref:System.Windows.Controls.Control>是公共的,因此您可以給出此預設值不同的<xref:System.Windows.Controls.Control><xref:System.Windows.Controls.ControlTemplate>。 通常可以為<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.Control>指定 new,而不是從控制項繼承以自訂<xref:System.Windows.Controls.Control>的外觀。  
  
 請考慮很常見的控制。 <xref:System.Windows.Controls.Button>  的主要行為<xref:System.Windows.Controls.Button>是使應用程式能夠在用戶按一下時執行某些操作。  默認情況下,in<xref:System.Windows.Controls.Button>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]顯示為凸起的矩形。  在開發應用程式時,您可能希望利用<xref:System.Windows.Controls.Button>-- -- 即透過處理按鈕的單擊事件來利用「的行為」,但您可以透過更改按鈕的屬性來更改按鈕的外觀, 超出您可以執行的操作。  在這種情況下,您可以建立新的<xref:System.Windows.Controls.ControlTemplate>。  
  
 下面的範例為<xref:System.Windows.Controls.ControlTemplate>建立<xref:System.Windows.Controls.Button>。  建立<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.Button>以圓角與漸層背景的 。  <xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.Border><xref:System.Windows.Controls.Border.Background%2A>此項目是<xref:System.Windows.Media.LinearGradientBrush>具有<xref:System.Windows.Media.GradientStop>兩個 物件的 。  第一<xref:System.Windows.Media.GradientStop>個使用數據綁定<xref:System.Windows.Media.GradientStop.Color%2A>將<xref:System.Windows.Media.GradientStop>的屬性 綁定到按鈕背景的顏色。  設定的屬性<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Button>時,該值的顏色會用作第一<xref:System.Windows.Media.GradientStop>個 。 如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。 此範<xref:System.Windows.Trigger>例建立一個,用於變更<xref:System.Windows.Controls.Button>時<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>的外觀`true`。  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> 必須<xref:System.Windows.Controls.Control.Background%2A>將的<xref:System.Windows.Controls.Button>屬性 設定<xref:System.Windows.Media.SolidColorBrush>為 , 以便範例正常工作。  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>訂閱事件  
 可以使用 任[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]一 或代碼訂閱控制項的事件,但只能在代碼中處理事件。  下面的範例展示如何訂閱的事件`Click`<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 下面的範例處理`Click`的<xref:System.Windows.Controls.Button>事件 。  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>控制項中的多格式內容  
 從<xref:System.Windows.Controls.Control>類繼承的大多數類都具有包含豐富內容的能力。 例如,可以<xref:System.Windows.Controls.Label>包含任何物件,如字串、或<xref:System.Windows.Controls.Image>。 <xref:System.Windows.Controls.Panel>  以下類支援豐富的內容,並充當[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中 大多數控件的基類。  
  
- <xref:System.Windows.Controls.ContentControl>-- 從此類繼承的類別的一些範<xref:System.Windows.Controls.Label>例<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ToolTip>是 , 和 。  
  
- <xref:System.Windows.Controls.ItemsControl>-- 從此類繼承的類別的一些範<xref:System.Windows.Controls.ListBox>例<xref:System.Windows.Controls.Menu><xref:System.Windows.Controls.Primitives.StatusBar>是 , 和 。  
  
- <xref:System.Windows.Controls.HeaderedContentControl>-- 從此類繼承的類別的一些範<xref:System.Windows.Controls.TabItem>例<xref:System.Windows.Controls.GroupBox><xref:System.Windows.Controls.Expander>是 , 和 。  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>-- 從此類繼承的類別的一些範<xref:System.Windows.Controls.MenuItem>例<xref:System.Windows.Controls.TreeViewItem><xref:System.Windows.Controls.ToolBar>是 , 和 。  

 有關這些基類的詳細資訊,請參閱[WPF 內容模型](wpf-content-model.md)。  
  
## <a name="see-also"></a>另請參閱

- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [按分類區隔控制項](controls-by-category.md)
- [控制項程式庫](control-library.md)
- [資料範本化概觀](../data/data-templating-overview.md)
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [輸入](../advanced/input-wpf.md)
- [啟用命令](../advanced/how-to-enable-a-command.md)
- [逐步解說：建立自訂動畫按鈕](walkthroughs-create-a-custom-animated-button.md)
- [控制項自訂](control-customization.md)
