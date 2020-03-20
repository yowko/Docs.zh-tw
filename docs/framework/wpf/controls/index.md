---
title: 控制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 2ec8c0a99f4e2431aed0d8c24168b7329de669f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187524"
---
# <a name="controls"></a>控制
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]附帶許多常用的 UI 元件，這些元件用於幾乎每個 Windows 應用程式，例如<xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.ListBox>。 在過去，這些物件是稱為控制項。 雖然[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]SDK 繼續使用術語"控制項"來鬆散地表示表示應用程式中可見物件的任何類，但請務必注意，類不需要從<xref:System.Windows.Controls.Control>類繼承來具有可見狀態。 從類繼承的<xref:System.Windows.Controls.Control>類包含 ，<xref:System.Windows.Controls.ControlTemplate>它允許控制項的消費者從根本上改變控制項的外觀，而無需創建新的子類。  本主題討論如何在 中<xref:System.Windows.Controls.Control>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]常用控制項（從類繼承的控制項和未從類繼承的控制項）  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>建立控制項的執行個體  
 可以使用 任一或[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]代碼向應用程式添加控制項。  下列範例示範如何建立一個要求使用者輸入其名字和姓氏的簡單應用程式。  本示例在 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]創建六個控制項：兩個標籤、兩個文字方塊和兩個按鈕。 您可以用類似的方式建立所有控制項。  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 下列範例會以程式碼建立相同的應用程式。 為簡潔起見，從樣本中排除了<xref:System.Windows.Controls.Grid>的`grid1`創建。 `grid1`具有與上例[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]所示相同的列和行定義。  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>變更控制項的外觀  
 變更控制項的外觀以符合您應用程式的外觀及操作，是很常見的做法。 您可以根據想要達成的目的，執行下列其中一項操作來變更控制項的外觀：  
  
- 變更控制項的屬性值。  
  
- 為控制項<xref:System.Windows.Style>創建 。  
  
- <xref:System.Windows.Controls.ControlTemplate>為控制項創建新控制項。  
  
### <a name="changing-a-controls-property-value"></a>變更控制項的屬性值  
 許多控制項具有允許您更改控制項顯示方式的屬性，例如<xref:System.Windows.Controls.Control.Background%2A>。 <xref:System.Windows.Controls.Button> 您可以在 和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]代碼中設置值屬性。 下面的示例在<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Control.FontSize%2A><xref:System.Windows.Controls.Control.FontWeight%2A><xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設置 、 和 屬性。  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 下列範例會以程式碼設定相同的屬性。  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>為控制項建立樣式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]通過創建 ，可以大規模指定控制項的外觀，而不是設置應用程式中每個實例的屬性<xref:System.Windows.Style>。 下面的示例創建<xref:System.Windows.Style>應用於應用程式中每個應用<xref:System.Windows.Controls.Button>的 。 <xref:System.Windows.Style>定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]通常在 中<xref:System.Windows.ResourceDictionary>定義，如<xref:System.Windows.FrameworkElement.Resources%2A>的屬性。 <xref:System.Windows.FrameworkElement>  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 還可以通過將鍵分配給樣式並在控制項`Style`的屬性中指定該鍵，僅將樣式應用於特定類型的特定控制項。  有關樣式的詳細資訊，請參閱[樣式和範本](styling-and-templating.md)化。  
  
