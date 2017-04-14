---
title: "WPF 中的程式碼後置和 XAML | Microsoft Docs"
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
  - "程式碼後置檔案, XAML"
  - "XAML, 程式碼後置"
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# WPF 中的程式碼後置和 XAML
<a name="introduction"></a> 程式碼後置 \(Code\-Behind\) 一詞是用來描述以標記編譯 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面時，與標記定義的物件聯結的程式碼。  本主題說明程式碼後置的需求，以及 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中程式碼的替代內嵌程式碼機制。  
  
 此主題包括下列章節：  
  
-   [必要條件](#Prerequisites)  
  
-   [程式碼後置和 XAML 語言](#codebehind_and_the_xaml_language)  
  
-   [WPF 中程式碼後置、事件處理常式和部分類別的需求](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x:Code](#x_Code)  
  
-   [內嵌程式碼限制](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## 必要條件  
 本主題假設您已讀過 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)，而且有一些 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 和物件導向程式設計的基本知識。  
  
<a name="codebehind_and_the_xaml_language"></a>   
## 程式碼後置和 XAML 語言  
 XAML 語言包括語言層級的功能，這些功能可從標記檔這一端讓程式碼檔與標記檔產生關聯。  具體而言，XAML 語言會定義語言功能 [x:Class 指示詞](../../../../docs/framework/xaml-services/x-class-directive.md)、[x:Subclass 指示詞](../../../../docs/framework/xaml-services/x-subclass-directive.md)和 [x:ClassModifier 指示詞](../../../../docs/framework/xaml-services/x-classmodifier-directive.md)。  不過，XAML 語言指定的範圍並不包括該如何產生程式碼，以及如何整合標記和程式碼。  這類工作取決於架構 \(例如 WPF\)，決定如何整合程式碼、如何在應用程式和程式設計模型中使用 XAML，以及這類工作需要的所有建置動作或其他支援。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## WPF 中程式碼後置、事件處理常式和部分類別的需求  
  
-   部分類別必須衍生自支援根項目的型別。  
  
-   請注意，在標記編譯建置動作的行為之下，您可以在程式碼後置端的部分類別定義中將衍生留白。  即使沒有指定，編譯的結果仍會採用頁面根項目的支援類型做為部分類別的基礎。  不過，倚賴此行為並不是最佳做法。  
  
-   您在程式碼後置中撰寫的事件處理常式必須是執行個體方法，而不能是靜態方法。  這些方法必須由部分類別在 `x:Class` 所識別的 CLR 命名空間內定義。  您無法限制事件處理常式的名稱，藉此指示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器在不同的類別範圍中尋找事件連接的事件處理常式。  
  
-   處理常式必須符合支援類型系統中適當事件的委派。  
  
-   您可特別針對 [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] 語言，使用語言特定 `Handles` 關鍵字建立處理常式與處理常式宣告中執行個體和事件的關聯，而不必附加處理常式與 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的屬性 \(Attribute\)。  不過，這項技術有一些限制，因為 `Handles` 關鍵字無法支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系統的所有特定功能，例如特定路由事件情節或附加事件。  如需詳細資訊，請參閱 [Visual Basic 和 WPF 事件處理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。  
  
<a name="x_Code"></a>   
## x:Code  
 [x:Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) 是 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中定義的指示詞項目。`x:Code` 指示詞項目可以包含內嵌程式碼。  這種以內嵌方式定義的程式碼可以與相同頁面上的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 互動。  下列範例顯示內嵌的 [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] 程式碼。  請注意此程式碼位於 `x:Code` 項目內，而且程式碼必須放在 `<CDATA[`...`]]>` 中，以逸出 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 的內容，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器 \(解譯 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 結構描述或 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 結構描述\) 才不會嘗試依字面將內容解譯為 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]。  
  
 [!code-xml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## 內嵌程式碼限制  
 您應該考慮避免或限制使用內嵌程式碼。  就架構和程式碼撰寫原理而言，將標記和程式碼後置分開，可以讓設計人員和開發人員的角色更為涇渭分明。  就較為技術性的層面來看，撰寫內嵌程式碼的難度可能較高，因為您總是寫入 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 產生的部分類別，而且只能使用預設 XML 命名空間對應。  因為您不能加入 `using` 陳述式，所以必須完整限定您所進行的許多 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 呼叫。  預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 對應包括存在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 組件中的多數 \(但非全部\) [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 命名空間；您必須完全限定對包含在其他 CLR 命名空間內之型別和成員的呼叫。  您也無法在內嵌程式碼中定義超出部分類別的任何項目，而且您參考的所有使用者程式碼實體都必須以成員或變數的形式存在於產生的部分類別內。  其他語言特定的程式設計功能，例如巨集或相對於全域變數或建置變數的 `#ifdef`，也無法使用。  如需詳細資訊，請參閱 [x:Code 內建 XAML 類型](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)。  
  
## 請參閱  
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [x:Code 內建 XAML 類型](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)   
 [建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)