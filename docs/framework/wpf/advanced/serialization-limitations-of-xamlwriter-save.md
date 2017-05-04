---
title: "XamlWriter.Save 的序列化限制 | Microsoft Docs"
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
  - "XamlWriter.Save 的限制"
  - "XamlWriter.Save 的序列化限制"
  - "XamlWriter.Save, 序列化限制"
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# XamlWriter.Save 的序列化限制
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> 可用於將 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式的內容序列化為[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案。  但是，確切進行序列化的項目方面有幾項限制必須注意。  這些限制與部分一般注意事項將在本主題中說明。  
  
   
  
<a name="Run_Time__Not_Design_Time_Representation"></a>   
## 執行階段、非設計階段的表示  
 呼叫 <xref:System.Windows.Markup.XamlWriter.Save%2A> 以序列化某項目的基本理論，就是結果會是進行序列化之物件在執行階段的表示。  原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案有許多設計階段屬性可能已在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 載入為記憶體中物件時最佳化或遺失，而在您呼叫 <xref:System.Windows.Markup.XamlWriter.Save%2A> 以進行序列化時已不存在。  序列化的結果就是應用程式之結構化邏輯樹狀結構的有效表示，但未必是產生該應用程式的原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  這些問題致使在擴充 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 設計介面中非常難以使用 <xref:System.Windows.Markup.XamlWriter.Save%2A> 序列化。  
  
<a name="Serialization_is_Self_Contained"></a>   
## 序列化是獨立的  
 <xref:System.Windows.Markup.XamlWriter.Save%2A> 的序列化輸出是獨立的 \(Self\-Contained\)，每個序列化的項目都包含在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 單一頁面內，其中含有單一根項目，且不含 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 以外的外部參考。  例如，若您的頁面參考來自應用程式資源的資源，這些資源會顯示為像是進行序列化之頁面的元件。  
  
<a name="Extension_References_are_Dereferenced"></a>   
## 延伸參考已取值  
 各種標記延伸格式所制定的一般物件參考 \(如 `StaticResource` 或 `Binding`\) 將會由序列化程序取值。  這些參考已在應用程式執行階段建立記憶體中物件時取值，且 <xref:System.Windows.Markup.XamlWriter.Save%2A> 邏輯不會重新造訪原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 以還原序列化輸出的此類參考。  這可能會將任何資料繫結或資源取得值凍結為執行階段表示最後使用的值，使用者只能透過有限或間接的方式來區分此值與其他本機設定的值。  影像在專案中時也會序列化為影像的物件參考，而非原始來源參考，並且失去原本所參考的檔案名稱或 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  資源即使是在相同的頁面內宣告，在其參考點上仍會以序列化的形式顯示，而不會保留為資源集合的索引鍵。  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## 不會保留事件處理  
 透過 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 加入的事件處理常式在進行序列化時並不會保留下來。  沒有程式碼後置 \(也沒有相關的 x:Code 機制\) 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 無法序列化執行階段程序邏輯。  由於序列化是獨立的且受限於邏輯樹狀結構，因此沒有相關功能可儲存事件處理常式。  因此，事件處理常式屬性 \(包括屬性本身與命名處理常式的字串值\) 會從輸出 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中移除。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## 使用 XAMLWriter.Save 的實際案例  
 儘管此處所列的限制已相當具體，但仍提供幾個使用 <xref:System.Windows.Markup.XamlWriter.Save%2A> 進行序列化的適當案例。  
  
-   向量或圖形輸出：呈現區域的輸出可用於重新載入相同的向量或圖形時予以重現。  
  
-   RTF 格式與非固定格式文件：其中的文字以及所有的項目格式與項目內容都會保留在輸出中。  這對於近似剪貼簿功能的機制而言很有用處。  
  
-   保留商業物件資料：若您將資料儲存在自訂項目中 \(如 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料\)，只要您的商業物件遵循基本 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 規則 \(例如提供傳址屬性值的自訂建構函式與轉換\)，這些商業物件即可透過序列化保存下來。