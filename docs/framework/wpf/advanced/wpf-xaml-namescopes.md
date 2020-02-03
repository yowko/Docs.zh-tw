---
title: XAML 名稱範圍
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: 4383492157191f61cf04a2fdd6ce27e9183bda8b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744413"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML 名稱範圍
XAML 名稱範圍是識別 XAML 中所定義物件的概念。 XAML 名稱範圍中的名稱可以用來建立物件的 XAML 定義名稱與其在物件樹狀結構中的執行個體對等項目之間的關聯性。 一般而言，載入 XAML 應用程式的個別 XAML 頁面根時，會建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Managed 程式碼中的 XAML 名稱範圍。 做為程式設計物件的 XAML 名稱範圍是由 <xref:System.Windows.Markup.INameScope> 介面所定義，而且也會由實體類別 <xref:System.Windows.NameScope>來執行。  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>所載入 XAML 應用程式中的名稱範圍  
 在更廣泛的程式設計或電腦科學內容中，程式設計概念通常包括可用來存取物件之唯一識別碼或名稱的原則。 針對使用識別碼或名稱的系統，在要求該名稱的物件時，名稱範圍會定義程序或技術將在其內搜尋的界限，或是在其中強制執行識別名稱唯一性的界限。 這些一般原則適用於 XAML 名稱範圍。 在 WPF 中，載入 XAML 頁面時，會在頁面的根項目上建立 XAML 名稱範圍。 在頁面根開始之 XAML 頁面內所指定的每個名稱都會新增至適當的 XAML 名稱範圍。  
  
 在 WPF XAML 中，屬於一般根項目的元素（例如 <xref:System.Windows.Controls.Page>和 <xref:System.Windows.Window>）一律會控制 XAML 名稱範圍。 如果 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 之類的專案是標記中頁面的根項目，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器會隱含地加入 <xref:System.Windows.Controls.Page> 根，讓 <xref:System.Windows.Controls.Page> 可以提供可運作的 XAML 名稱範圍。  
  
> [!NOTE]
> WPF 建置動作會針對 XAML 生產來建立 XAML 名稱範圍，即使未在 `Name` 標記的任何項目上定義 `x:Name` 或 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性也是一樣。  
  
 如果您嘗試在任何 XAML 名稱範圍中使用相同的名稱兩次，則會引發例外狀況。 針對具有程式碼後置且為已編譯應用程式一部分的 WPF XAML，在初始標記編譯期間建立頁面的已產生類別時，WPF 建置動作會在建置期間引發例外狀況。 針對未透過任何建置動作進行標記編譯的 XAML，在載入 XAML 時，可能會引發 XAML 名稱範圍問題的相關例外狀況。 XAML 設計工具也可能預期會在設計階段發生 XAML 名稱範圍問題。  
  
### <a name="adding-objects-to-runtime-object-trees"></a>將物件新增至執行階段物件樹狀結構  
 剖析 XAML 的時間點代表建立和定義 WPF XAML 名稱範圍的時間點。 如果您在剖析已產生該樹狀結構的 XAML 之後的某個時間點，將物件新增至物件樹狀結構，則新物件上的 `Name` 或 `x:Name` 值不會自動更新 XAML 名稱範圍中的資訊。 若要在載入 XAML 之後，將物件的名稱加入 WPF XAML 名稱範圍，您必須在定義 XAML 名稱範圍的物件上呼叫適當的 <xref:System.Windows.Markup.INameScope.RegisterName%2A> 執行，這通常是 XAML 頁面根目錄。 如果未註冊此名稱，則無法透過 <xref:System.Windows.FrameworkElement.FindName%2A>的方法參考新增的物件，而您也無法將該名稱用於以為目標的動畫。  
  
 應用程式開發人員最常見的案例是，您將使用 <xref:System.Windows.FrameworkElement.RegisterName%2A>，在頁面目前根目錄的 XAML 名稱範圍中註冊名稱。 <xref:System.Windows.FrameworkElement.RegisterName%2A> 是以動畫物件為目標之分鏡腳本的重要案例之一部分。 如需詳細資訊，請參閱[分鏡腳本概觀](../graphics-multimedia/storyboards-overview.md)。  
  
 如果您在定義 XAML 名稱範圍的物件以外的物件上呼叫 <xref:System.Windows.FrameworkElement.RegisterName%2A>，該名稱仍會註冊到呼叫物件所在的 XAML 名稱範圍內，就如同您在定義物件的 XAML 名稱範圍呼叫 <xref:System.Windows.FrameworkElement.RegisterName%2A> 一樣。  
  
