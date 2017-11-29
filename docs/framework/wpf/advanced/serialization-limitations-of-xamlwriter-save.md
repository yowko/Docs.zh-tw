---
title: "XamlWriter.Save 的序列化限制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06033c6a753dd567f613f0b848e806dfa14ee77d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save 的序列化限制
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A>可用於序列化的內容[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案。 不過，究竟要將哪些項目序列化，則有一些值得注意的限制。 本主題將說明這些限制及一些一般考量。  
  
 
  
<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>執行階段而非設計階段的表示法  
 序列化功能時所呼叫的基本原理<xref:System.Windows.Markup.XamlWriter.Save%2A>結果是，在執行階段正在序列化的物件的表示法。 許多設計階段屬性的原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案可能已最佳化或遺失的時間，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入為記憶體中的物件，且當您呼叫不會保留<xref:System.Windows.Markup.XamlWriter.Save%2A>序列化。 序列化的結果是有效呈現應用程式建構的邏輯樹狀結構，但不一定是產生它的原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 這些問題會變得非常難使用<xref:System.Windows.Markup.XamlWriter.Save%2A>一部分非常龐大的序列化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設計介面。  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>序列化是獨立的  
 序列化的輸出的<xref:System.Windows.Markup.XamlWriter.Save%2A>為獨立的; 所有序列化的項目包含在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]單一頁面上，具有單一根項目和以外沒有外部參考[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。 例如，如果您的頁面會參考來自應用程式資源的資源，這些資源的顯示方式，就像它們是要序列化的頁面元件一樣。  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>延伸模組參考已取值  
 透過各種不同標記延伸格式 (例如 `StaticResource` 或 `Binding`) 對物件所做的一般參考，將透過序列化程序來取值。 這些已取值在記憶體中的物件所建立的應用程式執行階段的時間和<xref:System.Windows.Markup.XamlWriter.Save%2A>邏輯不會重新瀏覽原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]還原序列化輸出的這類參考。 這可能會凍結任何資料繫結或資源取得的值，以做為執行階段表示法上一次使用的值，只透過有限或間接的方式來區分這類值與本機設定的任何其他值。 映像也會序列化為對映像的物件參考 (當它們存在於專案中，而不是原始來源參考)，會遺失原本所參考的任何檔名或 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。 實際上已將在同一個頁面內宣告的資源序列化至參考它們的點，而不是保留為資源集合的關鍵字。  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>不會保留事件處理  
 透過 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加入的事件處理常式均已序列化，不會保留它們。 不具程式碼後置 (而且沒有相關的 x:Code 機制) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，無法序列化執行階段程序邏輯。 由於序列化是獨立且受限於邏輯樹狀結構，所以，沒有任何功能可用來儲存事件處理常式。 因此，會從輸出 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中移除事件處理常式屬性 (屬性本身以及為處理常式命名的字串值)。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>使用 XAMLWriter.Save 的真實案例  
 雖然限制列出如下大量，仍然會有數個適當情況使用<xref:System.Windows.Markup.XamlWriter.Save%2A>進行序列化。  
  
-   向量或圖形輸出︰重新載入時，可以使用轉譯區域的輸出，重新產生相同的向量或圖形。  
  
-   Rich Text 格式和非固定格式文件︰輸出中會保留文字與所有已格式化的元素及其內部的元素內含項目。 這適用於估計剪貼簿功能的機制。  
  
-   保留商務物件資料︰如果您已將資料儲存於自訂元素中 (例如 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料)，只要您的商務物件遵循基本的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 規則 (例如，提供適用於傳址屬性值的自訂建構函式和轉換)，就可透過序列化永久保存這些商務物件。
