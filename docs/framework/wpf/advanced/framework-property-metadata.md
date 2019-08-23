---
title: 架構屬性中繼資料
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: c08cf28880d86331e3b561f1749333d401ba903e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964209"
---
# <a name="framework-property-metadata"></a>架構屬性中繼資料
針對在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 架構中視為 WPF 架構層級的物件項目屬性，報告架構屬性中繼資料選項。 一般而言, WPF 架構層級的指定會要求轉譯、資料系結和屬性系統調整等功能, 由[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]展示 api 和可執行檔處理。 這些系統會查詢架構屬性中繼資料，以判斷特定項目屬性的特定功能特性。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)。 您也應該已閱讀[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>架構屬性中繼資料通訊的內容  
 架構屬性中繼資料可分成下列分類︰  
  
- 會影響元素的報表配置屬性 (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>)。 如果屬性會影響這些個別層面, 您可能會在中繼資料中設定這些旗標, 而且<xref:System.Windows.FrameworkElement.MeasureOverride%2A>您也會在類別中執行 /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法, 以提供特定的轉譯行為和資訊給版面配置筆記本電腦. 一般而言，這類實作會檢查相依性屬性是否屬性失效，這些相依性屬性在屬性中繼資料中的任何配置屬性都是 true，而且只有這些失效需要要求新的配置傳遞。  
  
- 會影響元素之父元素的報表配置屬性 (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>、 <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>)。 預設會設定這些旗標的範例為<xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType>和。 <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. 相依性屬性預設不繼承值。 <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>允許繼承的路徑也會傳送至視覺化樹狀結構, 這是某些控制群組合案例的必要項。  
  
    > [!NOTE]
    > 屬性值內容中的「繼承」一詞表示相依性屬性的特定項目，它表示因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的 WPF 架構層級功能，子項目可以繼承父項目的實際相依性屬性值。 它和 Managed 程式碼類型及透過衍生類型的成員繼承沒有直接關係。 如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。  
  
- 報告資料系結特性<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>( <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>、)。 根據預設，架構中的相依性屬性以單向繫結行為支援資料繫結。 如果沒有任何案例, 您可能會停用資料系結 (因為它們的目的是要有彈性且可延伸, 因此在預設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] api 中, 這類屬性並不會有許多範例)。 您可能會將系結設定為具有雙向預設值, 以便將控制項的行為系結到其元件片段 (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>例如), 或雙向系結為使用者的常見和預期案例 (<xref:System.Windows.Controls.TextBox.Text%2A>例如)。 對預設值一律可以變更的每個繫結而言，變更與資料繫結相關的中繼資料只會影響預設值。 如需繫結模式和一般繫結的詳細資訊，請參閱[資料繫結概觀](../data/data-binding-overview.md)。  
  
- 報告屬性是否應由支援日誌的應用程式或服務記錄 (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>)。 一般項目預設不啟用日誌功能，但某些使用者輸入控制項會選擇性地啟用。 此屬性原由日誌服務讀取，包括 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作日誌功能，通常設定在使用者控制項，例如在所有瀏覽步驟都應保存之清單的使用者選取範圍。 如需日誌的相關資訊，請參閱[巡覽概觀](../app-development/navigation-overview.md)。  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>讀取 FrameworkPropertyMetadata  
 上述連結的每個屬性都是可<xref:System.Windows.FrameworkPropertyMetadata>新增至其直接<xref:System.Windows.UIPropertyMetadata>基類的特定屬性。 這些屬性每一個預設都是 `false`。 屬性的中繼資料要求若知道這些屬性的值, 就應該嘗試將傳回的中繼資料轉換成<xref:System.Windows.FrameworkPropertyMetadata>, 然後視需要檢查個別屬性的值。  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>指定中繼資料  
 當您建立新的中繼資料實例以將中繼資料套用至新的相依性屬性註冊時, 您可以選擇要使用的中繼資料類別: <xref:System.Windows.PropertyMetadata>基底或部分衍生類別<xref:System.Windows.FrameworkPropertyMetadata>, 例如。 一般來說, 您應該使用<xref:System.Windows.FrameworkPropertyMetadata>, 特別是當您的屬性與屬性系統和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]功能 (例如版面配置和資料系結) 互動時。 更複雜案例的另一個選項是從<xref:System.Windows.FrameworkPropertyMetadata>衍生, 以建立您自己的元資料包告類別, 並在其成員中攜帶額外的資訊。 或者, 您可以<xref:System.Windows.PropertyMetadata>使用<xref:System.Windows.UIPropertyMetadata>或來傳達您的執行功能的支援程度。  
  
 針對現有的屬性<xref:System.Windows.DependencyProperty.AddOwner%2A> ( <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>或呼叫), 您應該一律使用原始註冊所使用的元資料類型來覆寫。  
  
 如果您要建立<xref:System.Windows.FrameworkPropertyMetadata>實例, 有兩種方式可將特定屬性的值填入該中繼資料, 以傳達架構屬性的特性:  
  
1. 使用允許參數的<xref:System.Windows.FrameworkPropertyMetadata> `flags`函數簽章。 此參數應該填入<xref:System.Windows.FrameworkPropertyMetadataOptions>列舉旗標的所有所需組合值。  
  
2. 使用其中一個不含`flags`參數的簽章, 然後針對每個所需的特性變更, 將上<xref:System.Windows.FrameworkPropertyMetadata>的每個報告布林值屬性設定為`true` 。 如果這麼做，您必須先設定這些屬性，才能建構具有此相依性屬性的任何項目；布林值屬性為讀寫，以允許此避免 `flags` 參數的行為，且仍可填入中繼資料，但在屬性使用前必須有效密封中繼資料。 因此，嘗試在要求中繼資料之後設定屬性，是無效的作業。  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>架構屬性中繼資料合併行為  
 當您覆寫架構屬性中繼資料時，不同的中繼資料特性會被合併或取代。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>已合併。 如果您加入新<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>的, 該回呼就會儲存在中繼資料中。 如果您未<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>在覆寫中指定, 則的<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>值會升級為最接近的上階 (在中繼資料中指定) 的參考。  
  
- 的實際屬性系統行為<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>是, 階層中所有中繼資料擁有者的執行都會保留並加入至資料表中, 而屬性系統會透過此順序, 將最深層衍生類別的回呼設為先叫用。 繼承的回撥只執行一次，視為將它們放在中繼資料的類別所擁有。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>已取代。 如果您未<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>在覆寫中指定, 的<xref:System.Windows.PropertyMetadata.DefaultValue%2A>值會來自在中繼資料中指定它的最接近上階。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>系統會取代實作為。 如果您加入新<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>的, 該回呼就會儲存在中繼資料中。 如果您未<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>在覆寫中指定, 則的<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>值會升級為最接近的上階 (在中繼資料中指定) 的參考。  
  
- 屬性系統行為是只會叫用<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>立即中繼資料中的。 不會保留階層<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中其他實體系的參考。  
  
- <xref:System.Windows.FrameworkPropertyMetadataOptions>列舉的旗標會結合成位 or 運算。  如果您指定<xref:System.Windows.FrameworkPropertyMetadataOptions>, 則不會覆寫原始的選項。  若要變更選項, 請在上<xref:System.Windows.FrameworkPropertyMetadata>設定對應的屬性。 <xref:System.Windows.FrameworkPropertyMetadata>例如, 如果原始物件設定了<xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>旗標, 則您可以將設定<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType>為來`false`變更它。  
  
 這個行為是由<xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>所執行, 而且可以在衍生的中繼資料類別上覆寫。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
