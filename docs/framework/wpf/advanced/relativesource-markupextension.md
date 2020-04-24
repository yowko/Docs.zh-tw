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
# <a name="relativesource-markupextension"></a><span data-ttu-id="6e0c4-102">RelativeSource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="6e0c4-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="6e0c4-103">指定<xref:System.Windows.Data.RelativeSource>綁定源的屬性,用於[綁定標記擴展](binding-markup-extension.md)中,或在設置 XAML 中建立<xref:System.Windows.Data.Binding.RelativeSource%2A><xref:System.Windows.Data.Binding>的元素的屬性時。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="6e0c4-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="6e0c4-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="6e0c4-105">XAML 屬性使用方式 (以巢狀方式置於 Binding 延伸內)</span><span class="sxs-lookup"><span data-stu-id="6e0c4-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="6e0c4-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="6e0c4-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="6e0c4-107">-或-</span><span class="sxs-lookup"><span data-stu-id="6e0c4-107">-or-</span></span>

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

## <a name="xaml-values"></a><span data-ttu-id="6e0c4-108">XAML 值</span><span class="sxs-lookup"><span data-stu-id="6e0c4-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="6e0c4-109">下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="6e0c4-109">One of the following:</span></span><br /><br /> <span data-ttu-id="6e0c4-110">- 字串權杖`Self`;對應為<xref:System.Windows.Data.RelativeSource>其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.Self>的 建立的 as</span><span class="sxs-lookup"><span data-stu-id="6e0c4-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="6e0c4-111">- 字串權杖`TemplatedParent`;對應為<xref:System.Windows.Data.RelativeSource>其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>的 建立的 as</span><span class="sxs-lookup"><span data-stu-id="6e0c4-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="6e0c4-112">- 字串權杖`PreviousData`;對應為<xref:System.Windows.Data.RelativeSource>其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.PreviousData>的 建立的 as</span><span class="sxs-lookup"><span data-stu-id="6e0c4-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="6e0c4-113">- 有關模式的`FindAncestor`資訊, 請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="6e0c4-114">字串語彙基元 `FindAncestor`。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="6e0c4-115">使用此語彙基元可進入某個模式，讓 `RelativeSource` 指定上階類型以及選擇性指定上階層級。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="6e0c4-116">這相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="6e0c4-117">`FindAncestor` 模式的必要項。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="6e0c4-118">類型的名稱，可填入 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="6e0c4-119">`FindAncestor` 模式的選擇項。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="6e0c4-120">上階層級 (朝邏輯樹狀結構的父項目方向評估)。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e0c4-121">備註</span><span class="sxs-lookup"><span data-stu-id="6e0c4-121">Remarks</span></span>

