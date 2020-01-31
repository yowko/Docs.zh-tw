---
title: 逐步解說：使用 WindowsFormsHost 項目對應屬性
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: c076937d6431adf1750793d47ece88dc82edf95c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794106"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>逐步解說：使用 WindowsFormsHost 項目對應屬性

本逐步解說將示範如何使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> 屬性，將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性對應至裝載之 Windows Forms 控制項的對應屬性。

這個逐步解說中所述的工作包括：

- 建立專案。

- 定義應用程式版面配置。

- 定義新的屬性對應。

- 移除預設屬性對應。

- 取代預設屬性對應。

- 擴充預設屬性對應。

如需本逐步解說中所述工作的完整程式代碼清單，請參閱[使用 WindowsFormsHost 元素範例對應屬性](https://go.microsoft.com/fwlink/?LinkID=160019)。

當您完成時，您可以將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性對應至託管 Windows Forms 控制項上的對應屬性。

## <a name="prerequisites"></a>必要條件：

您需要下列元件才能完成此逐步解說：

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>建立和設定專案

1. 建立名為 `PropertyMappingWithWfhSample`的**WPF 應用程式**專案。

2. 在**方案總管**中，加入名為 WindowsFormsIntegration 的 WindowsFormsIntegration 元件參考。

3. 在**方案總管**中，新增對 System.web 和 system.web 元件的參考。

## <a name="defining-the-application-layout"></a>定義應用程式版面配置

以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式會使用 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素來裝載 Windows Forms 控制項。

### <a name="to-define-the-application-layout"></a>定義應用程式版面配置

1. 在 WPF 設計工具中開啟 Window1.xaml。

2. 將現有的程式碼取代為下列程式碼。

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. 在程式碼編輯器中，開啟 Window1.xaml.cs。

4. 在檔案頂端，匯入下列命名空間。

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>定義新的屬性對應

<xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素提供數個預設屬性對應。 您可以藉由在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> 方法，來加入新的屬性對應。

### <a name="to-define-a-new-property-mapping"></a>定義新的屬性對應

- 將下列程式碼複製到 `Window1` 類別的定義中。

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     `AddClipMapping` 方法會加入 <xref:System.Windows.UIElement.Clip%2A> 屬性的新對應。

     `OnClipChange` 方法會將 <xref:System.Windows.UIElement.Clip%2A> 屬性轉譯為 Windows Forms 的<xref:System.Windows.Forms.Control.Region%2A> 屬性。

     `Window1_SizeChanged` 方法會處理視窗的 <xref:System.Windows.FrameworkElement.SizeChanged> 事件，並調整裁剪區域的大小以符合應用程式視窗。

## <a name="removing-a-default-property-mapping"></a>移除預設屬性對應

藉由在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> 方法，移除預設屬性對應。

### <a name="to-remove-a-default-property-mapping"></a>移除預設屬性對應

- 將下列程式碼複製到 `Window1` 類別的定義中。

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     `RemoveCursorMapping` 方法會刪除 <xref:System.Windows.FrameworkElement.Cursor%2A> 屬性的預設對應。

## <a name="replacing-a-default-property-mapping"></a>取代預設屬性對應

藉由移除預設的對應，並在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> 方法，來取代預設的屬性對應。

### <a name="to-replace-a-default-property-mapping"></a>移除預設屬性對應

- 將下列程式碼複製到 `Window1` 類別的定義中。

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     `ReplaceFlowDirectionMapping` 方法會取代 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性的預設對應。

     `OnFlowDirectionChange` 方法會將 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性轉譯為 Windows Forms 的<xref:System.Windows.Forms.Control.RightToLeft%2A> 屬性。

     `cb_CheckedChanged` 方法會處理 <xref:System.Windows.Forms.CheckBox> 控制項上的 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件。 它會根據 <xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性的值來指派 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性

## <a name="extending-a-default-property-mapping"></a>擴充預設屬性對應

您可以使用預設屬性對應，也可以使用自己的對應來進行擴充。

### <a name="to-extend-a-default-property-mapping"></a>擴充預設屬性對應

- 將下列程式碼複製到 `Window1` 類別的定義中。

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     `ExtendBackgroundMapping` 方法會將自訂屬性 translator 加入至現有的 <xref:System.Windows.Controls.Control.Background%2A> 屬性對應。

     `OnBackgroundChange` 方法會將特定的影像指派給主控控制項的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 屬性。 套用預設屬性對應之後，會呼叫 `OnBackgroundChange` 方法。

## <a name="initializing-your-property-mappings"></a>初始化屬性對應

藉由呼叫 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式中先前所述的方法來設定屬性對應。

### <a name="to-initialize-your-property-mappings"></a>初始化屬性對應

1. 將下列程式碼複製到 `Window1` 類別的定義中。

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     `WindowLoaded` 方法會處理 <xref:System.Windows.FrameworkElement.Loaded> 事件，並執行下列初始化。

    - 建立 Windows Forms<xref:System.Windows.Forms.CheckBox> 控制項。

    - 呼叫您稍早在本逐步解說中所定義的方法來設定屬性對應。

    - 將初始值指派給對應的屬性。

2. 按 **F5** 鍵建置並執行應用程式。 按一下核取方塊以查看 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 對應的效果。 當您按一下核取方塊時，版面配置會反轉其左右方向。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [逐步解說：在 WPF 中裝載 Windows Forms 控制項](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
