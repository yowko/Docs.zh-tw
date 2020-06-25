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
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325729"
---
# <a name="create-a-template-for-a-control"></a>建立控制項的範本

使用 Windows Presentation Foundation （WPF），您可以使用自己可重複使用的範本，自訂現有控制項的視覺結構和行為。 範本可全域套用至您的應用程式、視窗和頁面，或直接套用到控制項。 大部分需要您建立新控制項的案例，可以改為涵蓋現有控制項的新範本。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

在本文中，您將探索如何建立 <xref:System.Windows.Controls.ControlTemplate> 控制項的新 <xref:System.Windows.Controls.Button> 。

## <a name="when-to-create-a-controltemplate"></a>建立 ControlTemplate 的時機

控制項有許多屬性，例如 <xref:System.Windows.Controls.Border.Background%2A> 、 <xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontFamily%2A> 。 這些屬性會控制控制面板的不同層面，但是您可以藉由設定這些屬性所做的變更會受到限制。 例如，您可以將屬性設定 <xref:System.Windows.Controls.Control.Foreground%2A> 為藍色，並將設 <xref:System.Windows.Controls.Control.FontStyle%2A> 為斜體 <xref:System.Windows.Controls.CheckBox> 。 當您想要自訂控制項的外觀，而不是控制項的其他屬性設定時，您會建立 <xref:System.Windows.Controls.ControlTemplate> 。

在大部分的使用者介面中，按鈕具有相同的一般外觀：具有一些文字的矩形。 如果您想要建立圓角按鈕，可以建立一個繼承自按鈕的新控制項，或重建按鈕的功能。 此外，新的使用者控制項也會提供圓形視覺效果。

您可以藉由自訂現有控制項的視覺化版面配置，來避免建立新的控制項。 使用圓角按鈕，您可以 <xref:System.Windows.Controls.ControlTemplate> 使用所需的視覺效果版面配置來建立。

另一方面，如果您需要具有新功能、不同屬性和新設定的控制項，則會建立新的 <xref:System.Windows.Controls.UserControl> 。

## <a name="prerequisites"></a>先決條件

建立新的 WPF 應用程式，並在*mainwindow.xaml* （或您選擇的另一個視窗）中，設定元素的下列屬性 **\<Window>** ：

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

將元素的內容設定 **\<Window>** 為下列 XAML：

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

最後， *mainwindow.xaml*應該看起來像下面這樣：

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

如果您執行應用程式，它看起來會像下面這樣：

![具有兩個 .unstyled-list 按鈕的 WPF 視窗](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>建立 ControlTemplate

宣告的最常見方式 <xref:System.Windows.Controls.ControlTemplate> 就是 XAML 檔案中區段的資源 `Resources` 。 因為範本是資源，所以它們會遵守適用于所有資源的相同範圍規則。 簡單地說，您可以在其中宣告範本會影響可套用範本的位置。 例如，如果您在應用程式定義 XAML 檔案的根項目中宣告範本，則範本可以在應用程式的任何位置使用。 如果您在視窗中定義範本，則只有該視窗中的控制項可以使用此範本。

若要開始，請將 `Window.Resources` 元素新增至您的*mainwindow.xaml*檔案：

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

建立 **\<ControlTemplate>** 具有下列屬性集的新：

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

這個控制項範本很簡單：

- 控制項的根項目，a<xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Shapes.Ellipse>，用來繪製按鈕的圓角外觀
- <xref:System.Windows.Controls.ContentPresenter>，用來顯示使用者指定的按鈕內容

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

當您建立新的時 <xref:System.Windows.Controls.ControlTemplate> ，您仍可能想要使用公用屬性來變更控制項的外觀。 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)標記延伸會將位於的專案屬性系結 <xref:System.Windows.Controls.ControlTemplate> 至控制項所定義的公用屬性。 當您使用[TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md)時，您會啟用控制項的屬性，作為範本的參數。 也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。

### <a name="ellipse"></a>橢圓形

請注意， **:::no-loc text="Fill":::** 元素的和 **:::no-loc text="Stroke":::** 屬性會系結 **\<Ellipse>** 至控制項的 <xref:System.Windows.Controls.Control.Foreground> 和 <xref:System.Windows.Controls.Control.Background> 屬性。

### <a name="contentpresenter"></a>ContentPresenter

[\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter)元素也會加入至範本。 由於此範本是針對按鈕而設計的，因此請考慮按鈕會繼承自 <xref:System.Windows.Controls.ContentControl> 。 按鈕會顯示元素的內容。 您可以在按鈕內設定任何專案，例如純文字或甚至另一個控制項。 下列這兩個都是有效的按鈕：

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

在上述兩個範例中，文字和核取方塊都會設定為 [ [Content](xref:System.Windows.Controls.ContentControl.Content) ] 屬性。 無論內容設定為何，都可以透過來呈現 **\<ContentPresenter>** ，這就是範本的用途。

