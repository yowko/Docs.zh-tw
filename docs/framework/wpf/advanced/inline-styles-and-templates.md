---
title: "內嵌樣式和範本 | Microsoft Docs"
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
  - "內嵌樣式"
  - "內嵌樣板"
  - "樣式, inline"
  - "範本, inline"
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 內嵌樣式和範本
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供 <xref:System.Windows.Style> 物件和樣板物件 \(<xref:System.Windows.FrameworkTemplate> 子類別 \(Class\)\)，做為定義資源項目之視覺化外觀的一種方法，因此這些物件可以多次重複使用。  基於這個原因，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中採用 <xref:System.Windows.Style> 和 <xref:System.Windows.FrameworkTemplate> 型別的屬性 \(Attribute\) 幾乎都會建立現有樣式和樣板的資源參考，而不會定義新的內嵌樣式和樣板。  
  
## 內嵌樣式和樣板的限制  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，技術上樣式和樣本屬性 \(Property\) 可以使用兩種方式來設定。  您可以使用屬性 \(Attribute\) 語法參考資源內定義的樣式，例如 `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`。  或者，您也可以使用屬性 \(Property\) 項目語法定義內嵌樣式，例如：  
  
 `<` *object* `>`  
  
 `<` *object* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *object* `.Style>`  
  
 `</` *object* `>`  
  
 使用屬性 \(Attribute\) 是最常見的做法。  以內嵌方式定義而資源中沒有定義的樣式，其範圍一定只限於包含項目，而且比較不容易重複使用，因為這種樣式並沒有資源索引鍵。  一般來說，資源定義的樣式用途較廣也較為實用，而且比較符合將程式碼中的程式邏輯與標記中的設計分開的一般 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 程式撰寫模型 \(Programming Model\) 準則。  
  
 通常，即使您只想在該位置使用該樣式或樣板，也沒有理由設定內嵌樣式或樣板。  可以採用樣式或樣板的項目大部分也都可以支援內容屬性和內容模型。  如果您只要使用透過執行一次樣式或樣板化所建立的邏輯樹狀結構，更簡單的做法是只在該內容屬性中填入直接標記中的對等子項目。  這種方法將會一併忽略樣式和樣板機制。  
  
 樣式和樣板也可以使用由標記延伸啟用，而且能夠重複執行物件的其他語法。  在具有可行案例的這類延伸中，其中兩個是 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) 和 <xref:System.Windows.Data.Binding>。  
  
## 請參閱  
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)