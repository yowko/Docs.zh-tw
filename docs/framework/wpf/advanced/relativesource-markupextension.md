---
title: RelativeSource 標記延伸
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 7a9c9fe379f361dec0d65b71c4d883958be9ed2f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834822"
---
# <a name="relativesource-markupextension"></a>RelativeSource 標記延伸

指定要在系結[標記延伸](binding-markup-extension.md)中使用之 @no__t 0 系結來源的屬性，或設定在 XAML 中建立之 <xref:System.Windows.Data.Binding> 元素的 <xref:System.Windows.Data.Binding.RelativeSource%2A> 屬性。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>XAML 屬性使用方式 (以巢狀方式置於 Binding 延伸內)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
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
|`modeEnumValue`|下列其中一項：<br /><br /> -字串 token `Self`;對應至已建立的 <xref:System.Windows.Data.RelativeSource>，其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設定為 <xref:System.Windows.Data.RelativeSourceMode.Self>。<br />-字串 token `TemplatedParent`;對應至已建立的 <xref:System.Windows.Data.RelativeSource>，其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設定為 <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>。<br />-字串 token `PreviousData`;對應至已建立的 <xref:System.Windows.Data.RelativeSource>，其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設定為 <xref:System.Windows.Data.RelativeSourceMode.PreviousData>。<br />-如需 `FindAncestor` 模式的相關資訊，請參閱下文。|
|`FindAncestor`|字串語彙基元 `FindAncestor`。 使用此語彙基元可進入某個模式，讓 `RelativeSource` 指定上階類型以及選擇性指定上階層級。 這相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>。|
|`typeName`|`FindAncestor` 模式的必要項。 類型的名稱，可填入 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 屬性。|
|`intLevel`|`FindAncestor` 模式的選擇項。 上階層級 (朝邏輯樹狀結構的父項目方向評估)。|

## <a name="remarks"></a>備註

`{RelativeSource TemplatedParent}` 系結使用方式是一種關鍵技巧，可解決控制項的 UI 與控制項的邏輯分離的較大概念。 這可讓您從樣板定義內繫結到樣板化父代 (套用該樣板的執行階段物件執行個體)。 在此情況下， [TemplateBinding 標記延伸](templatebinding-markup-extension.md)實際上是下列系結運算式的速記： `{Binding RelativeSource={RelativeSource TemplatedParent}}`。 `TemplateBinding` 或 @no__t 1 的使用方式，都只在定義範本的 XAML 中相關。 如需詳細資訊，請參閱[TemplateBinding 標記延伸](templatebinding-markup-extension.md)。

`{RelativeSource FindAncestor}` 主要用於控制項範本或可預測的獨立 UI 組合，適用于控制項一律應位於特定祖系類型的視覺化樹狀結構中的情況。 例如，項目控制項的項目可能會使用 `FindAncestor` 使用方法以繫結至其項目控制項父代的屬性。 或者，樣板中屬於控制項組合的項目也可以使用 `FindAncestor` 繫結至同一個組合結構中的父代項目。

在＜XAML 語法＞章節內顯示之 `FindAncestor` 模式的物件項目語法中，第二種物件項目語法特別適用於 `FindAncestor` 模式。 `FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。 您必須將 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 設定為使用要尋找之上階型別之[X:Type 標記延伸](../../xaml-services/x-type-markup-extension.md)參考的屬性。 在執行階段處理繫結要求時，會使用 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。

對於 `FindAncestor` 模式來說，當該類型在項目樹狀結構中可能存在一個以上的上階時，選擇性屬性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 將有助於釐清上階查閱。

如需關於如何使用 `FindAncestor` 模式的詳細資訊，請參閱 <xref:System.Windows.Data.RelativeSource>。

如果實例的一個屬性應該相依于相同實例之另一個屬性的值，而且這兩個屬性之間已經有一般相依性屬性關聯性（例如強制型轉），則 `{RelativeSource Self}` 非常有用。 雖然物件上有兩個屬性很罕見，因此這些值實際上是相同的（且具有相同的類型），您也可以將 `Converter` 參數套用至具有 `{RelativeSource Self}` 的系結，並使用轉換器在來源與目標型別之間進行轉換。 @No__t-0 的另一個案例是 <xref:System.Windows.MultiDataTrigger> 的一部分。

例如，下面 XAML 會定義 <xref:System.Windows.Shapes.Rectangle> 項目，使得無論為 <xref:System.Windows.FrameworkElement.Width%2A> 輸入的值為何，<xref:System.Windows.Shapes.Rectangle> 永遠都是正方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

在資料範本中，或在系結使用集合做為資料來源的情況下，`{RelativeSource PreviousData}` 很有用。 您可以使用 `{RelativeSource PreviousData}` 來反白顯示集合中相鄰資料項目之間的關聯性。 還有一個相關的技術，就是在資料來源中的目前和先前項目之間建立 <xref:System.Windows.Data.MultiBinding>，並在該繫結上使用轉換器來判斷這兩個項目及其屬性之間的不同。

在下面範例中，項目範本中的第一個 <xref:System.Windows.Controls.TextBlock> 會顯示目前的號碼。 第二個 <xref:System.Windows.Controls.TextBlock> 系結是一個 <xref:System.Windows.Data.MultiBinding>，名義上有兩個 @no__t 2 的共同要素：目前的記錄，以及使用 `{RelativeSource PreviousData}` 刻意使用先前資料記錄的系結。 然後，<xref:System.Windows.Data.MultiBinding> 上的轉換器會計算差異，並將它傳回給繫結。

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
```

此處未涵蓋以概念描述資料系結的說明，請參閱資料系結[總覽](../data/data-binding-overview.md)。

在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器執行中，此標記延伸模組的處理是由 <xref:System.Windows.Data.RelativeSource> 類別所定義。

`RelativeSource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 XAML 中的所有標記延伸都會在其屬性語法中使用 `{` 和 `}` 個字元，這是 XAML 處理器辨識標記延伸必須處理屬性的慣例。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.Binding>
- [樣式設定和範本化](../controls/styling-and-templating.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [資料繫結概觀](../data/data-binding-overview.md)
- [繫結宣告概觀](../data/binding-declarations-overview.md)
- [x:Type 標記延伸模組](../../xaml-services/x-type-markup-extension.md)
