---
title: 合併的資源字典
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: ae6c8dc3669ed46165f3d78e78735187ebbc3776
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377013"
---
# <a name="merged-resource-dictionaries"></a>合併的資源字典
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資源支援合併的資源字典功能。 這項功能提供一種方法，定義已編譯之 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式之外的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的資源部分。 然後，資源可在應用程式間共用，也更方便隔離進行當地語系化。  
  
## <a name="introducing-a-merged-resource-dictionary"></a>簡介合併的資源字典  
 在標記中，您使用下列語法將合併的資源字典引入頁面︰  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 請注意，<xref:System.Windows.ResourceDictionary>項目沒有[X:key 指示詞](../../xaml-services/x-key-directive.md)，通常都需要的資源集合中的所有項目。 但另一個<xref:System.Windows.ResourceDictionary>中參考<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合是特殊的案例中，保留給此合併的資源字典案例。 <xref:System.Windows.ResourceDictionary>導入合併資源字典不能有[X:key 指示詞](../../xaml-services/x-key-directive.md)。 一般而言，每個<xref:System.Windows.ResourceDictionary>內<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合指定<xref:System.Windows.ResourceDictionary.Source%2A>屬性。 值<xref:System.Windows.ResourceDictionary.Source%2A>應該是[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]解析為要合併的資源檔的位置。 目的地[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]必須是另一個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案，與<xref:System.Windows.ResourceDictionary>作為其根項目。  
  
> [!NOTE]
>  它是合法內定義資源<xref:System.Windows.ResourceDictionary>，為指定的替代方式指定為合併的字典， <xref:System.Windows.ResourceDictionary.Source%2A>，或是加上指定的來源會包含任何資源。 不過，這不是常見的案例。合併字典的主要案例是合併來自外部檔案位置的資源。 如果您想要指定網頁的標記內的資源，您通常應該定義這些主要<xref:System.Windows.ResourceDictionary>而不是在合併的字典。  
  
## <a name="merged-dictionary-behavior"></a>合併的字典行為  
 合併字典中的資源佔用資源查閱範圍中的位置，就在它們合併所在的主要資源字典範圍後面。 雖然資源索引鍵在任何個別的字典中必須是唯一的，但合併字典集合中可有多個索引鍵。 在此情況下，會傳回該資源會來自循序中找到的最後一個字典<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合。 如果<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>中所定義集合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，則合併的字典集合中的順序是項目的順序，因為在標記中未提供。 如果主要字典和合併的字典中都定義了索引鍵，則傳回的資源會來自主要字典。 這些範圍規則同樣適用於靜態資源參考和動態資源參考。  
  
### <a name="merged-dictionaries-and-code"></a>合併的字典和程式碼  
 合併的字典可以透過程式碼新增至 `Resources` 字典。 預設值，一開始是空<xref:System.Windows.ResourceDictionary>任何現有`Resources`屬性也會有預設值，一開始是空<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>集合屬性。 若要新增合併的字典，透過程式碼，您會取得所需的主要參考<xref:System.Windows.ResourceDictionary>，取得其<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>屬性值，並呼叫`Add`泛型`Collection`中所含<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>。 您新增的物件必須是新<xref:System.Windows.ResourceDictionary>。 程式碼中，您未設定<xref:System.Windows.ResourceDictionary.Source%2A>屬性。 相反地，您必須取得<xref:System.Windows.ResourceDictionary>建立或載入其中的物件。 其中一種方式載入的現有<xref:System.Windows.ResourceDictionary>來呼叫<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>上的現有[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]具有檔案資料流<xref:System.Windows.ResourceDictionary>根，然後轉換<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>傳回值，以<xref:System.Windows.ResourceDictionary>。  
  
### <a name="merged-resource-dictionary-uris"></a>合併的資源字典 URI  
 併入合併的資源字典有數種技巧，您將使用的 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 格式會加以說明。 廣泛而言，這些技巧可分為兩類︰編譯為專案一部分的資源，和不編譯為專案一部分的資源。  
  
 若為編譯為專案一部分的資源，您可以使用參照資源位置的相對路徑。 在編譯期間評估相對路徑。 您的資源必須定義為專案的一部分，作為資源建置動作。 如果您在專案中將資源 .xaml 檔案包含為資源，就不需要將資源檔複製到輸出目錄，該資源已包含在已編譯的應用程式中。 您也可以使用內容建置動作，但您必須接著將檔案複製到輸出目錄，也將資源檔部署在與可執行檔有關的同一路徑。  
  
> [!NOTE]
>  請勿使用內嵌資源建置動作。 支援建置動作本身[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，但的解析度<xref:System.Windows.ResourceDictionary.Source%2A>不會併入<xref:System.Resources.ResourceManager>，並因此無法分隔個別的資源，從資料流。 您仍然可以使用內嵌資源，基於其他目的，只要也使用了<xref:System.Resources.ResourceManager>才能存取資源。  
  
 相關技術是使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案的 Pack URI，並參考為來源。 Pack URI 可以參考參考組件的元件和其他技術。 如需 Pack URI 的詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](../app-development/wpf-application-resource-content-and-data-files.md)。  
  
 若為不編譯為專案一部分的資源，則會在執行階段評估 URI。 您可以使用一般的 URI 傳輸，例如 file: 或 http:，參考資源檔。 使用未編譯資源方法的缺點是 file: 存取需要額外的部署步驟，以及 http: 存取表示網際網路安全性區域。  
  
### <a name="reusing-merged-dictionaries"></a>重複使用合併的字典  
 應用程式之間可以重複使用或共用合併的資源字典，因為要合併的資源字典可透過任何有效的 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 參考。 至於確實該如何做，取決於您的應用程式部署策略以及您遵循的應用程式模型。 前述的 Pack URI 策略提供了一個常見的方法，在開發期間透過共用組件參考，在多個專案中取得合併的資源。 在此案例中，資源仍由用戶端散發，至少一個應用程式必須部署參考的組件。 也可以透過使用 http 通訊協定的分散式 URI 參考合併的資源。  
  
 將合併的字典撰寫為本機應用程式檔案，或寫入本機的共用存放裝置，是另一個可行的合併字典/應用程式部署案例。  
  
### <a name="localization"></a>當地語系化  
 如果需要當地語系化的資源隔離至合併到主要字典的字典，並保持鬆散如 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，則這些檔案可以分別進行當地語系化。 這項技術是當地語系化附屬資源組件的輕量型替代方案。 如需詳細資訊，請參閱 [WPF 全球化和當地語系化概觀](wpf-globalization-and-localization-overview.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.ResourceDictionary>
- [XAML 資源](xaml-resources.md)
- [資源和程式碼](resources-and-code.md)
- [WPF 應用程式資源、內容和資料檔案](../app-development/wpf-application-resource-content-and-data-files.md)
