---
title: "合併的資源字典 | Microsoft Docs"
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
  - "合併的資源字典"
  - "合併的資源字典"
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 合併的資源字典
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]資源可支援合併的資源字典功能。 這項功能提供方法來定義的資源部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]之外已編譯的應用程式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應用程式。 然後應用程式間共用資源，也更方便地隔離進行當地語系化。  
  
## <a name="introducing-a-merged-resource-dictionary"></a>簡介合併的資源字典  
 在標記中，您可以使用下列語法來合併的資源字典引入頁面︰  
  
 [!code-xml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 請注意， <xref:System.Windows.ResourceDictionary>項目沒有[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)，這通常會需要的資源集合中的所有項目。 但另一個<xref:System.Windows.ResourceDictionary>中參考<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合是特殊的案例中，保留此案例中合併的資源字典。 <xref:System.Windows.ResourceDictionary>導入合併的資源字典不能有[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)。 一般而言，每個<xref:System.Windows.ResourceDictionary>內<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合指定<xref:System.Windows.ResourceDictionary.Source%2A>屬性。 值<xref:System.Windows.ResourceDictionary.Source%2A>應該[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]解析為要合併的資源檔的位置。 該目的地[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]必須是另一個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案中，使用<xref:System.Windows.ResourceDictionary>作為其根元素。  
  
> [!NOTE]
>  這是合法的定義內的資源<xref:System.Windows.ResourceDictionary> ，而不用指定為指定為合併的字典，<xref:System.Windows.ResourceDictionary.Source%2A>，或除了任何一種資源會包含從指定的來源。 不過，這不是常見的案例。合併字典的主要案例是合併資源從外部檔案的位置。 如果您想要在網頁標記中指定資源，您通常應該定義這些主<xref:System.Windows.ResourceDictionary>而不是在合併的字典。  
  
## <a name="merged-dictionary-behavior"></a>合併的字典行為  
 合併的字典中的資源所佔用的資源查閱範圍只之後合併至主要資源字典的範圍中的位置。 資源索引鍵內必須是唯一任何個別的字典，雖然索引鍵組合併字典中可以有許多次。 在此情況下，傳回的資源，將來自循序中找到的最後一個字典<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合。 如果<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合定義在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，則合併的字典集合中的順序是項目的順序，在標記中提供。 如果主要字典中和已合併的字典中定義的索引鍵，則會傳回該資源將來自主要字典。 這些範圍規則同樣適用於靜態資源參考和動態資源參考。  
  
### <a name="merged-dictionaries-and-code"></a>合併的字典和程式碼  
 合併的字典可以加入至`Resources`透過程式碼的字典。 預設值，一開始是空<xref:System.Windows.ResourceDictionary>在於任何`Resources`屬性也有預設值，一開始是空<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合屬性。 若要可透過程式碼合併的字典，您會取得所需的主要參考<xref:System.Windows.ResourceDictionary>，取得其<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>屬性值，並呼叫`Add`對泛型`Collection`包含在<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>。 您加入的物件必須是新<xref:System.Windows.ResourceDictionary>。 程式碼中，您未設定<xref:System.Windows.ResourceDictionary.Source%2A>屬性。 相反地，您必須取得<xref:System.Windows.ResourceDictionary>建立或載入其中一個物件。 其中一種方式載入的現有<xref:System.Windows.ResourceDictionary>呼叫<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName>上的現有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案資料流具有<xref:System.Windows.ResourceDictionary>根目錄，然後將轉型<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName>傳回值以<xref:System.Windows.ResourceDictionary>。  
  
### <a name="merged-resource-dictionary-uris"></a>合併的資源字典 Uri  
 有數種技巧併入合併的資源字典，由指示[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]您將使用的格式。 廣泛地說，這些技術可分為兩類︰ 編譯為專案一部分的資源和資源，便不會編譯為專案的一部分。  
  
 資源是編譯為專案的一部分，您可以使用的資源位置的相對路徑。 編譯期間會評估相對路徑。 您的資源必須定義為資源的建置動作為專案的一部分。 如果您在專案中為資源包含資源.xaml 檔案，您不需要將資源檔複製到輸出目錄，該資源已包含在已編譯的應用程式。 您也可以使用內容的建置動作，但您必須再將檔案複製到輸出目錄，也可執行檔部署在相同的路徑關聯性中的資源檔。  
  
> [!NOTE]
>  請勿使用內嵌資源的建置動作。 支援的建置動作本身[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，但的解析度<xref:System.Windows.ResourceDictionary.Source%2A>不會加入<xref:System.Resources.ResourceManager>，因此不能分隔個別的資源資料流出。 您仍然可以使用內嵌資源，供其他用途，只要也使用了<xref:System.Resources.ResourceManager>來存取的資源。  
  
 相關的技術是使用 Pack URI[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，並做為來源參考它。 Pack URI 可以讓元件的參考組件和其他技術的參考。 如需有關 Pack Uri 的詳細資訊，請參閱[WPF 應用程式資源、 內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。  
  
 如需不會編譯為專案一部分的資源，URI 是在執行階段評估。 您可以使用一般的 URI 傳輸，例如檔案︰ 或 http︰ 參考的資源檔。 使用 file 資源方法的缺點是該檔案︰ 存取需要額外的部署步驟和 http︰ 存取表示網際網路安全性區域。  
  
### <a name="reusing-merged-dictionaries"></a>重複使用合併的字典  
 您可以重複使用或共用合併的資源字典之間的應用程式，因為要合併的資源字典，可透過任何參考有效[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。 完全的做法將取決於您的應用程式的部署策略與哪一個應用程式模型您遵循。 前述的 Pack URI 策略讓來源合併的資源在多個專案在開發期間透過共用的組件參考。 在此案例中的資源仍會散發用戶端，和至少其中一個應用程式必須將參考的組件的部署。 此外，也可以參考合併的資源，透過使用 http 通訊協定的分散式 URI。  
  
 本機應用程式檔案，或為本機的共用存放裝置是另一個可行的合併的字典撰寫合併的字典 / 應用程式部署案例。  
  
### <a name="localization"></a>當地語系化  
 如果需要當地語系化的資源隔離至某個合併到主要字典，並保留成為鬆散[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，這些檔案可以個別進行當地語系化。 這項技術是當地語系化的附屬資源組件的輕量型替代方案。 如需詳細資訊，請參閱[WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.ResourceDictionary>   
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [WPF 應用程式資源、 內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)