---
title: "XAML 資源 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "重複使用資源"
  - "重複使用的資源"
  - "重複使用一般定義的物件"
  - "XAML 中，重複使用的資源"
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# XAML 資源
資源是可重複使用您的應用程式中的不同位置中的物件。 資源的範例包括筆刷和樣式。 本概觀說明如何使用中的資源[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 您也可以建立及存取資源，使用程式碼，或交換程式碼之間和[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 如需詳細資訊，請參閱[資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)。  
  
> [!NOTE]
>  本主題中所述的資源檔案是不同於資源檔中所述[WPF 應用程式資源、 內容和資料檔](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)不同中所述的內嵌或連結的資源和[管理應用程式資源 (.NET)](../Topic/Managing%20Application%20Resources%20\(.NET\).md)。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>在 XAML 中使用的資源  
 下列範例會定義<xref:System.Windows.Media.SolidColorBrush>為頁面的根項目上的資源。 此範例會參考資源，並使用它來設定屬性的數個子項目，包括<xref:System.Windows.Shapes.Ellipse>、 <xref:System.Windows.Controls.TextBlock>，和<xref:System.Windows.Controls.Button>。  
  
 [!code-xml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 每個架構層級項目 ( <xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>) 具有<xref:System.Windows.FrameworkElement.Resources%2A>屬性，這是包含資源的屬性 (做為<xref:System.Windows.ResourceDictionary>) 的資源定義。 您可以定義資源上的任何項目。 不過，資源通常會定義在根項目，也就是<xref:System.Windows.Controls.Page>在範例中。  
  
 在資源字典中的每個資源都必須有唯一索引鍵。 當您在標記中定義的資源時，您指派唯一的索引鍵，透過[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)。 索引鍵通常是字串。不過，您也可以設定它到其他物件類型使用適當的標記延伸。 非字串資源的索引鍵由特定的功能區中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，值得注意的是針對樣式、 元件資源及資料樣式。  
  
 定義資源之後，您可以參考資源，用於使用指定的索引鍵的名稱，例如資源標記延伸語法屬性值︰  
  
 [!code-xml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 在上述範例中，當[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入器會處理值`{StaticResource MyBrush}`的<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.Button>，資源查閱邏輯會先檢查資源字典<xref:System.Windows.Controls.Button>項目。 如果<xref:System.Windows.Controls.Button>並沒有定義的資源索引鍵`MyBrush`（沒有實作; 其資源集合是空的），查閱接著會檢查的父項目<xref:System.Windows.Controls.Button>，也就是<xref:System.Windows.Controls.Page>。 因此，當您定義的資源上<xref:System.Windows.Controls.Page>根項目、 邏輯樹狀結構中的所有項目<xref:System.Windows.Controls.Page>可以存取它，並設定任何屬性的值可接受的您可以重複使用相同的資源<xref:System.Type>資源所代表。 在上述範例中，相同`MyBrush`資源設定兩個不同的屬性︰<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>，而<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>靜態和動態資源  
 資源可以當做靜態資源或動態資源參考。 這由使用[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)或[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)。 標記延伸是一項功能[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以讓標記延伸處理屬性字串，並傳回的物件指定的物件參考[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入器。 如需標記延伸行為的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 當您使用標記延伸時，通常會提供一或多個參數以字串形式會處理該特定標記延伸，而不是所設定之屬性的內容中評估。 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)處理按鍵，查看所有可用的資源字典中機碼值。 這會在載入中載入程序需要指派採用靜態資源參考的屬性值時的時間點的期間。 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)改為處理程序藉由建立運算式，以及該運算式的索引鍵會保留未評估實際執行應用程式之前，此時這個運算式會評估，並且提供的值。  
  
 當您參考資源時，無論您是使用靜態資源參考或動態資源參考，就可能會影響下列考量︰  
  
-   資源建立應用程式的整體設計 (每個頁面、 應用程式、 在鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，資源的唯一組件中)。  
  
-   應用程式的功能︰ 正在更新應用程式的需求即時部分中的資源嗎？  
  
-   該資源的參考類型的個別查閱行為。  
  
-   特定的屬性或資源類型，以及這些型別的原生的行為。  
  
### <a name="static-resources"></a>靜態資源  
 靜態資源參考最適合用於下列狀況︰  
  
-   應用程式的設計將所有其資源至網頁或應用程式層級資源的最著重的字典。 靜態資源參考不會重新評估執行階段行為，例如，重新載入頁面，為基礎，因此可以提高效能並不需要每個資源和應用程式的設計，避免大量動態資源參考。  
  
-   您正在設定不在屬性的值<xref:System.Windows.DependencyObject>或<xref:System.Windows.Freezable>。  
  
-   您正在建立之編譯成 DLL，並封裝應用程式的一部分或應用程式之間共用的資源字典。  
  
-   您要建立自訂控制項的佈景主題，而且會定義使用佈景主題內的資源。 在此情況下，您通常不想動態資源參考查閱行為，您會想靜態資源參考行為，以便查閱是可預測且獨立的主題。 使用動態資源參考，即使佈景主題內的參考將處於未評估直到執行階段，而且沒有機會套用佈景主題時，某些區域中的項目會重新定義您的佈景主題嘗試參考時，索引鍵和本機項目會落在查閱本身的主題。 如果發生這種情況，您的佈景主題不會表現按照預期的方式。  
  
-   您用來設定相依性屬性的大量資源。 相依性屬性具有有效值快取啟用的屬性系統，因此如果您提供可能的相依性屬性的值評估在載入期間，相依性屬性並沒有檢查重新評估後的運算式並可以傳回最後一個有效的值。 這項技術可以獲得效能優勢。  
  
-   您想要變更基礎資源的所有取用者，或您想要使用不同的可寫入執行個體維護的每個取用者[x︰ 共用屬性](../../../../docs/framework/xaml-services/x-shared-attribute.md)。  
  
#### <a name="static-resource-lookup-behavior"></a>靜態資源查閱行為  
  
1.  查閱處理序會檢查要求中設定屬性的項目所定義的資源字典的索引鍵。  
  
2.  查閱處理序然後周遊邏輯樹狀結構向上，父項目和其資源字典。 這會繼續直到到達根項目。  
  
3.  接下來，會檢查應用程式資源。 應用程式資源則由所定義的資源字典內<xref:System.Windows.Application>物件您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
 從資源字典內的靜態資源參考必須參考已定義語彙資源參考之前的資源。 靜態資源參考無法解析向前參考。 基於這個理由，如果您使用靜態資源參考，您必須設計資源字典結構，讓資源所使用的資源定義或幾乎每個個別的資源字典開頭的。  
  
 靜態資源查閱可以延伸到佈景主題，或系統資源，但只支援這種[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入器會延後的要求。 延遲是必要的以便在頁面載入時的執行階段佈景主題正確地套用至應用程式。 不過，靜態資源參考已知只存在於佈景主題或做為系統資源，所以不建議的索引鍵。 這是因為這類的參考都不會重新評估使用者即時變更佈景主題時。 當您要求佈景主題或系統資源時，動態資源參考會更為可靠。 例外狀況時，佈景主題項目本身要求另一個資源。 這些參考應該是靜態資源參考，如先前所述的原因。  
  
 如果找不到靜態資源參考的例外狀況行為而異。 如果延後資源，則會發生在執行階段例外狀況。 如果無法延後資源，在載入期間發生例外狀況。  
  
### <a name="dynamic-resources"></a>動態資源  
 動態資源最適用於下列狀況︰  
  
-   資源的值取決於執行階段才會知道的條件。 這包括系統資源或使用者可設定的資源。 比方說，您可以建立參考系統屬性的 setter 值所公開的<xref:System.Windows.SystemColors>， <xref:System.Windows.SystemFonts>，或<xref:System.Windows.SystemParameters>。 這些值是真正的動態的因為它們最後是來自使用者和作業系統的執行階段環境。 您可能也可以變更其中頁面層級資源的存取也必須擷取變更的應用程式層級主題。  
  
-   您要建立或參考自訂控制項的佈景主題樣式。  
  
-   您想要調整的內容<xref:System.Windows.ResourceDictionary>應用程式存留期間。  
  
-   您必須有相互依存性，可能需要向前參考的複雜的資源結構。 靜態資源參考不支援向前參考，但因為不需要執行階段之前評估資源，動態資源參考並支援這些，因此向前參考並不相關的概念。  
  
-   您所參考的是從編譯或工作集的觀點來看特別大的資源，並立即在載入頁面時，可能不使用的資源。 靜態資源參考一律從載入[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]當頁面載入; 不過，動態資源參考不會載入直到實際使用時。  
  
-   您正在建立的樣式，其中 setter 值可能來自於主題或其他使用者設定會影響其他值。  
  
-   將資源套用至項目，可能會重設父代的邏輯樹狀結構中的應用程式存留期間。 也可能會變更父系變更資源查閱範圍，因此如果您想要重設父代的項目重新評估的資源根據新的範圍，一律使用動態資源參考。  
  
#### <a name="dynamic-resource-lookup-behavior"></a>動態資源查閱行為  
 動態資源參考的資源查閱行為與查閱行為，在程式碼中的，如果您呼叫<xref:System.Windows.FrameworkElement.FindResource%2A>或<xref:System.Windows.FrameworkElement.SetResourceReference%2A>。  
  
1.  查閱處理序會檢查要求中設定屬性的項目所定義的資源字典的索引鍵。  
  
    -   如果項目會定義<xref:System.Windows.FrameworkElement.Style%2A>屬性，<xref:System.Windows.Style.Resources%2A>字典內<xref:System.Windows.Style>已核取。  
  
    -   如果項目會定義<xref:System.Windows.Controls.Control.Template%2A>屬性，<xref:System.Windows.FrameworkTemplate.Resources%2A>字典內<xref:System.Windows.FrameworkTemplate>已核取。  
  
2.  查閱處理序然後周遊邏輯樹狀結構向上，父項目和其資源字典。 這會繼續直到到達根項目。  
  
3.  接下來，會檢查應用程式資源。 應用程式資源則由所定義的資源字典內<xref:System.Windows.Application>物件您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
4.  檢查佈景主題資源字典，系統會針對目前使用中的主題。 如果在執行階段變更佈景主題，會重新評估的值。  
  
5.  檢查系統資源。  
  
 （如果有的話） 的例外狀況行為會有所不同︰  
  
-   如果要求之資源的<xref:System.Windows.FrameworkElement.FindResource%2A>呼叫，以及找不到，會引發例外狀況。  
  
-   如果要求之資源的<xref:System.Windows.FrameworkElement.TryFindResource%2A>呼叫，以及找不到，會引發任何例外狀況，但傳回的值是`null`。 如果要設定的屬性不接受`null`，則仍然可以更深入的例外狀況將會引發 （這取決於要設定的個別屬性）。  
  
-   如果要求中的動態資源參考資源[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，和找不到，則其行為取決於 一般屬性系統，但一般的行為會如同沒有屬性的設定作業發生在資源所在的層級。 比方說，如果您嘗試在設定背景使用的資源，不會評估為個別的按鈕項目，然後設定任何值的結果，但有效的值仍然可以來自其他參與屬性系統和值的優先順序。 比方說，背景值仍可能來自本機定義的按鈕樣式，或從佈景主題樣式。 佈景主題樣式所未定義的屬性，屬性中繼資料中的預設值可能來自於失敗的資源評估後的有效值。  
  
#### <a name="restrictions"></a>限制  
 動態資源參考有一些值得注意的限制。 至少一個下列必須為真︰  
  
-   要設定的屬性必須是屬性上<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。 必須由備份屬性<xref:System.Windows.DependencyProperty>。  
  
-   參考中的值是<xref:System.Windows.Style><xref:System.Windows.Setter>。  
  
-   要設定的屬性必須是屬性上<xref:System.Windows.Freezable>提供的值為<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>屬性，或<xref:System.Windows.Setter>值。  
  
 因為設定的屬性必須是<xref:System.Windows.DependencyProperty>或<xref:System.Windows.Freezable>屬性中，大部分的屬性變更可以傳播 UI，因為屬性變更 （已變更的動態資源值） 會在認可屬性系統。 大部分的控制項加入時，強制另一個控制項的配置的邏輯<xref:System.Windows.DependencyProperty>變更和屬性可能會影響配置。 不過，並非所有屬性，都有[DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)它們的值一定會提供一種他們更新 UI 中的即時值。 依據的屬性，以及根據類型屬性或甚至您的應用程式的邏輯結構擁有這項功能仍可能會有所不同。  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>樣式、 Datatemplate 和隱含的索引鍵  
 更早版本，它已指定所有項目中<xref:System.Windows.ResourceDictionary>必須有索引鍵。 不過，這不表示所有資源都必須明確`x:Key`。 多種物件型別支援隱含的索引鍵時定義為資源，其中的索引鍵值會繫結至另一個屬性的值。 這就所謂的隱含索引鍵，而`x:Key`屬性是明確的索引鍵。 您可以指定明確的索引鍵，以覆寫任何隱含的索引鍵。  
  
 資源非常重要的案例之一是當您定義<xref:System.Windows.Style>。 事實上，<xref:System.Windows.Style>幾乎都定義為資源字典中的項目因為樣式原本就是針對重複使用。 如需有關樣式的詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
 控制項的樣式能夠建立與使用隱含的索引鍵參考。 定義控制項的預設外觀的佈景主題樣式會依賴隱含索引鍵。 隱含的索引鍵，從要求它的角度來看是<xref:System.Type>控制項本身。 隱含的索引鍵，從定義資源的角度來看是<xref:System.Windows.Style.TargetType%2A>的樣式。 因此，如果您要建立自訂控制項的佈景主題，建立互動的樣式與現有的佈景主題樣式，您不需要指定[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)的<xref:System.Windows.Style>。 如果您想要使用佈景主題樣式，您不需要指定任何樣式。 例如，下列的樣式定義的運作方式，即使<xref:System.Windows.Style>資源並不具有索引鍵︰  
  
 [!code-xml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 樣式其實並沒有索引鍵︰ 隱含的索引鍵`typeof(`<xref:System.Windows.Controls.Button>`)`。 在標記中，您可以指定<xref:System.Windows.Style.TargetType%2A>直接做為類型名稱 (或您可以選擇性地使用[{X:type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) 傳回<xref:System.Type>。  
  
 透過所使用的預設佈景主題樣式機制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，做為執行階段樣式的已套用樣式<xref:System.Windows.Controls.Button>在頁面上，即使<xref:System.Windows.Controls.Button>本身不會指定其<xref:System.Windows.FrameworkElement.Style%2A>屬性或特定資源的參考樣式。 您的頁面中定義的樣式位於稍早在查閱順序早於主題字典樣式，使用相同的佈景主題字典樣式的金鑰。 您可以指定`<Button>Hello</Button>` 頁面上，並以您定義的樣式中的任何位置<xref:System.Windows.Style.TargetType%2A>的`Button`會套用到該按鈕。 如果您想，您仍會明確金鑰使用相同的型別值做為樣式<xref:System.Windows.Style.TargetType%2A>、 清楚的標記，但是這是選擇性的。  
  
 樣式的隱含索引鍵不會套用到控制項上如果<xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>是`true`(也請注意， <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A>可能設定為原生控制項類別，而不是明確的控制項執行個體上的行為的一部分)。 此外，為了支援隱含的索引鍵在衍生的類別的情況下，控制項必須覆寫<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (提供做為一部分的所有現有控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]這麼做)。 如需樣式、 主題和設計控制項的詳細資訊，請參閱[設計可設定樣式控制項的方針](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md)。  
  
 <xref:System.Windows.DataTemplate>也具有隱含的索引鍵。 隱含的索引鍵的<xref:System.Windows.DataTemplate>是<xref:System.Windows.DataTemplate.DataType%2A>屬性值。                  <xref:System.Windows.DataTemplate.DataType%2A>也可以指定為型別的名稱，而不是使用明確[{X:type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md). 如需詳細資訊，請參閱[資料範本化概觀](../../../../docs/framework/wpf/data/data-templating-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.ResourceDictionary>   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [定義和參考資源](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)   
 [應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)   
 [X:type 標記延伸](../../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)