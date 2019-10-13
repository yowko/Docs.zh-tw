---
title: WPF 的全球化
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 32caf87435e23008f9f300d231c2705e7894280f
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291470"
---
# <a name="globalization-for-wpf"></a>WPF 的全球化
本主題將介紹在為全球市場撰寫 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式時，您應該注意的問題。 全球化程式設計項目會在 .NET 的 <xref:System.Globalization> 命名空間中定義。

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML 全球化
 Extensible Application Markup Language （XAML）是以 @no__t 0 為基礎，並利用 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 規格中所定義的全球化支援。 下列各節描述一些您應該注意的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 功能。

<a name="char_reference"></a>
### <a name="character-references"></a>字元參考
字元參考會以十進位或十六進位提供它所代表之特定 @no__t 0 字元的 UTF16 程式碼單位。 下列範例會顯示「哥英數位元」或「Ϩ」的十進位字元參考：

```
&#1000;
```

下列範例顯示十六進位字元參考。 請注意，它在十六進位數位前面有一個**x** 。

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>編碼
 @No__t-0 支援的編碼是 ASCII、[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 和 UTF-8。 編碼語句位於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔的開頭。 如果沒有任何編碼屬性，而且沒有位元組順序，則剖析器預設為 UTF-8。 UTF-8 和 UTF-16 是慣用的編碼。 不支援 UTF-7。 下列範例示範如何在 @no__t 0 檔案中指定 UTF-8 編碼。

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>語言屬性
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 會使用[xml： lang](../../xaml-services/xml-lang-handling-in-xaml.md)來代表專案的 language 屬性。  若要利用 @no__t 0 類別，語言屬性值必須是預先定義的其中一個文化特性名稱 <xref:System.Globalization.CultureInfo>。 [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) 在項目樹狀結構中為可繼承 (依 XML 規則，不一定是因為相依性屬性繼承)，如未明確指派，其預設值為空字串。

 語言屬性在指定方言方面非常有用。 例如，法國、魁北克、比利時和瑞士的法文拼字、字彙和發音不同。 此外，中文、日文和韓文共用 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] 的程式碼點，但表意形狀不同，而且使用完全不同的字型。

 下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會使用 `fr-CA` language 屬性來指定加拿大法文。

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 支援所有的 @no__t 1 功能，包括代理。 只要字元集可以對應到 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]，就會受到支援。 例如，GB18030 推出可對應至中文、日文和韓文 (CFK) 延伸模組 A 和 B 及 surrogate 字組的某些字元，因此受到完整支援。 @No__t-0 應用程式可以使用 <xref:System.Globalization.StringInfo> 來操作字串，而不需要瞭解它們是否有代理項配對或結合字元。

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>使用 XAML 設計國際化的使用者介面
 本節說明您在撰寫應用程式時應考慮的 @no__t 0 功能。

<a name="intl_text"></a>
### <a name="international-text"></a>國際文字
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含內建的處理，適用于所有 Microsoft .NET Framework 支援的書寫系統。

 目前支援下列指令碼︰

- 阿拉伯文

- 孟加拉文

- 梵文字母

- 斯拉夫文

- 希臘文

- 古吉拉特文

- 果魯穆奇文

- 希伯來文

- 表意指令碼

- 坎那達文

- 寮文

- 拉丁文

- 馬來亞拉姆文

- 蒙古文

- 歐迪亞文

- 敘利亞文

- 坦米爾文

- 特拉古文

- 塔安那文

- 泰文*

- 西藏文

 *本版支援泰文文字的顯示和編輯，不支援斷詞。

 目前不支援下列指令碼︰

- 高棉文

- 古韓文

- 緬甸文

- 僧伽羅文

 所有的書寫系統引擎都支援 OpenType 字型。 OpenType 字型可以包含 OpenType 版面配置資料表，讓字型建立者能夠設計更好的國際和高階印刷樣式。 OpenType 字型版面配置表包含圖像替換、圖像定位、對齊和基準定位的相關資訊，可讓文字處理應用程式改善文字版面配置。

 OpenType 字型可讓您使用 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] 編碼來處理大型圖像集。 這類編碼促進廣泛的國際支援以及各種印刷樣式字符。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字轉譯是由支援解析度獨立性的 Microsoft ClearType 子圖元技術提供技術支援。 這會大幅改善可讀性，並可讓您支援所有指令碼的高品質雜誌樣式文件。

