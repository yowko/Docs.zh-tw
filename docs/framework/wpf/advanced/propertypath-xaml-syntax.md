---
title: "PropertyPath XAML 語法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PropertyPath 物件"
  - "XAML, PropertyPath 物件"
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# PropertyPath XAML 語法
<xref:System.Windows.PropertyPath> 物件支援複雜的內嵌 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法，以設定接受 <xref:System.Windows.PropertyPath> 型別做為其值的各種屬性。  本主題說明當做繫結和動畫語法使用時的 <xref:System.Windows.PropertyPath> 語法。  
  
   
  
<a name="where"></a>   
## PropertyPath 的用途  
 <xref:System.Windows.PropertyPath> 是在幾項 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 功能中使用的通用物件。  雖然通用 <xref:System.Windows.PropertyPath> 是用來傳遞屬性路徑資訊，但其在使用 <xref:System.Windows.PropertyPath> 做為型別的每項功能區域都有不同的用途。  因此，依功能來說明語法會比較實際。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 主要使用 <xref:System.Windows.PropertyPath> 描述周遊物件資料來源屬性的物件模型路徑，以及描述目標動畫的目標路徑。  
  
 部分樣式和樣板屬性 \(例如 <xref:System.Windows.Setter.Property%2A?displayProperty=fullName>\) 接受表面上類似 <xref:System.Windows.PropertyPath> 的完整屬性名稱。  但這不是真正的 <xref:System.Windows.PropertyPath>，而是限定的 *owner.property* 字串格式用法，由 WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器加上 <xref:System.Windows.DependencyProperty> 之型別轉換子的組合所啟用。  
  
