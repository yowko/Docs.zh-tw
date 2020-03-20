---
title: 相依性屬性中繼資料
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 3d84510fce69e81929cbe9b6088e12aaf3409769
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186372"
---
# <a name="dependency-property-metadata"></a>相依性屬性中繼資料
屬性[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]系統包括一個元資料包告系統，該系統超出了通過反射或通用語言運行時 （CLR） 特徵可以報告的屬性的範圍。 相依性屬性的中繼資料也可由定義相依性屬性的類別唯一指派、在相依性屬性新增至不同類別時變更，以及由從定義的基底類別繼承相依性屬性的所有衍生類別明確覆寫。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)。 為遵循本主題中的範例，您也應該了解 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="dp_metadata_contents"></a>
## <a name="how-dependency-property-metadata-is-used"></a>相依性屬性中繼資料的使用方式  
 相依性屬性中繼資料以物件的形式存在，可接受查詢來查看相依性屬性的特性。 屬性系統也經常存取此中繼資料，因為它會處理任何指定的相依性屬性。 相依性屬性的中繼資料物件可包含下列類型的資訊：  
  
- 依賴項屬性的預設值，如果無法按本地值、樣式、繼承等為依賴項屬性確定其他值。有關預設值在為依賴項屬性分配值時如何參與屬性系統使用的優先順序的徹底討論，請參閱[依賴項屬性值優先順序](dependency-property-value-precedence.md)。  
  
- 影響各擁有者類型之強制型轉或變更通知行為的回呼實作參考。 請注意，這些回呼通常是在非公用存取層級定義，因此一般無法從中繼資料取得實際參考，除非參考位於允許的存取範圍內。 如需相依性屬性回呼的詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。  
  
- 如果將考慮中的相依性屬性視為 WPF 架構層級屬性，中繼資料可能會包含 WPF 架構層級相依性屬性特性，以報告服務的資訊和狀態 (例如 WPF 架構層級配置引擎和屬性繼承邏輯)。 如需相依性屬性中繼資料在這方面的詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。  
  
<a name="APIs"></a>
## <a name="metadata-apis"></a>中繼資料 API  
 報告屬性系統使用的大部分中繼資料資訊的類型是類<xref:System.Windows.PropertyMetadata>。 當相依性屬性向屬性系統註冊時，會選擇性指定中繼資料執行個體，而且若有其他類型將自身作為擁有者新增或覆寫從基底類別相依性屬性定義繼承的中繼資料，則可再次指定中繼資料執行個體 （對於屬性註冊不指定中繼資料的情況，使用該類的預設值<xref:System.Windows.PropertyMetadata>創建預設值。當您調用從<xref:System.Windows.PropertyMetadata><xref:System.Windows.DependencyObject>實例上的依賴項屬性獲取中繼資料的各種<xref:System.Windows.DependencyProperty.GetMetadata%2A>重載時，將返回已註冊的中繼資料。  
  
 然後<xref:System.Windows.PropertyMetadata>派生類，為體系結構分區（如 WPF 框架級類）提供更具體的中繼資料。 <xref:System.Windows.UIPropertyMetadata>添加動畫報告，並提供<xref:System.Windows.FrameworkPropertyMetadata>上一節中提到的 WPF 框架級屬性。 註冊依賴項屬性時，可以對這些<xref:System.Windows.PropertyMetadata>派生類進行註冊。 檢查中繼資料時，可以將基<xref:System.Windows.PropertyMetadata>類型強制轉換為派生類，以便可以檢查更具體的屬性。  
  
> [!NOTE]
> 可在 中<xref:System.Windows.FrameworkPropertyMetadata>指定的屬性特徵有時在本文檔中稱為"標誌"。 創建新中繼資料實例以用於依賴項屬性註冊或中繼資料重寫時，可以使用 Flagwise 枚<xref:System.Windows.FrameworkPropertyMetadataOptions>舉指定這些值，然後將枚舉的可能串聯值供應給<xref:System.Windows.FrameworkPropertyMetadata>建構函式。 但是，一旦構造，這些選項特徵將作為一系列<xref:System.Windows.FrameworkPropertyMetadata>布林屬性公開，而不是構造枚舉值。 布林值屬性可讓您查看每個條件，而不需要將遮罩套用到旗標型列舉值以取得所需的資訊。 建構函式使用串聯<xref:System.Windows.FrameworkPropertyMetadataOptions>來保持建構函式簽名的長度合理，而實際構造的中繼資料公開離散屬性，使查詢中繼資料更加直觀。  
  
