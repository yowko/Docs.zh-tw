---
title: XamlWriter.Save 的序列化限制
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 96e917898320fb5d49f4e7dfc27daa7750af9d41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174364"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save 的序列化限制
API<xref:System.Windows.Markup.XamlWriter.Save%2A>可用於將[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式的內容序列化為[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔。 不過，究竟要將哪些項目序列化，則有一些值得注意的限制。 本主題將說明這些限制及一些一般考量。  

<a name="Run_Time__Not_Design_Time_Representation"></a>
## <a name="run-time-not-design-time-representation"></a>執行階段而非設計階段的表示法  
 調用 的序列化的基本理念<xref:System.Windows.Markup.XamlWriter.Save%2A>是，結果將在運行時序列化的物件表示。 原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔的許多設計時屬性可能已優化或丟失，當[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入為記憶體中的物件，並且在調用<xref:System.Windows.Markup.XamlWriter.Save%2A>序列化時不會保留。 序列化的結果是有效呈現應用程式建構的邏輯樹狀結構，但不一定是產生它的原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 這些問題使得將<xref:System.Windows.Markup.XamlWriter.Save%2A>序列化用作廣泛[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設計表面的一部分變得極其困難。  
  
<a name="Serialization_is_Self_Contained"></a>
## <a name="serialization-is-self-contained"></a>序列化是獨立的  
 序列<xref:System.Windows.Markup.XamlWriter.Save%2A>化輸出是自包含的;序列化的所有內容都包含在單個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面中，包含單個根項目，並且除了 URI 之外，沒有外部引用。 例如，如果您的頁面會參考來自應用程式資源的資源，這些資源的顯示方式，就像它們是要序列化的頁面元件一樣。  
  
<a name="Extension_References_are_Dereferenced"></a>
## <a name="extension-references-are-dereferenced"></a>延伸模組參考已取值  
 透過各種不同標記延伸格式 (例如 `StaticResource` 或 `Binding`) 對物件所做的一般參考，將透過序列化程序來取值。 在應用程式運行時創建記憶體中物件時，這些物件已被取消引用，<xref:System.Windows.Markup.XamlWriter.Save%2A>並且邏輯不會重新訪問原始物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]以還原對序列化輸出的此類引用。 這可能會凍結任何資料繫結或資源取得的值，以做為執行階段表示法上一次使用的值，只透過有限或間接的方式來區分這類值與本機設定的任何其他值。 圖像也會序列化為對專案中存在的圖像的物件引用，而不是原始源引用，丟失最初引用的任何檔案名或 URI。 實際上已將在同一個頁面內宣告的資源序列化至參考它們的點，而不是保留為資源集合的關鍵字。  
  
<a name="Event_Handling_is_Not_Preserved"></a>
## <a name="event-handling-is-not-preserved"></a>不會保留事件處理  
 透過 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加入的事件處理常式均已序列化，不會保留它們。 不具程式碼後置 (而且沒有相關的 x:Code 機制) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，無法序列化執行階段程序邏輯。 由於序列化是獨立且受限於邏輯樹狀結構，所以，沒有任何功能可用來儲存事件處理常式。 因此，會從輸出 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中移除事件處理常式屬性 (屬性本身以及為處理常式命名的字串值)。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>使用 XAMLWriter.Save 的真實案例  
 雖然此處列出的限制相當大，但仍有幾種適當的方案可用於<xref:System.Windows.Markup.XamlWriter.Save%2A>序列化。  
  
- 向量或圖形輸出︰重新載入時，可以使用轉譯區域的輸出，重新產生相同的向量或圖形。  
  
- Rich Text 格式和非固定格式文件︰輸出中會保留文字與所有已格式化的元素及其內部的元素內含項目。 這適用於估計剪貼簿功能的機制。  
  
- 保留業務物件資料：如果將資料存儲在自訂元素（如 XML 資料）中，只要業務物件遵循基本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]規則（如提供自訂建構函式和轉換引用屬性值），這些業務物件可以通過序列化永久化。
