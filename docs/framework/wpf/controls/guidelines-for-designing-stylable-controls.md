---
title: 設計可設定樣式控制項的方針
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 99644be4a275c1de7f4b89ca23368a26a8b76f5b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614547"
---
# <a name="guidelines-for-designing-stylable-controls"></a>設計可設定樣式控制項的方針
本文摘要說明當設計要能夠容易設定樣式及範本化的控制項時，可考量的一組最佳做法。 我們是在研究內建之 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項集的佈景主題控制項樣式時，經過許多嘗試和錯誤，才得出這組最佳做法。 我們了解到成功的樣式設定對設計良好的物件模型來說，不僅是樣式本身，也是一項功能。 本文件的適用對象是控制項作者，而不是樣式作者。  
  
  <a name="Terminology"></a>   
## <a name="terminology"></a>用語  
 「樣式設定和範本化」係指一套技術，可讓控制項作者將控制項的視覺方面交給控制項的樣式和範本去處理。 這套技術包括：  
  
- 樣式 (包括屬性 setter、觸發程序及分鏡腳本)。  
  
- 資源。  
  
- 控制項範本。  
  
- 資料範本。  
  
 如需樣式設定和範本化的簡介，請參閱[樣式設定和範本化範例](styling-and-templating.md)。  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## <a name="before-you-start-understanding-your-control"></a>在開始之前：了解您的控制項  
 在您開始研究這些方針之前，請務必先了解並定義您控制項的一般使用方式。 樣式設定所揭露的通常是一組難以駕馭的可能性。 撰寫來廣泛使用的控制項 (在許多應用程式中、供許多開發人員使用) 面臨挑戰，即樣式設定可用來對控制項的視覺外觀進行更深遠的變更。 事實上，已設定樣式的控制項甚至可能與控制項作者的意圖不符。 由於樣式設定所提供的彈性基本上是無限的，因此您可以使用一般使用方式的概念來協助限制您的決策範圍。  
  
 為了了解您控制項的一般使用方式，思考一下控制項的價值主張會相當有幫助。 您的控制項可為表格提供哪些任何其他控制所無法提供的效果？ 一般使用方式不包含任何特定的視覺外觀，而是包含控制項的原理，以及一組關於其使用方式的合理預期。 這項理解可讓您對一般情況下控制項的撰寫模型和已定義樣式的行為，進行一些假設。 若是<xref:System.Windows.Controls.ComboBox>，比方說，了解常見的用法不提供任何深入解析有關特定<xref:System.Windows.Controls.ComboBox>具有圓的角，但它可讓您深入了解這個事實，<xref:System.Windows.Controls.ComboBox>可能需要的快顯視窗和切換是否已開啟，所以某些方式。  
  
<a name="General_Guidelines"></a>   
## <a name="general-guidelines"></a>一般方針  
  
- **請勿強制執行範本合約。** 控制項的範本合約成份可能包含元素、命令、繫結、觸發程序，或甚至是讓控制項正常運作所需或應有的屬性設定。  
  
    - 將合約儘量縮減到最少。  
  
    - 設計時需有心理準備，即在設計階段 (亦即在使用設計工具時) 控制項範本處於不完整狀態是正常的。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 並不提供「撰寫中」狀態的基礎結構，因此建置控制項時，必須預期這類狀態可能是有效的狀態。  
  
    - 當有未遵守範本合約任何方面的情況時，請勿擲回例外狀況。 同樣地，面板在子系太多或太少時，也不應該擲回例外狀況。  
  
