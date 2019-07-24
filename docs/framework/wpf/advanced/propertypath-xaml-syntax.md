---
title: PropertyPath XAML 語法
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: deebdb690a6ba831730701de2608089af2d6bdfd
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401669"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath XAML 語法

物件支援複雜的內嵌[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]語法, 用於設定以<xref:System.Windows.PropertyPath>類型做為其值的各種屬性。 <xref:System.Windows.PropertyPath> 本主題記載適用<xref:System.Windows.PropertyPath>于系結和動畫語法的語法。

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>PropertyPath 的用途

<xref:System.Windows.PropertyPath>是常用於數個[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]功能的物件。 雖然使用一般<xref:System.Windows.PropertyPath>來傳達屬性路徑資訊, <xref:System.Windows.PropertyPath>但作為類型的每個功能區域的使用方式會有所不同。 因此，依功能來說明語法會比較實際。

主要是<xref:System.Windows.PropertyPath>用來描述物件模型路徑, 以便遍歷物件資料來源的屬性, 以及描述目標動畫的目標路徑。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

某些樣式和範本屬性 (例如<xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> ) 會採用表面上類似的<xref:System.Windows.PropertyPath>限定屬性名稱。 但這不是 true <xref:System.Windows.PropertyPath>, 而是由 WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器啟用的*屬性*字串格式用法, 與的類型轉換器<xref:System.Windows.DependencyProperty>結合。

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>資料繫結中物件的 PropertyPath

資料繫結是一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，您可藉以繫結至任何相依性屬性的目標值。 不過，這類資料繫結的來源不需要是相依性屬性；它可以是適用的資料提供者所能辨識的任何屬性類型。 屬性路徑特別用於<xref:System.Windows.Data.ObjectDataProvider>, 後者是用來從通用語言執行時間 (CLR) 物件及其屬性取得系結來源。

請[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]注意, 資料系結不會使用<xref:System.Windows.PropertyPath>, 因為它不會<xref:System.Windows.Data.Binding.Path%2A>使用中<xref:System.Windows.Data.Binding>的。 相反地, 您<xref:System.Windows.Data.Binding.XPath%2A>可以使用, 並在資料的[!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)]中指定有效的 XPath 語法。 <xref:System.Windows.Data.Binding.XPath%2A>也指定為字串, 但此處未記載。請參閱[使用 XMLDataProvider 和 XPath 查詢系結至 XML 資料](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。

若要了解資料繫結中的屬性路徑，關鍵在於您可以將繫結的目標設為個別的屬性值，也可以改為繫結至要取得清單或集合的目標屬性。 如果您要系結集合, 例如<xref:System.Windows.Controls.ListBox>系結會根據集合中有多少資料項目而展開, 則您的屬性路徑應該參考集合物件, 而不是個別的集合專案。 資料系結引擎會自動將當做資料來源使用的集合與系結目標的型別進行比對, 因而產生像是以<xref:System.Windows.Controls.ListBox>專案陣列填入的行為。

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>直接物件上做為資料內容的單一屬性

```xml
<Binding Path="propertyName" .../>
```

*propertyName*必須解析為目前<xref:System.Windows.FrameworkElement.DataContext%2A>中的屬性名稱, 以供<xref:System.Windows.Data.Binding.Path%2A>使用。 如果您的繫結會更新來源，則該屬性必須是讀取/寫入屬性，且來源物件必須是可變動的。

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>直接物件上做為資料內容的單一索引子

```xml
<Binding Path="[key]" .../>
```

`key` 必須是對字典或雜湊表之具類型的索引，或是陣列的整數索引。 此外，索引鍵值的類型必須是可直接繫結至要套用它的屬性。 例如, 包含字串索引鍵和字串值的雜湊表, 可以用這種方式系結至的<xref:System.Windows.Controls.TextBox>文字。 或者，如果索引鍵指向集合或子索引，您可以使用此語法來繫結至目標集合屬性。 否則，您需要透過語法 (例如 `<Binding Path="[key].propertyName" .../>`) 來參考特定的屬性。

您可以視需要指定索引的類型。 如需索引屬性路徑這方面的詳細資訊, 請<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>參閱。

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>多個屬性 (間接屬性目標設定)

```xml
<Binding Path="propertyName.propertyName2" .../>
```

`propertyName`必須解析為目前的屬性<xref:System.Windows.FrameworkElement.DataContext%2A>名稱。 路徑屬性 `propertyName` 和 `propertyName2` 可以是存在於關聯性中的任何屬性，其中 `propertyName2` 是存在於值為 `propertyName` 之類型中的屬性。

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>單一屬性 (附加或類型限定)

```xml
<object property="(ownerType.propertyName)" .../>
```

括弧表示中<xref:System.Windows.PropertyPath>的這個屬性應使用部分限定性來建立。 它可以使用 XML 命名空間來尋找具有適當對應的類型。 透過`ownerType`每個元件中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的<xref:System.Windows.Markup.XmlnsDefinitionAttribute>宣告, 搜尋處理器可以存取的類型。 大部分的應用程式都有對應至 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 命名空間的預設 XML 命名空間，因此，前置詞通常只需用於自訂類型或該命名空間以外的類型。  `propertyName` 必須解析為存在於 `ownerType` 上的屬性名稱。 此語法通常用於下列其中一種情況：

- 指定於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的路徑，其位於不具指定目標類型的樣式或範本中。 除此之外，限定用法通常是無效的，因為在非樣式和非範本的情況中，屬性會存在於執行個體上，而非類型上。

- 屬性是附加屬性。

- 您要繫結至靜態屬性。

若要當做分`propertyName` <xref:System.Windows.DependencyProperty>鏡腳本目標使用, 指定為的屬性必須是。

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>來源周遊 (繫結至集合的階層)

```xml
<object Path="propertyName/propertyNameX" .../>
```

此語法中的 / 是用來在階層式資料來源物件內進行巡覽，並支援含有連續 / 字元之階層的多個步驟。 來源周遊負責目前的記錄指標位置，這是藉由將資料與其檢視的 UI 同步處理來判斷。 如需與階層式資料來源物件繫結的詳細資訊，以及資料繫結中目前記錄指標的概念，請參閱[使用含階層式資料的主從式模式](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)或[資料繫結概觀](../data/data-binding-overview.md)。

> [!NOTE]
> 此語法外表上類似 [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]。 系結[!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] <xref:System.Windows.Data.Binding.Path%2A>至資料來源的 true 運算式不會當做值使用, <xref:System.Windows.Data.Binding.XPath%2A>應該改為用於互斥屬性。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]

