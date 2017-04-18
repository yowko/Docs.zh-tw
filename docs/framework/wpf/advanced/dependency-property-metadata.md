---
title: "相依性屬性中繼資料 | Microsoft Docs"
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
  - "API, 中繼資料"
  - "相依性屬性, 中繼資料"
  - "中繼資料, 適用於相依性屬性"
  - "覆寫中繼資料"
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 相依性屬性中繼資料
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統包含中繼資料報告系統，其針對屬性所報告的內容比透過反映 \(Reflection\) 或一般 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 特性報告的還多。  [相依性屬性](GTMT)的中繼資料也可由定義[相依性屬性](GTMT)的類別唯一指派，也可在[相依性屬性](GTMT)加入到不同類別時變更，而且從定義的基底類別繼承[相依性屬性](GTMT)的所有衍生類別都可以明確加以覆寫。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已經從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別上的現有相依性屬性的消費者觀點來了解相依性屬性，而且已閱讀過[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  為了能夠理解本主題中的範例，您也應該了解 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="dp_metadata_contents"></a>   
## 相依性屬性中繼資料的使用方式  
 相依性屬性中繼資料以物件的形式存在，可接受查詢來檢視相依性屬性的特性。  屬性系統也經常存取中繼資料，因為它會處理任何指定的相依性屬性。  相依性屬性的中繼資料物件可包含下列類型的資訊：  
  
-   相依性屬性的預設值 \(若無法從區域數值、樣式、繼承等判斷出相依性屬性其他值\)。  如需預設值在屬性系統指派相依性屬性的值時所佔的優先順序，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)的完整說明。  
  
-   影響各擁有者型別強制型轉或變更通知行為之回呼實作的參考。  請注意，這些回呼通常是在非公用存取層級定義，因此一般無法從中繼資料取得實際參考，除非參考位於允許的存取範圍內。  如需相依性屬性回呼的詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)。  
  
-   如果相依性屬性是 [WPF 架構層級](GTMT)的屬性，中繼資料可能包含 [WPF 架構層級](GTMT)的相依性屬性特性，報告內容會是服務 \(如 [WPF 架構層級](GTMT)配置引擎和屬性繼承邏輯\) 的資訊和狀態。  如需相依性屬性中繼資料在這方面的詳細資訊，請參閱[架構屬性中繼資料](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)。  
  
<a name="APIs"></a>   
## 中繼資料 API  
 報告最多中繼資料的資訊供屬性系統使用的型別就是 <xref:System.Windows.PropertyMetadata> 類別。  當相依性屬性向屬性系統註冊時，會選擇性指定中繼資料執行個體，而且若有其他型別將自身做為擁有者加入或覆寫從基底類別相依性屬性定義繼承的中繼資料，則可再次指定中繼資料執行個體   \(若屬性註冊時沒有指定中繼資料，則會使用該類別的預設值建立預設 <xref:System.Windows.PropertyMetadata>\)。當您呼叫各種 <xref:System.Windows.DependencyProperty.GetMetadata%2A> 多載，從 <xref:System.Windows.DependencyObject> 執行個體上的相依性屬性取得中繼資料時，註冊的中繼資料就會以 <xref:System.Windows.PropertyMetadata> 傳回。  
  
 接著會從 <xref:System.Windows.PropertyMetadata> 類別衍生，以針對像是 [WPF 架構層級](GTMT)類別等架構細部提供特定的中繼資料。  <xref:System.Windows.UIPropertyMetadata> 會加入動畫報告，而 <xref:System.Windows.FrameworkPropertyMetadata> 則會提供上一節所述的 [WPF 架構層級](GTMT)屬性。  註冊相依性屬性時，它們可以與這些 <xref:System.Windows.PropertyMetadata> 衍生類別一起註冊。  當查看中繼資料時，基底 <xref:System.Windows.PropertyMetadata> 型別有可能會轉型為衍生類別，以便您查看特定的屬性。  
  
> [!NOTE]
>  本文有時會將可在 <xref:System.Windows.FrameworkPropertyMetadata> 中指定的屬性特性稱為「旗標」\(Flag\)。  當您建立新的中繼資料執行個體以供相依性屬性註冊作業或中繼資料覆寫作業使用時，可使用旗標型式列舉型別 <xref:System.Windows.FrameworkPropertyMetadataOptions> 指定這些值，然後將列舉型別的可能串連值提供給 <xref:System.Windows.FrameworkPropertyMetadata> 建構函式。  不過，一旦建構好之後，這些選項特性會以一連串的布林值屬性 \(而非建構列舉值\) 的形式公開在 <xref:System.Windows.FrameworkPropertyMetadata> 內。  布林值屬性可讓您查看每個條件，而無須套用遮罩到旗標型式列舉值來取得所需的資訊。  建構函式會使用串連的 <xref:System.Windows.FrameworkPropertyMetadataOptions> 讓建構函式簽章保持合理的長度，而實際已建構的中繼資料則會公開個別屬性，使查詢中繼資料更容易進行。  
  
