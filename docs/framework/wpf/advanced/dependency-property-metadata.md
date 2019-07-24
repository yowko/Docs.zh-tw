---
title: 相依性屬性中繼資料
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: 800bf80e5ba3e697c122bcf4b1bc0f302357d087
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401623"
---
# <a name="dependency-property-metadata"></a>相依性屬性中繼資料
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]屬性系統包含的元資料包告系統, 超出了透過反映或通用 common language runtime (CLR) 特性來報告屬性的內容。 相依性屬性的中繼資料也可由定義相依性屬性的類別唯一指派、在相依性屬性新增至不同類別時變更，以及由從定義的基底類別繼承相依性屬性的所有衍生類別明確覆寫。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別的現有相依性屬性消費者角度了解相依性屬性，並已閱讀[相依性屬性概觀](dependency-properties-overview.md)。 為了解本主題中的範例，您也應該了解 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>相依性屬性中繼資料的使用方式  
 相依性屬性中繼資料以物件的形式存在，可接受查詢來查看相依性屬性的特性。 屬性系統也經常存取此中繼資料，因為它會處理任何指定的相依性屬性。 相依性屬性的中繼資料物件可包含下列類型的資訊：  
  
- 相依性屬性的預設值 (如果無法由區域數值、樣式、繼承等判斷出相依性屬性的其他值)。如需預設值在屬性系統指派相依性屬性的值時所佔優先順序的完整說明，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。  
  
- 影響各擁有者類型之強制型轉或變更通知行為的回呼實作參考。 請注意，這些回呼通常是在非公用存取層級定義，因此一般無法從中繼資料取得實際參考，除非參考位於允許的存取範圍內。 如需相依性屬性回呼的詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。  
  
- 如果將考慮中的相依性屬性視為 WPF 架構層級屬性，中繼資料可能會包含 WPF 架構層級相依性屬性特性，以報告服務的資訊和狀態 (例如 WPF 架構層級配置引擎和屬性繼承邏輯)。 如需相依性屬性中繼資料在這方面的詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>中繼資料 API  
 報告屬性系統所使用之大部分中繼資料資訊的型別是<xref:System.Windows.PropertyMetadata>類別。 當相依性屬性向屬性系統註冊時，會選擇性指定中繼資料執行個體，而且若有其他類型將自身作為擁有者新增或覆寫從基底類別相依性屬性定義繼承的中繼資料，則可再次指定中繼資料執行個體 (在屬性註冊未指定中繼資料的情況下, 會使用<xref:System.Windows.PropertyMetadata>該類別的預設值建立預設值)。<xref:System.Windows.PropertyMetadata>當您呼叫從<xref:System.Windows.DependencyObject>實例上的相依性屬性取得中繼資料的各種多<xref:System.Windows.DependencyProperty.GetMetadata%2A>載時, 會傳回已註冊的中繼資料。  
  
 然後<xref:System.Windows.PropertyMetadata> , 類別會衍生自, 以針對架構分割 (例如 WPF 架構層級類別) 提供更具體的中繼資料。 <xref:System.Windows.UIPropertyMetadata>加入動畫報表, 並<xref:System.Windows.FrameworkPropertyMetadata>提供上一節中所述的 WPF 架構層級屬性。 註冊相依性屬性時, 可以向這些<xref:System.Windows.PropertyMetadata>衍生類別註冊。 當檢查中繼資料時, 基底<xref:System.Windows.PropertyMetadata>類型可能會轉換成衍生類別, 讓您可以檢查更具體的屬性。  
  
