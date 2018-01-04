---
title: "架構屬性中繼資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fec11a973572dce9e8d6f77bf65ce31ee77eb41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="framework-property-metadata"></a>架構屬性中繼資料
針對在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 架構中視為 WPF 架構層級的物件項目屬性，報告架構屬性中繼資料選項。 WPF 架構層級指定一般會需要由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 簡報 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 和可執行檔處理的轉譯、資料繫結和屬性系統調整等功能。 這些系統會查詢架構屬性中繼資料，以判斷特定項目屬性的特定功能特性。  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。 您也應該已閱讀[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>架構屬性中繼資料通訊的內容  
 架構屬性中繼資料可分成下列分類︰  
  
-   報表配置的屬性會影響項目 (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>， <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>， <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>)。 如果屬性會影響的各個層面，而您一併實作，您可能會在中繼資料中設定這些旗標<xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>中您的類別，提供特定的轉譯行為和配置資訊的方法系統。 一般而言，這類實作會檢查相依性屬性是否屬性失效，這些相依性屬性在屬性中繼資料中的任何配置屬性都是 true，而且只有這些失效需要要求新的配置傳遞。  
  
-   報表配置的屬性會影響項目的父項目 (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>， <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>)。 預設設定這些旗標的其中一些範例像是<xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType>和<xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>。  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. 相依性屬性預設不繼承值。 <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>可讓繼承可以也傳送至視覺化樹狀結構進行某些控制複合案例所需的路徑。  
  
    > [!NOTE]
    >  屬性值內容中的「繼承」一詞表示相依性屬性的特定項目，它表示因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的 WPF 架構層級功能，子項目可以繼承父項目的實際相依性屬性值。 它和 Managed 程式碼類型及透過衍生類型的成員繼承沒有直接關係。 如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
-   報告資料繫結特性 (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>， <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>)。 根據預設，架構中的相依性屬性以單向繫結行為支援資料繫結。 如果沒有任何案例，您可能會停用資料繫結 (因為它們具有彈性且可延伸，所以預設的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 中沒有太多這類屬性的範例)。 您可能設定要繫結在一起的控制項在其元件部分之間的行為的屬性預設雙向繫結 (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>舉例)，或雙向繫結的一般和預期使用者實例 (<xref:System.Windows.Controls.TextBox.Text%2A>是範例)。 對預設值一律可以變更的每個繫結而言，變更與資料繫結相關的中繼資料只會影響預設值。 如需繫結模式和一般繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
-   報告內容是否應該由應用程式或服務所支援日誌日誌型 (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>)。 一般項目預設不啟用日誌功能，但某些使用者輸入控制項會選擇性地啟用。 此屬性原由日誌服務讀取，包括 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作日誌功能，通常設定在使用者控制項，例如在所有瀏覽步驟都應保存之清單的使用者選取範圍。 如需日誌的相關資訊，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>讀取 FrameworkPropertyMetadata  
 每個上述連結的屬性是特定的屬性，<xref:System.Windows.FrameworkPropertyMetadata>將其直接基底類別加入<xref:System.Windows.UIPropertyMetadata>。 這些屬性每一個預設都是 `false`。 屬性，其中了解這些屬性的值是重要的中繼資料要求，應嘗試轉換要傳回之中繼資料<xref:System.Windows.FrameworkPropertyMetadata>，然後視需要檢查個別屬性的值。  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>指定中繼資料  
 當您建立的中繼資料的新執行個體供套用至新的相依性屬性註冊中繼資料時，您可以使用哪些中繼資料類別的選擇： 基底<xref:System.Windows.PropertyMetadata>或某些衍生類別，例如<xref:System.Windows.FrameworkPropertyMetadata>。 一般情況下，您應該使用<xref:System.Windows.FrameworkPropertyMetadata>，特別是當您的屬性具有屬性系統的任何互動和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]函式，例如版面配置和資料繫結。 更複雜的情況下的另一個選項是衍生自<xref:System.Windows.FrameworkPropertyMetadata>建立您自己的中繼資料報告的額外資訊的類別中傳遞其成員。 或者，您可能使用<xref:System.Windows.PropertyMetadata>或<xref:System.Windows.UIPropertyMetadata>通訊實作的功能的支援程度。  
  
 現有的屬性 (<xref:System.Windows.DependencyProperty.AddOwner%2A>或<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>呼叫)，您應該一律覆寫原始註冊所使用的中繼資料類型。  
  
 如果您要建立<xref:System.Windows.FrameworkPropertyMetadata>執行個體，有兩種方法來填入該中繼資料與通訊的架構屬性特性的特定屬性的值：  
  
1.  使用<xref:System.Windows.FrameworkPropertyMetadata>建構函式簽章，讓`flags`參數。 這個參數必須包含所有所需的結合值的填滿<xref:System.Windows.FrameworkPropertyMetadataOptions>列舉旗標。  
  
2.  使用其中一個不含簽章`flags`參數，然後設定每個報告上的布林值屬性<xref:System.Windows.FrameworkPropertyMetadata>至`true`的每一個所要變更的特性。 如果這麼做，您必須先設定這些屬性，才能建構具有此相依性屬性的任何項目；布林值屬性為讀寫，以允許此避免 `flags` 參數的行為，且仍可填入中繼資料，但在屬性使用前必須有效密封中繼資料。 因此，嘗試在要求中繼資料之後設定屬性，是無效的作業。  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>架構屬性中繼資料合併行為  
 當您覆寫架構屬性中繼資料時，不同的中繼資料特性會被合併或取代。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>會合併。 如果您將加入新<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>，回撥會儲存在中繼資料。 如果您未指定<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>中覆寫時，值<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>升級為最接近的祖系所指定中繼資料中的參考。  
  
-   實際內容系統行為<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>是它實作的階層中的所有中繼資料擁有者會保留並新增至資料表，與正在，最深的衍生類別的回呼屬性系統的執行順序第一次叫用。 繼承的回撥只執行一次，視為將它們放在中繼資料的類別所擁有。  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A>會被取代。 如果您未指定<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>中覆寫時，值<xref:System.Windows.PropertyMetadata.DefaultValue%2A>來自指定中繼資料中最接近上階。  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>實作會被取代。 如果您將加入新<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>，回撥會儲存在中繼資料。 如果您未指定<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中覆寫時，值<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>升級為最接近的祖系所指定中繼資料中的參考。  
  
-   屬性的系統行為是只<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>立即的中繼資料中叫用。 沒有參考至其他<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>會保留階層中的實作。  
  
-   旗標<xref:System.Windows.FrameworkPropertyMetadataOptions>列舉型別會結合為位元 OR 運算。  如果您指定<xref:System.Windows.FrameworkPropertyMetadataOptions>，不會覆寫原始的選項。  若要變更選項，將對應的屬性上<xref:System.Windows.FrameworkPropertyMetadata>。 例如，如果原始<xref:System.Windows.FrameworkPropertyMetadata>物件集<xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>旗標，您可以藉由設定變更，<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType>至`false`。  
  
 此行為由實作<xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>，而且可以加以覆寫衍生的中繼資料類別上。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>  
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
