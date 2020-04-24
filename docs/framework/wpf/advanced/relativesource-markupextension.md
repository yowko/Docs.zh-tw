---
title: RelativeSource 標記延伸
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 6301299da966ade9b5cc7ccd105c8269a486744e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646221"
---
# <a name="relativesource-markupextension"></a>RelativeSource 標記延伸

指定<xref:System.Windows.Data.RelativeSource>綁定源的屬性,用於[綁定標記擴展](binding-markup-extension.md)中,或在設置 XAML 中建立<xref:System.Windows.Data.Binding.RelativeSource%2A><xref:System.Windows.Data.Binding>的元素的屬性時。

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
|`modeEnumValue`|下列其中之一：<br /><br /> - 字串權杖`Self`;對應為<xref:System.Windows.Data.RelativeSource>其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.Self>的 建立的 as<br />- 字串權杖`TemplatedParent`;對應為<xref:System.Windows.Data.RelativeSource>其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>的 建立的 as<br />- 字串權杖`PreviousData`;對應為<xref:System.Windows.Data.RelativeSource>其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.PreviousData>的 建立的 as<br />- 有關模式的`FindAncestor`資訊, 請參閱下文。|
|`FindAncestor`|字串語彙基元 `FindAncestor`。 使用此語彙基元可進入某個模式，讓 `RelativeSource` 指定上階類型以及選擇性指定上階層級。 這相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>。|
|`typeName`|`FindAncestor` 模式的必要項。 類型的名稱，可填入 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 屬性。|
|`intLevel`|`FindAncestor` 模式的選擇項。 上階層級 (朝邏輯樹狀結構的父項目方向評估)。|

## <a name="remarks"></a>備註

`{RelativeSource TemplatedParent}`綁定用法是一種關鍵技術,它解決了控件的 UI 和控件邏輯分離的較大概念。 這可讓您從樣板定義內繫結到樣板化父代 (套用該樣板的執行階段物件執行個體)。 在這種情況下,[樣本用標記延伸](templatebinding-markup-extension.md)實際上是以下繫式的縮寫: `{Binding RelativeSource={RelativeSource TemplatedParent}}`。 `TemplateBinding`或`{RelativeSource TemplatedParent}`用法都只與定義範本的 XAML 中相關。 有關詳細資訊,請參閱[樣本的結合的標記延伸](templatebinding-markup-extension.md)。

`{RelativeSource FindAncestor}`主要用於控制項樣本或可預測的自包含 UI 組合,用於始終預期控制項位於特定祖先類型的可視樹中的情況。 例如，項目控制項的項目可能會使用 `FindAncestor` 使用方法以繫結至其項目控制項父代的屬性。 或者，樣板中屬於控制項組合的項目也可以使用 `FindAncestor` 繫結至同一個組合結構中的父代項目。

在＜XAML 語法＞章節內顯示之 `FindAncestor` 模式的物件項目語法中，第二種物件項目語法特別適用於 `FindAncestor` 模式。 `FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。 您必須<xref:System.Windows.Data.RelativeSource.AncestorType%2A>使用[x:Type 標記擴展](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)引用設定為要查找的祖先類型的屬性。 在執行階段處理繫結要求時，會使用 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。

對於 `FindAncestor` 模式來說，當該類型在項目樹狀結構中可能存在一個以上的上階時，選擇性屬性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 將有助於釐清上階查閱。

如需關於如何使用 `FindAncestor` 模式的詳細資訊，請參閱 <xref:System.Windows.Data.RelativeSource>。

`{RelativeSource Self}`實例的一個屬性應依賴於同一實例的另一個屬性的值,並且這兩個屬性之間不存在常規依賴項屬性關係(如強制),則非常有用。 儘管在物件上存在兩個屬性,使值完全相同(並且類型相同)的情況很少見,但也可以將參數`Converter`應用於`{RelativeSource Self}`具有的綁定,並使用轉換器在源類型和目標類型之間轉換。 的另`{RelativeSource Self}`一個方案是作為的<xref:System.Windows.MultiDataTrigger>一部分。

例如，下面 XAML 會定義 <xref:System.Windows.Shapes.Rectangle> 項目，使得無論為 <xref:System.Windows.FrameworkElement.Width%2A> 輸入的值為何，<xref:System.Windows.Shapes.Rectangle> 永遠都是正方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`在數據範本中,或者在綁定使用集合作為數據源的情況下非常有用。 可以使用`{RelativeSource PreviousData}`突出顯示集合中相鄰數據項之間的關係。 還有一個相關的技術，就是在資料來源中的目前和先前項目之間建立 <xref:System.Windows.Data.MultiBinding>，並在該繫結上使用轉換器來判斷這兩個項目及其屬性之間的不同。

在下面範例中，項目範本中的第一個 <xref:System.Windows.Controls.TextBlock> 會顯示目前的號碼。 第二<xref:System.Windows.Controls.TextBlock>個綁<xref:System.Windows.Data.MultiBinding>定是 名義<xref:System.Windows.Data.Binding>上有兩 個成分的綁定:當前記錄和`{RelativeSource PreviousData}`使用 故意使用 以前的數據記錄的綁定。 然後，<xref:System.Windows.Data.MultiBinding> 上的轉換器會計算差異，並將它傳回給繫結。

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

此處不介紹將資料綁定描述為概念,請參閱[資料繫結此概述](../../../desktop-wpf/data/data-binding-overview.md)。

在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 處理器實現中,此標記擴展的<xref:System.Windows.Data.RelativeSource>處理由 類定義。

`RelativeSource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 XAML 中的所有標記擴展在其屬性語法中`{``}`使用和字元,這是 XAML 處理器識別標記擴展必須處理該屬性的約定。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.Binding>
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [繫結宣告概觀](../data/binding-declarations-overview.md)
- [x:Type 標記延伸](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