### <a name="xaml-namescopes-in-code"></a>程式碼中的 XAML 名稱範圍  
 您可以在程式碼中建立 XAML 名稱範圍後來加以使用。 甚至針對純程式碼用法，與 XAML 名稱範圍建立有關的 API 和概念也會相同，因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 XAML 處理器在處理 XAML 本身時會使用這些 API 和概念。 概念和 API 的存在目的主要是可以依名稱在物件樹狀結構內找到物件，而物件樹狀結構一般是在 XAML 中部分或完整定義。  
  
 若為以程式設計方式建立，而不是從載入的 XAML 建立的應用程式，則定義 XAML 名稱範圍的物件必須實作為 <xref:System.Windows.Markup.INameScope>，或必須是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 的衍生類別，才能支援在其實例上建立 XAML 名稱範圍。  
  
 此外，針對 XAML 處理器未載入和處理的任何項目，預設都不會建立或初始化物件的 XAML 名稱範圍。 您必須針對任何您要註冊名稱的物件，明確建立新的 XAML 名稱範圍。 若要建立 XAML 名稱範圍，請呼叫靜態 <xref:System.Windows.NameScope.SetNameScope%2A> 方法。 指定將會擁有它做為 `dependencyObject` 參數的物件，以及做為 `value` 參數的新 <xref:System.Windows.NameScope.%23ctor%2A> 的函式呼叫。  
  
 如果提供做為 <xref:System.Windows.NameScope.SetNameScope%2A> `dependencyObject` 的物件不是 <xref:System.Windows.Markup.INameScope> 的執行，<xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>，在任何子專案上呼叫 <xref:System.Windows.FrameworkElement.RegisterName%2A> 將不會有任何作用。 如果您無法明確建立新的 XAML 名稱範圍，則呼叫 <xref:System.Windows.FrameworkElement.RegisterName%2A> 將會引發例外狀況。  
  
 如需在程式碼中使用 XAML 名稱範圍 API 的範例，請參閱[定義名稱範圍](../graphics-multimedia/how-to-define-a-name-scope.md)。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>樣式和範本中的 XAML 名稱範圍  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的樣式和範本可以用更簡單的方式重複使用和重新套用內容。 不過，樣式和範本可能也包括具有範本層級所定義之 XAML 名稱的項目。 可能會在頁面中多次使用這個相同的範本。 因此，樣式和範本都會定義其專屬 XAML 名稱範圍，這與物件樹狀結構中套用樣式或範本的位置無關。  
  
 請考慮下列範例：  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 在這裡，相同的範本會套用至兩個不同的按鈕。 如果範本沒有離散 XAML 名稱範圍，則範本中所使用的 `TheBorder` 名稱會導致 XAML 名稱範圍中的名稱衝突。 範本的每個具現化都有其專屬的 XAML 名稱範圍；因此，在此範例中，每個具現化範本的 XAML 名稱範圍都只會包含一個名稱。  
  
 樣式也會定義其專屬的 XAML 名稱範圍；因此，分鏡腳本的各部分一般可以獲指派特定名稱。 即使已在控制項自訂時重新定義範本，這些名稱還是可以啟用將目標設為該名稱之項目的控制項特定行為。  
  
 因為不同的 XAML 名稱範圍，所以在範本中尋找具名項目會比在頁面中尋找非範本具名項目更具挑戰。 您必須先取得套用範本之控制項的 <xref:System.Windows.Controls.Control.Template%2A> 屬性值，來判斷已套用的範本。 然後，您可以呼叫 <xref:System.Windows.FrameworkTemplate.FindName%2A>的範本版本，並將套用範本的控制項傳遞為第二個參數。  
  
 如果您是控制項作者，而且您正在產生慣例，而所套用範本中的特定已命名專案是控制項本身所定義之行為的目標，您可以使用控制項執行程式碼中的 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> 方法。 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> 方法會受到保護，因此只有控制項作者可以存取它。  
  
 如果您是從範本內工作，而且需要取得套用範本的 XAML 名稱範圍，請取得 <xref:System.Windows.FrameworkElement.TemplatedParent%2A>的值，然後在該處呼叫 <xref:System.Windows.FrameworkElement.FindName%2A>。 在範本內運作的範例就是您要撰寫事件處理常式實作，其中，將從已套用範本中的項目引發事件。  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML 名稱範圍和名稱相關 API  
 <xref:System.Windows.FrameworkElement> 具有 <xref:System.Windows.FrameworkElement.FindName%2A>、<xref:System.Windows.FrameworkElement.RegisterName%2A> 和 <xref:System.Windows.FrameworkElement.UnregisterName%2A> 方法。 如果您在其上呼叫這些方法的物件擁有 XAML 名稱範圍，則方法會呼叫相關 XAML 名稱範圍的方法。 否則，會檢查父項目，確認它是否擁有 XAML 名稱範圍，而且此程序會遞迴地執行，直到找到 XAML 名稱範圍 (因為 XAML 處理器行為，所以根一定會有 XAML 名稱範圍)。 <xref:System.Windows.FrameworkContentElement> 具有類似的行為，唯一的例外是沒有任何 <xref:System.Windows.FrameworkContentElement> 會擁有 XAML 名稱範圍。 方法存在於 <xref:System.Windows.FrameworkContentElement>，因此可以將呼叫最後轉送至 <xref:System.Windows.FrameworkElement> 的父元素。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> 可用來將新的 XAML 名稱範圍對應至現有的物件。 您可以多次呼叫 <xref:System.Windows.NameScope.SetNameScope%2A>，以便重設或清除 XAML 名稱範圍，但這不是常見的用法。 此外，<xref:System.Windows.NameScope.GetNameScope%2A> 通常不會從程式碼使用。  
  