### <a name="collection-views"></a>集合檢視

若要參考具名的集合檢視，請在集合檢視名稱前面加上雜湊字元 (`#`)。

### <a name="current-record-pointer"></a>目前的記錄指標

若要參考集合檢視的目前記錄指標或是一對多資料繫結案例，請以正斜線 (`/`) 做為路徑字串的開頭。 任何超過正斜線的路徑，都會從目前的記錄指標開始周遊。

### <a name="multiple-indexers"></a>多個索引子

```xaml
<object Path="[index1,index2...]" .../>
```

或

```xaml
<object Path="propertyName[index,index2...]" .../>
```

如果特定物件支援多個索引子，就可依順序指定那些索引子，類似陣列參考語法。 上述物件可以是目前的內容，或是包含多重索引物件的屬性值。

根據預設，索引子值是使用基礎物件的特性來輸入。 您可以視需要指定索引的類型。 如需輸入索引子的詳細資訊<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>, 請參閱。

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>混合語法

上述語法可穿插使用。 例如, 下列範例會在`ColorGrid`屬性的特定 x、y 上建立色彩的屬性路徑, 其中包含<xref:System.Windows.Media.SolidColorBrush>物件的圖元格線陣列:

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>
```

### <a name="escapes-for-property-path-strings"></a>屬性路徑字串的逸出

對於某些商務物件，您可能會遇到屬性路徑字串需要逸出序列，才能正確剖析的情況。 需要逸出的情況應該相當罕見，因為在通常用來定義商務物件的語言中，這其中許多字元都有類似的命名互動問題。

- 在索引子 ([ ]) 內，插入號字元 (^) 會逸出下一個字元。

- 您必須將專屬於 XML 語言定義的某些字元逸出 (使用 XML 實體)。 使用 `&` 逸出 "&" 字元。 使用 `>` 逸出 ">" 結束標記。

- 您必須將專屬於用來處理標記延伸之 WPF XAML 剖析器行為的字元逸出 (使用反斜線 `\`)。

  - 反斜線 (`\`) 本身就是逸出字元。

  - 等號 (`=`) 會分隔屬性名稱和屬性值。

  - 逗號 (`,`) 會分隔屬性。

  - 右大括號 (`}`) 是標記延伸的結尾。

> [!NOTE]
> 技術上來說，這些逸出也適用於分鏡腳本屬性路徑，但您通常會周遊現有 WPF 物件的物件模型，因此應該不需要逸出。

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>動畫目標的 PropertyPath

動畫的目標屬性必須是接受<xref:System.Windows.Freezable>或基本類型的相依性屬性。 不過，類型上的目標屬性和最終動畫屬性可存在於不同物件上。 對動畫來說，屬性路徑是用來定義具名動畫目標物件的屬性與所需目標動畫屬性之間的關係，方法則是周遊屬性值中的物件-屬性關聯性。

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>動畫的一般物件-屬性考量

如需一般動畫概念的詳細資訊，請參閱[分鏡腳本概觀](../graphics-multimedia/storyboards-overview.md)和[動畫概觀](../graphics-multimedia/animation-overview.md)。

要製作動畫的實值型別或屬性必須<xref:System.Windows.Freezable>是型別或基本型別。 啟動路徑的屬性必須解析為存在於指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>類型上之相依性屬性的名稱。

為了支援複製已<xref:System.Windows.Freezable>凍結的動畫, 所<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>指定的物件必須是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>衍生類別。

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>目標物件上的單一屬性

```xml
<animation Storyboard.TargetProperty="propertyName" .../>
```

`propertyName`必須解析為存在於指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>類型上之相依性屬性的名稱。

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>間接屬性目標

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>
```

