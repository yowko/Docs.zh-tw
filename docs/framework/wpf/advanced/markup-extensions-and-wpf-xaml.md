---
title: "標記延伸和 WPF XAML | Microsoft Docs"
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
  - "*Extension 類別"
  - "繫結標記延伸"
  - "大括號字元"
  - "字元, 大括號"
  - "類別, MarkupExtension"
  - "大括號字元 ({})"
  - "DynamicResource 標記延伸"
  - "常值大括號字元 ({})"
  - "標記延伸"
  - "MarkupExtension 類別"
  - "巢狀延伸語法"
  - "RelativeSource 標記延伸"
  - "StaticResource 標記延伸"
  - "TemplateBinding 標記延伸"
  - "XAML, 標記延伸"
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 標記延伸和 WPF XAML
本主題介紹 XAML 標記延伸的概念，包括其語法規則、目的以及類別物件模型基礎。  標記延伸是 XAML 語言和 .NET XAML 服務實作的一般功能。  本主題專門說明在 WPF XAML 中使用的標記延伸。  
  
   
  
<a name="XAML_Processors_and_Markup_Extensions"></a>   
## XAML 處理器和標記延伸  
 一般而言，XAML 剖析器能夠解譯常值字串形式的屬性值 \(只要該常值字串可以轉換為基本型別\)，或是以某種方式將屬性值轉換成物件。  其中一種方式便是參考型別轉換子，[TypeConverter 和 XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md) 主題中有其說明。  不過，在某些情境下需要不同的行為。  例如，您可以指示 XAML 處理器，不應讓物件圖形因為屬性的值而產生新物件，  而是應該讓物件圖形參考已在圖形另一個部分建構的物件，或是靜態物件。  另一個情境則是，您可以指示 XAML 處理器使用為物件之建構函式提供非預設引數的語法。這些都是標記延伸可派上用場的幾種情境。  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## 基本標記延伸語法  
 實作標記延伸可以為屬性 \(Attribute\) 使用方式中的屬性 \(Property\)、屬性 \(Property\) 項目使用方式中的屬性 \(Property\) 或兩者提供值。  
  
 當用來提供屬性 \(Attribute\) 值時，XAML 處理器會根據存在的左右大括號 \({ 和 }\) 來判斷這是標記延伸序列的語法。  標記延伸的型別則是由緊接在右側大括號後面的字串語彙基元 \(Token\)。  
  
 當用在屬性 \(Property\) 項目語法中時，標記延伸在視覺上與用來提供屬性 \(Property\) 項目值的其他任何項目相同：一個會參考標記延伸類別做為項目的 XAML 項目宣告，前後以角括弧 \(\<\>\) 括住。  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## XAML 定義標記延伸  
 有幾個標記延伸不是 XAML 的 WPF 實作專用的標記延伸，而是 XAML 語言的內建函式或功能實作。  這類標記延伸是實作在 System.Xaml 組件中，做為一般 .NET Framework XAML 服務的一部分，並位於 XAML 語言 XAML 命名空間內。  從一般常見標記用法的觀點來看，這些標記延伸通常可透過用法中的 `x:` 前置字元加以識別。  所有標記延伸都應遵循 <xref:System.Windows.Markup.MarkupExtension> 基底類別 \(同樣定義於 System.Xaml 中\) 所提供的模式，才能在 XAML 讀取器和 XAML 寫入器 \(包含在 WPF XAML 中\) 中受到支援。  
  
-   `x:Type` 會提供具名型別的 <xref:System.Type> 物件。  這是樣式和樣板中最常使用的機能。  如需詳細資訊，請參閱 [x:Type 標記延伸](../../../../docs/framework/xaml-services/x-type-markup-extension.md)。  
  
-   `x:Static` 會產生靜態值。  這些值來自實值型別程式碼實體，而這些實體本身不是目標屬性值型別，但卻可評估為該型別。  如需詳細資訊，請參閱 [x:Static 標記延伸](../../../../docs/framework/xaml-services/x-static-markup-extension.md)。  
  
