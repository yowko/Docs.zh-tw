---
title: "WPF XAML 名稱範圍 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "API, 名稱相關"
  - "類別, FrameworkContentElement"
  - "類別, FrameworkElement"
  - "類別, RegisterName"
  - "FrameworkContentElement 類別"
  - "FrameworkElement 類別"
  - "名稱相關 API"
  - "名稱範圍"
  - "RegisterName 類別"
  - "樣式, 名稱範圍"
  - "範本, 名稱範圍"
  - "XAML, 名稱範圍"
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# WPF XAML 名稱範圍
XAML 名稱範圍 \(Namescope\) 是一種概念，用來識別在 XAML 中定義的物件。  XAML 名稱範圍中的名稱可以用來在 XAML 定義的物件名稱，與物件在物件樹狀結構中的對應執行個體之間建立關聯性。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Managed 程式碼中的 XAML 名稱範圍，通常是在載入 XAML 應用程式的個別 XAML 頁面根項目時建立。  XAML 名稱範圍如同程式設計物件，是由 <xref:System.Windows.Markup.INameScope> 介面所定義，而且是由實用類別 <xref:System.Windows.NameScope> 所實作。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## 載入之 XAML 應用程式中的命名範圍  
 在更廣泛的程式設計或電腦環境中，程式設計概念經常包含唯一識別項的準則或可用來存取物件的名稱。  針對使用識別碼或名稱的系統，名稱範圍會定義當要求該名稱的物件時，流程或技術將搜尋的範圍界限，或是定義必須在其內使用唯一識別名稱的範圍界限。  這些一般性準則適用於 XAML 名稱範圍。  在 WPF 中，XAML 名稱範圍是在載入 XAML 頁面時，建立於該頁面的根項目上。  在 XAML 頁面中，自頁面根項目起所指定的每個名稱，都會加入至關聯的 XAML 名稱範圍。  
  
 在 WPF XAML 中，屬於通用根項目的項目 \(例如 <xref:System.Windows.Controls.Page> 和 <xref:System.Windows.Window>\) 一定會控制 XAML 名稱範圍。  如果像 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 的項目是頁面標記的根項目，會有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器隱含加入 <xref:System.Windows.Controls.Page> 根項目，讓 <xref:System.Windows.Controls.Page> 能提供正常可用的 XAML 名稱範圍。  
  
> [!NOTE]
>  即使一開始未在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中的任何項目上定義 `Name` 或 `x:Name` 屬性，WPF 建置動作仍然會為 XAML 產物建立 XAML 名稱範圍。  
  
 如果您嘗試在任何 XAML 名稱範圍中使用相同的名稱兩次，則會引發例外狀況。  當遇到有程式碼後置且為完成編譯之應用程式一部分的 WPF XAML 時，WPF 建置動作會在建置期間初次進行標記編譯來為頁面建立產生的類別時，引發例外狀況。  當遇到未由建置動作進行標記編譯的 XAML 時，則可能會在載入 XAML 時引發與 XAML 名稱範圍相關的例外狀況。  XAML 設計工具也可能在設計階段遇到 XAML 名稱範圍問題。  
  
### 將物件加入至執行階段物件樹狀結構  
 剖析 XAML 的時間點，代表建立和定義 WPF XAML 名稱範圍的時間點。  如果您在產生物件樹狀結構的 XAML 受到剖析後，將物件加入至該物件樹狀結構，則新物件上的 `Name` 或 `x:Name` 值不會在 XAML 名稱範圍中自動更新該資訊。  若要在載入 XAML 後，將物件名稱加入至 WPF XAML 名稱範圍，必須在定義 XAML 名稱範圍的物件 \(通常是 XAML 頁面根項目\) 上呼叫適當的 <xref:System.Windows.Markup.INameScope.RegisterName%2A> 實作。  如果未註冊名稱，就無法透過 <xref:System.Windows.FrameworkElement.FindName%2A> 等方法依名稱來參考所加入的物件，也無法使用該名稱進行動畫目標設定。  
  
 對應用程式開發人員來說，最常見的案例就是使用 <xref:System.Windows.FrameworkElement.RegisterName%2A> 將名稱註冊到目前頁面根項目上的 XAML 名稱範圍。  在以物件做為動畫目標的重要腳本案例中，<xref:System.Windows.FrameworkElement.RegisterName%2A> 是其中一部分。  如需詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
 如果您在定義 XAML 名稱範圍的物件以外的其他物件上呼叫 <xref:System.Windows.FrameworkElement.RegisterName%2A>，名稱仍會註冊到呼叫時所在的物件使用的 XAML 名稱範圍中，就如同您在定義 XAML 名稱範圍的物件上呼叫 <xref:System.Windows.FrameworkElement.RegisterName%2A> 一樣。  
  
