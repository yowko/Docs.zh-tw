---
title: 標記延伸和 WPF XAML
ms.date: 03/30/2017
helpviewer_keywords:
- brace character [WPF]
- Binding markup extensions [WPF]
- RelativeSource markup extensions [WPF]
- XAML [WPF], markup extensions
- markup extensions [WPF]
- nesting extension syntax [WPF]
- curly brace characters ({})
- TemplateBinding markup extensions [WPF]
- StaticResource markup extensions [WPF]
- literal curly brace characters ({})
- characters [WPF], curly brace
- DynamicResource markup extensions [WPF]
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
ms.openlocfilehash: 562eea34af44a8fb24199e81477a4cb2ddb1046c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991824"
---
# <a name="markup-extensions-and-wpf-xaml"></a>標記延伸和 WPF XAML
本主題介紹 XAML 標記延伸模組概念，包括其語法規則、用途，以及其根據的類別物件模型。 標記延伸模組是 XAML 語言的一般功能，以及 XAML 服務之 .NET 實作的一般功能。 本主題會具體詳述 WPF XAML 中所使用的標記延伸模組。  

<a name="XAML_Processors_and_Markup_Extensions"></a>   
## <a name="xaml-processors-and-markup-extensions"></a>XAML 處理器和標記延伸模組  
 一般而言，XAML 剖析器可以將屬性值解譯為可轉換成基本項目的常值字串，或透過一些方法將它轉換成物件。 其中一種這類方式是透過參考類型轉換子；這記錄於 [TypeConverters 和 XAML](typeconverters-and-xaml.md) 主題。 不過，有些情況需要不同的行為。 例如，可以向 XAML 處理器指示，屬性的值不應該導致物件圖形中的新物件。 相反地，此屬性應該會產生參考圖形另一個組件中的已建構物件或靜態物件的物件圖表。 另一個情況是可以指示 XAML 處理器使用將非預設引數提供給物件建構函式的語法。 這些是標記延伸模組可提供解決方案的案例類型。  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## <a name="basic-markup-extension-syntax"></a>基本標記延伸模組語法  
 可以實作標記延伸模組，以提供屬性 (attribute) 用法中的屬性 (property) 值、屬性 (property) 項目用法中的屬性 (property)，或兩者。  
  
 用來提供屬性值時，可區分 XAML 處理器之標記延伸模組序列的語法是存在左右大括號 ({ 和 })。 標記延伸模組的類型則是透過緊接在左大括號後面的字串語彙基元所識別。  
  
 在屬性項目語法中使用時，標記延伸模組在視覺上與任何其他用來提供屬性項目值的項目相同︰將標記延伸模組類別參考為以角括弧括住 (<>) 之項目的 XAML 項目宣告。  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>已定義 XAML 的標記延伸  
 數個標記延伸模組不是 XAML 的 WPF 實作所特有，而是作為語言之 XAML 的內建功能或功能實作。 這些標記延伸模組在 System.Xaml 組件中實作為一般 .NET Framework XAML 服務的一部分，並且位在 XAML 語言 XAML 命名空間內。 根據常見標記用法，這些標記延伸模組通常可以透過用法中的 `x:` 前置詞進行識別。 <xref:System.Windows.Markup.MarkupExtension>基類 (也定義于 system.string) 提供了所有標記延伸應使用的模式, 以便在 xaml 讀取器和 xaml 寫入器中支援, 包括 WPF Xaml。  
  
- `x:Type` 提供具名類型的 <xref:System.Type> 物件。 這項工具最常用於樣式和範本。 如需詳細資訊，請參閱 [x:Type 標記延伸模組](../../xaml-services/x-type-markup-extension.md)。  
  
- `x:Static` 會產生靜態值。 值來自實值類型程式碼實體，而此實體不是直接為目標屬性值類型，但可以評估為該類型。 如需詳細資訊，請參閱 [x:Static 標記延伸模組](../../xaml-services/x-static-markup-extension.md)。  
  
