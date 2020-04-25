---
title: RelativeSource 標記延伸
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 47117d684a981f31e22cf513fc78e1e2dda73f8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141258"
---
# <a name="relativesource-markupextension"></a>RelativeSource 標記延伸

指定系結來源<xref:System.Windows.Data.RelativeSource>的屬性，以用於系結[標記延伸](binding-markup-extension.md)中，或設定在 XAML 中<xref:System.Windows.Data.Binding.RelativeSource%2A>建立之<xref:System.Windows.Data.Binding>元素的屬性。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>XAML 屬性使用方式 (以巢狀方式置於 Binding 延伸內)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
```

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

-或-

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`modeEnumValue`|下列其中之一：<br /><br /> -字串標記`Self`;對應至所<xref:System.Windows.Data.RelativeSource>建立的，其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.Self>。<br />-字串標記`TemplatedParent`;對應至所<xref:System.Windows.Data.RelativeSource>建立的，其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>。<br />-字串標記`PreviousData`;對應至所<xref:System.Windows.Data.RelativeSource>建立的，其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.PreviousData>。<br />-如需`FindAncestor`模式的相關資訊，請參閱下文。|
|`FindAncestor`|字串語彙基元 `FindAncestor`。 使用此語彙基元可進入某個模式，讓 `RelativeSource` 指定上階類型以及選擇性指定上階層級。 這相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>。|
|`typeName`|`FindAncestor` 模式的必要項。 類型的名稱，可填入 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 屬性。|
|`intLevel`|`FindAncestor` 模式的選擇項。 上階層級 (朝邏輯樹狀結構的父項目方向評估)。|

## <a name="remarks"></a>備註

`{RelativeSource TemplatedParent}`系結使用方式是一種關鍵技巧，可解決控制項的 UI 與控制項的邏輯分離的較大概念。 這可讓您從樣板定義內繫結到樣板化父代 (套用該樣板的執行階段物件執行個體)。 在此情況下， [TemplateBinding 標記延伸](templatebinding-markup-extension.md)實際上是下列系結運算式的速記： `{Binding RelativeSource={RelativeSource TemplatedParent}}`。 `TemplateBinding`或`{RelativeSource TemplatedParent}`使用方式在定義範本的 XAML 中都是相關的。 如需詳細資訊，請參閱[TemplateBinding 標記延伸](templatebinding-markup-extension.md)。

`{RelativeSource FindAncestor}`主要用於控制項範本或可預測的獨立 UI 組合，適用于控制項一律應位於特定祖系類型的視覺化樹狀結構中的情況。 例如，項目控制項的項目可能會使用 `FindAncestor` 使用方法以繫結至其項目控制項父代的屬性。 或者，樣板中屬於控制項組合的項目也可以使用 `FindAncestor` 繫結至同一個組合結構中的父代項目。

在＜XAML 語法＞章節內顯示之 `FindAncestor` 模式的物件項目語法中，第二種物件項目語法特別適用於 `FindAncestor` 模式。 `FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。 您必須使用<xref:System.Windows.Data.RelativeSource.AncestorType%2A>要尋找之上階類型的[x:Type 標記延伸](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)參考，將設定為屬性。 在執行階段處理繫結要求時，會使用 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。

對於 `FindAncestor` 模式來說，當該類型在項目樹狀結構中可能存在一個以上的上階時，選擇性屬性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 將有助於釐清上階查閱。

如需關於如何使用 `FindAncestor` 模式的詳細資訊，請參閱 <xref:System.Windows.Data.RelativeSource>。

`{RelativeSource Self}`適用于實例的一個屬性應該相依于相同實例之另一個屬性的值，而且這兩個屬性之間已經有一般相依性屬性關聯性（例如強制型轉）的情況。 雖然物件上有兩個屬性是很罕見的，因此這些值實際上是相同的（且具有相同的型別），您也`Converter`可以將參數套用至具有`{RelativeSource Self}`的系結，並使用轉換器在來源和目標型別之間進行轉換。 的另一個`{RelativeSource Self}`案例是的一部分<xref:System.Windows.MultiDataTrigger>。

例如，下面 XAML 會定義 <xref:System.Windows.Shapes.Rectangle> 項目，使得無論為 <xref:System.Windows.FrameworkElement.Width%2A> 輸入的值為何，<xref:System.Windows.Shapes.Rectangle> 永遠都是正方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`在資料範本中，或系結使用集合做為資料來源的情況下很有用。 您可以使用`{RelativeSource PreviousData}`來反白顯示集合中相鄰資料項目之間的關聯性。 還有一個相關的技術，就是在資料來源中的目前和先前項目之間建立 <xref:System.Windows.Data.MultiBinding>，並在該繫結上使用轉換器來判斷這兩個項目及其屬性之間的不同。

在下面範例中，項目範本中的第一個 <xref:System.Windows.Controls.TextBlock> 會顯示目前的號碼。 第二<xref:System.Windows.Controls.TextBlock>個系結<xref:System.Windows.Data.MultiBinding>是，名義上有<xref:System.Windows.Data.Binding>兩個要素：目前的記錄，以及刻意使用先前資料記錄的系結`{RelativeSource PreviousData}`。 然後，<xref:System.Windows.Data.MultiBinding> 上的轉換器會計算差異，並將它傳回給繫結。

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox>
```

此處未涵蓋以概念描述資料系結的說明，請參閱資料系結[總覽](../../../desktop-wpf/data/data-binding-overview.md)。

在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器執行中，此標記延伸模組的處理是由<xref:System.Windows.Data.RelativeSource>類別所定義。

`RelativeSource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 XAML 中的`{`所有標記延伸都會在`}`其屬性語法中使用和字元，這是 xaml 處理器識別標記延伸必須處理屬性的慣例。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.Binding>
- [樣式設定和範本化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [繫結宣告概觀](../data/binding-declarations-overview.md)
- [x:Type 標記延伸](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
