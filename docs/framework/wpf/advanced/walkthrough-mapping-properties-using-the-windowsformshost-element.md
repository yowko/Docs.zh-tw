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
ms.openlocfilehash: 77027d771cf471e563e24c46d7794a18ad223541
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258514"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>逐步解說：使用 WindowsFormsHost 項目對應屬性

本逐步解說會示範如何使用<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>屬性來對應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性，以對應的屬性，在裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。

這個逐步解說中所述的工作包括：

-   建立專案。

-   定義應用程式版面配置。

-   定義新的屬性對應。

-   移除預設屬性對應。

-   取代預設屬性對應。

-   擴充預設屬性對應。

在此逐步解說中所述工作的完整程式碼清單，請參閱 <<c0> [ 對應屬性使用 WindowsFormsHost 項目範例](http://go.microsoft.com/fwlink/?LinkID=160019)。

當您完成時，您將能夠對應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]上裝載的對應屬性的屬性[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

-   Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>建立並設定專案

1.  建立**WPF 應用程式**專案，命名為`PropertyMappingWithWfhSample`。

2.  在 [**方案總管] 中**，加入名為 WindowsFormsIntegration.dll 之 WindowsFormsIntegration 組件的參考。

3.  在 [**方案總管] 中**，新增 System.Drawing 和 System.Windows.Forms 組件的參考。

## <a name="defining-the-application-layout"></a>定義應用程式版面配置

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-根據應用程式會使用<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目來裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。

### <a name="to-define-the-application-layout"></a>定義應用程式版面配置

1.  中，開啟 Window1.xaml [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。

2.  將現有的程式碼取代為下列程式碼。

     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3.  在程式碼編輯器中，開啟 Window1.xaml.cs。

4.  在檔案頂端，匯入下列命名空間。

     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>定義新的屬性對應

<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目會提供數個預設屬性對應。 您加入新的屬性對應，藉由呼叫<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>。

### <a name="to-define-a-new-property-mapping"></a>定義新的屬性對應

-   將下列程式碼複製到的定義`Window1`類別。

     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     `AddClipMapping`方法會將新的對應，如<xref:System.Windows.UIElement.Clip%2A>屬性。

     `OnClipChange`方法會將轉譯<xref:System.Windows.UIElement.Clip%2A>屬性設[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A>屬性。

     `Window1_SizeChanged`方法會處理該視窗的<xref:System.Windows.FrameworkElement.SizeChanged>事件，並調整大小以符合應用程式視窗的裁剪區域。

## <a name="removing-a-default-property-mapping"></a>移除預設屬性對應

移除預設屬性對應，藉由呼叫<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>。

### <a name="to-remove-a-default-property-mapping"></a>移除預設屬性對應

-   將下列程式碼複製到的定義`Window1`類別。

     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     `RemoveCursorMapping`方法會刪除預設對應<xref:System.Windows.FrameworkElement.Cursor%2A>屬性。

## <a name="replacing-a-default-property-mapping"></a>取代預設屬性對應

藉由移除預設對應，並呼叫來取代預設屬性對應<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>項目的<xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>。

### <a name="to-replace-a-default-property-mapping"></a>移除預設屬性對應

-   將下列程式碼複製到的定義`Window1`類別。

     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     `ReplaceFlowDirectionMapping`方法會取代預設對應<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性。

     `OnFlowDirectionChange`方法會將轉譯<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性設[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A>屬性。

     `cb_CheckedChanged`方法會處理<xref:System.Windows.Forms.CheckBox.CheckedChanged>上的事件<xref:System.Windows.Forms.CheckBox>控制項。 它會將指派<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性的值，根據<xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性

## <a name="extending-a-default-property-mapping"></a>擴充預設屬性對應

您可以使用預設屬性對應，也可以使用自己的對應來進行擴充。

### <a name="to-extend-a-default-property-mapping"></a>擴充預設屬性對應

-   將下列程式碼複製到的定義`Window1`類別。

     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     `ExtendBackgroundMapping`方法會將自訂屬性轉譯器加入至現有<xref:System.Windows.Controls.Control.Background%2A>屬性對應。

     `OnBackgroundChange`方法會將特定的映像指派給裝載的控制項<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性。 `OnBackgroundChange`套用預設屬性對應之後，會呼叫方法。

## <a name="initializing-your-property-mappings"></a>初始化屬性對應

設定 藉由呼叫先前所述的方法的 屬性對應<xref:System.Windows.FrameworkElement.Loaded>事件處理常式。

### <a name="to-initialize-your-property-mappings"></a>初始化屬性對應

1.  將下列程式碼複製到的定義`Window1`類別。

     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     `WindowLoaded`方法會處理<xref:System.Windows.FrameworkElement.Loaded>事件，並執行下列初始化。

    -   會建立[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox>控制項。

    -   呼叫您稍早在本逐步解說中所定義的方法來設定屬性對應。

    -   將初始值指派給對應的屬性。

2.  按 **F5** 鍵建置並執行應用程式。 按一下核取方塊，若要查看的效果<xref:System.Windows.FrameworkElement.FlowDirection%2A>對應。 當您按一下核取方塊時，版面配置會反轉其左右方向。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [逐步解說：在 WPF 中裝載 Windows Forms 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)