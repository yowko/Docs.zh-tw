---
title: XAML 命名範圍
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
ms.openlocfilehash: f9d4439c6b102d0d430b5201e3649985daee0b7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186279"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML 名稱範圍
XAML 名稱範圍是識別 XAML 中所定義物件的概念。 XAML 名稱範圍中的名稱可以用來建立物件的 XAML 定義名稱與其在物件樹狀結構中的執行個體對等項目之間的關聯性。 一般而言，載入 XAML 應用程式的個別 XAML 頁面根時，會建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Managed 程式碼中的 XAML 名稱範圍。 XAML名稱範圍作為程式設計物件由<xref:System.Windows.Markup.INameScope>介面定義，也由實用類<xref:System.Windows.NameScope>實現。  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>
## <a name="namescopes-in-loaded-xaml-applications"></a>所載入 XAML 應用程式中的名稱範圍  
 在更廣泛的程式設計或電腦科學內容中，程式設計概念通常包括可用來存取物件之唯一識別碼或名稱的原則。 針對使用識別碼或名稱的系統，在要求該名稱的物件時，名稱範圍會定義程序或技術將在其內搜尋的界限，或是在其中強制執行識別名稱唯一性的界限。 這些一般原則適用於 XAML 名稱範圍。 在 WPF 中，載入 XAML 頁面時，會在頁面的根項目上建立 XAML 名稱範圍。 在頁面根開始之 XAML 頁面內所指定的每個名稱都會新增至適當的 XAML 名稱範圍。  
  
 在 WPF XAML 中，作為公共根項目的元素<xref:System.Windows.Controls.Page>（如<xref:System.Windows.Window>和 ） 始終控制 XAML 命名範圍。 如果元素<xref:System.Windows.FrameworkElement>（如 或<xref:System.Windows.FrameworkContentElement>是標記中頁面的根項目），[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]則處理器隱式添加<xref:System.Windows.Controls.Page>根，以便<xref:System.Windows.Controls.Page>可以提供有效的 XAML 命名範圍。  
  
> [!NOTE]
> WPF 建置動作會針對 XAML 生產來建立 XAML 名稱範圍，即使未在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記的任何項目上定義 `Name` 或 `x:Name` 屬性也是一樣。  
  
 如果您嘗試在任何 XAML 名稱範圍中使用相同的名稱兩次，則會引發例外狀況。 針對具有程式碼後置且為已編譯應用程式一部分的 WPF XAML，在初始標記編譯期間建立頁面的已產生類別時，WPF 建置動作會在建置期間引發例外狀況。 針對未透過任何建置動作進行標記編譯的 XAML，在載入 XAML 時，可能會引發 XAML 名稱範圍問題的相關例外狀況。 XAML 設計工具也可能預期會在設計階段發生 XAML 名稱範圍問題。  
  
### <a name="adding-objects-to-runtime-object-trees"></a>將物件新增至執行階段物件樹狀結構  
 剖析 XAML 的時間點代表建立和定義 WPF XAML 名稱範圍的時間點。 如果您在剖析已產生該樹狀結構的 XAML 之後的某個時間點，將物件新增至物件樹狀結構，則新物件上的 `Name` 或 `x:Name` 值不會自動更新 XAML 名稱範圍中的資訊。 要在載入 XAML 後將物件的名稱添加到 WPF XAML 命名範圍中，必須在定義 XAML 名稱範圍的物件<xref:System.Windows.Markup.INameScope.RegisterName%2A>上調用相應的實現，該名稱範圍通常是 XAML 頁面根。 如果未註冊該名稱，則無法通過 方法（如<xref:System.Windows.FrameworkElement.FindName%2A>） 引用添加的物件，也不能將該名稱用於動畫定位。  
  
 對於應用程式開發人員來說，最常見的方案是，您將使用<xref:System.Windows.FrameworkElement.RegisterName%2A>在頁面當前根目錄上的 XAML 命名範圍中註冊名稱。 <xref:System.Windows.FrameworkElement.RegisterName%2A>是面向動畫物件的分鏡腳本的重要方案的一部分。 如需詳細資訊，請參閱[分鏡腳本概觀](../graphics-multimedia/storyboards-overview.md)。  
  
 如果對定義<xref:System.Windows.FrameworkElement.RegisterName%2A>XAML 名稱範圍的物件以外的物件進行調用，則該名稱仍註冊到調用物件所持有的 XAML 命名範圍，就像調用 XAML<xref:System.Windows.FrameworkElement.RegisterName%2A>命名物件一樣。  
  