<a name="override_or_subclass"></a>   
## 覆寫中繼資料的時機，衍生類別的時機  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統能夠變更相依性屬性的部分特性，而無須重新實作整個屬性。  這是因為它會為位於特定型別的相依性屬性，建構不同的屬性中繼資料執行個體。  請注意，大多數現有相依性屬性都不是虛擬屬性，因此嚴格來說，要在繼承的類別上「重新實作」這些屬性，只能藉由遮蔽現有成員來達成。  
  
 如果您要嘗試為某個型別上的相依性屬性啟用的案例，但無法藉由修改現有相依性屬性的特性來達成，那麼就可能需要建立衍生類別，然後在該衍生類別上宣告自訂相依性屬性。  自訂相依性屬性的行為與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] 定義的相依性屬性完全相同。  如需自訂相依性屬性的詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
 相依性屬性有一個值得注意的特性是無法覆寫的，那就是它的實值型別。  如果您繼承的相依性屬性所具有的行為大致符合所需，但型別不是您所要的，就必須實作自訂相依性屬性，而且可能需要透過型別轉換或自訂類別上的其他實作連結屬性。  此外，您不能取代現有 <xref:System.Windows.ValidateValueCallback>，因為此回呼位於註冊欄位本身，而不是在其中繼資料內。  
  
<a name="scenarios"></a>   
## 變更現有中繼資料的案例  
 如果您使用現有相依性屬性的中繼資料，變更相依性屬性中繼資料的常見做法就是變更預設值。  變更或加入屬性系統回呼是更進階的做法。  如果您的衍生類別實作在相依性屬性之間有不同的相互關係，就可能會想要這麼做。  要程式撰寫模型 \(Programming Model\) 同時支援程式碼和宣告式使用方式的條件之一，就是屬性必須能夠以任何順序設定。  因此，任何相依性屬性都必須在沒有內容的情況下進行 Just\-In\-Time 設定，不能靠著建構函式中可找到的設定順序來進行設定。  如需屬性系統在這方面的詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)。  請注意，驗證回呼不屬於中繼資料的一部分，而是相依性屬性識別項的一部分。  因此，驗證回呼不能藉由覆寫中繼資料來變更。  
  
 在某些情況下，您可能也想變更現有相依性屬性上的 [WPF 架構層級](GTMT)屬性中繼資料選項。  這些選項會將 [WPF 架構層級](GTMT)屬性的某些已知條件傳達給其他 [WPF 架構層級](GTMT)處理序 \(例如配置系統\)。  這些選項通常只會在註冊新相依性屬性時進行設定，但也可以呼叫 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 或 <xref:System.Windows.DependencyProperty.AddOwner%2A> 來變更 [WPF 架構層級](GTMT)屬性中繼資料。  如需要使用的特定值和詳細資訊，請參閱[架構屬性中繼資料](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)。  如需如何針對新註冊的相依性屬性設定這些選項的詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
