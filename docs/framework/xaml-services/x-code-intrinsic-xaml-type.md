---
title: "x:Code Intrinsic XAML Type | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Code"
  - "x:Code"
  - "xCode"
helpviewer_keywords: 
  - "Code directive in XAML [XAML Services]"
  - "x:Code XAML directive element [XAML Services]"
  - "XAML [XAML Services], x:Code directive element"
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: 19
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 19
---
# x:Code Intrinsic XAML Type
允許在 XAML 產物內放置程式碼。  這類程式碼可由會編譯 XAML 的任何 XAML 處理器加以編譯，或是讓 XAML 產物於稍後使用，例如在執行階段解譯。  
  
## XAML 物件項目用法  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## 備註  
 `x:Code` XAML 指示詞項目內的程式碼，依然會在一般 XAML 命名空間和提供的 XML 命名空間內進行解譯。  因此，通常也必須將為 `x:Code` 使用的程式碼置於 `CDATA` 區段內。  
  
 XAML 產物的所有可能部署機制都不允許 `x:Code`。  在特定的架構中 \(例如 WPF\)，必須編譯程式碼。  在其他架構中，一般都不允許 `x:Code` 使用方式。  
  
 對於允許 Managed `x:Code` 內容的架構，適用於 `x:Code` 內容的正確語言編譯器，必須取決於用來編譯應用程式之包含專案的設定和目標。  
  
## WPF 使用注意事項  
 `x:Code` 內宣告的 WPF 程式碼有幾項必須注意的限制：  
  
-   `x:Code` 指示詞項目必須是 XAML 產物根項目的直接子項目。  
  
-   [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) 必須在父代根項目上提供。  
  
-   編譯必須將放在 `x:Code` 內的程式碼，視為包含在該 XAML 頁面已建立之部分類別的範圍內。  因此，您定義的所有程式碼都必須是該部分類別的成員或變數。  
  
-   除了在部分類別內將類別巢狀化 \(允許巢狀化但不常見，因為在 XAML 中無法參考巢狀類別\) 之外，您無法定義其他類別。  除了現有部分類別所使用的命名空間以外，您無法定義或加入至其他 CLR 命名空間。  
  
-   您必須完整限定部分類別 CLR 命名空間外部的程式碼實體參考。  如果宣告的成員是部分類別可覆寫成員的覆寫項目，則必須使用語言特定覆寫關鍵字加以指定。  如果在 `x:Code` 範圍中宣告的成員與在 XAML 外部建立的部分類別成員產生衝突，而導致編譯器回報這種衝突狀況，則 XAML 檔案會無法編譯或載入。  
  
## 請參閱  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [WPF 中的程式碼後置和 XAML](../../../ocs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [XAML 概觀 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)