- **將周邊功能列入為範本協助程式元素的考量因素。** 每個控制項都應該將焦點放在其核心功能和實際的價值主張，並由控制項的一般使用方式定義。 為了達到該目的，請使用範本內的撰寫和協助程式元素來啟用周邊行為和視覺效果，也就是未包含在控制項核心功能內的那些行為和視覺效果。 協助程式元素分成三個分類：  
  
    - 「獨立」協助程式是範本中公開且可重複使用的控制項，或是以「匿名方式」使用的基本型別，也就是說，協助程式元素和已設定樣式的控制項都不知道彼此。 就技術而言，任何元素都可以是匿名型別，但在此內容中，此詞彙所描述的是那些封裝特製化功能來實現目標案例的型別。  
  
    - 「型別型」協助程式元素是封裝了特製化功能的新型別。 與一般控制項或基本型別相比，這些元素通常是設計為功能範圍較窄。 與獨立協助程式元素不同，型別型協助程式元素知道所處的使用內容，且通常必須與其所屬控制項範本的控制項共用資料。  
  
    - 「具名」協助程式元素是控制項預期要在其範本內，依名稱找到的一般控制項或基本型別。 這些元素在範本內都有一個已知的名稱，使得控制項能夠透過程式設計方式找到元素並與其進行互動。 在任一範本中，只能有一個元素具有指定的名稱。  
  
     下表說明現今控制項樣式所採用的協助程式元素 (本清單並不完全)：  
  
    |項目|類型|使用對象|  
    |-------------|----------|-------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|型別型|<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.CheckBox>， <xref:System.Windows.Controls.RadioButton>，<xref:System.Windows.Controls.Frame>等等 (所有<xref:System.Windows.Controls.ContentControl>類型)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|型別型|<xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ComboBox>，<xref:System.Windows.Controls.Menu>等等 (所有<xref:System.Windows.Controls.ItemsControl>類型)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|具名|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|獨立|<xref:System.Windows.Controls.ComboBox><xref:System.Windows.Controls.ToolBar>， <xref:System.Windows.Controls.Menu>，<xref:System.Windows.Controls.ToolTip>等等|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|具名|<xref:System.Windows.Controls.Slider><xref:System.Windows.Controls.Primitives.ScrollBar>等等|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|具名|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|獨立|<xref:System.Windows.Controls.ListBox><xref:System.Windows.Controls.ComboBox>， <xref:System.Windows.Controls.Menu>，<xref:System.Windows.Controls.Frame>等等|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|獨立|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|具名|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|型別型|<xref:System.Windows.Controls.Slider>|  
  
- **將在協助程式元素上所需的使用者指定繫結或屬性設定縮減到最少**。 協助程式元素通常必須要有特定繫結或屬性設定，才能在控制項範本內正常運作。 協助程式元素和樣板化控制項應該儘可能建立這些設定。 設定屬性或建立繫結時，應該小心，不要覆寫使用者所設定的值。 特定的最佳做法如下：  
  
    - 具名協助程式元素應該可由父代識別，而父代應該在該協助程式元素上建立任何必要的設定。  
  
    - 型別型協助程式元素應該在本身直接建立任何必要的設定。 這麼做可能需要協助程式元素查詢所處的使用資訊內容，包括其 `TemplatedParent` (所處使用範本的控制項型別)。 例如，<xref:System.Windows.Controls.ContentPresenter>自動繫結`Content`屬性其`TemplatedParent`至其<xref:System.Windows.Controls.ContentPresenter.Content%2A>屬性中使用時<xref:System.Windows.Controls.ContentControl>衍生型別。  
  
    - 您無法以此方式將獨立協助程式元素最佳化，因為根據定義，協助程式元素和父代都不知道彼此。  
  
- **使用 Name 屬性在範本內標幟元素**。 控制項如果需要在其樣式中尋找元素，以便透過程式設計方式存取該元素，應該使用 `Name` 屬性和 `FindName` 典型來執行此操作。 控制項不應該在找不到元素時擲回例外狀況，而是應該以無訊息且依正常程序的方式，停用需要該元素的功能。  
  
- **使用可表達樣式中控制項狀態和行為的最佳做法。** 以下是已排序的最佳做法清單，用來表達樣式中的控制項狀態變更和行為。 您應該使用清單上第一個可實現您案例的項目。  
  
    1. 屬性繫結。 範例： 繫結之間<xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType>和<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>。  
  
    2. 觸發的屬性變更或屬性動畫。 範例： 暫留狀態<xref:System.Windows.Controls.Button>。  
  
    3. 命令。 範例： <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand>  /  <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand>在<xref:System.Windows.Controls.Primitives.ScrollBar>。  
  
    4. 獨立協助程式元素。 範例：<xref:System.Windows.Controls.Primitives.TabPanel>在<xref:System.Windows.Controls.TabControl>。  
  
    5. 型別型協助程式型別。 範例：<xref:System.Windows.Controls.ContentPresenter>中<xref:System.Windows.Controls.Button>，<xref:System.Windows.Controls.Primitives.TickBar>在<xref:System.Windows.Controls.Slider>。  
  
    6. 具名協助程式元素。 範例：<xref:System.Windows.Controls.TextBox>在<xref:System.Windows.Controls.ComboBox>。  
  
    7. 來自具名協助程式型別的反昇事件。 如果您接聽來自樣式元素的反昇事件，您應該要求必須能夠唯一識別產生該事件的元素。 範例：<xref:System.Windows.Controls.Primitives.Thumb>在<xref:System.Windows.Controls.ToolBar>。  
  
    8. 自訂的 `OnRender` 行為。 範例：<xref:Microsoft.Windows.Themes.ButtonChrome>在<xref:System.Windows.Controls.Button>。  
  