<a name="dp_override_metadata"></a>   
### 覆寫中繼資料  
 覆寫中繼資料的目的，主要是讓您有機會變更各種中繼資料衍生的行為，這些行為會套用到型別上的相依性屬性。  [中繼資料](#dp_metadata_contents)一節會詳細說明原因。  如需詳細資訊與程式碼範例，請參閱 [覆寫相依性屬性的中繼資料](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)。  
  
 相依性屬性的屬性中繼資料可在註冊呼叫 \(<xref:System.Windows.DependencyProperty.Register%2A>\) 期間提供。  不過，在許多情況下，當類別繼承該相依性屬性時，您會想為類別提供型別特定的中繼資料。  您可以藉由呼叫 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 方法來完成。  從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 舉例來說，<xref:System.Windows.FrameworkElement> 類別是第一個註冊 <xref:System.Windows.UIElement.Focusable%2A> 相依性屬性的型別。  但 <xref:System.Windows.Controls.Control> 類別會覆寫該相依性屬性的中繼資料，以提供自己的初始預設值 \(也就是將它從 `false` 變更為 `true`\) 並且重複使用原始 <xref:System.Windows.UIElement.Focusable%2A> 實作。  
  
 覆寫中繼資料時，不同的中繼資料特性會被合併或取代。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> 會合併。  如果您加入新的 <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>，該回呼會儲存在中繼資料裡。  如果沒有在覆寫中指定 <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>，<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> 的值會從中繼資料裡參考最接近它的祖系。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> 的實際屬性系統行為如下：階層架構中所有中繼資料擁有者的實作都會保留並加入到資料表，屬性系統的執行順序為最末層衍生類別的回呼會最先叫用。  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> 會被取代。  如果沒有在覆寫中指定 <xref:System.Windows.PropertyMetadata.DefaultValue%2A>，<xref:System.Windows.PropertyMetadata.DefaultValue%2A> 的值會取自在中繼資料裡指定它的最接近祖系。  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 實作會被取代。  如果您加入新的 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>，該回呼會儲存在中繼資料裡。  如果沒有在覆寫中指定 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>，<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 的值會從中繼資料裡指定它的最接近祖系升級為參考。  
  
-   屬性系統行為是只會叫用直接中繼資料裡的 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>。  階層架構中其他 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 實作的參考都不會保留。  
  
 此行為是由 <xref:System.Windows.PropertyMetadata.Merge%2A> 實作，可在衍生的中繼資料類別上覆寫。  
  
#### 覆寫附加屬性中繼資料  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，[附加屬性](GTMT)會實作為相依性屬性。  這表示它們也有屬性中繼資料，可供個別類別覆寫。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中附加屬性的範圍考量通常與在其上設定附加屬性的 <xref:System.Windows.DependencyObject> 相同。  因此，任何 <xref:System.Windows.DependencyObject> 衍生類別都可以覆寫在其執行個體上所設定的任何附加屬性。  您可以覆寫預設值、回呼或 [WPF 架構階層](GTMT)特性報告屬性。  如果在類別的執行個體上設定附加屬性，那麼將會套用這些覆寫屬性的中繼資料特性。  例如，您可以覆寫預設值，只要沒有另外設定屬性，就會將覆寫值回報為類別執行個體上附加屬性的值。  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> 屬性與附加屬性無關。  
  
<a name="dp_add_owner"></a>   
### 加入類別當做現有相依性屬性的擁有者  
 類別可藉由使用 <xref:System.Windows.DependencyProperty.AddOwner%2A> 方法，自行加入做為已註冊之相依性屬性的擁有者。  這可讓類別使用原本是不同型別所註冊的相依性屬性。  加入的類別通常不是原先註冊該相依性屬性之擁有者型別的衍生類別。  實際上，這可讓類別及其衍生類別「繼承」[相依性屬性](GTMT)實作，而原始擁有者類別和加入的類別不需要在同一個真實類別階層中。  此外，加入的類別 \(和所有衍生類別\) 接著可為原始相依性屬性提供型別特定的中繼資料。  
  
 除了透過屬性系統公用程式方法自行加入做為擁有者，加入的類別也應在本身上宣告其他公用成員，讓[相依性屬性](GTMT)完全融合在屬性系統中，並能公開給程式碼和標記。  加入現有相依性屬性的類別與定義新相依性屬性的類別一樣，也必須公開該相依性屬性的物件模型。  第一個公開的成員是相依性屬性識別項欄位。  此欄位應為 <xref:System.Windows.DependencyProperty> 型別的 `public static readonly` 欄位，這會指派給 <xref:System.Windows.DependencyProperty.AddOwner%2A> 呼叫的傳回值。  第二個要定義的成員是 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]「包裝函式」屬性。  包裝函式可讓您更方便在程式碼中操作相依性屬性 \(這可免去每次都要呼叫 <xref:System.Windows.DependencyObject.SetValue%2A>，只要在包裝函式中呼叫一次即可\)。  包裝函式的實作方式與註冊自訂[相依性屬性](GTMT)時實作包裝函式的方式完全相同。  如需實作[相依性屬性](GTMT)的詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)和 [加入相依性屬性的擁有者類型](../../../../docs/framework/wpf/advanced/how-to-add-an-owner-type-for-a-dependency-property.md)。  
  
#### AddOwner 和附加屬性  
 您可以為擁有者類別定義為附加屬性的相依性屬性呼叫 <xref:System.Windows.DependencyProperty.AddOwner%2A>。  一般這麼做的原因是要將先前的附加屬性公開為非附加相依性屬性。  您接著就可以將 <xref:System.Windows.DependencyProperty.AddOwner%2A> 傳回值公開為 `public static readonly` 欄位，以當做相依性屬性識別項使用，並定義適當的「包裝函式」屬性，以便屬性出現在成員表中並支援在類別中當做非附加屬性使用。  
  
## 請參閱  
 <xref:System.Windows.PropertyMetadata>   
 <xref:System.Windows.DependencyObject>   
 <xref:System.Windows.DependencyProperty>   
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [架構屬性中繼資料](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)