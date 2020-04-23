---
title: 在 WPF - .NET 桌面建立樣本
description: 瞭解如何在 Windows 演示文稿基礎和 .NET Core 中創建和引用控制項樣本。
author: thraka
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
ms.openlocfilehash: c901864d387b8de976bbfa9a9b3c14a7d5a0b4d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "82071245"
---
# <a name="create-a-template-for-a-control"></a>為控制項建立樣本

使用 Windows 簡報簡報 (WPF),您可以使用自己的可重用範本自訂現有控制項的可視結構和行為。 範本可以全域應用於應用程式、視窗和頁面,也可以直接應用於控件。 通過為現有控制項創建新範本,可以涵蓋大多數需要您創建新控制項的方案。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

在本文中,您將探討<xref:System.Windows.Controls.ControlTemplate><xref:System.Windows.Controls.Button>為控制項創建新控制項。

## <a name="when-to-create-a-controltemplate"></a>何時建立控制項樣本

控制項具有許多屬性,例如<xref:System.Windows.Controls.Border.Background%2A>與<xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.FontFamily%2A> 。 這些屬性控制控制件外觀的不同方面,但通過設置這些屬性可以進行的更改是有限的。 例如,可以將<xref:System.Windows.Controls.Control.Foreground%2A>屬性設置為藍色,<xref:System.Windows.Controls.Control.FontStyle%2A>將 屬性設置為斜<xref:System.Windows.Controls.CheckBox>體。 如果要自訂控制件的外觀,超出控制項上其他屬性設定可以執行的內容,請建立一個<xref:System.Windows.Controls.ControlTemplate>。

在大多數用戶介面中,按鈕具有相同的常規外觀:帶有某些文本的矩形。 如果要創建圓角按鈕,可以創建從按鈕繼承的新控制項或重新創建按鈕的功能。 此外,新的使用者控制項將提供圓形視覺物件。

通過自定義現有控制項的可視佈局,可以避免創建新控制項。 使用圓角按鈕,建立<xref:System.Windows.Controls.ControlTemplate>具有所需視覺佈局的 。

另一方面,如果需要具有新功能、不同屬性和新設置的控制項,則可以創建新<xref:System.Windows.Controls.UserControl>的 。

## <a name="prerequisites"></a>Prerequisites

建立新的 WPF 應用程式,並在*MainWindow.xaml(* 或您選擇的其他視窗)中設定**\<視窗>** 元素上的以下屬性:

|     |     |
| --- | --- |
| **[!OP.NO-LOC(Title)]**         | `Template Intro Sample` |
| **[!OP.NO-LOC(SizeToContent)]** | `WidthAndHeight` |
| **[!OP.NO-LOC(MinWidth)]**      | `250` |

將**\<視窗>** 元素的內容設定為以下 XAML:

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

最後 *,MainWindow.xaml*檔案應類似於以下內容:

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

如果運行該應用程式,它如下所示:

