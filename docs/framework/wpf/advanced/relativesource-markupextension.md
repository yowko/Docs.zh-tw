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
# <a name="relativesource-markupextension"></a><span data-ttu-id="10be3-102">RelativeSource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="10be3-102">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="10be3-103">指定系結來源<xref:System.Windows.Data.RelativeSource>的屬性，以用於系結[標記延伸](binding-markup-extension.md)中，或設定在 XAML 中<xref:System.Windows.Data.Binding.RelativeSource%2A>建立之<xref:System.Windows.Data.Binding>元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="10be3-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="10be3-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="10be3-104">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="10be3-105">XAML 屬性使用方式 (以巢狀方式置於 Binding 延伸內)</span><span class="sxs-lookup"><span data-stu-id="10be3-105">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="10be3-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="10be3-106">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="10be3-107">-或-</span><span class="sxs-lookup"><span data-stu-id="10be3-107">-or-</span></span>

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

## <a name="xaml-values"></a><span data-ttu-id="10be3-108">XAML 值</span><span class="sxs-lookup"><span data-stu-id="10be3-108">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="10be3-109">下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="10be3-109">One of the following:</span></span><br /><br /> <span data-ttu-id="10be3-110">-字串標記`Self`;對應至所<xref:System.Windows.Data.RelativeSource>建立的，其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.Self>。</span><span class="sxs-lookup"><span data-stu-id="10be3-110">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="10be3-111">-字串標記`TemplatedParent`;對應至所<xref:System.Windows.Data.RelativeSource>建立的，其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>。</span><span class="sxs-lookup"><span data-stu-id="10be3-111">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="10be3-112">-字串標記`PreviousData`;對應至所<xref:System.Windows.Data.RelativeSource>建立的，其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.PreviousData>。</span><span class="sxs-lookup"><span data-stu-id="10be3-112">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="10be3-113">-如需`FindAncestor`模式的相關資訊，請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="10be3-113">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="10be3-114">字串語彙基元 `FindAncestor`。</span><span class="sxs-lookup"><span data-stu-id="10be3-114">The string token `FindAncestor`.</span></span> <span data-ttu-id="10be3-115">使用此語彙基元可進入某個模式，讓 `RelativeSource` 指定上階類型以及選擇性指定上階層級。</span><span class="sxs-lookup"><span data-stu-id="10be3-115">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="10be3-116">這相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>。</span><span class="sxs-lookup"><span data-stu-id="10be3-116">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="10be3-117">`FindAncestor` 模式的必要項。</span><span class="sxs-lookup"><span data-stu-id="10be3-117">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="10be3-118">類型的名稱，可填入 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="10be3-118">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="10be3-119">`FindAncestor` 模式的選擇項。</span><span class="sxs-lookup"><span data-stu-id="10be3-119">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="10be3-120">上階層級 (朝邏輯樹狀結構的父項目方向評估)。</span><span class="sxs-lookup"><span data-stu-id="10be3-120">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="10be3-121">備註</span><span class="sxs-lookup"><span data-stu-id="10be3-121">Remarks</span></span>