### <a name="xaml-namescopes-in-code"></a>程式碼中的 XAML 名稱範圍  
 您可以在程式碼中建立 XAML 名稱範圍後來加以使用。 甚至針對純程式碼用法，與 XAML 名稱範圍建立有關的 API 和概念也會相同，因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 XAML 處理器在處理 XAML 本身時會使用這些 API 和概念。 概念和 API 的存在目的主要是可以依名稱在物件樹狀結構內找到物件，而物件樹狀結構一般是在 XAML 中部分或完整定義。  
  
 對於以程式設計方式創建而不是從載入的 XAML 創建的應用程式，定義 XAML 名稱範圍的物件必須實現<xref:System.Windows.Markup.INameScope>或 或<xref:System.Windows.FrameworkElement><xref:System.Windows.FrameworkContentElement>派生類，以支援在其實例上創建 XAML 命名範圍。  
  
 此外，針對 XAML 處理器未載入和處理的任何項目，預設都不會建立或初始化物件的 XAML 名稱範圍。 您必須針對任何您要註冊名稱的物件，明確建立新的 XAML 名稱範圍。 要創建 XAML 命名範圍，請調用靜態<xref:System.Windows.NameScope.SetNameScope%2A>方法。 指定將具有該物件為`dependencyObject`參數的物件，並將新的<xref:System.Windows.NameScope.%23ctor%2A>建構函式調用作為`value`參數。  
  
 如果所`dependencyObject`<xref:System.Windows.NameScope.SetNameScope%2A>提供的物件<xref:System.Windows.Markup.INameScope>不是實現，<xref:System.Windows.FrameworkElement>或者<xref:System.Windows.FrameworkContentElement>調用<xref:System.Windows.FrameworkElement.RegisterName%2A>任何子項目將不起作用。 如果無法顯式創建新的 XAML 命名範圍，則調用 將<xref:System.Windows.FrameworkElement.RegisterName%2A>引發異常。  
  
 如需在程式碼中使用 XAML 名稱範圍 API 的範例，請參閱[定義名稱範圍](../graphics-multimedia/how-to-define-a-name-scope.md)。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>
## <a name="xaml-namescopes-in-styles-and-templates"></a>樣式和範本中的 XAML 名稱範圍  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的樣式和範本可以用更簡單的方式重複使用和重新套用內容。 不過，樣式和範本可能也包括具有範本層級所定義之 XAML 名稱的項目。 可能會在頁面中多次使用這個相同的範本。 因此，樣式和範本都會定義其專屬 XAML 名稱範圍，這與物件樹狀結構中套用樣式或範本的位置無關。  
  
 請考慮下列範例：  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 在這裡，相同的範本會套用至兩個不同的按鈕。 如果範本沒有離散 XAML 名稱範圍，則範本中所使用的 `TheBorder` 名稱會導致 XAML 名稱範圍中的名稱衝突。 範本的每個具現化都有其專屬的 XAML 名稱範圍；因此，在此範例中，每個具現化範本的 XAML 名稱範圍都只會包含一個名稱。  
  
 樣式也會定義其專屬的 XAML 名稱範圍；因此，分鏡腳本的各部分一般可以獲指派特定名稱。 即使已在控制項自訂時重新定義範本，這些名稱還是可以啟用將目標設為該名稱之項目的控制項特定行為。  
  
 因為不同的 XAML 名稱範圍，所以在範本中尋找具名項目會比在頁面中尋找非範本具名項目更具挑戰。 首先需要通過獲取應用範本的控制項<xref:System.Windows.Controls.Control.Template%2A>的屬性值來確定應用的範本。 然後，調用 的<xref:System.Windows.FrameworkTemplate.FindName%2A>範本版本，傳遞作為第二個參數應用範本的控制項。  
  
 如果您是控制項作者，並且正在生成一個約定，其中應用範本中的特定命名元素是控制項本身定義的行為的目標，則可以使用控制項實現代碼中<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>的方法。 該方法<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>受到保護，因此只有控制項作者才能訪問它。  
  
 如果您正在範本內工作，並且需要訪問應用範本的 XAML 名稱範圍，請獲取 的值<xref:System.Windows.FrameworkElement.TemplatedParent%2A>，然後調用<xref:System.Windows.FrameworkElement.FindName%2A>該值。 在範本內運作的範例就是您要撰寫事件處理常式實作，其中，將從已套用範本中的項目引發事件。  
  
