---
title: "PropertyPath XAML 語法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9778094eb098d1e119ef4ef0c25dd022130a11ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath XAML 語法
<xref:System.Windows.PropertyPath>物件支援複雜的內嵌[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設定需要的各種屬性語法<xref:System.Windows.PropertyPath>其值的型別。 此主題記載<xref:System.Windows.PropertyPath>套用至繫結和動畫語法的語法。  
    
  
<a name="where"></a>   
## <a name="where-propertypath-is-used"></a>PropertyPath 的用途  
 <xref:System.Windows.PropertyPath>是一個常見的物件，可用於數種[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]功能。 即使使用一般<xref:System.Windows.PropertyPath>傳達屬性路徑資訊，每個使用方式功能區域其中<xref:System.Windows.PropertyPath>當做型別而改變。 因此，依功能來說明語法會比較實際。  
  
 主要[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用<xref:System.Windows.PropertyPath>來描述物件模型的路徑周遊物件資料來源的屬性，並描述的目標動畫目標路徑。  
  
 某些樣式和範本的屬性，例如<xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType>採取限定的屬性名稱，表面上類似於<xref:System.Windows.PropertyPath>。 但這不是真的<xref:System.Windows.PropertyPath>; 而是它限定*owner.property*字串格式的使用方式啟用 WPF[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器的類型轉換器搭配<xref:System.Windows.DependencyProperty>。  
  
<a name="databinding_s"></a>   
## <a name="propertypath-for-objects-in-data-binding"></a>資料繫結中物件的 PropertyPath  
 資料繫結是一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，您可藉以繫結至任何相依性屬性的目標值。 不過，這類資料繫結的來源不需要是相依性屬性；它可以是適用的資料提供者所能辨識的任何屬性類型。 屬性路徑特別用於<xref:System.Windows.Data.ObjectDataProvider>，它用來取得繫結來源從[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件和其屬性。  
  
 請注意，資料繫結至[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]不會使用<xref:System.Windows.PropertyPath>，因為它不會使用<xref:System.Windows.Data.Binding.Path%2A>中<xref:System.Windows.Data.Binding>。 相反地，您使用<xref:System.Windows.Data.Binding.XPath%2A>並指定有效的 XPath 語法，到[!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)]的資料。 <xref:System.Windows.Data.Binding.XPath%2A>也會指定為字串，但未受記載。請參閱[XMLDataProvider 和 XPath 查詢來使用 XML 資料繫結](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。  
  
 若要了解資料繫結中的屬性路徑，關鍵在於您可以將繫結的目標設為個別的屬性值，也可以改為繫結至要取得清單或集合的目標屬性。 如果您要繫結集合，例如繫結<xref:System.Windows.Controls.ListBox>可根據多少資料項目位於集合中，展開，則屬性路徑應該參考的集合物件、 不是個別的收集項。 資料繫結引擎會比對集合的資料來源繫結目標的類型，自動產生的行為，例如填入做<xref:System.Windows.Controls.ListBox>的項目陣列。  
  
<a name="singlecurrent"></a>   
### <a name="single-property-on-the-immediate-object-as-data-context"></a>直接物件上做為資料內容的單一屬性  
  
```xml  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName*必須解析成是在目前的屬性名稱<xref:System.Windows.FrameworkElement.DataContext%2A>如<xref:System.Windows.Data.Binding.Path%2A>使用量。 如果您的繫結會更新來源，則該屬性必須是讀取/寫入屬性，且來源物件必須是可變動的。  
  
<a name="singleindex"></a>   
### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>直接物件上做為資料內容的單一索引子  
  
```xml  
<Binding Path="[key]" .../>  
```  
  
 `key` 必須是對字典或雜湊表之具類型的索引，或是陣列的整數索引。 此外，索引鍵值的類型必須是可直接繫結至要套用它的屬性。 比方說，包含 string 索引鍵和 string 值的雜湊表可用於這種方式將繫結至文字<xref:System.Windows.Controls.TextBox>。 或者，如果索引鍵指向集合或子索引，您可以使用此語法來繫結至目標集合屬性。 否則，您需要透過語法 (例如 `<Binding Path="[``key``].``propertyName``" .../>`) 來參考特定的屬性。  
  
 您可以視需要指定索引的類型。 如需這方面的索引的屬性路徑的詳細資訊，請參閱<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>。  
  
<a name="multipleindirect"></a>   
### <a name="multiple-property-indirect-property-targeting"></a>多個屬性 (間接屬性目標設定)  
  
```xml  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName`必須是目前屬性的名稱解析<xref:System.Windows.FrameworkElement.DataContext%2A>。 路徑屬性 `propertyName` 和 `propertyName2` 可以是存在於關聯性中的任何屬性，其中 `propertyName2` 是存在於值為 `propertyName` 之類型中的屬性。  
  
<a name="singleattached"></a>   
### <a name="single-property-attached-or-otherwise-type-qualified"></a>單一屬性 (附加或類型限定)  
  
```xml  
<object property="(ownerType.propertyName)" .../>  
```  
  
 括號，表示這個屬性中的<xref:System.Windows.PropertyPath>應該使用部分限定性條件建構。 它可以使用 XML 命名空間來尋找具有適當對應的類型。 `ownerType`搜尋類型[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器可以存取，透過<xref:System.Windows.Markup.XmlnsDefinitionAttribute>每個組件中的宣告。 大部分的應用程式都有對應至 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 命名空間的預設 XML 命名空間，因此，前置詞通常只需用於自訂類型或該命名空間以外的類型。  `propertyName` 必須解析為存在於 `ownerType` 上的屬性名稱。 此語法通常用於下列其中一種情況：  
  
-   指定於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的路徑，其位於不具指定目標類型的樣式或範本中。 除此之外，限定用法通常是無效的，因為在非樣式和非範本的情況中，屬性會存在於執行個體上，而非類型上。  
  
-   屬性是附加屬性。  
  
-   您要繫結至靜態屬性。  
  
 屬性指定為用做分鏡腳本目標，`propertyName`必須<xref:System.Windows.DependencyProperty>。  
  
<a name="sourcetraversal"></a>   
### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>來源周遊 (繫結至集合的階層)  
  
```xml  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 此語法中的 / 是用來在階層式資料來源物件內進行巡覽，並支援含有連續 / 字元之階層的多個步驟。 來源周遊負責目前的記錄指標位置，這是藉由將資料與其檢視的 UI 同步處理來判斷。 如需與階層式資料來源物件繫結的詳細資訊，以及資料繫結中目前記錄指標的概念，請參閱[使用含階層式資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)或[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
> [!NOTE]
>  此語法外表上類似 [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]。 True[!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]運算式繫結至[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料來源不是做為<xref:System.Windows.Data.Binding.Path%2A>值而且應該改為使用互斥<xref:System.Windows.Data.Binding.XPath%2A>屬性。  
  
### <a name="collection-views"></a>集合檢視  
 若要參考具名的集合檢視，請在集合檢視名稱前面加上雜湊字元 (`#`)。  
  
### <a name="current-record-pointer"></a>目前的記錄指標  
 若要參考集合檢視的目前記錄指標或是一對多資料繫結案例，請以正斜線 (`/`) 做為路徑字串的開頭。 任何超過正斜線的路徑，都會從目前的記錄指標開始周遊。  
  
### <a name="multiple-indexers"></a>多個索引子  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 如果特定物件支援多個索引子，就可依順序指定那些索引子，類似陣列參考語法。 上述物件可以是目前的內容，或是包含多重索引物件的屬性值。  
  
 根據預設，索引子值是使用基礎物件的特性來輸入。 您可以視需要指定索引的類型。 如需輸入的索引子的詳細資訊，請參閱<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>。  
  
<a name="mixing"></a>   
### <a name="mixing-syntaxes"></a>混合語法  
 上述語法可穿插使用。 例如，以下是範例會建立在特定的 x、 y 屬性路徑的色彩`ColorGrid`屬性，其中包含的像素格線陣列<xref:System.Windows.Media.SolidColorBrush>物件：  
  
```xml  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### <a name="escapes-for-property-path-strings"></a>屬性路徑字串的逸出  
 對於某些商務物件，您可能會遇到屬性路徑字串需要逸出序列，才能正確剖析的情況。 需要逸出的情況應該相當罕見，因為在通常用來定義商務物件的語言中，這其中許多字元都有類似的命名互動問題。  
  
-   在索引子 ([ ]) 內，插入號字元 (^) 會逸出下一個字元。  
  
-   您必須將專屬於 XML 語言定義的某些字元逸出 (使用 XML 實體)。 使用 `&` 逸出 "&" 字元。 使用 `>` 逸出 ">" 結束標記。  
  
-   您必須將專屬於用來處理標記延伸之 WPF XAML 剖析器行為的字元逸出 (使用反斜線 `\`)。  
  
    -   反斜線 (`\`) 本身就是逸出字元。  
  
    -   等號 (`=`) 會分隔屬性名稱和屬性值。  
  
    -   逗號 (`,`) 會分隔屬性。  
  
    -   右大括號 (`}`) 是標記延伸的結尾。  
  
> [!NOTE]
>  技術上來說，這些逸出也適用於分鏡腳本屬性路徑，但您通常會周遊現有 WPF 物件的物件模型，因此應該不需要逸出。  
  
<a name="databinding_sa"></a>   
## <a name="propertypath-for-animation-targets"></a>動畫目標的 PropertyPath  
 動畫的目標屬性必須是相依性屬性，會接受<xref:System.Windows.Freezable>或基本類型。 不過，類型上的目標屬性和最終動畫屬性可存在於不同物件上。 對動畫來說，屬性路徑是用來定義具名動畫目標物件的屬性與所需目標動畫屬性之間的關係，方法則是周遊屬性值中的物件-屬性關聯性。  
  
<a name="general"></a>   
### <a name="general-object-property-considerations-for-animations"></a>動畫的一般物件-屬性考量  
 如需一般動畫概念的詳細資訊，請參閱[分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)和[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 實值型別或正在顯示動畫之屬性必須是<xref:System.Windows.Freezable>型別或基本型別。 啟動路徑的屬性必須存在於指定的相依性屬性的名稱解析<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>型別。  
  
 若要支援適用於複製<xref:System.Windows.Freezable>，已凍結，所指定的物件<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>必須<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>衍生的類別。  
  
<a name="singlestepanim"></a>   
### <a name="single-property-on-the-target-object"></a>目標物件上的單一屬性  
  
```xml  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName`必須存在於指定的相依性屬性的名稱解析<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>型別。  
  
<a name="indirectanim"></a>   
### <a name="indirect-property-targeting"></a>間接屬性目標  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName`必須是屬性<xref:System.Windows.Freezable>實值型別或基本型別，這存在於指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>型別。  
  
 `propertyName2` 必須是存在於值為 `propertyName` 之物件上的相依性屬性名稱。 換句話說，`propertyName2`為相依性屬性的型別上必須存在`propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>。  
  
 由於已套用樣式和範本，因此需要間接設定動畫的目標。 若要以動畫為目標，您需要<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>目標物件，而且該名稱藉由[X:name](../../../../docs/framework/xaml-services/x-name-directive.md)或<xref:System.Windows.FrameworkElement.Name%2A>。 雖然範本和樣式元素也可以有名稱，但那些名稱只在樣式和範本的名稱範圍內有效 (如果範本和樣式會與應用程式標記共用名稱範圍，則名稱不能是唯一的。 樣式和範本實際上會在執行個體之間共用，因此會永久保存重複的名稱)。所以，如果您希望顯示為動畫之元素的個別屬性是來自樣式或範本，您就必須從不是來自樣式範本的具名元素執行個體開始，然後將目標設為樣式或範本視覺化樹狀結構中，以到達您要顯示為動畫的屬性。  
  
 比方說，<xref:System.Windows.Controls.Panel.Background%2A>屬性<xref:System.Windows.Controls.Panel>完成<xref:System.Windows.Media.Brush>(實際上<xref:System.Windows.Media.SolidColorBrush>)，來自佈景主題範本。 要製作動畫<xref:System.Windows.Media.Brush>完全，那里不需要是 BrushAnimation (可能是一個用於每個<xref:System.Windows.Media.Brush>類型) 並沒有這類的型別。 若要製作動畫的筆刷，您改為以動畫顯示的特定屬性<xref:System.Windows.Media.Brush>型別。 您必須向<xref:System.Windows.Media.SolidColorBrush>至其<xref:System.Windows.Media.SolidColorBrush.Color%2A>套用<xref:System.Windows.Media.Animation.ColorAnimation>那里。 此範例的屬性路徑就是 `Background.Color`。  
  
<a name="attachedanim"></a>   
### <a name="attached-properties"></a>附加屬性  
  
```xml  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 括號，表示這個屬性中的<xref:System.Windows.PropertyPath>應該使用部分限定性條件建構。 它可使用 XML 命名空間來尋找此類型。 `ownerType`搜尋類型[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器可以存取，透過<xref:System.Windows.Markup.XmlnsDefinitionAttribute>每個組件中的宣告。 大部分的應用程式都有對應至 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 命名空間的預設 XML 命名空間，因此，前置詞通常只需用於自訂類型或該命名空間以外的類型。 `propertyName` 必須解析為存在於 `ownerType` 上的屬性名稱。 指定為`propertyName`必須<xref:System.Windows.DependencyProperty>。 (所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加屬性都會實作為相依性屬性，因此只有自訂附加屬性才會發生此問題)。  
  
<a name="indexanim"></a>   
### <a name="indexers"></a>索引子  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 大多數相依性屬性或<xref:System.Windows.Freezable>類型不支援索引子。 因此，若要在動畫路徑中使用索引子，就只能在具名目標上開始鏈結的屬性與最終動畫屬性之間的中繼位置上使用。 在所提供的語法中，就是 `propertyName2`。 比方說，可能需要如果中繼屬性是例如集合索引子使用<xref:System.Windows.Media.TransformGroup>，例如屬性之路徑中`RenderTransform.Children[1].Angle`。  
  
<a name="ppincode"></a>   
## <a name="propertypath-in-code"></a>程式碼中的 PropertyPath  
 程式碼的使用方式<xref:System.Windows.PropertyPath>，包括如何建構<xref:System.Windows.PropertyPath>中的參考主題會說明<xref:System.Windows.PropertyPath>。  
  
 一般情況下，<xref:System.Windows.PropertyPath>設計為使用兩個不同的建構函式，一種用於繫結使用方式和最簡單的動畫用法，一個用於複雜的動畫使用方式。 使用<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29>簽章的繫結使用方式，其中的物件字串。 使用<xref:System.Windows.PropertyPath.%23ctor%28System.Object%29>單一步驟動畫的路徑，且物件的簽章<xref:System.Windows.DependencyProperty>。 使用<xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29>簽章的複雜的動畫。 後面這個建構函式會針對第一個參數使用語彙基元字串，並使用物件陣列來填滿語彙基元字串中的位置，以定義屬性路徑關聯性。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.PropertyPath>  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