-   `x:Null` 會將屬性 \(Property\) 的值指定為 `null`，而且可用於屬性 \(Attribute\) 或屬性 \(Property\) 項目值。  如需詳細資訊，請參閱 [x:Null 標記延伸](../../../../docs/framework/xaml-services/x-null-markup-extension.md)。  
  
-   `x:Array` 可提供使用 XAML 語法來建立一般陣列的支援 \(若刻意不要使用 WPF 基底項目和控制項模型提供的集合支援\)。  如需詳細資訊，請參閱 [x:Array 標記延伸](../../../../docs/framework/xaml-services/x-array-markup-extension.md)。  
  
> [!NOTE]
>  `x:` 前置詞可在 XAML 檔案或產物的根項目中，用於 XAML 語言內建函式的一般 XAML 命名空間對應。  例如，適用於 WPF 應用程式的 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 範本，便會使用這種 `x:` 對應啟始 XAML 檔案。  您可以在自己的 XAML 命名空間對應中選擇不同的前置字元語彙基元，但是這份文件會以預設的 `x:` 對應，識別 XAML 語言的 XAML 命名空間 \(而不是 WPF 預設命名空間或其他與特定架構無關的 XAML 命名空間\) 中已定義的實體部分。  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## WPF 專用標記延伸  
 WPF 程式設計中最常使用的標記延伸是支援資源參考 \(`StaticResource` 和 `DynamicResource`\) 的標記延伸，以及支援資料繫結 \(`Binding`\) 的標記延伸。  
  
-   `StaticResource` 提供屬性值的方式，是直接替換成所定義資源的值。  `StaticResource` 值的評估作業最終是在 XAML 載入階段進行，而且無法在執行階段存取物件圖形。如需詳細資訊，請參閱 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
-   `DynamicResource` 提供屬性值的方式，是採用資源參考的方式將該值延後到執行階段才評估。  動態資源參考可在每次存取這類資源時強制執行新的查詢作業，而且可在執行階段存取物件圖形。  為了取得此存取權，WPF 屬性系統中的相依性屬性以及評估運算式都會支援 `DynamicResource` 概念。  因此，您只能將 `DynamicResource` 用於相依性屬性目標。  如需詳細資訊，請參閱 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。  
  
-   `Binding` 會在執行階段使用適用於父物件的資料內容，提供屬性的資料繫結值。  這個標記延伸相當複雜，因為它會啟用用來指定資料繫結的基本內嵌語法。  如需詳細資訊，請參閱[繫結標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)。  
  
-   `RelativeSource` 提供 <xref:System.Windows.Data.Binding> 的來源資訊，可以巡覽執行階段物件樹狀結構中數種可能的關聯性。  如此即使未能完全了解周圍的物件樹狀結構，也可以針對在多次使用樣板中建立的繫結，或是在程式碼中建立的繫結，提供特製化來源。  如需詳細資訊，請參閱 [RelativeSource 標記延伸](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)。  
  