- `x:Null` 指定 `null` 作為屬性的值，而且可以用於屬性 (attribute) 或屬性 (property) 項目值。 如需詳細資訊，請參閱 [x:Null 標記延伸模組](../../xaml-services/x-null-markup-extension.md)。  
  
- 如果故意不使用 WPF 基底項目和控制項模型所提供的集合支援，則 `x:Array` 支援使用 XAML 語法來建立一般陣列。 如需詳細資訊，請參閱 [x:Array 標記延伸模組](../../xaml-services/x-array-markup-extension.md)。  
  
> [!NOTE]
> `x:` 前置詞用於 XAML 檔案或生產的根項目中 XAML 語言內建功能的一般 XAML 命名空間對應。 例如, WPF 應用程式的 Visual Studio 範本會使用此`x:`對應來起始 XAML 檔案。 您可以選擇專屬 XAML 命名空間對應中的不同前置詞語彙基元，但是這份文件將假設使用預設 `x:` 對應來識別這些是 XAML 語言 XAML 命名空間之已定義部分的實體，而非與特定架構無關的 WPF 預設命名空間或其他 XML 命名空間。  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## <a name="wpf-specific-markup-extensions"></a>WPF 特定標記延伸模組  
 WPF 程式設計中所使用的最常見標記延伸模組是支援資源參考的標記延伸模組 (`StaticResource` 和 `DynamicResource`)，以及支援資料繫結的標記延伸模組 (`Binding`)。  
  
- `StaticResource` 會替代已定義資源的值，來提供屬性的值。 `StaticResource` 評估最終會在 XAML 載入期間進行，而且無法在執行階段存取物件圖形。 如需詳細資訊，請參閱 [StaticResource 標記延伸模組](staticresource-markup-extension.md)。  
  
- `DynamicResource` 會針對屬性提供一個值，方式是延後該值，使其變成資源的執行階段參考。 動態資源參考可在每次存取這類資源時強制執行新的查閱作業，而且可以在執行階段存取物件圖形。 若要取得這項存取，WPF 屬性系統中的相依性屬性以及評估過的運算式都支援 `DynamicResource` 概念。 因此，您只能針對相依性屬性目標使用 `DynamicResource`。 如需詳細資訊，請參閱 [DynamicResource 標記延伸模組](dynamicresource-markup-extension.md)。  
  
- `Binding` 使用在執行階段套用至父物件的資料內容，來提供屬性的資料繫結值。 此標記延伸模組啟用用於指定資料繫結的重大內嵌語法，因此相當複雜。 如需詳細資訊，請參閱[Binding 標記延伸模組](binding-markup-extension.md)。  
  
- `RelativeSource`提供的來源資訊<xref:System.Windows.Data.Binding> , 可以在執行時間物件樹狀結構中流覽數個可能的關聯性。 這會提供在多用途範本中所建立或使用程式碼所建立之繫結的特殊化來源，而不需要完全了解周圍物件樹狀結構。 如需詳細資訊，請參閱 [RelativeSource 標記延伸模組](relativesource-markupextension.md)。  
  
