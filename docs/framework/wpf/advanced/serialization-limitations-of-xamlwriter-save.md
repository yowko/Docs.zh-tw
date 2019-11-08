---
title: XamlWriter.Save 的序列化限制
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 5b9141d5df40d74c4682f418a8fb089fddcfcaa9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740749"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save 的序列化限制
您可以使用 API <xref:System.Windows.Markup.XamlWriter.Save%2A>，將 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式的內容序列化為 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔。 不過，究竟要將哪些項目序列化，則有一些值得注意的限制。 本主題將說明這些限制及一些一般考量。  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>執行階段而非設計階段的表示法  
 <xref:System.Windows.Markup.XamlWriter.Save%2A> 的呼叫所序列化的基本原理是，在執行時間，結果會是要序列化之物件的標記法。 原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案的許多設計階段屬性可能已經在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 載入為記憶體內建物件時優化或遺失，而且當您呼叫 <xref:System.Windows.Markup.XamlWriter.Save%2A> 序列化時，並不會保留。 序列化的結果是有效呈現應用程式建構的邏輯樹狀結構，但不一定是產生它的原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 這些問題使得在廣泛的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 設計介面中使用 <xref:System.Windows.Markup.XamlWriter.Save%2A> 序列化變得非常困難。  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>序列化是獨立的  
 <xref:System.Windows.Markup.XamlWriter.Save%2A> 的序列化輸出是獨立的;序列化的所有專案都包含在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 單一頁面中，其中包含單一根項目，而且沒有 Uri 以外的外部參考。 例如，如果您的頁面會參考來自應用程式資源的資源，這些資源的顯示方式，就像它們是要序列化的頁面元件一樣。  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>延伸模組參考已取值  
 透過各種不同標記延伸格式 (例如 `StaticResource` 或 `Binding`) 對物件所做的一般參考，將透過序列化程序來取值。 當應用程式執行時間建立記憶體內建物件時，這些已解除引用，而 <xref:System.Windows.Markup.XamlWriter.Save%2A> 邏輯並不會重新流覽原始的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來還原序列化輸出的這類參考。 這可能會凍結任何資料繫結或資源取得的值，以做為執行階段表示法上一次使用的值，只透過有限或間接的方式來區分這類值與本機設定的任何其他值。 影像也會序列化為影像的物件參考，因為它們存在於專案中，而不是原始來源參考，因而遺失原本參考的任何檔案名或 URI。 實際上已將在同一個頁面內宣告的資源序列化至參考它們的點，而不是保留為資源集合的關鍵字。  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>不會保留事件處理  
 透過 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加入的事件處理常式均已序列化，不會保留它們。 不具程式碼後置 (而且沒有相關的 x:Code 機制) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，無法序列化執行階段程序邏輯。 由於序列化是獨立且受限於邏輯樹狀結構，所以，沒有任何功能可用來儲存事件處理常式。 因此，會從輸出 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中移除事件處理常式屬性 (屬性本身以及為處理常式命名的字串值)。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>使用 XAMLWriter.Save 的真實案例  
 雖然此處所列的限制相當可觀，但仍有幾個適當的案例可使用 <xref:System.Windows.Markup.XamlWriter.Save%2A> 進行序列化。  
  
- 向量或圖形輸出︰重新載入時，可以使用轉譯區域的輸出，重新產生相同的向量或圖形。  
  
- Rich Text 格式和非固定格式文件︰輸出中會保留文字與所有已格式化的元素及其內部的元素內含項目。 這適用於估計剪貼簿功能的機制。  
  
- 保留商務物件資料：如果您已將資料儲存在自訂元素中（例如 XML 資料），只要您的商務物件遵循基本 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 規則，例如提供自訂的函式和依參考屬性值的轉換，這些商務可以透過序列化 perpetuated 物件。