<a name="intl_layout"></a>
### <a name="international-layout"></a>國際版面配置
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供非常方便的方式來支援水平、雙向和垂直版面配置。 在展示架構中，可以使用 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性來定義版面配置。 流程方向模式有︰

- *LeftToRight* - 拉丁文、東亞等的水平配置。

- *RightToLeft* - 阿拉伯文、希伯來文等的雙向配置。

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>開發可當地語系化的應用程式
 當您撰寫供全域使用的應用程式時，您應該記住應用程式必須是可當地語系化。 下列主題指出要考量的事項。

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>多語系使用者介面
 多語系使用者介面（MUI）是一種 Microsoft 支援，可將 Ui 從某種語言切換成另一種語言。 @No__t-0 應用程式會使用元件模型來支援 MUI。 一個應用程式包含語言中性的組件以及語言相關的附屬資源組件。 進入點是主要組件中的 Managed .EXE。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資源載入器會利用 @no__t 1 的資源管理員來支援資源查閱和回溯。 多語言附屬組件使用相同的主要組件。 載入的資源元件取決於目前線程的 @no__t 0。

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>可當地語系化的使用者介面
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來定義其 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 可讓開發人員使用一組屬性和邏輯指定物件的階層。 @No__t-0 的主要用途是開發 @no__t 1 應用程式，但它可以用來指定任何 common language runtime （CLR）物件的階層架構。 大部分的開發人員會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來指定其應用程式的 @no__t 1，並使用之類C#的程式設計語言來回應使用者互動。

 從資源的觀點來看，設計用來描述語言相依 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 @no__t 0 檔案是資源元素，因此其最終散發格式必須可當地語系化以支援國際語言。 因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 無法處理事件，許多 @no__t 1 應用程式包含執行這項操作的區塊。 如需詳細資訊，請參閱[XAML 總覽（WPF）](xaml-overview-wpf.md)。 當 @no__t 0 檔案標記為 XAML 的 BAML 形式時，程式碼會被移除並編譯成不同的二進位檔。 BAML 格式的 XAML 檔案、映像和其他類型的 Managed 資源物件會內嵌到附屬資源組件中，以當地語系化為其他語言，或在不需要當地語系化時內嵌到主要組件中。

> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式支援所有 @no__t 1CLR 資源，包括字串資料表、影像等等。

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>組建可當地語系化的應用程式
 當地語系化表示將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 調整為不同的文化特性。 若要讓 @no__t 0 應用程式可當地語系化，開發人員需要將所有可當地語系化的資源建立到資源元件中。 資源元件已當地語系化成不同的語言，而程式碼後置使用資源管理 API 來載入。 @No__t-0 應用程式所需的其中一個檔案是專案檔（proj）。 專案檔案應該包含您在應用程式中使用的所有資源。 以下的 .csproj 檔案範例示範如何執行這項工作。

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 若要在您的應用程式中使用資源，請具現化 <xref:System.Resources.ResourceManager>，並載入您想要使用的資源。 下列範例示範如何進行這項操作。

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>使用 ClickOnce 與當地語系化的應用程式
 ClickOnce 是一種新的 Windows Forms 部署技術，會 Visual Studio 2005 發行。 它能讓應用程式安裝及升級 Web 應用程式。 當地語系化使用 ClickOnce 部署的應用程式時，只能在已當地語系化的文化特性中檢視它。 例如，如果已部署的應用程式已當地語系化為日文，則只能在日文 [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] （而不是英文視窗）上觀看。 這會造成問題，因為這是日文使用者執行英文版 Windows 的常見案例。

 此問題的解決方案是設定中性的語言後援屬性。 應用程式開發人員可以選擇性地從主要組件中移除資源，指定可在附屬組件中找到的資源對應至特定的文化特性。 若要控制此進程，請使用 <xref:System.Resources.NeutralResourcesLanguageAttribute>。 @No__t 0 類別的函式有兩個簽章，其中一個會採用 <xref:System.Resources.UltimateResourceFallbackLocation> 參數來指定 <xref:System.Resources.ResourceManager> 應將回退資源解壓縮的位置：主要元件或附屬元件。 下列範例顯示如何使用這個屬性。 針對最終的回溯位置，程式碼會讓 <xref:System.Resources.ResourceManager> 在目前執行之元件的目錄 "de" 子目錄中尋找資源。

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>另請參閱

- [WPF 全球化和當地語系化概觀](wpf-globalization-and-localization-overview.md)