<a name="override_or_subclass"></a>
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>何時覆寫中繼資料及衍生類別  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統能夠變更相依性屬性的部分特性，而不需要重新實作整個屬性。 這是由於相依性屬性位於特定類型上，因此可藉由為相依性屬性建構不同的屬性中繼資料執行個體來達成。 請注意，大多數現有相依性屬性不是虛擬屬性，因此嚴格來說，要在繼承的類別上「重新實作」這些屬性，只能藉由鏡像處理現有成員來達成。  
  
 如果您要嘗試為某個類型上的相依性屬性啟用的情節，無法藉由修改現有相依性屬性的特性來達成，則可能需要建立衍生類別，然後在該衍生類別上宣告自訂相依性屬性。 自訂依賴項屬性的行為與[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API 定義的依賴項屬性相同。 如需自訂相依性屬性的詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)。  
  
 您無法覆寫的相依性屬性有一個值得注意的特性，那就是它的實值型別。 如果您繼承的相依性屬性所具有的行為大致符合需求，但此相依性屬性需要不同的類型，就必須實作自訂相依性屬性，而且可能需要透過類型轉換或自訂類別上的其他實作連結屬性。 此外，您不能替換現有的<xref:System.Windows.ValidateValueCallback>，因為此回檔存在於註冊欄位本身中，而不是在其中繼資料中。  
  
<a name="scenarios"></a>
## <a name="scenarios-for-changing-existing-metadata"></a>變更現有中繼資料的情節  
 如果您使用現有相依性屬性的中繼資料，變更相依性屬性中繼資料的一個常見情節是變更預設值。 變更或新增屬性系統回呼是更進階的情節。 如果您的衍生類別實作在相依性屬性之間有不同的相互關係，就可能會想要這麼做。 具有同時支援程式碼和宣告式使用方式之程式設計模型的條件之一，就是屬性必須能夠以任何順序設定。 因此，任何相依性屬性都必須在沒有內容的情況下進行 Just-In-Time 設定，不能依賴建構函式中可能找到的設定順序來進行設定。 如需屬性系統在這方面的詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。 請注意，驗證回呼不是中繼資料的一部分，而是相依性屬性識別項的一部分。 因此，您無法藉由覆寫中繼資料來變更驗證回呼。  
  
 在某些情況下，您可能也想變更現有相依性屬性上的 WPF 架構層級屬性中繼資料選項。 這些選項會將 WPF 架構層級屬性的某些已知條件傳達給其他 WPF 架構層級處理序 (例如配置系統)。  設置選項通常僅在註冊新的依賴項屬性時完成，但也可以更改 WPF 框架級屬性中繼資料作為 或<xref:System.Windows.DependencyProperty.OverrideMetadata%2A><xref:System.Windows.DependencyProperty.AddOwner%2A>調用的一部分。 如需要使用的特定值和詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。 如需如何針對新註冊的相依性屬性設定這些選項的詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)。  
  
