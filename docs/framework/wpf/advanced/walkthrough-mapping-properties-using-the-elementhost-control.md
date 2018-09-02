---
title: 逐步解說：使用 ElementHost 控制項對應屬性
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 34119d889c8d6600fdda12cac33192c32d8e0fa6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467120"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>逐步解說：使用 ElementHost 控制項對應屬性

本逐步解說會示範如何使用<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>屬性來對應[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]屬性，以對應的屬性，在裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]項目。

這個逐步解說中所述的工作包括：

-   建立專案。

-   定義新的屬性對應。

-   移除預設屬性對應。

-   擴充預設屬性對應。

在此逐步解說中所述工作的完整程式碼清單，請參閱 <<c0> [ 對應屬性使用 ElementHost 控制項範例](https://go.microsoft.com/fwlink/?LinkID=160018)。

當您完成時，您將能夠對應[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]屬性，以對應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]上裝載的項目屬性。

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成此逐步解說：

-   Visual Studio 2017

## <a name="creating-the-project"></a>建立專案

### <a name="to-create-the-project"></a>若要建立專案

1.  建立**Windows Forms 應用程式**專案，命名為`PropertyMappingWithElementHost`。

2.  在 **方案總管**，將參考加入至下列[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組件。

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

    -   WindowsFormsIntegration

3.  將下列程式碼複製到頂端`Form1`程式碼檔案。

     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4.  在 Windows Form 設計工具中開啟 `Form1`。 按兩下表單，以新增事件處理常式<xref:System.Windows.Forms.Form.Load>事件。

5.  返回 Windows Form 設計工具，並新增事件處理常式的表單<xref:System.Windows.Forms.Control.Resize>事件。 如需詳細資訊，請參閱 <<c0> [ 如何： 使用設計工具建立事件處理常式](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)。

6.  宣告<xref:System.Windows.Forms.Integration.ElementHost>欄位中`Form1`類別。

     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>定義新的屬性對應

<xref:System.Windows.Forms.Integration.ElementHost>控制項提供數個預設屬性對應。 您加入新的屬性對應，藉由呼叫<xref:System.Windows.Forms.Integration.PropertyMap.Add%2A>方法<xref:System.Windows.Forms.Integration.ElementHost>控制項的<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>。

### <a name="to-define-new-property-mappings"></a>若要定義新的屬性對應

1.  將下列程式碼複製到的定義`Form1`類別。

     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     `AddMarginMapping`方法會將新的對應，如<xref:System.Windows.Forms.Control.Margin%2A>屬性。

     `OnMarginChange`方法會將轉譯<xref:System.Windows.Forms.Control.Margin%2A>屬性設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.FrameworkElement.Margin%2A>屬性。

2.  將下列程式碼複製到的定義`Form1`類別。

     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     `AddRegionMapping`方法會將新的對應，如<xref:System.Windows.Forms.Control.Region%2A>屬性。

     `OnRegionChange`方法會將轉譯<xref:System.Windows.Forms.Control.Region%2A>屬性設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.UIElement.Clip%2A>屬性。

     `Form1_Resize`方法會處理表單的<xref:System.Windows.Forms.Control.Resize>事件，並調整大小以符合裝載的項目之裁剪區域。

## <a name="removing-a-default-property-mapping"></a>移除預設屬性對應

移除預設屬性對應，藉由呼叫<xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A>方法<xref:System.Windows.Forms.Integration.ElementHost>控制項的<xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>。

### <a name="to-remove-a-default-property-mapping"></a>移除預設屬性對應

-   將下列程式碼複製到的定義`Form1`類別。

     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     `RemoveCursorMapping`方法會刪除預設對應<xref:System.Windows.Forms.Control.Cursor%2A>屬性。

## <a name="extending-a-default-property-mapping"></a>擴充預設屬性對應

您可以使用預設屬性對應，也可以使用自己的對應來進行擴充。

### <a name="to-extend-a-default-property-mapping"></a>擴充預設屬性對應

-   將下列程式碼複製到的定義`Form1`類別。

     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     `ExtendBackColorMapping`方法會將自訂屬性轉譯器加入至現有<xref:System.Windows.Forms.Control.BackColor%2A>屬性對應。

     `OnBackColorChange`方法會將特定的映像指派給裝載的控制項<xref:System.Windows.Controls.Control.Background%2A>屬性。 `OnBackColorChange`套用預設屬性對應之後，會呼叫方法。

## <a name="initialize-your-property-mappings"></a>初始化屬性對應

1.  將下列程式碼複製到的定義`Form1`類別。

     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     `Form1_Load`方法會處理<xref:System.Windows.Forms.Form.Load>事件，並執行下列初始化。

    -   會建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Button>項目。

    -   呼叫您稍早在本逐步解說中所定義的方法來設定屬性對應。

    -   將初始值指派給對應的屬性。

2.  按 F5 鍵建置並執行應用程式。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms 和 WPF 屬性對應](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/designers/designing-xaml-in-visual-studio)
- [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)