如果套用 <xref:System.Windows.Controls.ControlTemplate> 至 <xref:System.Windows.Controls.ContentControl> 型別（例如 `Button` ）， <xref:System.Windows.Controls.ContentPresenter> 則會在專案樹狀結構中搜尋。 如果 `ContentPresenter` 找到，此範本會自動將控制項的屬性系結 <xref:System.Windows.Controls.ContentControl.Content> 至 `ContentPresenter` 。

## <a name="use-the-template"></a>使用範本

尋找在本文開頭所宣告的按鈕。

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

將第二個按鈕的 <xref:System.Windows.Controls.Control.Template> 屬性設定為 `roundbutton` 資源：

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

如果您執行專案並查看結果，您會看到按鈕具有圓角背景。

![具有一個樣板橢圓形按鈕的 WPF 視窗](media/create-apply-template/styled-button.png)

您可能已經注意到按鈕不是圓形，而是扭曲。 由於元素的運作方式 **\<Ellipse>** ，它一律會展開以填滿可用的空間。 將按鈕的 **:::no-loc text="width":::** 和 **:::no-loc text="height":::** 屬性變更為相同的值，使圓形成為一致：

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![具有一個範本迴圈按鈕的 WPF 視窗](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>新增觸發程式

雖然套用範本的按鈕看起來不同，但其行為與任何其他按鈕相同。 如果您按下按鈕，就會 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 引發事件。 不過，您可能已經注意到，當您將滑鼠移至按鈕上方時，按鈕的視覺效果不會變更。 這些視覺效果的互動都是由範本定義。

透過 WPF 提供的動態事件和屬性系統，您可以監看特定屬性的值，然後在適當時重新建立範本的樣式。 在此範例中，您會看到按鈕的 <xref:System.Windows.UIElement.IsMouseOver> 屬性。 當滑鼠停留在控制項上時，使用新的色彩來建立樣式 **\<Ellipse>** 。 這種類型的觸發程式稱為*PropertyTrigger*。

若要讓此作業正常執行，您必須將名稱新增至 **\<Ellipse>** 您可以參考的。 為它命名為**backgroundElement**。

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

接下來，將新的新增 <xref:System.Windows.Trigger> 至[ControlTemplate](xref:System.Windows.Controls.ControlTemplate.Triggers)集合。 觸發程式將會監看此 `IsMouseOver` 值的事件 `true` 。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

接下來，將新增 **\<Setter>** 至 **\<Trigger>** ，將的**Fill**屬性變更 **\<Ellipse>** 為新的色彩。

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

執行專案。 請注意，當您將滑鼠游標移至按鈕上方時，會 **\<Ellipse>** 發生變更的色彩。

![滑鼠移至 WPF 按鈕以變更填滿色彩](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>使用 VisualState

視覺狀態是由控制項所定義和觸發。 例如，當滑鼠移到控制項上方時， `CommonStates.MouseOver` 就會觸發狀態。 您可以根據控制項的目前狀態來建立屬性變更的動畫。 在上一節中， **\<PropertyTrigger>** 當屬性為時，用來將按鈕的前景變更為 `AliceBlue` `IsMouseOver` `true` 。 而是建立視覺狀態，以動畫顯示此色彩的變更，並提供順暢的轉換。 如需*VisualStates*的詳細資訊，請參閱[WPF 中的樣式和範本](../fundamentals/styles-templates-overview.md#visual-states)。

若要將轉換成 **\<PropertyTrigger>** 動畫視覺狀態，請先 **\<ControlTemplate.Triggers>** 從您的範本中移除元素。

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

接下來，在 **\<Grid>** 控制項範本的根目錄中，加入具有之的 **\<VisualStateManager.VisualStateGroups>** 元素 **\<VisualStateGroup>** `CommonStates` 。 定義兩個狀態： `Normal` 和 `MouseOver` 。

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

**\<VisualState>** 當觸發該狀態時，會套用在中定義的任何動畫。 建立每個狀態的動畫。 動畫會放在元素內 **\<Storyboard>** 。 如需有關分鏡腳本的詳細資訊，請參閱分鏡腳本[總覽](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。

- 正常

  此狀態會將橢圓形填滿動畫，並將其還原為控制項的 `Background` 色彩。

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  此狀態會以動畫將橢圓形 `Background` 色彩繪製到新的色彩： `Yellow` 。

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

**\<ControlTemplate>** 現在看起來應該如下所示。

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

執行專案。 請注意，當您將滑鼠游標移至按鈕上方時，會以動畫的色彩呈現 **\<Ellipse>** 。

![滑鼠移至 WPF 按鈕以變更填滿色彩](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>後續步驟

- [在 WPF 中建立控制項的樣式](../fundamentals/styles-templates-create-apply-style.md)
- [WPF 中的樣式和範本](../fundamentals/styles-templates-overview.md)
- [XAML 資源的總覽](../fundamentals/xaml-resources-define.md)
