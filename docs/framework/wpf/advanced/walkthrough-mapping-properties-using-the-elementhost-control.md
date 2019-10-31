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
ms.openlocfilehash: 7d1cf353f7e6c4b87c13598e7e6029960cd0f715
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197811"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>逐步解說：使用 ElementHost 控制項對應屬性

本逐步解說將示範如何使用 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> 屬性，將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 屬性對應至 hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 專案上的對應屬性。

這個逐步解說中所述的工作包括：

- 建立專案。

- 定義新的屬性對應。

- 移除預設屬性對應。

- 擴充預設屬性對應。

如需本逐步解說中所述工作的完整程式代碼清單，請參閱[使用 ElementHost 控制項範例對應屬性](https://go.microsoft.com/fwlink/?LinkID=160018)。

當您完成時，您將能夠將 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 屬性對應至裝載專案上相對應的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性。

## <a name="prerequisites"></a>Prerequisites

您需要下列元件才能完成此逐步解說：

- Visual Studio 2017

## <a name="creating-the-project"></a>建立專案

### <a name="to-create-the-project"></a>建立專案

1. 建立名為 `PropertyMappingWithElementHost`**Windows Forms 應用程式**專案。

2. 在**方案總管**中，將參考加入至下列 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元件。

    - PresentationCore

    - PresentationFramework

    - WindowsBase

    - WindowsFormsIntegration

3. 將下列程式碼複製到 `Form1` 程式碼檔案的頂端。

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. 在 Windows Form 設計工具中開啟 `Form1`。 按兩下表單，加入 <xref:System.Windows.Forms.Form.Load> 事件的事件處理常式。

5. 返回 Windows Form 設計工具，並加入表單 <xref:System.Windows.Forms.Control.Resize> 事件的事件處理常式。 如需詳細資訊，請參閱[如何：使用設計工具建立事件處理常式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))。

6. 在 `Form1` 類別中宣告 <xref:System.Windows.Forms.Integration.ElementHost> 欄位。

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>定義新的屬性對應

<xref:System.Windows.Forms.Integration.ElementHost> 控制項提供數個預設的屬性對應。 您可以藉由在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> 方法，來加入新的屬性對應。

### <a name="to-define-new-property-mappings"></a>若要定義新的屬性對應

1. 將下列程式碼複製到 `Form1` 類別的定義中。

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     `AddMarginMapping` 方法會加入 <xref:System.Windows.Forms.Control.Margin%2A> 屬性的新對應。

     `OnMarginChange` 方法會將 <xref:System.Windows.Forms.Control.Margin%2A> 屬性轉譯為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 <xref:System.Windows.FrameworkElement.Margin%2A> 屬性。

2. 將下列程式碼複製到 `Form1` 類別的定義中。

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     `AddRegionMapping` 方法會加入 <xref:System.Windows.Forms.Control.Region%2A> 屬性的新對應。

     `OnRegionChange` 方法會將 <xref:System.Windows.Forms.Control.Region%2A> 屬性轉譯為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 <xref:System.Windows.UIElement.Clip%2A> 屬性。

     `Form1_Resize` 方法會處理表單的 <xref:System.Windows.Forms.Control.Resize> 事件，並調整裁剪區域的大小，使其符合主控的元素。

## <a name="removing-a-default-property-mapping"></a>移除預設屬性對應

藉由在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>上呼叫 <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> 方法，移除預設屬性對應。

### <a name="to-remove-a-default-property-mapping"></a>移除預設屬性對應

- 將下列程式碼複製到 `Form1` 類別的定義中。

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     `RemoveCursorMapping` 方法會刪除 <xref:System.Windows.Forms.Control.Cursor%2A> 屬性的預設對應。

## <a name="extending-a-default-property-mapping"></a>擴充預設屬性對應

您可以使用預設屬性對應，也可以使用自己的對應來進行擴充。

### <a name="to-extend-a-default-property-mapping"></a>擴充預設屬性對應

- 將下列程式碼複製到 `Form1` 類別的定義中。

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     `ExtendBackColorMapping` 方法會將自訂屬性 translator 加入至現有的 <xref:System.Windows.Forms.Control.BackColor%2A> 屬性對應。

     `OnBackColorChange` 方法會將特定的影像指派給主控控制項的 <xref:System.Windows.Controls.Control.Background%2A> 屬性。 套用預設屬性對應之後，會呼叫 `OnBackColorChange` 方法。

## <a name="initialize-your-property-mappings"></a>初始化您的屬性對應

1. 將下列程式碼複製到 `Form1` 類別的定義中。

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     `Form1_Load` 方法會處理 <xref:System.Windows.Forms.Form.Load> 事件，並執行下列初始化。

    - 建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> 元素。

    - 呼叫您稍早在本逐步解說中所定義的方法來設定屬性對應。

    - 將初始值指派給對應的屬性。

2. 按 F5 鍵建置並執行應用程式。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms 和 WPF 屬性對應](windows-forms-and-wpf-property-mapping.md)
- [在 Visual Studio 中設計 XAML](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
