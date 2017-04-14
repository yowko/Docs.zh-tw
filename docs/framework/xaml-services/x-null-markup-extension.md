---
title: "x:Null Markup Extension | Microsoft Docs"
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
  - "NullExtension"
  - "x:NullExtension"
  - "x:Null"
  - "Null"
  - "xNull"
helpviewer_keywords: 
  - "Null markup extension in XAML [XAML Services]"
  - "x:Null markup extension [XAML Services]"
  - "XAML [XAML Services], x:Null markup extension"
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Null Markup Extension
指定 `null` 做為 XAML 成員的值。  
  
## XAML Attribute Usage  
  
```  
<object property="{x:Null}" .../>  
```  
  
## 備註  
 [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] 和 [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] 中的 Null 參考關鍵字是 Null。  Null 參考的 [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] 關鍵字是 `Nothing`，但無論何種程式碼後置語言與 XAML 相關聯，您一定都會使用 `{x:Null}`。  
  
 `x:Null` 標記延伸沒有可設定的屬性。  
  
 null 的使用方式通常都與 CLR <xref:System.Nullable%601> 值的 XAML 成員公開相關聯。  
  
 與所有的 XAML 標記延伸一樣，`x:Null` 標記延伸會使用大括號 \(`{,}`\) 將屬性值的處理逸出為常值或處理常式參考以外的值。  屬性語法是最常配合這個標記延伸使用的語法。  物件項目語法 `<x:Null />` 在技術上可能，但是很少使用，因為 `x:Null` 標記延伸並沒有位置參數或建構引數。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
 在 .NET Framework XAML Services 中，這個標記延伸的處理是由 <xref:System.Windows.Markup.NullExtension> 類別所定義。  
  
## WPF 使用注意事項  
 請注意，`null` 不一定是參考型別相依性屬性的初始未設定值。  每個相依性屬性的初始預設值都有所不同，而且可能取決於屬性特定的中繼資料。  由於其驗證回呼 \(Callback\) 實作 \(Implementation\) 的原因，許多相依性屬性都不會接受 `null` 做為值，不論是透過標記或程式碼都一樣。  如需相依性屬性的詳細資訊，請參閱[相依性屬性概觀](../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.DependencyProperty.UnsetValue>   
 [XAML 概觀 \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)