### 程式碼中的 XAML 名稱範圍  
 您可以在程式碼中建立然後使用 XAML 名稱範圍。  即使是純使用程式碼，建立 XAML 名稱範圍時牽涉到的 API 與概念仍是相同的，這是因為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 XAML 處理器在處理 XAML 本身時會使用這些 API 和概念。  這些概念和 API 存在的主要目的在於，能夠在物件樹狀結構 \(通常是部分或完全以 XAML 定義\) 中依名稱尋找物件。  
  
 對於以程式設計方式 \(而且不是來自於載入的 XAML\) 建立的應用程式，定義 XAML 名稱範圍的物件必須實作 <xref:System.Windows.Markup.INameScope>，或者必須是 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 衍生的類別，才支援在該應用程式的執行個體上建立 XAML 名稱範圍。  
  
 此外，對於任何不是由 XAML 處理器載入和處理的項目，預設不會建立或初始化物件的 XAML 名稱範圍。  您必須先明確建立新的 XAML 名稱範圍，才能將物件名稱註冊到其中。  若要建立 XAML 名稱範圍，請呼叫靜態 <xref:System.Windows.NameScope.SetNameScope%2A> 方法。  將要擁有它的物件指定為 `dependencyObject` 參數，並將新的 <xref:System.Windows.NameScope.%23ctor%2A> 建構函式呼叫指定為 `value` 參數。  
  
 如果在 <xref:System.Windows.NameScope.SetNameScope%2A> 提供的 `dependencyObject` 物件不是 <xref:System.Windows.Markup.INameScope> 實作、<xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>，那麼在任何子項目上呼叫 <xref:System.Windows.FrameworkElement.RegisterName%2A> 將不會有任何作用。  如果您無法明確建立新的 XAML 名稱範圍，則呼叫 <xref:System.Windows.FrameworkElement.RegisterName%2A> 會引發例外狀況。  
  
 如需在程式碼中使用 XAML 名稱範圍 API 的範例，請參閱 [定義名稱範圍](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md)。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## 樣式和樣板中的 XAML 名稱範圍  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的樣式和範本可讓您直接重複使用和重新套用內容。  但是，樣式和範本也可能包含具有在範本層級中所定義 XAML 名稱的項目。  同一頁面可能會多次使用該樣板。  因此，樣式和範本都會定義其本身的 XAML 名稱範圍，不受套用樣式或範本的物件樹狀結構所在位置影響。  
  
 參考下列範例：  
  
 [!code-xml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 在此例中，相同的樣板套用到兩個不同的按鈕。  如果範本沒有獨立的 XAML 名稱範圍，範本中所使用的 `TheBorder` 名稱就會造成 XAML 名稱範圍中的名稱衝突。  樣板的每個執行個體都有自己的 XAML 名稱範圍，因此在這個範例中，每個已執行個體化之樣板的 XAML 名稱範圍都只會包含一個名稱。  
  
 樣式也會定義自己的 XAML 名稱範圍，主要是讓 Storyboard 的各部分能夠有特定的名稱。  這些名稱可產生控制項特定行為，然後對應到該名稱的項目，即使在自訂控制項時重新定義了樣板。  
  
 由於 XAML 名稱範圍各自獨立，因此在樣板中尋找具名項目要比在頁面中尋找非樣板具名項目更困難。  您首先需要取得套用樣板之控制項的 <xref:System.Windows.Controls.Control.Template%2A> 屬性值，以判斷套用的樣板。  接著，您會呼叫所取得的 <xref:System.Windows.FrameworkTemplate.FindName%2A> 樣板，將套用樣板的控制項當做第二個參數傳遞。  
  
 如果您是控制項作者，並設定慣例 \(Convention\) 讓控制項本身定義的行為，是以所套用之樣板中的特定具名項目為目標，那麼就可以在控制項實作程式碼中使用 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> 方法。  <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> 方法是受到保護的，因此只有控制項作者可以存取它。  
  
 如果您在樣板中執行工作，且需要取得套用樣板的 XAML 名稱範圍，請取得 <xref:System.Windows.FrameworkElement.TemplatedParent%2A> 的值，然後再從該處呼叫 <xref:System.Windows.FrameworkElement.FindName%2A>。  在使用樣板的範例中，如果您撰寫事件處理常式實作，其中事件會從所套用之樣板中的項目來引發。  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## XAML 名稱範圍以及與名稱相關的 API  
 <xref:System.Windows.FrameworkElement> 有 <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> 和 <xref:System.Windows.FrameworkElement.UnregisterName%2A> 方法。  如果呼叫這些方法的物件擁有 XAML 名稱範圍，那麼方法就會呼叫相關 XAML 名稱範圍的方法。  否則，會檢查父項目是否擁有 XAML 名稱範圍，並反覆不斷進行此檢查，直到找到 XAML 名稱範圍 \(由於 XAML 處理器行為之故，根項目一定會有 XAML 名稱範圍\)。  <xref:System.Windows.FrameworkContentElement> 也有類似的行為，不同的是 <xref:System.Windows.FrameworkContentElement> 將不會擁有 XAML 名稱範圍。  方法是存在於 <xref:System.Windows.FrameworkContentElement> 上，因此呼叫最後可轉送到 <xref:System.Windows.FrameworkElement> 父項目。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> 可用來將新的 XAML 名稱範圍對應到現有的物件。  您可以呼叫 <xref:System.Windows.NameScope.SetNameScope%2A> 多次來重設或清除 XAML 名稱範圍，但這並不是常見的用法。  此外，<xref:System.Windows.NameScope.GetNameScope%2A> 也通常不在程式碼中使用。  
  
### XAML 名稱範圍實作  
 下列類別會直接實作 <xref:System.Windows.Markup.INameScope>：  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> 不使用 XAML 名稱或名稱範圍，而是使用索引鍵，因為它是字典實作。  <xref:System.Windows.ResourceDictionary> 實作 <xref:System.Windows.Markup.INameScope> 的唯一理由是可以對使用者程式碼引發例外狀況，如此有助於說明真正 XAML 名稱範圍與 <xref:System.Windows.ResourceDictionary> 處理索引鍵的方式之間的不同之處，而且也可確保父項目不會特別將 XAML 名稱範圍套用到 <xref:System.Windows.ResourceDictionary>。  
  
 <xref:System.Windows.FrameworkTemplate> 和 <xref:System.Windows.Style> 透過明確介面定義實作 <xref:System.Windows.Markup.INameScope>。  明確實作可讓這些 XAML 名稱範圍在透過 <xref:System.Windows.Markup.INameScope> 介面存取 \(這是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內部處理序傳遞 XAML 名稱範圍的方式\) 時，產生慣例的行為。  不過明確介面定義不屬於 <xref:System.Windows.FrameworkTemplate> 和 <xref:System.Windows.Style> 傳統 API 介面的一部分，因為您很少需要直接在 <xref:System.Windows.FrameworkTemplate> 和 <xref:System.Windows.Style> 上呼叫 <xref:System.Windows.Markup.INameScope> 方法，而會使用其他 API，例如 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>。  
  
 下列類別會定義自己的 XAML 名稱範圍，方法是使用 <xref:System.Windows.NameScope?displayProperty=fullName> Helper 類別並透過 <xref:System.Windows.NameScope.NameScope%2A?displayProperty=fullName> 附加屬性連接至其 XAML 名稱範圍實作：  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## 請參閱  
 [WPF XAML 的 XAML 命名空間和命名空間對應](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)   
 [x:Name 指示詞](../../../../docs/framework/xaml-services/x-name-directive.md)