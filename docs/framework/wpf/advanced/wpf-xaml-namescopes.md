---
title: WPF XAML 名稱範圍
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
ms.openlocfilehash: 52fc542996f2fe691b62aeff5296e045643fcc7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498342"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML 名稱範圍
XAML 名稱範圍是識別 XAML 中所定義物件的概念。 XAML 名稱範圍中的名稱可以用來建立物件的 XAML 定義名稱與其在物件樹狀結構中的執行個體對等項目之間的關聯性。 一般而言，載入 XAML 應用程式的個別 XAML 頁面根時，會建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Managed 程式碼中的 XAML 名稱範圍。 作為程式設計物件的 XAML 名稱範圍由<xref:System.Windows.Markup.INameScope>介面，並由實際的類別也會實作<xref:System.Windows.NameScope>。  
  
  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>所載入 XAML 應用程式中的名稱範圍  
 在更廣泛的程式設計或電腦科學內容中，程式設計概念通常包括可用來存取物件之唯一識別碼或名稱的原則。 針對使用識別碼或名稱的系統，在要求該名稱的物件時，名稱範圍會定義程序或技術將在其內搜尋的界限，或是在其中強制執行識別名稱唯一性的界限。 這些一般原則適用於 XAML 名稱範圍。 在 WPF 中，載入 XAML 頁面時，會在頁面的根項目上建立 XAML 名稱範圍。 在頁面根開始之 XAML 頁面內所指定的每個名稱都會新增至適當的 XAML 名稱範圍。  
  
 在 WPF XAML，屬於常見的根元素的項目 (例如<xref:System.Windows.Controls.Page>，和<xref:System.Windows.Window>) 一律會控制 XAML 名稱範圍。 如果這類項目<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>是在標記中，頁面的根項目[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器加入<xref:System.Windows.Controls.Page>隱含根以便<xref:System.Windows.Controls.Page>可以提供工作的 XAML 名稱範圍。  
  
> [!NOTE]
>  WPF 建置動作會針對 XAML 生產來建立 XAML 名稱範圍，即使未在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記的任何項目上定義 `Name` 或 `x:Name` 屬性也是一樣。  
  
 如果您嘗試在任何 XAML 名稱範圍中使用相同的名稱兩次，則會引發例外狀況。 針對具有程式碼後置且為已編譯應用程式一部分的 WPF XAML，在初始標記編譯期間建立頁面的已產生類別時，WPF 建置動作會在建置期間引發例外狀況。 針對未透過任何建置動作進行標記編譯的 XAML，在載入 XAML 時，可能會引發 XAML 名稱範圍問題的相關例外狀況。 XAML 設計工具也可能預期會在設計階段發生 XAML 名稱範圍問題。  
  
### <a name="adding-objects-to-runtime-object-trees"></a>將物件新增至執行階段物件樹狀結構  
 剖析 XAML 的時間點代表建立和定義 WPF XAML 名稱範圍的時間點。 如果您在剖析已產生該樹狀結構的 XAML 之後的某個時間點，將物件新增至物件樹狀結構，則新物件上的 `Name` 或 `x:Name` 值不會自動更新 XAML 名稱範圍中的資訊。 載入 XAML 之後，請將物件的名稱新增至 WPF XAML 名稱範圍，您必須呼叫的適當實作<xref:System.Windows.Markup.INameScope.RegisterName%2A>上定義的 XAML 名稱範圍的物件，通常是 XAML 頁面根。 如果未註冊名稱，加入的物件無法依名稱來參考方法透過例如<xref:System.Windows.FrameworkElement.FindName%2A>，而且您無法使用該名稱作為動畫目標。  
  
 應用程式開發人員最常見的案例是，您將使用<xref:System.Windows.FrameworkElement.RegisterName%2A>將名稱註冊到目前頁面根目錄上的 XAML 名稱範圍。 <xref:System.Windows.FrameworkElement.RegisterName%2A> 該動畫的目標物件是分鏡腳本的重要案例的一部分。 如需詳細資訊，請參閱[分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 如果您呼叫<xref:System.Windows.FrameworkElement.RegisterName%2A>以外的物件，定義 XAML 名稱範圍的物件，在名稱仍註冊內，保存呼叫物件的 XAML 名稱範圍視為已呼叫<xref:System.Windows.FrameworkElement.RegisterName%2A>上定義物件的 XAML 名稱範圍。  
  
### <a name="xaml-namescopes-in-code"></a>程式碼中的 XAML 名稱範圍  
 您可以在程式碼中建立 XAML 名稱範圍後來加以使用。 甚至針對純程式碼用法，與 XAML 名稱範圍建立有關的 API 和概念也會相同，因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 XAML 處理器在處理 XAML 本身時會使用這些 API 和概念。 概念和 API 的存在目的主要是可以依名稱在物件樹狀結構內找到物件，而物件樹狀結構一般是在 XAML 中部分或完整定義。  
  
 以程式設計方式建立的應用程式，而不是從載入的 XAML，定義 XAML 名稱範圍的物件必須實作<xref:System.Windows.Markup.INameScope>，或者是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>衍生類別，才能支援建立 XAML 名稱範圍，在其執行個體。  
  
 此外，針對 XAML 處理器未載入和處理的任何項目，預設都不會建立或初始化物件的 XAML 名稱範圍。 您必須針對任何您要註冊名稱的物件，明確建立新的 XAML 名稱範圍。 若要建立 XAML 名稱範圍，您可以呼叫靜態<xref:System.Windows.NameScope.SetNameScope%2A>方法。 指定將擁有它做為物件`dependencyObject`參數，而且新<xref:System.Windows.NameScope.%23ctor%2A>做為建構函式呼叫`value`參數。  
  
 如果物件提供作為`dependencyObject`for<xref:System.Windows.NameScope.SetNameScope%2A>不是<xref:System.Windows.Markup.INameScope>實作中，<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>，則呼叫<xref:System.Windows.FrameworkElement.RegisterName%2A>上任何子系項目會有任何作用。 如果您無法明確地建立新的 XAML 名稱範圍，然後呼叫<xref:System.Windows.FrameworkElement.RegisterName%2A>會引發例外狀況。  
  
 如需在程式碼中使用 XAML 名稱範圍 API 的範例，請參閱[定義名稱範圍](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md)。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>樣式和範本中的 XAML 名稱範圍  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的樣式和範本可以用更簡單的方式重複使用和重新套用內容。 不過，樣式和範本可能也包括具有範本層級所定義之 XAML 名稱的項目。 可能會在頁面中多次使用這個相同的範本。 因此，樣式和範本都會定義其專屬 XAML 名稱範圍，這與物件樹狀結構中套用樣式或範本的位置無關。  
  
 參考下列範例：  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 在這裡，相同的範本會套用至兩個不同的按鈕。 如果範本沒有離散 XAML 名稱範圍，則範本中所使用的 `TheBorder` 名稱會導致 XAML 名稱範圍中的名稱衝突。 範本的每個具現化都有其專屬的 XAML 名稱範圍；因此，在此範例中，每個具現化範本的 XAML 名稱範圍都只會包含一個名稱。  
  
 樣式也會定義其專屬的 XAML 名稱範圍；因此，分鏡腳本的各部分一般可以獲指派特定名稱。 即使已在控制項自訂時重新定義範本，這些名稱還是可以啟用將目標設為該名稱之項目的控制項特定行為。  
  
 因為不同的 XAML 名稱範圍，所以在範本中尋找具名項目會比在頁面中尋找非範本具名項目更具挑戰。 您必須先決定套用的範本，藉由取得<xref:System.Windows.Controls.Control.Template%2A>套用範本之控制項的屬性值。 然後，您可以呼叫的範本版本<xref:System.Windows.FrameworkTemplate.FindName%2A>，將控制項傳遞已套用範本做為第二個參數。  
  
 如果您是控制項作者，而且您要產生的特定具名已套用範本中的項目所在的目標由控制項本身所定義的行為的慣例，您可以使用<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>從控制項實作程式碼的方法。 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>方法受到保護，因此只有控制項作者可存取它。  
  
 如果您使用範本，以及為取得 XAML 名稱範圍套用範本，取得的值<xref:System.Windows.FrameworkElement.TemplatedParent%2A>，然後呼叫<xref:System.Windows.FrameworkElement.FindName%2A>那里。 在範本內運作的範例就是您要撰寫事件處理常式實作，其中，將從已套用範本中的項目引發事件。  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML 名稱範圍和名稱相關 API  
 <xref:System.Windows.FrameworkElement> 已<xref:System.Windows.FrameworkElement.FindName%2A>，<xref:System.Windows.FrameworkElement.RegisterName%2A>和<xref:System.Windows.FrameworkElement.UnregisterName%2A>方法。 如果您在其上呼叫這些方法的物件擁有 XAML 名稱範圍，則方法會呼叫相關 XAML 名稱範圍的方法。 否則，會檢查父項目，確認它是否擁有 XAML 名稱範圍，而且此程序會遞迴地執行，直到找到 XAML 名稱範圍 (因為 XAML 處理器行為，所以根一定會有 XAML 名稱範圍)。 <xref:System.Windows.FrameworkContentElement> 具有類似的行為，與例外狀況，任何<xref:System.Windows.FrameworkContentElement>會擁有 XAML 名稱範圍。 這些方法存在於<xref:System.Windows.FrameworkContentElement>這樣的呼叫可以轉送至最終<xref:System.Windows.FrameworkElement>父項目。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> 用來將新的 XAML 名稱範圍對應至現有的物件。 您可以呼叫<xref:System.Windows.NameScope.SetNameScope%2A>多次來重設或清除 XAML 名稱範圍，但不是常見的用法。 此外，<xref:System.Windows.NameScope.GetNameScope%2A>通常不會使用從程式碼。  
  
### <a name="xaml-namescope-implementations"></a>XAML 名稱範圍實作  
 下列類別會實作<xref:System.Windows.Markup.INameScope>直接：  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> 不使用 XAML 名稱範圍;它會改用索引鍵，因為它是一個字典實作。 唯一原因<xref:System.Windows.ResourceDictionary>會實作<xref:System.Windows.Markup.INameScope>是讓它可以引發例外狀況給使用者程式碼協助釐清，則為 true 的 XAML 名稱範圍之間的差異，以及如何<xref:System.Windows.ResourceDictionary>處理按鍵，並也確保 XAML 名稱範圍不會套用至<xref:System.Windows.ResourceDictionary>父項目。  
  
 <xref:System.Windows.FrameworkTemplate> 並<xref:System.Windows.Style>實作<xref:System.Windows.Markup.INameScope>透過明確介面定義。 明確的實作可讓運作存取透過時這些 XAML 名稱範圍<xref:System.Windows.Markup.INameScope>介面，也就是如何把傳達 XAML 名稱範圍的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內部處理程序。 明確介面定義不是傳統 API 介面的一部分，但是<xref:System.Windows.FrameworkTemplate>並<xref:System.Windows.Style>，因為您很少需要呼叫<xref:System.Windows.Markup.INameScope>上的方法<xref:System.Windows.FrameworkTemplate>和<xref:System.Windows.Style>直接，並改為使用其他 API這類<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>。  
  
 下列類別定義其專屬 XAML 名稱範圍中，使用<xref:System.Windows.NameScope?displayProperty=nameWithType>協助程式類別，並連接到它的 XAML 名稱範圍實作透過<xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType>附加屬性：  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>另請參閱
- [WPF XAML 的 XAML 命名空間和命名空間對應](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)