<span data-ttu-id="10be3-122">`{RelativeSource TemplatedParent}`系結使用方式是一種關鍵技巧，可解決控制項的 UI 與控制項的邏輯分離的較大概念。</span><span class="sxs-lookup"><span data-stu-id="10be3-122">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="10be3-123">這可讓您從樣板定義內繫結到樣板化父代 (套用該樣板的執行階段物件執行個體)。</span><span class="sxs-lookup"><span data-stu-id="10be3-123">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="10be3-124">在此情況下， [TemplateBinding 標記延伸](templatebinding-markup-extension.md)實際上是下列系結運算式的速記： `{Binding RelativeSource={RelativeSource TemplatedParent}}`。</span><span class="sxs-lookup"><span data-stu-id="10be3-124">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="10be3-125">`TemplateBinding`或`{RelativeSource TemplatedParent}`使用方式在定義範本的 XAML 中都是相關的。</span><span class="sxs-lookup"><span data-stu-id="10be3-125">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="10be3-126">如需詳細資訊，請參閱[TemplateBinding 標記延伸](templatebinding-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="10be3-126">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="10be3-127">`{RelativeSource FindAncestor}`主要用於控制項範本或可預測的獨立 UI 組合，適用于控制項一律應位於特定祖系類型的視覺化樹狀結構中的情況。</span><span class="sxs-lookup"><span data-stu-id="10be3-127">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="10be3-128">例如，項目控制項的項目可能會使用 `FindAncestor` 使用方法以繫結至其項目控制項父代的屬性。</span><span class="sxs-lookup"><span data-stu-id="10be3-128">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="10be3-129">或者，樣板中屬於控制項組合的項目也可以使用 `FindAncestor` 繫結至同一個組合結構中的父代項目。</span><span class="sxs-lookup"><span data-stu-id="10be3-129">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="10be3-130">在＜XAML 語法＞章節內顯示之 `FindAncestor` 模式的物件項目語法中，第二種物件項目語法特別適用於 `FindAncestor` 模式。</span><span class="sxs-lookup"><span data-stu-id="10be3-130">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="10be3-131">`FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="10be3-131">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="10be3-132">您必須使用<xref:System.Windows.Data.RelativeSource.AncestorType%2A>要尋找之上階類型的[x:Type 標記延伸](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)參考，將設定為屬性。</span><span class="sxs-lookup"><span data-stu-id="10be3-132">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="10be3-133">在執行階段處理繫結要求時，會使用 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="10be3-133">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="10be3-134">對於 `FindAncestor` 模式來說，當該類型在項目樹狀結構中可能存在一個以上的上階時，選擇性屬性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 將有助於釐清上階查閱。</span><span class="sxs-lookup"><span data-stu-id="10be3-134">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="10be3-135">如需關於如何使用 `FindAncestor` 模式的詳細資訊，請參閱 <xref:System.Windows.Data.RelativeSource>。</span><span class="sxs-lookup"><span data-stu-id="10be3-135">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="10be3-136">`{RelativeSource Self}`適用于實例的一個屬性應該相依于相同實例之另一個屬性的值，而且這兩個屬性之間已經有一般相依性屬性關聯性（例如強制型轉）的情況。</span><span class="sxs-lookup"><span data-stu-id="10be3-136">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="10be3-137">雖然物件上有兩個屬性是很罕見的，因此這些值實際上是相同的（且具有相同的型別），您也`Converter`可以將參數套用至具有`{RelativeSource Self}`的系結，並使用轉換器在來源和目標型別之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="10be3-137">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="10be3-138">的另一個`{RelativeSource Self}`案例是的一部分<xref:System.Windows.MultiDataTrigger>。</span><span class="sxs-lookup"><span data-stu-id="10be3-138">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="10be3-139">例如，下面 XAML 會定義 <xref:System.Windows.Shapes.Rectangle> 項目，使得無論為 <xref:System.Windows.FrameworkElement.Width%2A> 輸入的值為何，<xref:System.Windows.Shapes.Rectangle> 永遠都是正方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="10be3-139">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="10be3-140">`{RelativeSource PreviousData}`在資料範本中，或系結使用集合做為資料來源的情況下很有用。</span><span class="sxs-lookup"><span data-stu-id="10be3-140">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="10be3-141">您可以使用`{RelativeSource PreviousData}`來反白顯示集合中相鄰資料項目之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="10be3-141">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="10be3-142">還有一個相關的技術，就是在資料來源中的目前和先前項目之間建立 <xref:System.Windows.Data.MultiBinding>，並在該繫結上使用轉換器來判斷這兩個項目及其屬性之間的不同。</span><span class="sxs-lookup"><span data-stu-id="10be3-142">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="10be3-143">在下面範例中，項目範本中的第一個 <xref:System.Windows.Controls.TextBlock> 會顯示目前的號碼。</span><span class="sxs-lookup"><span data-stu-id="10be3-143">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="10be3-144">第二<xref:System.Windows.Controls.TextBlock>個系結<xref:System.Windows.Data.MultiBinding>是，名義上有<xref:System.Windows.Data.Binding>兩個要素：目前的記錄，以及刻意使用先前資料記錄的系結`{RelativeSource PreviousData}`。</span><span class="sxs-lookup"><span data-stu-id="10be3-144">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="10be3-145">然後，<xref:System.Windows.Data.MultiBinding> 上的轉換器會計算差異，並將它傳回給繫結。</span><span class="sxs-lookup"><span data-stu-id="10be3-145">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

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

<span data-ttu-id="10be3-146">此處未涵蓋以概念描述資料系結的說明，請參閱資料系結[總覽](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="10be3-146">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="10be3-147">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器執行中，此標記延伸模組的處理是由<xref:System.Windows.Data.RelativeSource>類別所定義。</span><span class="sxs-lookup"><span data-stu-id="10be3-147">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="10be3-148">`RelativeSource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="10be3-148">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="10be3-149">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="10be3-149">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="10be3-150">XAML 中的`{`所有標記延伸都會在`}`其屬性語法中使用和字元，這是 xaml 處理器識別標記延伸必須處理屬性的慣例。</span><span class="sxs-lookup"><span data-stu-id="10be3-150">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="10be3-151">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="10be3-151">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10be3-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10be3-152">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="10be3-153">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="10be3-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="10be3-154">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="10be3-154">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="10be3-155">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="10be3-155">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="10be3-156">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="10be3-156">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="10be3-157">繫結宣告概觀</span><span class="sxs-lookup"><span data-stu-id="10be3-157">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="10be3-158">x:Type 標記延伸</span><span class="sxs-lookup"><span data-stu-id="10be3-158">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