<a name="Namescopes_and_Name_related_APIs"></a>
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML 名稱範圍和名稱相關 API  
 <xref:System.Windows.FrameworkElement>有<xref:System.Windows.FrameworkElement.FindName%2A> <xref:System.Windows.FrameworkElement.RegisterName%2A> ，<xref:System.Windows.FrameworkElement.UnregisterName%2A>和方法。 如果您在其上呼叫這些方法的物件擁有 XAML 名稱範圍，則方法會呼叫相關 XAML 名稱範圍的方法。 否則，會檢查父項目，確認它是否擁有 XAML 名稱範圍，而且此程序會遞迴地執行，直到找到 XAML 名稱範圍 (因為 XAML 處理器行為，所以根一定會有 XAML 名稱範圍)。 <xref:System.Windows.FrameworkContentElement>具有類似行為，但沒有任何<xref:System.Windows.FrameworkContentElement>人擁有 XAML 名稱範圍。 這些方法存在，<xref:System.Windows.FrameworkContentElement>以便最終可以將調用轉發到<xref:System.Windows.FrameworkElement>父元素。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>用於將新的 XAML 命名範圍映射到現有物件。 您可以多次調用<xref:System.Windows.NameScope.SetNameScope%2A>以重置或清除 XAML 名稱範圍，但這不是常見用法。 此外，<xref:System.Windows.NameScope.GetNameScope%2A>通常不從代碼中使用。  
  
### <a name="xaml-namescope-implementations"></a>XAML 名稱範圍實作  
 以下類直接實現<xref:System.Windows.Markup.INameScope>：  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>不使用 XAML 名稱或名稱範圍;它使用鍵，因為它是字典實現。 實現<xref:System.Windows.ResourceDictionary><xref:System.Windows.Markup.INameScope>的唯一原因是，它可以對使用者代碼引發異常，以説明闡明真正的 XAML 命名範圍與<xref:System.Windows.ResourceDictionary>處理金鑰的方式之間的區別，並確保 XAML 命名碼不<xref:System.Windows.ResourceDictionary>應用於父元素。  
  
 <xref:System.Windows.FrameworkTemplate>並通過<xref:System.Windows.Style>顯式<xref:System.Windows.Markup.INameScope>介面定義實現。 顯式實現允許這些 XAML 命名範圍在通過<xref:System.Windows.Markup.INameScope>介面訪問時按常規方式執行，這是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]內部進程傳達 XAML 名稱範圍的方式。 但是顯式介面定義不是<xref:System.Windows.FrameworkTemplate>和<xref:System.Windows.Style>的常規 API 表面的一部分，因為您很少需要直接調用<xref:System.Windows.Markup.INameScope>方法<xref:System.Windows.FrameworkTemplate><xref:System.Windows.Style>，而是使用其他 API（如<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>）。  
  
 以下類通過使用<xref:System.Windows.NameScope?displayProperty=nameWithType>説明器類並通過<xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType>附加屬性連接到其 XAML 命名範圍實現，定義它們自己的 XAML 命名範圍：  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>另請參閱

- [WPF XAML 的 XAML 命名空間和命名空間對應](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name 指示詞](../../../desktop-wpf/xaml-services/xname-directive.md)