### <a name="xaml-namescope-implementations"></a>XAML 名稱範圍實作  
 下列類別會直接執行 <xref:System.Windows.Markup.INameScope>：  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> 不使用 XAML 名稱或名稱範圍;它會改為使用索引鍵，因為它是字典的執行。 <xref:System.Windows.ResourceDictionary> 執行 <xref:System.Windows.Markup.INameScope> 的唯一理由是，它可以引發例外狀況給使用者程式碼，以協助闡明真正 XAML 名稱範圍與 <xref:System.Windows.ResourceDictionary> 如何處理索引鍵之間的差異，以及確保 XAML 名稱範圍不會套用至父元素所 <xref:System.Windows.ResourceDictionary>。  
  
 <xref:System.Windows.FrameworkTemplate> 和 <xref:System.Windows.Style> 透過明確介面定義來執行 <xref:System.Windows.Markup.INameScope>。 當透過 <xref:System.Windows.Markup.INameScope> 介面存取 XAML 名稱範圍時，明確的執行可讓這些 XAML 名稱範圍的行為，也就是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內部處理常式如何傳達 XAML 名稱範圍。 但是明確的介面定義並不是 <xref:System.Windows.FrameworkTemplate> 和 <xref:System.Windows.Style>之傳統 API 介面的一部分，因為您很少需要在 <xref:System.Windows.FrameworkTemplate> 上呼叫 <xref:System.Windows.Markup.INameScope> 方法並直接 <xref:System.Windows.Style>，而改為使用 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>之類的其他 API。  
  
 下列類別定義自己的 XAML 名稱範圍，方法是使用 <xref:System.Windows.NameScope?displayProperty=nameWithType> helper 類別，並透過 <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> 附加屬性連接到它的 XAML 名稱範圍執行：  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>另請參閱

- [WPF XAML 的 XAML 命名空間和命名空間對應](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name 指示詞](../../../desktop-wpf/xaml-services/xname-directive.md)