> [!NOTE]
>  在此檔中, 可以指定<xref:System.Windows.FrameworkPropertyMetadata>的屬性特性有時稱為「旗標」。 當您建立新的中繼資料實例以用於相依性屬性註冊或中繼資料覆寫時, 您可以使用<xref:System.Windows.FrameworkPropertyMetadataOptions>旗標型列舉來指定這些值, 然後將列舉的可能串連值提供給<xref:System.Windows.FrameworkPropertyMetadata>函數。 不過, 在結構化之後, 這些選項特性會<xref:System.Windows.FrameworkPropertyMetadata>以一系列的布林值屬性 (而不是「結構化列舉值」) 的形式公開在中。 布林值屬性可讓您查看每個條件，而不需要將遮罩套用到旗標型列舉值以取得所需的資訊。 此函式會使用<xref:System.Windows.FrameworkPropertyMetadataOptions>串連的, 以保持可合理的函式簽章長度, 而實際的結構化中繼資料會公開離散屬性, 讓查詢中繼資料更加直覺。  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>何時覆寫中繼資料及衍生類別  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統能夠變更相依性屬性的部分特性，而不需要重新實作整個屬性。 這是由於相依性屬性位於特定類型上，因此可藉由為相依性屬性建構不同的屬性中繼資料執行個體來達成。 請注意，大多數現有相依性屬性不是虛擬屬性，因此嚴格來說，要在繼承的類別上「重新實作」這些屬性，只能藉由鏡像處理現有成員來達成。  
  
 如果您要嘗試為某個類型上的相依性屬性啟用的情節，無法藉由修改現有相依性屬性的特性來達成，則可能需要建立衍生類別，然後在該衍生類別上宣告自訂相依性屬性。 自訂相依性屬性的行為與 api 所[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]定義的相依性屬性完全相同。 如需自訂相依性屬性的詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)。  
  
 您無法覆寫的相依性屬性有一個值得注意的特性，那就是它的實值型別。 如果您繼承的相依性屬性所具有的行為大致符合需求，但此相依性屬性需要不同的類型，就必須實作自訂相依性屬性，而且可能需要透過類型轉換或自訂類別上的其他實作連結屬性。 此外, 您也無法取代現有<xref:System.Windows.ValidateValueCallback>的, 因為此回呼存在於註冊欄位本身, 而不在其中繼資料內。  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>變更現有中繼資料的情節  
 如果您使用現有相依性屬性的中繼資料，變更相依性屬性中繼資料的一個常見情節是變更預設值。 變更或新增屬性系統回呼是更進階的情節。 如果您的衍生類別實作在相依性屬性之間有不同的相互關係，就可能會想要這麼做。 具有同時支援程式碼和宣告式使用方式之程式設計模型的條件之一，就是屬性必須能夠以任何順序設定。 因此，任何相依性屬性都必須在沒有內容的情況下進行 Just-In-Time 設定，不能依賴建構函式中可能找到的設定順序來進行設定。 如需屬性系統在這方面的詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。 請注意，驗證回呼不是中繼資料的一部分，而是相依性屬性識別項的一部分。 因此，您無法藉由覆寫中繼資料來變更驗證回呼。  
  
 在某些情況下，您可能也想變更現有相依性屬性上的 WPF 架構層級屬性中繼資料選項。 這些選項會將 WPF 架構層級屬性的某些已知條件傳達給其他 WPF 架構層級處理序 (例如配置系統)。  設定選項通常只有在註冊新的相依性屬性時才會完成, 但是也可以在<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>或<xref:System.Windows.DependencyProperty.AddOwner%2A>呼叫中變更 WPF 架構層級的屬性中繼資料。 如需要使用的特定值和詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。 如需如何針對新註冊的相依性屬性設定這些選項的詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)。  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>覆寫中繼資料  
 覆寫中繼資料的目的，主要是讓您有機會變更各種中繼資料衍生的行為，這些行為會套用到類型上的相依性屬性。 [中繼資料](#dp_metadata_contents)一節會詳細說明原因。 如需詳細資訊，包括一些程式碼範例，請參閱[覆寫相依性屬性的中繼資料](how-to-override-metadata-for-a-dependency-property.md)。  
  
 在註冊呼叫 (<xref:System.Windows.DependencyProperty.Register%2A>) 期間, 可以提供相依性屬性的屬性中繼資料。 不過，在許多情況下，當您的類別繼承該相依性屬性時，您可能會想要為類別提供特定類型的中繼資料。 您可以藉由呼叫<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>方法來執行這項操作。  如需[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] api 的範例<xref:System.Windows.FrameworkElement> , 類別是第一次註冊<xref:System.Windows.UIElement.Focusable%2A>相依性屬性的型別。 但是, `false` `true` <xref:System.Windows.UIElement.Focusable%2A>類別會覆寫相依性屬性的中繼資料, 以提供它自己的初始預設值, 將它從變更為, 否則會重新使用原始的執行。 <xref:System.Windows.Controls.Control>  
  
 當您覆寫中繼資料時，不同的中繼資料特性會被合併或取代。  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>已合併。 如果您加入新<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>的, 該回呼就會儲存在中繼資料中。 如果您未<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>在覆寫中指定, 則的<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>值會升級為最接近的上階 (在中繼資料中指定) 的參考。  
  
- 的實際屬性系統行為<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>是將階層中所有中繼資料擁有者的執行保留並加入資料表中, 而屬性系統會先叫用最常衍生的類別回呼。  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>已取代。 如果您未<xref:System.Windows.PropertyMetadata.DefaultValue%2A>在覆寫中指定, 的<xref:System.Windows.PropertyMetadata.DefaultValue%2A>值會來自在中繼資料中指定它的最接近上階。  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>系統會取代實作為。 如果您加入新<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>的, 該回呼就會儲存在中繼資料中。 如果您未<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>在覆寫中指定, 則的<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>值會升級為最接近的上階 (在中繼資料中指定) 的參考。  
  
- 屬性系統行為是只會叫用<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>立即中繼資料中的。 不會保留階層<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>中其他實體系的參考。  
  
 這個行為是由<xref:System.Windows.PropertyMetadata.Merge%2A>所執行, 而且可以在衍生的中繼資料類別上覆寫。  
  
#### <a name="overriding-attached-property-metadata"></a>覆寫附加屬性中繼資料  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，附加屬性會以相依性屬性的方式實作。 這表示它們也有屬性中繼資料，可供個別類別覆寫。 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , 附加屬性的範圍考慮通常是任何<xref:System.Windows.DependencyObject>可以設定的附加屬性。 因此, 任何<xref:System.Windows.DependencyObject>衍生的類別都可以覆寫任何附加屬性的中繼資料, 因為它可能會在類別的實例上設定。 您可以覆寫預設值、回呼或 WPF 架構層級特性報告屬性。 如果在類別執行個體上設定附加屬性，則會套用這些覆寫屬性中繼資料特性。 例如，您可以覆寫預設值，只要沒有另外設定屬性，就會將覆寫值回報為類別執行個體上附加屬性的值。  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>屬性與附加屬性不相關。  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>新增類別作為現有相依性屬性的擁有者  
 類別可以使用<xref:System.Windows.DependencyProperty.AddOwner%2A>方法, 將本身新增為已註冊之相依性屬性的擁有者。 這可讓類別使用原本註冊給其他類型的相依性屬性。 新增的類別通常不是原先註冊該相依性屬性作為擁有者之類型的衍生類別。 實際上，這可讓類別及其衍生類別「繼承」相依性屬性實作，而原始擁有者類別和新增的類別不需要在同一個真實類別階層中。 此外，新增的類別 (及所有衍生類別) 接著可為原始相依性屬性提供特定類型的中繼資料。  
  
 除了透過屬性系統公用程式方法自行新增作為擁有者，新增的類別也應在本身上宣告其他公用成員，讓相依性屬性完全融合在屬性系統中，並能公開給程式碼和標記。 新增現有相依性屬性的類別與定義新自訂相依性屬性的類別一樣，也必須公開該相依性屬性的物件模型。 第一個要公開的成員是相依性屬性識別項欄位。 此欄位應該`public static readonly`是類型<xref:System.Windows.DependencyProperty>的欄位, 它會指派給<xref:System.Windows.DependencyProperty.AddOwner%2A>呼叫的傳回值。 要定義的第二個成員是 common language runtime (CLR) 「包裝函式」屬性。 包裝函式可讓您更方便地在程式碼中操作相依性屬性 (您<xref:System.Windows.DependencyObject.SetValue%2A>可以避免每次呼叫, 而且只能在包裝函式本身中呼叫一次)。 包裝函式的實作方式與註冊自訂相依性屬性時實作包裝函式的方式完全相同。 如需實作相依性屬性的詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)和[新增相依性屬性的擁有者類型](how-to-add-an-owner-type-for-a-dependency-property.md)。  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner 和附加屬性  
 您可以針對<xref:System.Windows.DependencyProperty.AddOwner%2A>由 owner 類別定義為附加屬性的相依性屬性呼叫。 一般這麼做的原因是要將先前的附加屬性公開為非附加相依性屬性。 接著, 您會將<xref:System.Windows.DependencyProperty.AddOwner%2A>傳回值`public static readonly`公開為當做相依性屬性識別碼使用的欄位, 並定義適當的「包裝函式」屬性, 讓屬性出現在 members 資料表中, 並支援非附加屬性類別中的使用方式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.PropertyMetadata>
- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [相依性屬性概觀](dependency-properties-overview.md)
- [架構屬性中繼資料](framework-property-metadata.md)