### <a name="creating-a-controltemplate"></a>建立 ControlTemplate  
 允許您<xref:System.Windows.Style>一次在多個控制項上設置屬性，但有時您可能希望自訂 的外觀<xref:System.Windows.Controls.Control>，超出通過創建 可以執行的內容。 <xref:System.Windows.Style> 從類繼承的<xref:System.Windows.Controls.Control>類具有 ，<xref:System.Windows.Controls.ControlTemplate>它定義 的<xref:System.Windows.Controls.Control>結構和外觀。 的屬性<xref:System.Windows.Controls.Control.Template%2A><xref:System.Windows.Controls.Control>是公共的，因此您可以給出與其預設值不同的 。 <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> 通常可以為 指定<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.Control>new，而不是從控制項繼承以自訂 的外觀。 <xref:System.Windows.Controls.Control>  
  
 請考慮很常見的控制。 <xref:System.Windows.Controls.Button>  的主要行為<xref:System.Windows.Controls.Button>是使應用程式能夠在使用者按一下時執行某些操作。  預設情況下，in<xref:System.Windows.Controls.Button>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]顯示為凸起的矩形。  在開發應用程式時，您可能希望利用<xref:System.Windows.Controls.Button>-- -- 即通過處理按鈕的按一下事件來利用 " 的行為"，但您可以通過更改按鈕的屬性來更改按鈕的外觀， 超出您可以執行的操作。  在這種情況下，您可以創建一個新的<xref:System.Windows.Controls.ControlTemplate>。  
  
 下面的示例為 創建<xref:System.Windows.Controls.ControlTemplate>。 <xref:System.Windows.Controls.Button>  創建<xref:System.Windows.Controls.ControlTemplate>具有<xref:System.Windows.Controls.Button>圓角和漸變背景的 。  <xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.Border>其<xref:System.Windows.Controls.Border.Background%2A>是 具有兩<xref:System.Windows.Media.LinearGradientBrush>個<xref:System.Windows.Media.GradientStop>物件的 的 。  第一<xref:System.Windows.Media.GradientStop>個使用資料繫結將<xref:System.Windows.Media.GradientStop.Color%2A>的屬性<xref:System.Windows.Media.GradientStop>綁定到按鈕背景的顏色。  設置 的屬性<xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Button>時，該值的顏色將用作第一個<xref:System.Windows.Media.GradientStop>。 如需資料繫結的詳細資訊，請參閱[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。 該示例還創建<xref:System.Windows.Trigger>一個，用於更改<xref:System.Windows.Controls.Button>時<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>的外觀`true`。  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> 必須<xref:System.Windows.Controls.Control.Background%2A>將 的屬性<xref:System.Windows.Controls.Button>設置為 ，<xref:System.Windows.Media.SolidColorBrush>以便示例正常工作。  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>訂閱事件  
 可以使用 任一[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]或代碼訂閱控制項的事件，但只能在代碼中處理事件。  下面的示例演示如何訂閱 的事件`Click`<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 下面的示例處理`Click`的事件<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>控制項中的多格式內容  
 從<xref:System.Windows.Controls.Control>類繼承的大多數類都具有包含豐富內容的能力。 例如，可以<xref:System.Windows.Controls.Label>包含任何物件，如字串、或<xref:System.Windows.Controls.Image>。 <xref:System.Windows.Controls.Panel>  以下類支援豐富的內容，並充當 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]大多數控制項的基類。  
  
- <xref:System.Windows.Controls.ContentControl>-- 從此類繼承的類的一些示例<xref:System.Windows.Controls.Label>是<xref:System.Windows.Controls.Button>，<xref:System.Windows.Controls.ToolTip>和 。  
  
- <xref:System.Windows.Controls.ItemsControl>-- 從此類繼承的類的一些示例<xref:System.Windows.Controls.ListBox>是<xref:System.Windows.Controls.Menu>，<xref:System.Windows.Controls.Primitives.StatusBar>和 。  
  
- <xref:System.Windows.Controls.HeaderedContentControl>-- 從此類繼承的類的一些示例<xref:System.Windows.Controls.TabItem>是<xref:System.Windows.Controls.GroupBox>，<xref:System.Windows.Controls.Expander>和 。  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>-- 從此類繼承的類的一些示例<xref:System.Windows.Controls.MenuItem>是<xref:System.Windows.Controls.TreeViewItem>，<xref:System.Windows.Controls.ToolBar>和 。  

 有關這些基類的詳細資訊，請參閱[WPF 內容模型](wpf-content-model.md)。  
  
## <a name="see-also"></a>另請參閱

- [設定樣式和範本](styling-and-templating.md)
- [按分類區隔控制項](controls-by-category.md)
- [控制項程式庫](control-library.md)
- [資料範本化概觀](../data/data-templating-overview.md)
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [輸入](../advanced/input-wpf.md)
- [啟用命令](../advanced/how-to-enable-a-command.md)
- [逐步解說：建立自訂動畫按鈕](walkthroughs-create-a-custom-animated-button.md)
- [控制項自訂](control-customization.md)
