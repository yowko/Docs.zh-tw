---
title: 合併的資源字典
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: ff6720a4f0e99e8274a608b4177044451d8c828d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582477"
---
# <a name="merged-resource-dictionaries"></a>合併的資源字典
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資源支援合併的資源字典功能。 這項功能提供一種方法，定義已編譯之 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式之外的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式的資源部分。 然後，資源可在應用程式間共用，也更方便隔離進行當地語系化。  
  
## <a name="introducing-a-merged-resource-dictionary"></a>簡介合併的資源字典  
 在標記中，您使用下列語法將合併的資源字典引入頁面︰  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 請注意，<xref:System.Windows.ResourceDictionary> 元素並沒有[x：Key](../../xaml-services/x-key-directive.md)指示詞，資源集合中的所有專案通常都需要此指示詞。 但是，<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> 集合內的另一個 <xref:System.Windows.ResourceDictionary> 參考是特殊案例，保留給這個合併的資源字典案例。 引進合併資源字典的 <xref:System.Windows.ResourceDictionary> 不能有[x：Key](../../xaml-services/x-key-directive.md)指示詞。 一般來說，<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> 集合中的每個 <xref:System.Windows.ResourceDictionary> 都會指定一個 <xref:System.Windows.ResourceDictionary.Source%2A> 屬性。 @No__t_0 的值應該是統一資源識別元（URI），它會解析為要合併之資源檔的位置。 該 URI 的目的地必須是另一個 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案，並以 <xref:System.Windows.ResourceDictionary> 作為其根項目。  
  
> [!NOTE]
> 在指定為合併字典的 <xref:System.Windows.ResourceDictionary> 中定義資源是合法的，這可以做為指定 <xref:System.Windows.ResourceDictionary.Source%2A> 的替代方法，或是除了指定的來源所包含的任何資源之外。 不過，這不是常見的案例。合併字典的主要案例是合併來自外部檔案位置的資源。 如果您想要在頁面的標記內指定資源，通常應該在主要 <xref:System.Windows.ResourceDictionary> 中定義，而不是在合併的字典中。  
  
## <a name="merged-dictionary-behavior"></a>合併的字典行為  
 合併字典中的資源佔用資源查閱範圍中的位置，就在它們合併所在的主要資源字典範圍後面。 雖然資源索引鍵在任何個別的字典中必須是唯一的，但合併字典集合中可有多個索引鍵。 在此情況下，傳回的資源會來自 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> 集合中順序的最後一個字典。 如果 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> 集合是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中定義，則集合中合併字典的順序就是標記中所提供專案的順序。 如果主要字典和合併的字典中都定義了索引鍵，則傳回的資源會來自主要字典。 這些範圍規則同樣適用於靜態資源參考和動態資源參考。  
  
### <a name="merged-dictionaries-and-code"></a>合併的字典和程式碼  
 合併的字典可以透過程式碼新增至 `Resources` 字典。 任何 `Resources` 屬性的預設 <xref:System.Windows.ResourceDictionary>，一開始都會有一個預設的空 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> 集合屬性。 若要透過程式碼加入合併的字典，您可以取得所需主要 <xref:System.Windows.ResourceDictionary> 的參考、取得其 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> 屬性值，並在 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> 所包含的泛型 `Collection` 上呼叫 `Add`。 您加入的物件必須是新的 <xref:System.Windows.ResourceDictionary>。 在程式碼中，您不會設定 <xref:System.Windows.ResourceDictionary.Source%2A> 屬性。 相反地，您必須建立一個或載入一個 <xref:System.Windows.ResourceDictionary> 物件來取得。 載入現有 <xref:System.Windows.ResourceDictionary> 以在具有 <xref:System.Windows.ResourceDictionary> 根的現有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案資料流程上呼叫 <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>，然後將 <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> 傳回值轉換為 <xref:System.Windows.ResourceDictionary> 的其中一種方式。  
  
### <a name="merged-resource-dictionary-uris"></a>合併的資源字典 URI  
 有幾種方法可讓您加入合併的資源字典，這會以您將使用的統一資源識別項（URI）格式來表示。 廣泛而言，這些技巧可分為兩類︰編譯為專案一部分的資源，和不編譯為專案一部分的資源。  
  
 若為編譯為專案一部分的資源，您可以使用參照資源位置的相對路徑。 在編譯期間評估相對路徑。 您的資源必須定義為專案的一部分，作為資源建置動作。 如果您在專案中將資源 .xaml 檔案包含為資源，就不需要將資源檔複製到輸出目錄，該資源已包含在已編譯的應用程式中。 您也可以使用內容建置動作，但您必須接著將檔案複製到輸出目錄，也將資源檔部署在與可執行檔有關的同一路徑。  
  
> [!NOTE]
> 請勿使用內嵌資源建置動作。 @No__t_0 的應用程式支援組建動作本身，但 <xref:System.Windows.ResourceDictionary.Source%2A> 的解決方式不會納入 <xref:System.Resources.ResourceManager>，因此無法將個別資源從資料流程中分離出來。 您仍然可以使用內嵌資源來進行其他目的，只要您也使用 <xref:System.Resources.ResourceManager> 來存取資源。  
  
 相關技術是使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案的 Pack URI，並參考為來源。 Pack URI 可以參考參考組件的元件和其他技術。 如需 Pack URI 的詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](../app-development/wpf-application-resource-content-and-data-files.md)。  
  
 若為不編譯為專案一部分的資源，則會在執行階段評估 URI。 您可以使用一般的 URI 傳輸，例如 file: 或 http:，參考資源檔。 使用未編譯資源方法的缺點是 file: 存取需要額外的部署步驟，以及 http: 存取表示網際網路安全性區域。  
  
### <a name="reusing-merged-dictionaries"></a>重複使用合併的字典  
 您可以在應用程式之間重複使用或共用合併的資源字典，因為要合併的資源字典可以透過任何有效的統一資源識別元（URI）來參考。 至於確實該如何做，取決於您的應用程式部署策略以及您遵循的應用程式模型。 前述的 Pack URI 策略提供了一個常見的方法，在開發期間透過共用組件參考，在多個專案中取得合併的資源。 在此案例中，資源仍由用戶端散發，至少一個應用程式必須部署參考的組件。 也可以透過使用 http 通訊協定的分散式 URI 參考合併的資源。  
  
 將合併的字典撰寫為本機應用程式檔案，或寫入本機的共用存放裝置，是另一個可行的合併字典/應用程式部署案例。  
  
### <a name="localization"></a>當地語系化  
 如果需要當地語系化的資源隔離至合併到主要字典的字典，並保持鬆散如 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，則這些檔案可以分別進行當地語系化。 這項技術是當地語系化附屬資源組件的輕量型替代方案。 如需詳細資訊，請參閱 [WPF 全球化和當地語系化概觀](wpf-globalization-and-localization-overview.md)。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.ResourceDictionary>
- [XAML 資源](xaml-resources.md)
- [資源和程式碼](resources-and-code.md)
- [WPF 應用程式資源、內容和資料檔案](../app-development/wpf-application-resource-content-and-data-files.md)
