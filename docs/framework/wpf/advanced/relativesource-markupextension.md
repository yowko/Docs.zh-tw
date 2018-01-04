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
ms.workload: dotnet
ms.openlocfilehash: 6ea5d269c3d455a4fbe3a34dca4335e0d8999d80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="relativesource-markupextension"></a>RelativeSource 標記延伸
指定屬性<xref:System.Windows.Data.RelativeSource>內要使用的繫結來源[繫結標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)，或設定時<xref:System.Windows.Data.Binding.RelativeSource%2A>屬性<xref:System.Windows.Data.Binding>在 XAML 中建立的項目。  
  
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
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`modeEnumValue`|下列其中一項：<br /><br /> -的字串語彙基元`Self`; 對應至<xref:System.Windows.Data.RelativeSource>與建立其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.Self>。<br />-的字串語彙基元`TemplatedParent`; 對應至<xref:System.Windows.Data.RelativeSource>與建立其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>。<br />-的字串語彙基元`PreviousData`; 對應至<xref:System.Windows.Data.RelativeSource>與建立其<xref:System.Windows.Data.RelativeSource.Mode%2A>屬性設定為<xref:System.Windows.Data.RelativeSourceMode.PreviousData>。<br />-請參閱下方的資訊上`FindAncestor`模式。|  
|`FindAncestor`|字串語彙基元 `FindAncestor`。 使用此語彙基元可進入某個模式，讓 `RelativeSource` 指定上階類型以及選擇性指定上階層級。 這相當於 <xref:System.Windows.Data.RelativeSource> 建立時將其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 屬性設為 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>。|  
|`typeName`|`FindAncestor` 模式的必要項。 類型的名稱，可填入 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 屬性。|  
|`intLevel`|`FindAncestor` 模式的選擇項。 上階層級 (朝邏輯樹狀結構的父項目方向評估)。|  
  
## <a name="remarks"></a>備註  
 `{RelativeSource TemplatedParent}`繫結使用方式是一種金鑰的技巧，以解決較大型的控制項的 UI 和控制項的邏輯分隔的概念。 這可讓您從樣板定義內繫結到樣板化父代 (套用該樣板的執行階段物件執行個體)。 此案例中， [TemplateBinding 標記延伸](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)事實上是下列繫結運算式的縮寫： `{Binding RelativeSource={RelativeSource TemplatedParent}}`。 `TemplateBinding`或`{RelativeSource TemplatedParent}`用法都定義的範本，在 XAML 中才相關。 如需詳細資訊，請參閱[TemplateBinding 標記延伸](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)  
  
 `{RelativeSource FindAncestor}`主要用於控制項樣板或可預測的獨立的 UI 組合，其中控制項一律必須是特定上階類型的視覺化樹狀結構中的案例。 例如，項目控制項的項目可能會使用 `FindAncestor` 使用方法以繫結至其項目控制項父代的屬性。 或者，樣板中屬於控制項組合的項目也可以使用 `FindAncestor` 繫結至同一個組合結構中的父代項目。  
  
 在＜XAML 語法＞章節內顯示之 `FindAncestor` 模式的物件項目語法中，第二種物件項目語法特別適用於 `FindAncestor` 模式。 `FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。 您必須設定<xref:System.Windows.Data.RelativeSource.AncestorType%2A>當做屬性使用[X:type 標記延伸](../../../../docs/framework/xaml-services/x-type-markup-extension.md)尋找上階的型別參考。 在執行階段處理繫結要求時，會使用 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。  
  
 對於 `FindAncestor` 模式來說，當該類型在項目樹狀結構中可能存在一個以上的上階時，選擇性屬性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 將有助於釐清上階查閱。  
  
 如需關於如何使用 `FindAncestor` 模式的詳細資訊，請參閱 <xref:System.Windows.Data.RelativeSource>。  
  
 `{RelativeSource Self}`是適用於案例之間這兩個屬性其中一個屬性的執行個體應該相依於相同的執行個體，並沒有一般的相依性屬性的關聯性 （例如強制型轉） 的另一個屬性的值已經存在。 雖然罕見，值會逐字相同 （和具有相同類型） 的兩個屬性存在物件上，您也可以套用`Converter`了的繫結的參數`{RelativeSource Self}`，並使用轉換器來源之間進行轉換和目標類型。 另一個案例`{RelativeSource Self}`一部分<xref:System.Windows.MultiDataTrigger>。  
  
 例如，下面 XAML 會定義 <xref:System.Windows.Shapes.Rectangle> 項目，使得無論為 <xref:System.Windows.FrameworkElement.Width%2A> 輸入的值為何，<xref:System.Windows.Shapes.Rectangle> 永遠都是正方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`  
  
 `{RelativeSource PreviousData}`適用於資料範本，或在其中繫結會使用集合做為資料來源的情況下。 您可以使用`{RelativeSource PreviousData}`來反白顯示相鄰的資料集合中的項目之間的關聯性。 還有一個相關的技術，就是在資料來源中的目前和先前項目之間建立 <xref:System.Windows.Data.MultiBinding>，並在該繫結上使用轉換器來判斷這兩個項目及其屬性之間的不同。  
  
 在下面範例中，項目範本中的第一個 <xref:System.Windows.Controls.TextBlock> 會顯示目前的號碼。 第二個<xref:System.Windows.Controls.TextBlock>繫結是<xref:System.Windows.Data.MultiBinding>名義具有兩個<xref:System.Windows.Data.Binding>consistuents： 目前的記錄，以及刻意使用先前的資料記錄所使用的繫結`{RelativeSource PreviousData}`。 然後，<xref:System.Windows.Data.MultiBinding> 上的轉換器會計算差異，並將它傳回給繫結。  
  
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
  
 描述資料繫結，因為未涵蓋的概念，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作 XAML 處理器，這個標記延伸的處理由定義<xref:System.Windows.Data.RelativeSource>類別。  
  
 `RelativeSource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 所有標記延伸在 XAML 使用`{`和`}`其屬性的語法，這是的慣例，XAML 處理器會辨識的標記延伸必須處理屬性中的字元。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Data.Binding>  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [繫結宣告概觀](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [x:Type 標記延伸模組](../../../../docs/framework/xaml-services/x-type-markup-extension.md)
