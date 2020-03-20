---
title: 架構屬性中繼資料
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 8fb6e1b4cf6aed9454e9e9f1a77277d2f3611ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186659"
---
# <a name="framework-property-metadata"></a>架構屬性中繼資料
針對在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 架構中視為 WPF 架構層級的物件項目屬性，報告架構屬性中繼資料選項。 通常，WPF 框架級別指定需要由[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]呈現 API 和可執行檔處理呈現、資料繫結和屬性系統優化等功能。 這些系統會查詢架構屬性中繼資料，以判斷特定項目屬性的特定功能特性。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)。 您也應該已閱讀[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>
## <a name="what-is-communicated-by-framework-property-metadata"></a>架構屬性中繼資料通訊的內容  
 架構屬性中繼資料可分成下列分類︰  
  
- 影響元素 （的報表佈局屬性<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>。 如果屬性影響這些相關方面，並且還在實現<xref:System.Windows.FrameworkElement.MeasureOverride%2A> / <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>類中的方法向佈局系統提供特定的呈現行為和資訊，則可以在中繼資料中設置這些標誌。 一般而言，這類實作會檢查相依性屬性是否屬性失效，這些相依性屬性在屬性中繼資料中的任何配置屬性都是 true，而且只有這些失效需要要求新的配置傳遞。  
  
- 影響元素的父元素 （） 的報告佈局屬性<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>。 預設情況下設置這些標誌的一些示例是<xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType>和<xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>。  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. 相依性屬性預設不繼承值。 <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>允許繼承路徑也進入視覺化樹，這是某些控制合成方案所必需的。  
  
    > [!NOTE]
    > 屬性值內容中的「繼承」一詞表示相依性屬性的特定項目，它表示因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的 WPF 架構層級功能，子項目可以繼承父項目的實際相依性屬性值。 它和 Managed 程式碼類型及透過衍生類型的成員繼承沒有直接關係。 如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。  
  
- 報告資料繫結特徵<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>（。 <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> 根據預設，架構中的相依性屬性以單向繫結行為支援資料繫結。 如果沒有任何方案，則可以禁用資料繫結（因為它們旨在靈活且可擴展，因此預設[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API 中此類屬性的示例並不多）。 您可以將綁定設置為具有雙向預設值，這些屬性將控制項的行為綁定到其元件部分（<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>示例），或者雙向綁定是使用者常見和預期方案（<xref:System.Windows.Controls.TextBox.Text%2A>示例）。 對預設值一律可以變更的每個繫結而言，變更與資料繫結相關的中繼資料只會影響預設值。 如需繫結模式和一般繫結的詳細資訊，請參閱[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。  
  
- 報告是否應由支援日記的應用程式或服務進行日記。<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A> 一般項目預設不啟用日誌功能，但某些使用者輸入控制項會選擇性地啟用。 此屬性原由日誌服務讀取，包括 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作日誌功能，通常設定在使用者控制項，例如在所有瀏覽步驟都應保存之清單的使用者選取範圍。 如需日誌的相關資訊，請參閱[巡覽概觀](../app-development/navigation-overview.md)。  
  
<a name="Reading_FrameworkPropertyMetadata"></a>
## <a name="reading-frameworkpropertymetadata"></a>讀取 FrameworkPropertyMetadata  
 上面連結的每個屬性都是添加到<xref:System.Windows.FrameworkPropertyMetadata>其直接基類<xref:System.Windows.UIPropertyMetadata>的特定屬性。 這些屬性每一個預設都是 `false`。 知道這些屬性的值很重要的屬性的中繼資料請求應嘗試將返回的中繼資料強制轉換為<xref:System.Windows.FrameworkPropertyMetadata>，然後根據需要檢查各個屬性的值。  
  
<a name="Specifying_Metadata"></a>
## <a name="specifying-metadata"></a>指定中繼資料  
 當您創建新的中繼資料實例以將中繼資料應用於新的依賴項屬性註冊時，您可以選擇要使用的中繼資料類：基<xref:System.Windows.PropertyMetadata>或某些派生類（如<xref:System.Windows.FrameworkPropertyMetadata>）。 通常，應使用<xref:System.Windows.FrameworkPropertyMetadata>，特別是如果屬性與屬性系統和佈局和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料繫結等函數有任何交互。 更複雜的方案的另一個選項是從中派生<xref:System.Windows.FrameworkPropertyMetadata>來創建自己的元資料包告類，其中包含了額外的資訊。 或者，<xref:System.Windows.PropertyMetadata>您可以使用或<xref:System.Windows.UIPropertyMetadata>傳達對實現功能的支援程度。  
  
 對於現有屬性（<xref:System.Windows.DependencyProperty.AddOwner%2A>或<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>調用），應始終使用原始註冊使用的元資料類型進行重寫。  
  
 如果要創建<xref:System.Windows.FrameworkPropertyMetadata>實例，有兩種方法可以用傳達框架屬性特徵的特定屬性的值填充該中繼資料：  
  
1. 使用允許<xref:System.Windows.FrameworkPropertyMetadata>參數`flags`的建構函式簽名。 此參數應用<xref:System.Windows.FrameworkPropertyMetadataOptions>枚舉標記的所有所需組合值填充。  
  
2. 使用沒有參數的簽名之一`flags`，然後為每個所需的特徵更改設置每個報告布林屬性。 <xref:System.Windows.FrameworkPropertyMetadata> `true` 如果這麼做，您必須先設定這些屬性，才能建構具有此相依性屬性的任何項目；布林值屬性為讀寫，以允許此避免 `flags` 參數的行為，且仍可填入中繼資料，但在屬性使用前必須有效密封中繼資料。 因此，嘗試在要求中繼資料之後設定屬性，是無效的作業。  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>
## <a name="framework-property-metadata-merge-behavior"></a>架構屬性中繼資料合併行為  
 當您覆寫架構屬性中繼資料時，不同的中繼資料特性會被合併或取代。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>合併。 如果添加新<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>，則回檔將存儲在中繼資料中。 如果在重寫<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>中未指定<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>.  
  
- 的實際<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>屬性系統行為是保留層次結構中所有中繼資料擁有者的實現並將其添加到表中，屬性系統的執行順序是首先調用最深入派生的類的回檔。 繼承的回撥只執行一次，視為將它們放在中繼資料的類別所擁有。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>已更換。 如果在重寫<xref:System.Windows.PropertyMetadata.DefaultValue%2A>中未指定<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>將替換實現。 如果添加新<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>，則回檔將存儲在中繼資料中。 如果在重寫<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中未指定<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>.  
  
- 屬性系統行為是僅調用直接中繼資料<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中的。 不會保留對層次結構<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中其他實現的引用。  
  
- <xref:System.Windows.FrameworkPropertyMetadataOptions>枚舉標誌合併為位或操作。  如果指定<xref:System.Windows.FrameworkPropertyMetadataOptions>，則原始選項不會覆蓋。  要更改選項，在 上<xref:System.Windows.FrameworkPropertyMetadata>設置相應的屬性。 例如，<xref:System.Windows.FrameworkPropertyMetadata>如果原始物件設置<xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>標誌，則可以通過設置為<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType>`false`更改該標誌。  
  
 此行為由<xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>實現，可以在派生中繼資料類上重寫。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