`propertyName`必須是實<xref:System.Windows.Freezable>數值型別或基本類型的屬性, 其存在於指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>的類型上。

`propertyName2` 必須是存在於值為 `propertyName` 之物件上的相依性屬性名稱。 換句話說, `propertyName2`必須當做類型`propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>的相依性屬性存在。

由於已套用樣式和範本，因此需要間接設定動畫的目標。 若要以動畫為目標, 您需要目標<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>物件上的, 而且該名稱是由[x:Name](../../xaml-services/x-name-directive.md)或<xref:System.Windows.FrameworkElement.Name%2A>所建立。 雖然範本和樣式元素也可以有名稱，但那些名稱只在樣式和範本的名稱範圍內有效 (如果範本和樣式會與應用程式標記共用名稱範圍，則名稱不能是唯一的。 樣式和範本實際上會在執行個體之間共用，因此會永久保存重複的名稱)。所以，如果您希望顯示為動畫之元素的個別屬性是來自樣式或範本，您就必須從不是來自樣式範本的具名元素執行個體開始，然後將目標設為樣式或範本視覺化樹狀結構中，以到達您要顯示為動畫的屬性。

例如, <xref:System.Windows.Controls.Panel.Background%2A>的屬性<xref:System.Windows.Controls.Panel>是來自主題範本的完整<xref:System.Windows.Media.Brush> (實際上是<xref:System.Windows.Media.SolidColorBrush>)。 若要完全<xref:System.Windows.Media.Brush>建立動畫, 必須是 BrushAnimation (可能是每個<xref:System.Windows.Media.Brush>類型都有一個), 而且沒有這種類型。 若要建立筆刷的動畫, 您可以改為<xref:System.Windows.Media.Brush>建立特定類型之屬性的動畫。 您必須從<xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A>取得,才能在該處套用。<xref:System.Windows.Media.Animation.ColorAnimation> 此範例的屬性路徑就是 `Background.Color`。

<a name="attachedanim"></a>

### <a name="attached-properties"></a>附加屬性

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>
```

括弧表示中<xref:System.Windows.PropertyPath>的這個屬性應使用部分限定性來建立。 它可使用 XML 命名空間來尋找此類型。 透過`ownerType`每個元件中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的<xref:System.Windows.Markup.XmlnsDefinitionAttribute>宣告, 搜尋處理器可以存取的類型。 大部分的應用程式都有對應至 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 命名空間的預設 XML 命名空間，因此，前置詞通常只需用於自訂類型或該命名空間以外的類型。 `propertyName` 必須解析為存在於 `ownerType` 上的屬性名稱。 指定為`propertyName`的屬性必須<xref:System.Windows.DependencyProperty>是。 (所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加屬性都會實作為相依性屬性，因此只有自訂附加屬性才會發生此問題)。

<a name="indexanim"></a>

### <a name="indexers"></a>索引子

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>
```

大部分的相依性<xref:System.Windows.Freezable>屬性或類型都不支援索引子。 因此，若要在動畫路徑中使用索引子，就只能在具名目標上開始鏈結的屬性與最終動畫屬性之間的中繼位置上使用。 在所提供的語法中，就是 `propertyName2`。 例如, 如果中繼屬性是中<xref:System.Windows.Media.TransformGroup> `RenderTransform.Children[1].Angle`的集合 (例如), 則可能需要索引子使用方式。

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>程式碼中的 PropertyPath

的程式碼<xref:System.Windows.PropertyPath>使用方式 (包括如何<xref:System.Windows.PropertyPath>建立) 記載<xref:System.Windows.PropertyPath>于的參考主題。

一般而言, <xref:System.Windows.PropertyPath>設計成使用兩個不同的函式, 一個用於系結使用方式和最簡單的動畫用法, 另一個用於複雜的動畫使用方式。 <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29>將簽章用於系結使用方式, 其中物件為字串。 使用單一步驟動畫路徑的簽章, 其中物件<xref:System.Windows.DependencyProperty>為。 <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> 針對複雜<xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29>的動畫使用簽章。 後面這個建構函式會針對第一個參數使用語彙基元字串，並使用物件陣列來填滿語彙基元字串中的位置，以定義屬性路徑關聯性。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.PropertyPath>
- [資料繫結概觀](../data/data-binding-overview.md)
- [分鏡腳本概觀](../graphics-multimedia/storyboards-overview.md)