<span data-ttu-id="6e0c4-122">`{RelativeSource TemplatedParent}`綁定用法是一種關鍵技術,它解決了控件的 UI 和控件邏輯分離的較大概念。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="6e0c4-123">這可讓您從樣板定義內繫結到樣板化父代 (套用該樣板的執行階段物件執行個體)。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="6e0c4-124">在這種情況下,[樣本用標記延伸](templatebinding-markup-extension.md)實際上是以下繫式的縮寫: `{Binding RelativeSource={RelativeSource TemplatedParent}}`。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="6e0c4-125">`TemplateBinding`或`{RelativeSource TemplatedParent}`用法都只與定義範本的 XAML 中相關。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="6e0c4-126">有關詳細資訊,請參閱[樣本的結合的標記延伸](templatebinding-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="6e0c4-127">`{RelativeSource FindAncestor}`主要用於控制項樣本或可預測的自包含 UI 組合,用於始終預期控制項位於特定祖先類型的可視樹中的情況。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="6e0c4-128">例如，項目控制項的項目可能會使用 `FindAncestor` 使用方法以繫結至其項目控制項父代的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="6e0c4-129">或者，樣板中屬於控制項組合的項目也可以使用 `FindAncestor` 繫結至同一個組合結構中的父代項目。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="6e0c4-130">在＜XAML 語法＞章節內顯示之 `FindAncestor` 模式的物件項目語法中，第二種物件項目語法特別適用於 `FindAncestor` 模式。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="6e0c4-131">`FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="6e0c4-132">您必須<xref:System.Windows.Data.RelativeSource.AncestorType%2A>使用[x:Type 標記擴展](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)引用設定為要查找的祖先類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="6e0c4-133">在執行階段處理繫結要求時，會使用 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="6e0c4-134">對於 `FindAncestor` 模式來說，當該類型在項目樹狀結構中可能存在一個以上的上階時，選擇性屬性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 將有助於釐清上階查閱。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="6e0c4-135">如需關於如何使用 `FindAncestor` 模式的詳細資訊，請參閱 <xref:System.Windows.Data.RelativeSource>。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="6e0c4-136">`{RelativeSource Self}`實例的一個屬性應依賴於同一實例的另一個屬性的值,並且這兩個屬性之間不存在常規依賴項屬性關係(如強制),則非常有用。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="6e0c4-137">儘管在物件上存在兩個屬性,使值完全相同(並且類型相同)的情況很少見,但也可以將參數`Converter`應用於`{RelativeSource Self}`具有的綁定,並使用轉換器在源類型和目標類型之間轉換。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="6e0c4-138">的另`{RelativeSource Self}`一個方案是作為的<xref:System.Windows.MultiDataTrigger>一部分。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="6e0c4-139">例如，下面 XAML 會定義 <xref:System.Windows.Shapes.Rectangle> 項目，使得無論為 <xref:System.Windows.FrameworkElement.Width%2A> 輸入的值為何，<xref:System.Windows.Shapes.Rectangle> 永遠都是正方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="6e0c4-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="6e0c4-140">`{RelativeSource PreviousData}`在數據範本中,或者在綁定使用集合作為數據源的情況下非常有用。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="6e0c4-141">可以使用`{RelativeSource PreviousData}`突出顯示集合中相鄰數據項之間的關係。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="6e0c4-142">還有一個相關的技術，就是在資料來源中的目前和先前項目之間建立 <xref:System.Windows.Data.MultiBinding>，並在該繫結上使用轉換器來判斷這兩個項目及其屬性之間的不同。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="6e0c4-143">在下面範例中，項目範本中的第一個 <xref:System.Windows.Controls.TextBlock> 會顯示目前的號碼。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="6e0c4-144">第二<xref:System.Windows.Controls.TextBlock>個綁<xref:System.Windows.Data.MultiBinding>定是 名義<xref:System.Windows.Data.Binding>上有兩 個成分的綁定:當前記錄和`{RelativeSource PreviousData}`使用 故意使用 以前的數據記錄的綁定。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="6e0c4-145">然後，<xref:System.Windows.Data.MultiBinding> 上的轉換器會計算差異，並將它傳回給繫結。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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

<span data-ttu-id="6e0c4-146">此處不介紹將資料綁定描述為概念,請參閱[資料繫結此概述](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="6e0c4-147">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 處理器實現中,此標記擴展的<xref:System.Windows.Data.RelativeSource>處理由 類定義。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="6e0c4-148">`RelativeSource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="6e0c4-149">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="6e0c4-150">XAML 中的所有標記擴展在其屬性語法中`{``}`使用和字元,這是 XAML 處理器識別標記擴展必須處理該屬性的約定。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="6e0c4-151">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="6e0c4-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e0c4-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e0c4-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="6e0c4-153">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="6e0c4-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6e0c4-154">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="6e0c4-154">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="6e0c4-155">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="6e0c4-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="6e0c4-156">資料繫結概述</span><span class="sxs-lookup"><span data-stu-id="6e0c4-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6e0c4-157">繫結宣告概觀</span><span class="sxs-lookup"><span data-stu-id="6e0c4-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="6e0c4-158">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="6e0c4-158">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