- `TemplateBinding` 可讓控制項範本使用範本屬性的值，而範本屬性來自將使用範本之類別的物件模型定義屬性。 換句話說，範本定義內的屬性可以存取只在套用範本後存在的內容。 如需詳細資訊，請參閱 [TemplateBinding 標記延伸模組](templatebinding-markup-extension.md)。 如需 `TemplateBinding` 實際使用的詳細資訊，請參閱 [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (使用 ControlTemplates 設定樣式範例)。  
  
- `ColorConvertedBitmap` 支援一個相當進階的影像處理案例。 如需詳細資訊，請參閱 [ColorConvertedBitmap 標記延伸模組](colorconvertedbitmap-markup-extension.md)。  
  
- `ComponentResourceKey` 和 `ThemeDictionary` 支援資源查閱各層面，特別是針對與自訂控制項一起封裝的資源和主題。 如需詳細資訊，請參閱 [ComponentResourceKey 標記延伸模組](componentresourcekey-markup-extension.md)、[ThemeDictionary 標記延伸模組](themedictionary-markup-extension.md)或[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
<a name="StarExtension"></a>   
## <a name="extension-classes"></a>\*延伸模組類別  
 針對一般 XAML 語言和 WPF 特定的標記延伸, 每個標記延伸的行為都會透過`*Extension`衍生自<xref:System.Windows.Markup.MarkupExtension>的類別識別為 XAML 處理器, 並提供<xref:System.Windows.Markup.StaticExtension.ProvideValue%2A>方法. 每個延伸模組上的這個方法提供在評估標記延伸模組時所傳回的物件。 所傳回的物件一般是根據傳遞至標記延伸模組的各種字串語彙基元所評估。  
  
 例如, <xref:System.Windows.StaticResourceExtension>類別會提供實際資源查閱的介面執行, 讓其<xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>實值傳回要求的物件, 而該特定執行的輸入是用來執行的字串。依其`x:Key`查詢資源。 如果您要使用現有的標記延伸模組，則此實作詳細資料大部分不重要。  
  
 某些標記延伸模組未使用字串語彙基元引數。 這是因為它們會傳回靜態或一致值，或利用透過 `serviceProvider` 參數所傳遞的其中一個服務可以取得應該傳回值的內容。  
  
 `*Extension` 命名模式是基於方便性和一致性。 XAML 處理器將該類別識別為標記延伸模組支援，則不需要它。 只要您的程式碼基底包含 system.string, 並使用 .NET Framework xaml 服務實作為, 就必須將它辨識為 xaml 標記延伸, 以衍生自<xref:System.Windows.Markup.MarkupExtension>和以支援結構化語法。 WPF 會定義標記延伸模組, 並啟用不遵循`*Extension`命名模式的類別, <xref:System.Windows.Data.Binding>例如。 通常這是因為此類別支援純標記延伸模組支援以外的案例。 在案例<xref:System.Windows.Data.Binding>中, 該類別針對與 XAML 無關的案例, 支援對物件的方法和屬性進行執行時間存取。  
  
### <a name="extension-class-interpretation-of-initialization-text"></a>初始化文字的延伸模組類別解譯  
 XAML 處理器會使用下列其中一種方式來解譯位在標記延伸模組名稱後面而且仍在大括弧內的字串語彙基元：  
  
- 逗號一律會代表個別語彙基元的分隔符號。  
  
- 如果個別分隔的語彙基元未包含任何等號，則會將每個語彙基元視為建構函式引數。 每個建構函式參數都必須指定為該簽章所預期的類型，並且為該簽章所預期的適當順序。  
  
    > [!NOTE]
    > XAML 處理器必須呼叫建構函式，以與配對數目的引數計數相符。 基於這個理由, 如果您正在執行自訂標記延伸, 請不要提供具有相同引數計數的多個函式。 有多個具有相同參數計數的標記延伸模組建構函式路徑時，未定義 XAML 處理器運作方式的行為，但您應該預期在標記延伸模組類型定義發生此情況時，允許 XAML 處理器擲回用法例外狀況。  
  
- 如果個別的分隔標記包含等號, 則 XAML 處理器會先呼叫標記延伸的無參數的函式。 則每個「名稱=值」配對都會解譯為標記延伸模組上的屬性名稱，以及要指派給該屬性的值。  
  
- 如果建構函式行為與標記延伸模組中的屬性設定行為之間有平行結果，則所使用的行為就不重要。 如果只因為可讓您的標記更具意圖，而且您較不可能意外轉置建構函式參數，則較常見用法是使用有多個可設定屬性之標記延伸模組的「屬性」`=`「值」 (當您指定「屬性=值」配對時，這些屬性可能是任意順序)。另外，不保證標記延伸模組提供可設定所有其可設定屬性的建構函式參數。 例如, <xref:System.Windows.Data.Binding>是一個標記延伸, 其中包含許多可透過*屬性*`=`*值*表單中的延伸模組來設定的<xref:System.Windows.Data.Binding>屬性, 但僅支援兩個函式: 無參數的函式, 以及一個這會設定初始路徑。  
  
- 必須逸出，才能將常值逗號傳遞給標記延伸模組。  
  
<a name="EscapeSequences"></a>   
## <a name="escape-sequences-and-markup-extensions"></a>逸出序列和標記延伸模組  
 XAML 處理器中的屬性處理使用大括號作為標記延伸模組序列的指標。 此外，必要時，也可能產生常值大括號字元屬性值，方法是使用後接常值大括號的空大括號配對來輸入逸出序列。 請參閱[ {} Escape 序列標記延伸](../../xaml-services/escape-sequence-markup-extension.md)。  
  
<a name="Nesting"></a>   
## <a name="nesting-markup-extensions-in-xaml-usage"></a>XAML 用法中的巢狀標記延伸模組  
 支援巢狀多個標記延伸模組，並且會先更深入地評估每個標記延伸模組。 例如，請考慮下列用法：  
  
```xaml  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
```  
  
 在此用法中，會先評估 `x:Static` 陳述式，並傳回字串。 該字串接著會用作 `DynamicResource` 的引數。  
  
## <a name="markup-extensions-and-property-element-syntax"></a>標記延伸模組和屬性項目語法  
 用作填入屬性項目值的物件項目時，無法從可在 XAML 中使用的一般類型支援物件項目來透過視覺方式區別標記延伸模組類別。 一般物件項目與標記延伸模組的實際差異，在於標記延伸模組會評估為類型值或延後為運算式。 因此，標記延伸模組之屬性值的任何可能類型錯誤的機制會不同，就像其他程式設計模型中處理晚期繫結屬性的方式一樣。 將會針對剖析 XAML 時所設定的目標屬性，評估一般物件項目的類型是否相符。  
  
 用於物件項目語法以填入屬性項目時，大部分標記延伸模組內不會有內容或任何進一步屬性項目語法。 因此，您可以關閉物件項目標記，且不提供任何子項目。 只要 XAML 處理器遇到任何物件項目時，就會呼叫該類別的建構函式，以具現化從剖析的項目所建立的物件。 標記延伸類別是不一樣的: 如果您想要在物件專案語法中使用標記延伸模組, 則必須提供無參數的函式。 某些現有標記延伸模組有至少一個必要屬性值，而且必須指定一個必要屬性值才能進行有效初始化。 如果是這樣，該屬性值一般會指定為物件項目上屬性 (property) 的屬性 (attribute)。 [在 XAML 命名空間 (x:) 中語言功能](../../xaml-services/xaml-namespace-x-language-features.md)和[WPF XAML 延伸](wpf-xaml-extensions.md)模組參考頁面, 將會注明具有必要屬性的標記延伸 (以及必要屬性的名稱)。 參考頁面也會標註是否不允許特定標記延伸模組的物件項目語法或屬性語法。 值得注意的案例是 [x:Array 標記延伸模組](../../xaml-services/x-array-markup-extension.md)，這無法支援屬性語法，因為必須在標記內將該陣列的內容指定為內容。 陣列內容會當成一般物件處理；因此，沒有屬性的預設類型轉換子是可行的。 此外，[x:Array 標記延伸模組](../../xaml-services/x-array-markup-extension.md)需要 `type` 參數。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [XAML 命名空間 (x:)語言功能](../../xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML 延伸](wpf-xaml-extensions.md)
- [StaticResource 標記延伸](staticresource-markup-extension.md)
- [Binding 標記延伸](binding-markup-extension.md)
- [DynamicResource 標記延伸](dynamicresource-markup-extension.md)
- [x:Type 標記延伸模組](../../xaml-services/x-type-markup-extension.md)