-   `TemplateBinding` 可讓控制項樣板使用樣板化屬性的值，而這些樣板化屬性是來自將要使用此樣板之類別的物件模型定義屬性。  換句話說，樣板定義中的屬性可以存取只有在套用樣板時才存在的內容。  如需詳細資訊，請參閱 [TemplateBinding 標記延伸](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)。  如需實際使用 `TemplateBinding` 的詳細資訊，請參閱[使用 ControlTemplates 設定樣式範例](http://go.microsoft.com/fwlink/?LinkID=160041) \(英文\)。  
  
-   `ColorConvertedBitmap` 支援相當進階的影像處理情節。  如需詳細資訊，請參閱 [ColorConvertedBitmap 標記延伸](../../../../docs/framework/wpf/advanced/colorconvertedbitmap-markup-extension.md)。  
  
-   `ComponentResourceKey` 和 `ThemeDictionary` 支援的是資源查閱面，尤其是以自訂控制項包住的資源和佈景主題。  如需詳細資訊，請參閱[ComponentResourceKey 標記延伸](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)、[ThemeDictionary 標記延伸](../../../../docs/framework/wpf/advanced/themedictionary-markup-extension.md) 或 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
<a name="StarExtension"></a>   
## \*Extension 類別  
 對於一般 XAML 語言和 WPF 專用的標記延伸，每個標記延伸的行為都是透過衍生自 <xref:System.Windows.Markup.MarkupExtension> 而且提供 <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A> 方法實作的 `*Extension` 類別，讓 XAML 處理器識別。  各個延伸項目上的這個方法，都會提供在評估標記延伸時傳回的物件。  傳回的物件通常是根據傳遞至標記延伸的各種字串語彙基元來受到評估。  
  
 例如，<xref:System.Windows.StaticResourceExtension> 類別可提供實際資源查詢的介面實作，使其 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> 實作能夠使用該特定實作的輸入做為依據其 `x:Key` 查詢資源的字串，以傳回要求的物件。  如果您使用的是現有的標記延伸，這項實作詳細資料大多無關緊要。  
  
 有些標記延伸不使用字串語彙基元引數。  這是因為它們傳回靜態或一致的值，或是因為應傳回值的內容可以透過 `serviceProvider` 參數傳遞的服務之一而取得。  
  
 採用 `*Extension` 命名樣式的用意是為了求方便和一致，  倒不一定是為了讓 XAML 處理器將該類別識別為標記延伸的支援。  只要您的程式碼基底包含 System.Xaml 並使用 .NET Framework XAML 服務實作，要被認做 XAML 標記延伸，所要做的就是從 <xref:System.Windows.Markup.MarkupExtension> 衍生並支援建構語法。  WPF 即定義了可支援標記延伸，但未遵循 `*Extension` 命名樣式的類別，例如 <xref:System.Windows.Data.Binding>。  以上的常見原因是該類別支援的案例不只是純標記延伸支援。  在 <xref:System.Windows.Data.Binding> 的例子中，該類別支援在與 XAML 完全無關的情形下，於執行階段存取物件的方法和屬性。  
  
### 延伸類別對於初始設定文字的解譯  
 XAML 處理器會使用下列其中一種方法，解譯位於標記延伸名稱後面且尚在括號內的字串語彙基元：  
  
-   逗號一律代表個別語彙基元的分隔字元或分隔符號 \(Delimiter\)。  
  
-   如果個別的分隔語彙基元沒有包含任何等號，每個語彙基元都會被視為建構函式引數。  每個建構函式參數都必須依照該簽章所預期的適當順序，以該簽章預期的型別來提供。  
  
    > [!NOTE]
    >  XAML 處理器必須呼叫符合成對數目之引數計數的建構函式。  因此，如果您在實作自訂標記延伸，請不要提供多個具有相同引數計數的參數。  雖然目前並未定義當有一個以上標記延伸建構函式路徑具有相同的參數數目時 XAML 處理器的行為，但您應該預期當標記延伸型別定義中存在這種狀況時，XAML 處理器要能夠擲回用法例外狀況。  
  
-   如果個別的分隔語彙基元包含等號，則 XAML 處理器會先呼叫標記延伸的預設建構函式。  接著再將每個 name\=value 的配對解譯成存在於標記延伸中的屬性名稱，以及要指派給該屬性的值。  
  
-   如果標記延伸中的建構函式行為和屬性設定行為之間有對等的結果，則不論您使用哪種行為都沒有關係。  比較常見的用法是在具有一個以上可設定屬性的標記延伸中使用 *property*`=`*value* 配對，這純粹是因為它可讓您的標記更符合目的，而且不慎調換建構函式參數的可能性也較低   \(當您指定 property\=value 配對時，這些屬性可以是任何順序\)。 此外，標記延伸也不一定會提供用來設定每個可設定屬性的建構函式參數。  例如，<xref:System.Windows.Data.Binding> 是標記延伸，其具有許多可透過 *property*`=`*value* 格式的延伸項目來設定的屬性，但 <xref:System.Windows.Data.Binding> 只支援兩個建構函式：一個是預設建構函式，另一個是用於設定初始路徑的建構函式。  
  
-   常值逗號不能沒加上逸出符號就傳遞至標記延伸。  
  
<a name="EscapeSequences"></a>   
## 逸出序列和標記延伸  
 XAML 處理器中處理屬性 \(Attribute\) 時，會使用大括號來表示標記延伸。  如果必要，也可以使用一組空白大括號後接常值大括號來輸入逸出序列 \(Escape Sequence\)，以便產生常值大括號字元屬性值。  請參閱 [{} 逸出序列 \/ 標記延伸](../../../../docs/framework/xaml-services/escape-sequence-markup-extension.md)。  
  
<a name="Nesting"></a>   
## XAML 用法中的標記延伸巢狀結構  
 此系統支援多重標記延伸的巢狀結構，而且每個標記延伸都會先進行最深層的評估。  例如，假設有下列用法：  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
  
```  
  
 在此用法中，會先評估 `x:Static` 陳述式並傳回字串。  接著將該字串當做 `DynamicResource` 的引數。  
  
## 標記延伸和屬性項目語法  
 標記延伸類別做為填入屬性項目值的物件項目使用時，在視覺上與可用於 XAML 之中的一般型別支援物件項目並無任何分別。  一般物件項目和標記延伸之間的實際差異在於，標記延伸會評估為型別值，或是會採取運算式的形式以延後評估。  因此對於標記延伸而言，找出屬性值可能有的任何型別錯誤時使用的機制會不同，類似其他程式設計模型中處理晚期繫結屬性的方式。  一般的物件項目在剖析 XAML 時，則會評估正在設定的目標屬性是否符合型別。  
  
 在物件項目語法中用來填入屬性 \(Property\) 項目的標記延伸，多半不需包含內容或任何進一步的屬性項目語法。  因此您可以結束物件項目標記，而不提供任何子項目。  每當 XAML 處理器遇到任何物件項目時，都會呼叫該類別的建構函式，以具現化從剖析項目建立的物件。  標記延伸類別也一樣：如果您想要在物件項目語法中使用自己的標記延伸，則必須提供預設建構函式。  某些現有的標記延伸會有至少一個必要屬性 \(Property\) 值，您必須指定這個屬性值才能有效進行初始設定。  如果是這種情況，該屬性值通常會指定成物件項目上屬性 \(Property\) 的屬性 \(Attribute\)。  在 [XAML 命名空間 \(x:\) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)和 [WPF XAML 擴充功能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)參考頁面上，都會特別註明具有必要屬性 \(以及必要屬性之名稱\) 的標記延伸。  參考頁面也會註明特定標記延伸是否不允許物件項目語法或屬性語法。  其中一個值得注意的案例是 [x:Array 標記延伸](../../../../docs/framework/xaml-services/x-array-markup-extension.md)，它不支援屬性語法，因為必須在標記內容中指定該陣列的內容。  陣列內容的處理方式與一般物件相同，因此無法使用屬性的任何預設型別轉換子。  此外，[x:Array 標記延伸](../../../../docs/framework/xaml-services/x-array-markup-extension.md)也需要 `type` 參數。  
  
## 請參閱  
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [XAML 命名空間 \(x:\) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)   
 [WPF XAML 擴充功能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)   
 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [繫結標記延伸](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)   
 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)   
 [x:Type 標記延伸](../../../../docs/framework/xaml-services/x-type-markup-extension.md)