---
title: "RelativeSource 標記延伸 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RelativeSource"
helpviewer_keywords: 
  - "RelativeSource 標記延伸"
  - "XAML, RelativeSource 標記延伸"
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# RelativeSource 標記延伸
指定 <xref:System.Windows.Data.RelativeSource> 繫結來源的屬性，以在[繫結標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)內使用，或在設定 XAML 中所建立 <xref:System.Windows.Data.Binding> 項目的 <xref:System.Windows.Data.Binding.RelativeSource%2A> 屬性時使用。  
  
## XAML Attribute Usage  
  
```  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## XAML 屬性使用方式 \(以巢狀方式置於 Binding 延伸內\)  
  
```  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## XAML 物件項目用法  
  
```  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`modeEnumValue`|下列其中一項：<br /><br /> -   字串語彙基元 `Self`；相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode>。<br />-   字串語彙基元 `TemplatedParent`；相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode>。<br />-   字串語彙基元 `PreviousData`；相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode>。<br />-   請參閱下面有關 `FindAncestor` 模式的資訊。|  
|`FindAncestor`|字串語彙基元 `FindAncestor`。  使用此語彙基元可進入某個模式，讓 `RelativeSource` 指定上階類型以及選擇性指定上階層級。  這相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode>。|  
|`typeName`|`FindAncestor` 模式的必要項。  類型的名稱，可填入 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 屬性。|  
|`intLevel`|`FindAncestor` 模式的選擇項。  上階層級 \(朝邏輯樹狀結構的父項目方向評估\)。|  
  
## 備註  
 `{RelativeSource TemplatedParent}` 繫結使用方式是一項重要技術，能夠處理區分控制項 UI 及控制項邏輯的大概念。  這可讓您從樣板定義內繫結到樣板化父代 \(套用該樣板的執行階段物件執行個體\)。  在這種情況下，[TemplateBinding 標記延伸](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)其實是下面繫結運算式的簡寫：`{Binding RelativeSource={RelativeSource TemplatedParent}}`。  `TemplateBinding` 或 `{RelativeSource TemplatedParent}` 使用方式都只在定義樣板的 XAML 中相關。  如需詳細資訊，請參閱 [TemplateBinding 標記延伸](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)。  
  
 `{RelativeSource FindAncestor}` 主要用於控制項樣板或可預測的獨立 UI 組合中，例如像是特定上階類型的視覺化樹狀結構中一律需要控制項的情況。  例如，項目控制項的項目可能會使用 `FindAncestor` 使用方法以繫結至其項目控制項父代的屬性。  或者，樣板中屬於控制項組合的項目也可以使用 `FindAncestor` 繫結至同一個組合結構中的父代項目。  
  
 在＜XAML 語法＞章節內顯示之 `FindAncestor` 模式的物件項目語法中，第二種物件項目語法特別適用於 `FindAncestor` 模式。  `FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。  您必須使用要尋找之上階類型的 [x:Type 標記延伸](../../../../docs/framework/xaml-services/x-type-markup-extension.md)參考，將 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 設為屬性。  在執行階段處理繫結要求時，會使用 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。  
  
 對於 `FindAncestor` 模式來說，當該類型在項目樹狀結構中可能存在一個以上的上階時，選擇性屬性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 將有助於釐清上階查閱。  
  
 如需關於如何使用 `FindAncestor` 模式的詳細資訊，請參閱 <xref:System.Windows.Data.RelativeSource>。  
  
 如果執行個體的其中一個屬性依賴於同一個執行個體另一個屬性的值，且這兩個屬性之間並沒有存在一般性的相依性屬性關係 \(例如強制型轉\)，此時就適合使用 `{RelativeSource Self}`。  雖然物件的兩個屬性很少會有完全一樣的值 \(並且是相同類型\)，但您也可以將 `Converter` 參數套用至含有 `{RelativeSource Self}` 的繫結，並使用轉換器來轉換來源和目標類型。  另一種 `{RelativeSource Self}` 的情況是做為 <xref:System.Windows.MultiDataTrigger> 的一部分。  
  
 例如，下面 XAML 會定義 <xref:System.Windows.Shapes.Rectangle> 項目，使得無論為 <xref:System.Windows.FrameworkElement.Width%2A> 輸入的值為何，<xref:System.Windows.Shapes.Rectangle> 永遠都是正方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}` 適用於資料範本，或者繫結是使用集合做為資料來源的情況。  您可以使用 `{RelativeSource PreviousData}` 反白顯示集合中相鄰資料項目之間的關聯性。  還有一個相關的技術，就是在資料來源中的目前和先前項目之間建立 <xref:System.Windows.Data.MultiBinding>，並在該繫結上使用轉換器來判斷這兩個項目及其屬性之間的不同。  
  
 在下面範例中，項目範本中的第一個 <xref:System.Windows.Controls.TextBlock> 會顯示目前的號碼。  第二個 <xref:System.Windows.Controls.TextBlock> 繫結是 <xref:System.Windows.Data.MultiBinding>，這名義上會有兩個 <xref:System.Windows.Data.Binding> 組成部分：目前的記錄，以及一個特意透過 `{RelativeSource PreviousData}` 使用上一筆資料記錄的繫結。  然後，<xref:System.Windows.Data.MultiBinding> 上的轉換器會計算差異，並將它傳回給繫結。  
  
```  
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
  
 這裡將不說明資料繫結的概念，另請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器實作中，這個標記延伸的處理是由 <xref:System.Windows.Data.RelativeSource> 類別所定義。  
  
 `RelativeSource` 是一種標記延伸。  如果必須將屬性 \(Attribute\) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 \(而不是只對特定類型或屬性 \(Property\) 設定類型轉換子 \(Type Converter\)\)，則通常會實作標記延伸。  所有 XAML 標記延伸都會在其屬性 \(Attribute\) 語法中使用 `{` 與 `}` 字元，這個慣例讓 XAML 處理器知道某個標記延伸必須處理這個屬性 \(Attribute\)。  如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## 請參閱  
 <xref:System.Windows.Data.Binding>   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [繫結宣告概觀](../../../../docs/framework/wpf/data/binding-declarations-overview.md)   
 [x:Type 標記延伸](../../../../docs/framework/xaml-services/x-type-markup-extension.md)