![帶兩個未樣式按鈕的 WPF 視窗](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>建立 ControlTemplate

聲明<xref:System.Windows.Controls.ControlTemplate>的最常見方法是作為 XAML`Resources`檔中 的節中的資源。 由於範本是資源,因此它們遵循適用於所有資源的相同範圍規則。 簡單地說,聲明範本的位置會影響範本的應用位置。 例如,如果在應用程式定義 XAML 檔的根元素中聲明範本,則可以在應用程式中的任何位置使用該範本。 如果在視窗中定義範本,則只有該視窗中的控制項可以使用該範本。

首先,向`Window.Resources`*MainWindow.xaml*檔案加入元素:

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

使用以下屬性集建立新**\<的 ControlTemplate>:**

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

此控制項樣本非常簡單:

- 控件的根元素,<xref:System.Windows.Controls.Grid>
- 繪製<xref:System.Windows.Shapes.Ellipse>按鍵的圓舍入外觀
- a<xref:System.Windows.Controls.ContentPresenter>以顯示使用者指定的按鈕內容

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

創建新<xref:System.Windows.Controls.ControlTemplate>時 ,仍可能仍要使用公共屬性來更改控制件的外觀。 [樣本繫結](../../framework/wpf/advanced/templatebinding-markup-extension.md)標記延伸將 元素的屬性綁定<xref:System.Windows.Controls.ControlTemplate>到由控制項定義的公共屬性。 使用[範本繫結](../../framework/wpf/advanced/templatebinding-markup-extension.md)項時,將啟用控制件上的屬性作為範本的參數。 也就是說，已設定控制項上的屬性時，該值會傳遞給具有 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。

### <a name="ellipse"></a>橢圓形

**:::no-loc text="Fill":::** 請注意**:::no-loc text="Stroke":::**<xref:System.Windows.Controls.Control.Foreground>,**\<橢圓>** 元素的 和 屬性綁<xref:System.Windows.Controls.Control.Background>定到控制項和 屬性。

### <a name="contentpresenter"></a>ContentPresenter

內容演示者>元素也會添加到範本中。 [ \< ](xref:System.Windows.Controls.ContentPresenter) 由於此範本是為按鈕設計的,因此,考慮到該按鈕從<xref:System.Windows.Controls.ContentControl>繼承。 該按鈕顯示元素的內容。 您可以在按鈕內設置任何內容,例如純文本或其他控件。 以下兩個按鈕均為有效按鈕:

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

在前面的兩個範例中,文本和複選框都設置為[Button.Content](xref:System.Windows.Controls.ContentControl.Content)屬性。 任何設置為內容的內容都可以通過**\<ContentPresenter>**(即範本)顯示,這是範本的作用。

如果 套<xref:System.Windows.Controls.ContentControl>用型態`Button`(如元素樹中搜尋<xref:System.Windows.Controls.ContentPresenter><xref:System.Windows.Controls.ControlTemplate>。 找不到`ContentPresenter`,樣本會自動將控制的屬性 的<xref:System.Windows.Controls.ContentControl.Content>屬性 。 `ContentPresenter`

## <a name="use-the-template"></a>使用範本

查找本文開頭聲明的按鈕。

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

將第二個按鈕的屬性<xref:System.Windows.Controls.Control.Template>設定`roundbutton`為 資源:

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

如果執行項目並查看結果,您將看到該按鈕具有圓潤的背景。

![帶一個樣本橢圓形按鈕的 WPF 視窗](media/create-apply-template/styled-button.png)

您可能已經注意到該按鈕不是圓,而是偏斜的。 由於**\<橢圓>** 元素的工作方式,它總是展開以填充可用空間。 透過按鈕**:::no-loc text="width":::** 與屬性**:::no-loc text="height":::** 變更為相同的值,使圓均勻:

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![以樣本圓形按鈕的 WPF 視窗](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>新增觸發器

即使應用了範本的按鈕看起來不同,它的外觀與任何其他按鈕相同。 如果按下該按鈕,事件將<xref:System.Windows.Controls.Primitives.ButtonBase.Click>觸發。 但是,您可能已經注意到,當您將滑鼠移到按鈕上時,按鈕的視覺效果不會更改。 這些可視化交互都由範本定義。

使用 WPF 提供的動態事件和屬性系統,可以監視值的特定屬性,然後在適當的時候重新設置範本的樣式。 這個選項, 您會觀看按鈕的屬性<xref:System.Windows.UIElement.IsMouseOver>。 當滑鼠位於控件上時,使用新顏色對**\<橢圓>** 進行樣式設置。 這種類型的觸發器稱為*屬性觸發器*。

為此,您需要向**\<橢圓>** 添加一個名稱,以便參考。 給它的背景**元素**的名稱。

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

接下來,<xref:System.Windows.Trigger>向[控件範本.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers)集合添加新。 觸發器將監視值`IsMouseOver``true`的事件。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

接下來,將**\<setter>** 添加到**\<將****\<橢圓>** 的**填充**屬性更改為新顏色的觸發器>。

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

執行專案。 請注意,當您將滑鼠移到按鈕上時,**\<橢圓的顏色>** 更改。

![滑鼠在 WPF 按鍵上移動以改變填充顏色](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>使用視覺狀態

可視狀態由控件定義和觸發。 例如,當滑鼠移動到控制項的頂部時,`CommonStates.MouseOver`將觸發狀態。 您可以根據控制項的當前狀態為屬性更改設定動畫。 在`AliceBlue``IsMouseOver``true`上**一\<節中,屬性觸發器>** 用於將按鈕的前景更改為 屬性為 時。 相反,創建一個可視狀態,為更改此顏色設置動畫,從而提供平滑過渡。 有關 Visual*狀態*的詳細資訊,請參閱[WPF 中的樣式和樣本](../fundamentals/styles-templates-overview.md#visual-states)。

要將**\<屬性觸發>** 轉換為動畫視覺狀態,首先,請從範本中刪除**\<ControlTemplate.Trigger>** 元素。

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

接下來,在**\<控件範本的網格>** 根中,添加**\<VisualStateManager.VisualStateGroup>** 元素,該元素具有**\<VisualStateGroup** `CommonStates`>。 定義兩種狀態`Normal`,`MouseOver`與 。

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

觸發**\<該**狀態時,將應用 VisualState>中定义的任何动画。 為每個狀態創建動畫。 動畫放在**\<情節提要>** 元素的內。 有關情節提要的詳細資訊,請參閱[情節提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。

- 正常

  此狀態為橢圓填充設置動畫,將其還原到控制項`Background`的顏色。

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  此狀態將橢圓`Background`顏色動畫為新顏色`Yellow`: 。

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

控件範本>現在應如下所示。 ** \< **

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

執行專案。 請注意,當您將滑鼠移到按鈕上時,**\<橢圓的顏色>** 動畫。

![滑鼠在 WPF 按鍵上移動以改變填充顏色](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>後續步驟

- [為 WPF 中的控制項建立樣式](../fundamentals/styles-templates-create-apply-style.md)
- [WPF 中的樣式和樣本](../fundamentals/styles-templates-overview.md)
- [XAML 資源概述](../fundamentals/xaml-resources-define.md)