<a name="databinding_s"></a>   
## 資料繫結中物件的 PropertyPath  
 資料繫結是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的一項功能，您可以藉此繫結至任何[相依性屬性](GTMT)的目標值。  不過，這類資料繫結的來源不一定要是[相依性屬性](GTMT)，它可以是所用資料提供者能辨識的任何屬性型別 \(Property Type\)。  屬性路徑專供 <xref:System.Windows.Data.ObjectDataProvider> 使用。後者可用於由 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件及其屬性取得繫結來源。  
  
 請注意，[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 的資料繫結不使用 <xref:System.Windows.PropertyPath>，因為它在 <xref:System.Windows.Data.Binding> 中不使用 <xref:System.Windows.Data.Binding.Path%2A>。  您會改用 <xref:System.Windows.Data.Binding.XPath%2A>，並指定有效的 XPath 語法至資料的 [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)]。  <xref:System.Windows.Data.Binding.XPath%2A> 也被指定為字串，但是在此沒有說明，請參閱 [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。  
  
 要了解資料繫結中的屬性路徑，關鍵在於您可以將繫結的目標設為個別屬性值，也可以改為繫結至接受清單或集合的目標屬性。  如果您要繫結集合，例如，繫結一個會因為集合中項目數量而擴充的 <xref:System.Windows.Controls.ListBox>，那麼屬性路徑應該參照集合物件，而不是個別的集合項目。  資料繫結引擎會自動將做為資料來源的集合與繫結目標類型進行比對，而最後產生的行為會像是以項目陣列填入 <xref:System.Windows.Controls.ListBox>。  
  
<a name="singlecurrent"></a>   
### 直接物件上的單一屬性做為資料內容  
  
```  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName* 必須解析為目前 <xref:System.Windows.FrameworkElement.DataContext%2A> 中的屬性名稱，才能當做 <xref:System.Windows.Data.Binding.Path%2A> 使用。  如果繫結更新來源，則該屬性必須是讀取\/寫入屬性，且來源物件必須是可變動的。  
  
<a name="singleindex"></a>   
### 直接物件上的單一索引子做為資料內容  
  
```  
<Binding Path="[key]" .../>  
```  
  
 `key` 必須是字典或雜湊資料表的型別索引，或是陣列的整數索引。  此外，索引鍵值的型別必須可直接繫結至套用它的屬性。  例如，包含字串索引鍵和字串值的雜湊資料表就能以這種方式使用，來繫結至 <xref:System.Windows.Controls.TextBox> 的文字。  或者，如果索引鍵指向集合或子索引，您可以使用此語法來繫結至目標集合屬性。  否則，您就必須透過像是 `<Binding Path="[``key``].``propertyName``" .../>` 這樣的語法來參考特定屬性。  
  
 您可以視需要指定索引的型別。  如需索引屬性路徑在這方面的詳細資訊，請參閱 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName>。  
  
<a name="multipleindirect"></a>   
### 多重屬性 \(間接屬性目標設定\)  
  
```  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` 必須解析為是目前 <xref:System.Windows.FrameworkElement.DataContext%2A> 的屬性名稱。  路徑屬性 `propertyName` 和 `propertyName2` 可以是存在於關聯性中的任何屬性，其中 `propertyName2` 是存在於表示為 `propertyName` 值的型別上的屬性。  
  
<a name="singleattached"></a>   
### 單一屬性，不是符加就是型別限定的  
  
```  
<object property="(ownerType.propertyName)" .../>  
```  
  
 括號表示 <xref:System.Windows.PropertyPath> 中的這個屬性應使用部分限定建構。  它可以使用 XML 命名空間來尋找具有適當對應的型別。  `ownerType` 會透過每個組件中的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 宣告，搜尋 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器可存取的型別。  大多數的應用程式都有預設 XML 命名空間對應至 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 命名空間，所以前置詞通常只對自訂型別或是該命名空間外部的型別才有必要。  `propertyName` 必須解析為存在於 `ownerType` 之上的屬性名稱。  此語法通常用於下列其中一種情況：  
  
-   路徑在樣式或樣板中的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 指定，但該樣式或樣板沒有指定的目標型別。  除此之外，限定用法一般無效，因為在非樣式和非樣板的情況中，屬性會存在於執行個體上，而非型別上。  
  
-   屬性是附加屬性。  
  
-   您繫結至靜態屬性。  
  
 若要當做腳本目標使用，指定為 `propertyName` 的屬性必須是 <xref:System.Windows.DependencyProperty>。  
  
<a name="sourcetraversal"></a>   
### 來源周遊 \(繫結至集合的階層架構\)  
  
```  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 此語法中的 \/ 是用來在階層式資料來源物件巡覽，而且支援使用連續的 \/ 字元表示到階層架構的多個步驟。  來源周遊負責目前記錄指標位置，這是藉由將資料與其檢視的 UI 同步處理來判斷。  如需與階層式資料來源物件繫結的詳細資訊，以及資料繫結中的目前記錄指標的概念，請參閱 [使用含階層式資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)或[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
> [!NOTE]
>  表面上來看，此語法類似 [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]。  但繫結至 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料來源的真正 [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] 運算式不會當做 <xref:System.Windows.Data.Binding.Path%2A> 值使用，而應該用於互斥 \(Mutually Exclusive\) 的 <xref:System.Windows.Data.Binding.XPath%2A> 屬性。  
  
### 集合檢視  
 若要參考具名的集合檢視，請以雜湊字元 \(`#`\) 前置在集合檢視名稱之前。  
  
### 目前的記錄指標  
 若要參考集合檢視的目前記錄指標，或是主要版面詳細資料繫結案例，請以正斜線 \(`/`\) 開始路徑字串。  超出正斜線的任何路徑，都會從目前的記錄指標開始周遊。  
  
### 多個索引子  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 如果特定物件支援多個索引子，這些索引子可依順序指定，類似於陣列參考語法。  此物件可以是目前內容或包含多重索引物件之屬性的值。  
  
 根據預設，索引子值會使用基礎物件的特性設定型別。  您可以視需要指定索引的型別。  如需設定索引子型別的詳細資訊，請參閱 <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName>。  
  
<a name="mixing"></a>   
### 混合語法  
 上述語法可穿插使用。  例如，下列範例會建立屬性路徑指向位於 `ColorGrid` 屬性特定 x,y 的色彩，而該屬性包含 <xref:System.Windows.Media.SolidColorBrush> 物件的像素格線陣列：  
  
```  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### 屬性路徑字串的逸出  
 對於某些商務物件，您可能會遇到屬性路徑字串需要逸出序列，才能正確剖析的情況。  需要逸出的情況應該相當罕見，因為在通常會用來定義商務物件的語言中，許多這些字元都有相似的命名互動問題。  
  
-   在索引子 \(\[ \]\) 內，插入號 \(Caret\) 字元 \(^\) 會逸出下一個子元。  
  
-   您必須將 XML 語言定義的某些特殊字元逸出 \(使用 XML 實體\)。  使用 `&` 逸出 "&" 字元。  使用 `>` 逸出 "\>" 結束標記。  
  
-   您必須將特殊於處理標記延伸之 WPF XAML 剖析器行為的字元逸出 \(使用反斜線 `\`\)。  
  
    -   反斜線 \(`\`\) 本身是逸出字元。  
  
    -   等號 \(`=`\) 會分隔屬性名稱和屬性值。  
  
    -   逗號 \(`,`\) 分隔屬性。  
  
    -   右大括號 \(`}`\) 是標記延伸的結尾。  
  
> [!NOTE]
>  技術上，這些逸出也對腳本屬性路徑有效，但您通常會周遊現有 WPF 物件的物件模型，因此應該不需要逸出。  
  
<a name="databinding_sa"></a>   
## 動畫目標的 PropertyPath  
 動畫的目標屬性必須是接受 <xref:System.Windows.Freezable> 或基本型別 \(Primitive Type\) 的[相依性屬性](GTMT)。  不過，型別上的目標屬性和最後的動畫屬性可存在於不同的物件上。  對動畫來說，屬性路徑是用來定義具名動畫目標物件的屬性與所要目標動畫屬性之間的關係，它會周遊屬性值中的物件\-屬性關聯性。  
  
<a name="general"></a>   
### 動畫的一般物件\-屬性考量  
 如需一般動畫概念的詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)和[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 要顯示為動畫的實值型別或屬性必須是 <xref:System.Windows.Freezable> 型別或基本型別。  開始路徑的屬性必須解析為存在於所指定 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 型別上的[相依性屬性](GTMT)名稱。  
  
 為支援複製來將已凍結的 <xref:System.Windows.Freezable> 顯示為動畫，<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 指定的物件必須是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 衍生類別 \(Derived Class\)。  
  
<a name="singlestepanim"></a>   
### 目標物件上的單一屬性  
  
```  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` 必須解析為存在於所指定 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 型別上的[相依性屬性](GTMT)名稱。  
  
<a name="indirectanim"></a>   
### 間接屬性目標設定  
  
```  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` 必須是屬於 <xref:System.Windows.Freezable> 實值型別或基本型別的屬性，且存在於所指定的 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 型別上。  
  
 `propertyName2` 必須是存在於型別為 `propertyName` 的物件上的[相依性屬性](GTMT)名稱。  換句話說，`propertyName2` 必須是 `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A> 型別上的相依性屬性。  
  
 由於套用樣式和範本，因此需要間接設定動畫的目標。  要設定動畫的目標，您需要目標物件上的 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>，而且該名稱是以 [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) 或 <xref:System.Windows.FrameworkElement.Name%2A>. 建立的。  雖然樣板和樣式項目也可以有名稱，但這些名稱只在樣式和樣板的名稱範圍內有效  \(如果樣板和樣式與應用程式標記共用名稱範圍，則名稱不能是唯一的。  樣式和樣板基本上就是在執行個體之間共用，因此會保存重複的名稱\)。 因此，如果要顯示為動畫的項目個別屬性來自於樣式或樣板，您就必須從不是來自於樣式樣板的具名項目執行個體開始，然後將目標設為樣式或樣板視覺化樹狀結構中，以到達您要顯示為動畫的屬性。  
  
 例如，<xref:System.Windows.Controls.Panel> 的 <xref:System.Windows.Controls.Panel.Background%2A> 屬性是來自於主題樣板的完整 <xref:System.Windows.Media.Brush> \(實際上是 <xref:System.Windows.Media.SolidColorBrush>\)。  若要將 <xref:System.Windows.Media.Brush> 完整顯示為動畫，就必須有 BrushAnimation \(可能每個 <xref:System.Windows.Media.Brush> 型別一個\)，但並沒有這種型別。  若要將 Brush 顯示為動畫，就要改為顯示特定 <xref:System.Windows.Media.Brush> 型別的屬性。  您必須從 <xref:System.Windows.Media.SolidColorBrush> 取得它的 <xref:System.Windows.Media.SolidColorBrush.Color%2A>，以在該處套用 <xref:System.Windows.Media.Animation.ColorAnimation>。  這個範例的屬性路徑就是 `Background.Color`。  
  
<a name="attachedanim"></a>   
### 附加屬性  
  
```  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 括號表示 <xref:System.Windows.PropertyPath> 中的這個屬性應使用部分限定建構。  它可以使用 XML 命名空間尋找型別。  `ownerType` 會透過每個組件中的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 宣告，搜尋 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器可存取的型別。  大多數的應用程式都有預設 XML 命名空間對應至 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 命名空間，所以前置詞通常只對自訂型別或是該命名空間外部的型別才有必要。  `propertyName` 必須解析為存在於 `ownerType` 之上的屬性名稱。  指定為 `propertyName` 的屬性必須是 <xref:System.Windows.DependencyProperty> \(所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加屬性都會實作為相依性屬性，因此只有自訂附加屬性才有此問題\)。  
  
<a name="indexanim"></a>   
### 索引子  
  
```  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 大多數相依性屬性或 <xref:System.Windows.Freezable> 型別並不支援索引子。  因此，要在動畫路徑中使用索引子，就只能在具名目標上開始鏈結的屬性與最後動畫屬性之間的中繼位置使用。  在上面的語法中，就是 `propertyName2`。  例如，如果中繼屬性是集合 \(例如 <xref:System.Windows.Media.TransformGroup>\)、在像是 `RenderTransform.Children[1].Angle` 的屬性路徑中，就可能需要用到索引子。  
  
<a name="ppincode"></a>   
## 程式碼中的 PropertyPath  
 <xref:System.Windows.PropertyPath> 的程式碼使用方式，包括如何建構 <xref:System.Windows.PropertyPath>，在 <xref:System.Windows.PropertyPath> 的參考主題中有詳細說明。  
  
 一般來說，<xref:System.Windows.PropertyPath> 是設計來使用兩種不同的建構函式，一是用於繫結和最簡單的動畫，另一則是用於複雜動畫。  <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> 簽章可用於其中物件是字串的繫結。  <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> 簽章也可用於其中物件是 <xref:System.Windows.DependencyProperty> 的單一步驟動畫路徑。  [PropertyPath\(String, Object\<xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> 簽章則可用於複雜動畫。  後面這個建構函式會在第一個參數使用語彙基元字串，並使用物件陣列填滿語彙基元字串中的位置，以定義屬性路徑關聯性。  
  
## 請參閱  
 <xref:System.Windows.PropertyPath>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)