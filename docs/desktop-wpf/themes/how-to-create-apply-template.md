---
title: 在 WPF 中建立範本-.NET Desktop
description: 瞭解如何在 Windows Presentation Foundation 和 .NET Core 中建立和參考控制項範本。
author: adegeo
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: 8be38a2b4f046a43ab187ea3517335437ec49b08
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551890"
---
# <a name="create-a-template-for-a-control"></a>建立控制項的範本

使用 Windows Presentation Foundation (WPF) ，您可以使用自己可重複使用的範本自訂現有控制項的視覺化結構和行為。 範本可全域套用至您的應用程式、windows 和頁面，或直接套用至控制項。 您可以改為建立現有控制項的新範本，以涵蓋需要您建立新控制項的大部分案例。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

在本文中，您將探索如何為控制項建立新的 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> 。

## <a name="when-to-create-a-controltemplate"></a>建立 ControlTemplate 的時機

控制項有許多屬性，例如 <xref:System.Windows.Controls.Border.Background%2A> 、 <xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontFamily%2A> 。 這些屬性會控制控制面板的不同層面，但您可以藉由設定這些屬性進行的變更會受到限制。 例如，您可以將屬性設定 <xref:System.Windows.Controls.Control.Foreground%2A> 為 [藍色]，並將設定 <xref:System.Windows.Controls.Control.FontStyle%2A> 為 [斜體] <xref:System.Windows.Controls.CheckBox> 。 如果您想要自訂控制項的外觀，而不是控制項上其他屬性所能做的設定，您可以建立 <xref:System.Windows.Controls.ControlTemplate> 。

在大部分的使用者介面中，按鈕具有相同的一般外觀：有一些文字的矩形。 如果您想要建立圓角按鈕，您可以建立繼承自按鈕的新控制項，或重新建立按鈕的功能。 此外，新的使用者控制項會提供圓形視覺效果。

您可以自訂現有控制項的視覺化配置，以避免建立新的控制項。 使用圓角按鈕時，您可以 <xref:System.Windows.Controls.ControlTemplate> 使用所需的視覺版面配置來建立。

另一方面，如果您需要的控制項有新功能、不同的屬性和新的設定，您可以建立新的 <xref:System.Windows.Controls.UserControl> 。

## <a name="prerequisites"></a>Prerequisites

建立新的 WPF 應用程式，並在*MainWindow*中 (或您選擇的另一個視窗) 在** \: ：： no loc (<Window>) ：：：** 元素上設定下列屬性：

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

將** \: ：：非 loc (<Window>) ：：：** 元素的內容設定為下列 XAML：

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

最後， *MainWindow .xaml* 檔案看起來應該會如下所示：

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

如果您執行應用程式，它看起來如下所示：

![具有兩個 .unstyled-list 按鈕的 WPF 視窗](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>建立 ControlTemplate

最常見的宣告方式是在 <xref:System.Windows.Controls.ControlTemplate> XAML 檔案中的區段中做為資源 `Resources` 。 因為範本是資源，所以它們會遵守適用于所有資源的相同範圍規則。 單純地說，您宣告範本的位置會影響可以套用範本的位置。 例如，如果您在應用程式定義 XAML 檔案的根項目中宣告範本，則範本可以在應用程式中的任何位置使用。 如果您在視窗中定義範本，則只有該視窗中的控制項可以使用該範本。

若要開始，請將專案新增 `Window.Resources` 至您的 *MainWindow .xaml* 檔案：

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

建立新的** \: ：：非 loc (<ControlTemplate>) ：：：** 並設定下列屬性：

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

此控制項範本將很簡單：

- 控制項的根項目，a <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Shapes.Ellipse>，用來繪製按鈕的圓角外觀
- <xref:System.Windows.Controls.ContentPresenter>，顯示使用者指定的按鈕內容

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

當您建立新的時 <xref:System.Windows.Controls.ControlTemplate> ，您仍然可能會想要使用公用屬性來變更控制項的外觀。 [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension)標記延伸會將中的元素屬性系結 <xref:System.Windows.Controls.ControlTemplate> 至控制項所定義的公用屬性。 當您使用 [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension)時，您可以讓控制項上的屬性作為範本的參數。 也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](/dotnet/desktop/wpf/advanced/templatebinding-markup-extension) 的元素。

### <a name="ellipse"></a>橢圓形

請注意 **:::no-loc text="Fill":::** ：： **:::no-loc text="Stroke":::** ** \: no loc (<Ellipse>) ：：：** element 的和屬性會系結至控制項的 <xref:System.Windows.Controls.Control.Foreground> 和 <xref:System.Windows.Controls.Control.Background> 屬性。

### <a name="contentpresenter"></a>ContentPresenter

您也會將[ \: ：：非 loc (<ContentPresenter>) ：：：](xref:System.Windows.Controls.ContentPresenter)專案新增至範本。 因為這個範本是針對按鈕所設計，請考慮按鈕繼承自 <xref:System.Windows.Controls.ContentControl> 。 按鈕會顯示元素的內容。 您可以設定按鈕內的任何內容，例如純文字或甚至另一個控制項。 下列兩項都是有效的按鈕：

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

在上述兩個範例中，文字和核取方塊都會設定為 [ [內容](xref:System.Windows.Controls.ContentControl.Content) ] 屬性。 無論內容為何，都可以透過** \: ：：非 loc (<ContentPresenter>) ：：：** 來呈現，這就是範本的用途。