<a name="dp_override_metadata"></a>
### <a name="overriding-metadata"></a>覆寫中繼資料  
 覆寫中繼資料的目的，主要是讓您有機會變更各種中繼資料衍生的行為，這些行為會套用到類型上的相依性屬性。 [中繼資料](#dp_metadata_contents)一節會詳細說明原因。 如需詳細資訊，包括一些程式碼範例，請參閱[覆寫相依性屬性的中繼資料](how-to-override-metadata-for-a-dependency-property.md)。  
  
 可以在註冊調用期間為依賴項屬性提供屬性中繼資料 。<xref:System.Windows.DependencyProperty.Register%2A> 不過，在許多情況下，當您的類別繼承該相依性屬性時，您可能會想要為類別提供特定類型的中繼資料。 可以通過調用<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>方法來執行此操作。  對於 API 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的示例，<xref:System.Windows.FrameworkElement>類是首先註冊<xref:System.Windows.UIElement.Focusable%2A>依賴項屬性的類型。 但是，<xref:System.Windows.Controls.Control>該類重寫依賴項屬性的中繼資料以提供其自己的初始預設值，將其從`false`更改為`true`，然後重新使用原始<xref:System.Windows.UIElement.Focusable%2A>實現。  
  
 當您覆寫中繼資料時，不同的中繼資料特性會被合併或取代。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>合併。 如果添加新<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>，則回檔將存儲在中繼資料中。 如果在重寫<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>中未指定<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>.  
  
- 的實際<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>屬性系統行為是保留層次結構中所有中繼資料擁有者的實現並將其添加到表中，屬性系統的執行順序是首先調用派生最多的類的回檔。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>已更換。 如果在重寫<xref:System.Windows.PropertyMetadata.DefaultValue%2A>中未指定<xref:System.Windows.PropertyMetadata.DefaultValue%2A>。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>將替換實現。 如果添加新<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>，則回檔將存儲在中繼資料中。 如果在重寫<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中未指定<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>.  
  
- 屬性系統行為是僅調用直接中繼資料<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中的。 不會保留對層次結構<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中其他實現的引用。  
  
 此行為由<xref:System.Windows.PropertyMetadata.Merge%2A>實現，可以在派生中繼資料類上重寫。  
  
#### <a name="overriding-attached-property-metadata"></a>覆寫附加屬性中繼資料  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，附加屬性會以相依性屬性的方式實作。 這表示它們也有屬性中繼資料，可供個別類別覆寫。 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]附加屬性的範圍注意事項通常是，任何<xref:System.Windows.DependencyObject>屬性都可以在它們上設置附加屬性。 因此，任何<xref:System.Windows.DependencyObject>派生類都可以覆蓋任何附加屬性的中繼資料，因為它可能在類的實例上設置。 您可以覆寫預設值、回呼或 WPF 架構層級特性報告屬性。 如果在類別執行個體上設定附加屬性，則會套用這些覆寫屬性中繼資料特性。 例如，您可以覆寫預設值，只要沒有另外設定屬性，就會將覆寫值回報為類別執行個體上附加屬性的值。  
  
> [!NOTE]
> 該<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>屬性與附加屬性無關。  
  
<a name="dp_add_owner"></a>
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>新增類別作為現有相依性屬性的擁有者  
 類可以使用<xref:System.Windows.DependencyProperty.AddOwner%2A>方法將自己添加為已註冊的依賴項屬性的擁有者。 這可讓類別使用原本註冊給其他類型的相依性屬性。 新增的類別通常不是原先註冊該相依性屬性作為擁有者之類型的衍生類別。 實際上，這可讓類別及其衍生類別「繼承」相依性屬性實作，而原始擁有者類別和新增的類別不需要在同一個真實類別階層中。 此外，新增的類別 (及所有衍生類別) 接著可為原始相依性屬性提供特定類型的中繼資料。  
  
 除了透過屬性系統公用程式方法自行新增作為擁有者，新增的類別也應在本身上宣告其他公用成員，讓相依性屬性完全融合在屬性系統中，並能公開給程式碼和標記。 新增現有相依性屬性的類別與定義新自訂相依性屬性的類別一樣，也必須公開該相依性屬性的物件模型。 第一個要公開的成員是相依性屬性識別項欄位。 此欄位應為 類型`public static readonly`<xref:System.Windows.DependencyProperty>欄位，該欄位分配給調用的<xref:System.Windows.DependencyProperty.AddOwner%2A>傳回值。 要定義的第二個成員是通用語言運行時 （CLR） "包裝器"屬性。 包裝器使在代碼中操作依賴項屬性變得更加方便（您避免每次都調用<xref:System.Windows.DependencyObject.SetValue%2A>，並且只能在包裝器本身中進行一次調用）。 包裝函式的實作方式與註冊自訂相依性屬性時實作包裝函式的方式完全相同。 如需實作相依性屬性的詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)和[新增相依性屬性的擁有者類型](how-to-add-an-owner-type-for-a-dependency-property.md)。  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner 和附加屬性  
 您可以調用<xref:System.Windows.DependencyProperty.AddOwner%2A>由擁有者類定義為附加屬性的依賴項屬性。 一般這麼做的原因是要將先前的附加屬性公開為非附加相依性屬性。 然後，<xref:System.Windows.DependencyProperty.AddOwner%2A>您將將傳回值公開為用作`public static readonly`依賴項屬性識別碼的欄位，並將定義適當的"包裝"屬性，以便該屬性顯示在成員表中，並支援類中的非附加屬性用法。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [相依性屬性概觀](dependency-properties-overview.md)
- [架構屬性中繼資料](framework-property-metadata.md)