- **儘量不要使用樣式觸發程序 (與範本觸發程序相反)**。 針對會影響範本中元素上屬性的觸發程序，您必須在範本中進行宣告。 針對會影響控制項 (無 `TargetName`) 上屬性的觸發程序，除非您知道變更範本應該也會終結觸發程序，否則您可以在樣式中進行宣告。  
  
- **與現有的樣式設定模式保持一致。** 在很多時候，都有多種方式可以解決問題。 請注意，儘可能與現有的控制項樣式設定模式保持一致。 這點特別重要，衍生自相同基底類型的控制項 (例如<xref:System.Windows.Controls.ContentControl>， <xref:System.Windows.Controls.ItemsControl>，<xref:System.Windows.Controls.Primitives.RangeBase>等等)。  
  
- **公開屬性來啟用常見的自訂案例，而不重新範本化**。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 不支援可插式/可自訂的組件，因此控制項使用者僅有兩種自訂方法可用：直接設定屬性，或使用樣式來設定屬性。 記住這一點之後，就可以公開以非常常見、高優先順序自訂案例為目標的數量有限屬性，否則這些案例將需要重新範本化。 以下是啟用自訂案例的時機和方式的最佳做法：  
  
    - 非常常見的自訂應該以控制項上屬性的形式公開，並由範本取用。  
  
    - 較不常見 (但並非罕見) 的自訂應該以附加屬性的形式公開，並由範本取用。  
  
    - 針對已知但罕見的自訂，則可接受要求重新範本化。  
  
<a name="Theme_Considerations"></a>   
## <a name="theme-considerations"></a>佈景主題考量  
  
- **佈景主題樣式應該嘗試在所有佈景主題都具有一致的屬性語意，但不保證能做到**。 作為其記載的一部分，您的控制項應該要有一份文件，其中描述控制項的屬性語意，也就是控制項屬性的「意義」。 例如，<xref:System.Windows.Controls.ComboBox>控制項應該定義的意義<xref:System.Windows.Controls.Control.Background%2A>內的屬性<xref:System.Windows.Controls.ComboBox>。 您控制項的預設樣式應該嘗試在所有佈景主題都遵守該文件中定義的語意。 另一方面，控制項使用者則應該注意屬性語意可能會因佈景主題不同而改變。 在某些情況下，在特定佈景主題所需的視覺條件約束下，可能會無法表達指定的屬性。 (例如，「傳統」佈景主題並沒有可針對許多控制項套用 `Thickness` 的單一框線)。  
  
- **佈景主題樣式不需要在所有佈景主題都具有一致的觸發程序語意**。 控制項樣式透過觸發程序或動畫公開的行為可能會因佈景主題不同而不同。 控制項使用者應該注意，控制項未必會採用相同的機制在所有佈景主題達到特定的行為。 例如，可能有一個佈景主題使用動畫來表達暫留行為，而另一個佈景主題則使用觸發程序。 這會導致在保留自訂控制項上的行為時不一致。 (例如，變更背景屬性可能不會影響控制項的暫留狀態，如果是使用觸發程序來表達該狀態。 不過，如果是使用動畫來實作暫留狀態，變更背景可能就會無法挽回地破壞動畫，也因而破壞狀態轉換)。  
  
- **佈景主題樣式不需要在所有佈景主題都具有一致的「版面配置」語意**。 例如，預設樣式不需要保證控制項在所有佈景主題中都佔據相同的大小，或是保證控制項在所有佈景主題中都具有相同的內容邊界/邊框間距。  
  
## <a name="see-also"></a>另請參閱

- [樣式設定和範本化](styling-and-templating.md)
- [控制項撰寫概觀](control-authoring-overview.md)