如果套用 <xref:System.Windows.Controls.ControlTemplate> 至 <xref:System.Windows.Controls.ContentControl> 類型（例如 `Button` ），則 <xref:System.Windows.Controls.ContentPresenter> 會在元素樹狀結構中搜尋。 如果 `ContentPresenter` 找到，則範本會自動將控制項的屬性系結 <xref:System.Windows.Controls.ContentControl.Content> 至 `ContentPresenter` 。

## <a name="use-the-template"></a>使用範本

尋找在本文一開始所宣告的按鈕。

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

將第二個按鈕的 <xref:System.Windows.Controls.Control.Template> 屬性設為 `roundbutton` 資源：

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

如果您執行專案並查看結果，您會看到按鈕具有圓角背景。

![具有一個範本 oval 按鈕的 WPF 視窗](media/create-apply-template/styled-button.png)

您可能已經注意到按鈕不是圓形，但卻扭曲。 由於** \: ：： no loc (<Ellipse>) ：：：** element 的運作方式，它一律會展開以填滿可用的空間。 將按鈕的  **:::no-loc text="width":::** 和 **:::no-loc text="height":::** 屬性變更為相同的值，讓圓形保持一致：

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![具有一個範本迴圈按鈕的 WPF 視窗](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>新增觸發程式

雖然套用範本的按鈕看起來不同，但它的行為與任何其他按鈕的行為相同。 如果您按下按鈕，就會 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 引發事件。 不過，您可能已經注意到，當您將滑鼠移至按鈕上方時，按鈕的視覺效果不會變更。 這些視覺效果互動全都由範本所定義。

使用 WPF 提供的動態事件和屬性系統，您可以監看某個值的特定屬性，然後在適當的情況下重新造型範本。 在此範例中，您將監看按鈕的 <xref:System.Windows.UIElement.IsMouseOver> 屬性。 當滑鼠停留在控制項上時，使用新的色彩來將** \: ：： no loc (<Ellipse>) ：：：** 樣式。 這種類型的觸發程式稱為 *PropertyTrigger*。

若要這樣做，您必須將名稱新增至您可以參考的** \: ：： no loc (<Ellipse>) ：：：** 。 指定 **backgroundElement**的名稱。

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

接下來，將新的新增 <xref:System.Windows.Trigger> 至 [ControlTemplate](xref:System.Windows.Controls.ControlTemplate.Triggers) 集合。 觸發程式會監看 `IsMouseOver` 值的事件 `true` 。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

接下來，將** \: ：：非 loc (<Setter>) ：** ：：新增至** \: ：：非 loc (<Trigger>) ：：：** ，將** \: ：： no loc (<Ellipse>) ：：：** 的**Fill**屬性變更為新的色彩。

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

執行專案。 請注意，當您將滑鼠移至按鈕上方時，：： ** \: no loc (<Ellipse>) ：：：** 會變更色彩。

![滑鼠移至 WPF 按鈕以變更填滿色彩](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>使用 VisualState

視覺狀態是由控制項所定義和觸發。 例如，當滑鼠移到控制項上方時， `CommonStates.MouseOver` 就會觸發狀態。 您可以根據控制項目前的狀態，建立屬性變更的動畫。 在上一節中，已使用** \: ：： no loc (<PropertyTrigger>) ：：：** 將按鈕的前景變更為 `AliceBlue` 當屬性為時 `IsMouseOver` `true` 。 相反地，請建立以動畫顯示此色彩變更的視覺狀態，以提供順暢的轉換。 如需 *VisualStates*的詳細資訊，請參閱 [WPF 中的樣式和範本](../fundamentals/styles-templates-overview.md#visual-states)。

若要將** \: ：： no loc (<PropertyTrigger>) ：：：** 轉換為動畫的視覺狀態，請先 **\<ControlTemplate.Triggers>** 從您的範本中移除該元素。

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

接下來，在控制項範本的** \: ：： no loc (<Grid>) ：** ： root 中，加入** \: ：： No-Loc ( # B0 VisualStateManager. system.windows.visualstatemanager.visualstategroups>) ：：：** element，其具有** \: ：：無 loc (<VisualStateGroup>) ：：：** `CommonStates` 。 定義兩個狀態： `Normal` 和 `MouseOver` 。

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

當觸發該狀態時，會套用在** \: ：：非 loc (<VisualState>) ：：：** 中定義的任何動畫。 建立每個狀態的動畫。 動畫會置於** \: ：：非 loc (<Storyboard>) ：：：** 元素內。 如需分鏡腳本的詳細資訊，請參閱分鏡腳本 [總覽](/dotnet/desktop/wpf/graphics-multimedia/storyboards-overview)。

- 正常

  此狀態會將橢圓形填滿，並將其還原為控制項的 `Background` 色彩。

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  這個狀態會將橢圓形 `Background` 色彩繪製成新的色彩： `Yellow` 。

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

** \: ：：非 loc (<ControlTemplate>) ：：：** 現在看起來應該如下所示。

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

執行專案。 請注意，當您將滑鼠移至按鈕上方時，：： ** \: no loc (<Ellipse>) ：：：** 動畫的色彩。

![滑鼠移至 WPF 按鈕以變更填滿色彩](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>後續步驟

- [在 WPF 中建立控制項的樣式](../fundamentals/styles-templates-create-apply-style.md)
- [WPF 中的樣式和範本](../fundamentals/styles-templates-overview.md)
- [XAML 資源總覽](../fundamentals/xaml-resources-define.md)
