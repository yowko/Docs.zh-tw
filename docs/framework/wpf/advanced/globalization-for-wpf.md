---
title: 全球化
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 2d7cf73e37fe8c4bbdbef3d356f1dbb8903815f3
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812324"
---
# <a name="globalization-for-wpf"></a>WPF 的全球化
本主題介紹在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 為全球市場撰寫應用程式時，您應該注意的問題。 全球化程式設計項目是在命名空間的 .NET 中定義 <xref:System.Globalization> 。

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML 全球化
 Extensible Application Markup Language (XAML) 是以 XML 為基礎，而且會利用 XML 規格中定義的全球化支援。 下列各節說明 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 您應該注意的一些功能。

<a name="char_reference"></a>
### <a name="character-references"></a>字元參考
字元參考會提供其所代表之特定 Unicode 字元的 UTF16 程式碼單位（以十進位或十六進位為單位）。 下列範例顯示適用于英數位元或 ' Ϩ ' 的十進位字元參考：

```xaml
&#1000;
```

下列範例顯示十六進位字元參考。 請注意，它的十六進位數位前面有 **x** 。

```xaml
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>編碼
 支援的編碼 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是 ASCII、UNICODE utf-16 和 utf-8。 編碼語句位於檔的開頭 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 如果沒有任何編碼屬性，而且沒有位元組順序，則剖析器預設為 UTF-8。 UTF-8 和 UTF-16 是慣用的編碼。 不支援 UTF-7。 下列範例示範如何在檔案中指定 UTF-8 編碼 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>語言屬性
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 使用 [xml： lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) 來代表專案的語言屬性。  若要利用 <xref:System.Globalization.CultureInfo> 類別，語言屬性值必須是預先定義的其中一個文化特性名稱 <xref:System.Globalization.CultureInfo> 。 [xml:lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) 在項目樹狀結構中為可繼承 (依 XML 規則，不一定是因為相依性屬性繼承)，如未明確指派，其預設值為空字串。

 語言屬性在指定方言方面非常有用。 例如，法國、魁北克、比利時和瑞士的法文拼字、字彙和發音不同。 此外，中文、日文和韓文也會以 Unicode 共用程式碼點，但表意圖案不同，而是使用完全不同的字型。

 下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會使用 `fr-CA` language 屬性來指定加拿大法文。

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 支援所有 Unicode 功能，包括代理。 只要字元集可以對應至 Unicode，就會受到支援。 例如，GB18030 推出可對應至中文、日文和韓文 (CFK) 延伸模組 A 和 B 及 surrogate 字組的某些字元，因此受到完整支援。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式可以使用 <xref:System.Globalization.StringInfo> 來操作字串，而不需要瞭解它們是否擁有代理配對或合併字元。

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>使用 XAML 設計國際化的使用者介面
 本節說明在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 撰寫應用程式時，您應該考慮的功能。

<a name="intl_text"></a>
### <a name="international-text"></a>國際文字
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含所有 Microsoft .NET Framework 支援的寫入系統內建處理。

 目前支援下列指令碼︰

- 阿拉伯文

- 孟加拉文

- 梵文字母

- 古斯拉夫文

- 希臘文

- 古吉拉特文

- 古木基文

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

- 泰盧固文

- 塔安那文

- 泰文*

- 西藏文

 *本版支援泰文文字的顯示和編輯，不支援斷詞。

 目前不支援下列指令碼︰

- 高棉文

- 古韓文

- 緬甸

- 僧伽羅文

 所有書寫系統引擎都支援 OpenType 字型。 OpenType 字型可以包含 OpenType 版面配置表，讓字型建立者可以設計更好的國際和高階印刷樣式字型。 OpenType 字型版面配置表包含圖像替換、圖像定位、理由和基準定位的相關資訊，可讓文字處理應用程式改善文字版面配置。

 OpenType 字型可讓您使用 Unicode 編碼來處理大型圖像集。 這類編碼促進廣泛的國際支援以及各種印刷樣式字符。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字轉譯是由支援解析度獨立性的 Microsoft ClearType 子圖元技術所提供。 這會大幅改善可讀性，並可讓您支援所有指令碼的高品質雜誌樣式文件。

<a name="intl_layout"></a>
### <a name="international-layout"></a>國際版面配置
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供非常方便的方式來支援水平、雙向和垂直版面配置。 在展示架構中， <xref:System.Windows.FrameworkElement.FlowDirection%2A> 可以使用屬性來定義版面配置。 流程方向模式有︰

- *LeftToRight* - 拉丁文、東亞等的水平配置。

- *RightToLeft* - 阿拉伯文、希伯來文等的雙向配置。

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>開發可當地語系化的應用程式
 當您撰寫供全域使用的應用程式時，您應該記住應用程式必須是可當地語系化。 下列主題指出要考量的事項。

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>多語系使用者介面
 多語系使用者介面 (MUI) 是 Microsoft 針對將 Ui 從一種語言切換至另一種語言的支援。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式會使用元件模型來支援 MUI。 一個應用程式包含語言中性的組件以及語言相關的附屬資源組件。 進入點是主要組件中的 Managed .EXE。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資源載入器會利用架構的資源管理員來支援資源查閱和回復。 多語言附屬組件使用相同的主要組件。 載入的資源元件取決於 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> 目前線程的。

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>可當地語系化的使用者介面
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來定義其 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 可讓開發人員使用一組屬性和邏輯指定物件的階層。 的主要用途 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 是開發 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式，但可以用來指定任何 common language RUNTIME (CLR) 物件的階層。 大部分的開發人員會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來指定其應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，並使用 c # 之類的程式設計語言來回應使用者互動。

 從資源的觀點來看， [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 設計用來描述語言相依的檔案 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 是資源元素，因此它的最終發佈格式必須可以當地語系化以支援國際語言。 因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 無法處理事件，所以許多 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式都包含程式碼區塊來進行這項作業。 如需詳細資訊，請參閱 [XAML 總覽 (WPF) ](../../../desktop-wpf/fundamentals/xaml.md)。 當檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 被標記為 BAML 形式的 XAML 時，會將程式碼去除並編譯成不同的二進位檔。 BAML 格式的 XAML 檔案、映像和其他類型的 Managed 資源物件會內嵌到附屬資源組件中，以當地語系化為其他語言，或在不需要當地語系化時內嵌到主要組件中。

> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式支援所有 FrameworkCLR 資源，包括字串資料表、影像等。

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>組建可當地語系化的應用程式
 當地語系化是指將調整 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 成不同的文化特性。 為了讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式可當地語系化，開發人員需要將所有可當地語系化的資源建立到資源元件中。 資源元件已當地語系化成不同的語言，而程式碼後端會使用資源管理 API 來載入。 應用程式所需的其中一個檔案 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是專案檔 ( 專案檔) 。 專案檔案應該包含您在應用程式中使用的所有資源。 以下的 .csproj 檔案範例示範如何執行這項工作。

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 若要在您的應用程式中使用資源，請具現化 <xref:System.Resources.ResourceManager> ，並載入您想要使用的資源。 下列範例示範如何進行這項操作。

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>使用 ClickOnce 與當地語系化的應用程式
 ClickOnce 是一種新的 Windows Forms 部署技術，將隨附 Visual Studio 2005。 它能讓應用程式安裝及升級 Web 應用程式。 當地語系化使用 ClickOnce 部署的應用程式時，只能在已當地語系化的文化特性中檢視它。 例如，如果已部署的應用程式已當地語系化為日文，則只能在日文 Microsoft Windows 上查看，而不是在英文 Windows 上。 這會造成問題，因為這是日文使用者執行英文版 Windows 的常見案例。

 此問題的解決方案是設定中性的語言後援屬性。 應用程式開發人員可以選擇性地從主要組件中移除資源，指定可在附屬組件中找到的資源對應至特定的文化特性。 若要控制此進程，請使用 <xref:System.Resources.NeutralResourcesLanguageAttribute> 。 類別的函式 <xref:System.Resources.NeutralResourcesLanguageAttribute> 有兩個簽章，一個採用 <xref:System.Resources.UltimateResourceFallbackLocation> 參數來指定應將其解壓縮回 <xref:System.Resources.ResourceManager> 資源的位置：主要元件或附屬元件。 下列範例顯示如何使用這個屬性。 針對最終的回溯位置，程式碼會使在 <xref:System.Resources.ResourceManager> 目前執行之元件目錄的 "de" 子目錄中尋找資源。

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>另請參閱

- [WPF 全球化和當地語系化概觀](wpf-globalization-and-localization-overview.md)
