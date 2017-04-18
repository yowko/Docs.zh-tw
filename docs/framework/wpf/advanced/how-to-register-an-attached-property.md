---
title: "如何：註冊附加屬性 | Microsoft Docs"
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
  - "附加屬性, 註冊"
  - "註冊附加屬性"
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：註冊附加屬性
本範例顯示如何註冊[附加屬性](GTMT)並提供公用存取子，以便在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼中都可以使用該屬性。  附加屬性是[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 所定義的語法概念。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 型別的大部分附加屬性也會以[相依性屬性](GTMT)的方式實作。  您可以在任何 <xref:System.Windows.DependencyObject> 型別上使用[相依性屬性](GTMT)。  
  
## 範例  
 下列範例顯示如何藉由使用 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 方法，將附加屬性註冊為相依性屬性。  提供者類別有個選項可以提供屬性的預設中繼資料，適用於在其他類別上使用屬性時，除非類別會覆寫中繼資料。  在本範例中，`IsBubbleSource` 屬性的預設值會設為 `false`。  
  
 附加屬性 \(Property\) 的提供者類別 \(即使未註冊成相依性屬性 \(Property\)\) 必須提供遵循命名慣例 `Set`*\[AttachedPropertyName\]* 和 `Get`*\[AttachedPropertyName\]* 的靜態 get 和 set 存取子。這些存取子是必要的，才能讓作用的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 讀取器將屬性 \(Property\) 辨認為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的屬性 \(Attribute\) 並解析適當的型別。  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## 請參閱  
 <xref:System.Windows.DependencyProperty>   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)