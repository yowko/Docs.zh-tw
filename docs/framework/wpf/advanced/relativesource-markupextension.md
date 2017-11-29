---
title: "RelativeSource 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41978e7b91c50b33649bd88e23d22fce7a272c5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="9d58b-102">RelativeSource 標記延伸</span><span class="sxs-lookup"><span data-stu-id="9d58b-102">RelativeSource MarkupExtension</span></span>
<span data-ttu-id="9d58b-103">指定屬性<xref:System.Windows.Data.RelativeSource>內要使用的繫結來源[繫結標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)，或設定時<xref:System.Windows.Data.Binding.RelativeSource%2A>屬性<xref:System.Windows.Data.Binding>在 XAML 中建立的項目。</span><span class="sxs-lookup"><span data-stu-id="9d58b-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="9d58b-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="9d58b-104">XAML Attribute Usage</span></span>  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="9d58b-105">XAML 屬性使用方式 (以巢狀方式置於 Binding 延伸內)</span><span class="sxs-lookup"><span data-stu-id="9d58b-105">XAML Attribute Usage (nested within Binding extension)</span></span>  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="9d58b-106">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="9d58b-106">XAML Object Element Usage</span></span>  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
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
  
## <a name="xaml-values"></a><span data-ttu-id="9d58b-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="9d58b-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`modeEnumValue`|<span data-ttu-id="9d58b-108">下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="9d58b-108">One of the following:</span></span><br /><br /> <span data-ttu-id="9d58b-109">-的字串語彙基元`Self`; 對應至<xref:System.Windows.Data.RelativeSource>與建立其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.Self>。</span><span class="sxs-lookup"><span data-stu-id="9d58b-109">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="9d58b-110">-的字串語彙基元`TemplatedParent`; 對應至<xref:System.Windows.Data.RelativeSource>與建立其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>。</span><span class="sxs-lookup"><span data-stu-id="9d58b-110">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="9d58b-111">-的字串語彙基元`PreviousData`; 對應至<xref:System.Windows.Data.RelativeSource>與建立其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.PreviousData>。</span><span class="sxs-lookup"><span data-stu-id="9d58b-111">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="9d58b-112">-請參閱下方的資訊上`FindAncestor`模式。</span><span class="sxs-lookup"><span data-stu-id="9d58b-112">-   See below for information on `FindAncestor` mode.</span></span>|  
|`FindAncestor`|<span data-ttu-id="9d58b-113">字串語彙基元 `FindAncestor`。</span><span class="sxs-lookup"><span data-stu-id="9d58b-113">The string token `FindAncestor`.</span></span> <span data-ttu-id="9d58b-114">使用此語彙基元可進入某個模式，讓 `RelativeSource` 指定上階類型以及選擇性指定上階層級。</span><span class="sxs-lookup"><span data-stu-id="9d58b-114">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="9d58b-115">這相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>。</span><span class="sxs-lookup"><span data-stu-id="9d58b-115">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|  
|`typeName`|<span data-ttu-id="9d58b-116">`FindAncestor` 模式的必要項。</span><span class="sxs-lookup"><span data-stu-id="9d58b-116">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="9d58b-117">類型的名稱，可填入 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9d58b-117">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|  
|`intLevel`|<span data-ttu-id="9d58b-118">`FindAncestor` 模式的選擇項。</span><span class="sxs-lookup"><span data-stu-id="9d58b-118">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="9d58b-119">上階層級 (朝邏輯樹狀結構的父項目方向評估)。</span><span class="sxs-lookup"><span data-stu-id="9d58b-119">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d58b-120">備註</span><span class="sxs-lookup"><span data-stu-id="9d58b-120">Remarks</span></span>  
 <span data-ttu-id="9d58b-121">`{RelativeSource TemplatedParent}`繫結使用方式是一種金鑰的技巧，以解決較大型的控制項的 UI 和控制項的邏輯分隔的概念。</span><span class="sxs-lookup"><span data-stu-id="9d58b-121">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="9d58b-122">這可讓您從樣板定義內繫結到樣板化父代 (套用該樣板的執行階段物件執行個體)。</span><span class="sxs-lookup"><span data-stu-id="9d58b-122">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="9d58b-123">此案例中， [TemplateBinding 標記延伸](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)事實上是下列繫結運算式的縮寫： `{Binding RelativeSource={RelativeSource TemplatedParent}}`。</span><span class="sxs-lookup"><span data-stu-id="9d58b-123">For this case, the [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="9d58b-124">`TemplateBinding`或`{RelativeSource TemplatedParent}`用法都定義的範本，在 XAML 中才相關。</span><span class="sxs-lookup"><span data-stu-id="9d58b-124">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="9d58b-125">如需詳細資訊，請參閱[TemplateBinding 標記延伸](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="9d58b-125">For more information, see [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span></span>  
  
 <span data-ttu-id="9d58b-126">`{RelativeSource FindAncestor}`主要用於控制項樣板或可預測的獨立的 UI 組合，其中控制項一律必須是特定上階類型的視覺化樹狀結構中的案例。</span><span class="sxs-lookup"><span data-stu-id="9d58b-126">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="9d58b-127">例如，項目控制項的項目可能會使用 `FindAncestor` 使用方法以繫結至其項目控制項父代的屬性。</span><span class="sxs-lookup"><span data-stu-id="9d58b-127">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="9d58b-128">或者，樣板中屬於控制項組合的項目也可以使用 `FindAncestor` 繫結至同一個組合結構中的父代項目。</span><span class="sxs-lookup"><span data-stu-id="9d58b-128">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>  
  
 <span data-ttu-id="9d58b-129">在＜XAML 語法＞章節內顯示之 `FindAncestor` 模式的物件項目語法中，第二種物件項目語法特別適用於 `FindAncestor` 模式。</span><span class="sxs-lookup"><span data-stu-id="9d58b-129">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="9d58b-130">`FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="9d58b-130">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="9d58b-131">您必須設定<xref:System.Windows.Data.RelativeSource.AncestorType%2A>當做屬性使用[X:type 標記延伸](../../../../docs/framework/xaml-services/x-type-markup-extension.md)尋找上階的型別參考。</span><span class="sxs-lookup"><span data-stu-id="9d58b-131">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../../docs/framework/xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="9d58b-132">在執行階段處理繫結要求時，會使用 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="9d58b-132">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>  
  
 <span data-ttu-id="9d58b-133">對於 `FindAncestor` 模式來說，當該類型在項目樹狀結構中可能存在一個以上的上階時，選擇性屬性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 將有助於釐清上階查閱。</span><span class="sxs-lookup"><span data-stu-id="9d58b-133">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>  
  
 <span data-ttu-id="9d58b-134">如需關於如何使用 `FindAncestor` 模式的詳細資訊，請參閱 <xref:System.Windows.Data.RelativeSource>。</span><span class="sxs-lookup"><span data-stu-id="9d58b-134">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>  
  
 <span data-ttu-id="9d58b-135">`{RelativeSource Self}`是適用於案例之間這兩個屬性其中一個屬性的執行個體應該相依於相同的執行個體，並沒有一般的相依性屬性的關聯性 （例如強制型轉） 的另一個屬性的值已經存在。</span><span class="sxs-lookup"><span data-stu-id="9d58b-135">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="9d58b-136">雖然罕見，值會逐字相同 （和具有相同類型） 的兩個屬性存在物件上，您也可以套用`Converter`了的繫結的參數`{RelativeSource Self}`，並使用轉換器來源之間進行轉換和目標類型。</span><span class="sxs-lookup"><span data-stu-id="9d58b-136">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="9d58b-137">另一個案例`{RelativeSource Self}`一部分<xref:System.Windows.MultiDataTrigger>。</span><span class="sxs-lookup"><span data-stu-id="9d58b-137">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>  
  
 <span data-ttu-id="9d58b-138">例如，下面 XAML 會定義 <xref:System.Windows.Shapes.Rectangle> 項目，使得無論為 <xref:System.Windows.FrameworkElement.Width%2A> 輸入的值為何，<xref:System.Windows.Shapes.Rectangle> 永遠都是正方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="9d58b-138">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>  
  
 <span data-ttu-id="9d58b-139">`{RelativeSource PreviousData}`適用於資料範本，或在其中繫結會使用集合做為資料來源的情況下。</span><span class="sxs-lookup"><span data-stu-id="9d58b-139">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="9d58b-140">您可以使用`{RelativeSource PreviousData}`來反白顯示相鄰的資料集合中的項目之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="9d58b-140">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="9d58b-141">還有一個相關的技術，就是在資料來源中的目前和先前項目之間建立 <xref:System.Windows.Data.MultiBinding>，並在該繫結上使用轉換器來判斷這兩個項目及其屬性之間的不同。</span><span class="sxs-lookup"><span data-stu-id="9d58b-141">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>  
  
 <span data-ttu-id="9d58b-142">在下面範例中，項目範本中的第一個 <xref:System.Windows.Controls.TextBlock> 會顯示目前的號碼。</span><span class="sxs-lookup"><span data-stu-id="9d58b-142">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="9d58b-143">第二個<xref:System.Windows.Controls.TextBlock>繫結是<xref:System.Windows.Data.MultiBinding>名義具有兩個<xref:System.Windows.Data.Binding>consistuents： 目前的記錄，以及刻意使用先前的資料記錄所使用的繫結`{RelativeSource PreviousData}`。</span><span class="sxs-lookup"><span data-stu-id="9d58b-143">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> consistuents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="9d58b-144">然後，<xref:System.Windows.Data.MultiBinding> 上的轉換器會計算差異，並將它傳回給繫結。</span><span class="sxs-lookup"><span data-stu-id="9d58b-144">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>  
  
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
  
 <span data-ttu-id="9d58b-145">描述資料繫結，因為未涵蓋的概念，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9d58b-145">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="9d58b-146">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作 XAML 處理器，這個標記延伸的處理由定義<xref:System.Windows.Data.RelativeSource>類別。</span><span class="sxs-lookup"><span data-stu-id="9d58b-146">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>  
  
 <span data-ttu-id="9d58b-147">`RelativeSource` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="9d58b-147">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="9d58b-148">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="9d58b-148">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="9d58b-149">所有標記延伸在 XAML 使用`{`和`}`其屬性的語法，這是的慣例，XAML 處理器會辨識的標記延伸必須處理屬性中的字元。</span><span class="sxs-lookup"><span data-stu-id="9d58b-149">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="9d58b-150">如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="9d58b-150">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d58b-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d58b-151">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="9d58b-152">樣式設定和範本化</span><span class="sxs-lookup"><span data-stu-id="9d58b-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="9d58b-153">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="9d58b-153">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="9d58b-154">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="9d58b-154">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="9d58b-155">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="9d58b-155">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="9d58b-156">繫結宣告概觀</span><span class="sxs-lookup"><span data-stu-id="9d58b-156">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="9d58b-157">x:Type 標記延伸模組</span><span class="sxs-lookup"><span data-stu-id="9d58b-157">x:Type Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
