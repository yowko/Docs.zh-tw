---
title: "如何：定義和參考資源 | Microsoft Docs"
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
  - "定義資源"
  - "參考資源"
  - "資源, 定義"
  - "資源, 參考"
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：定義和參考資源
這個範例顯示如何定義資源，以及如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中的屬性 \(Attribute\) 參考它。  
  
## 範例  
 下列範例定義兩種資源：一個 <xref:System.Windows.Media.SolidColorBrush> 資源和數個 <xref:System.Windows.Style> 資源。  <xref:System.Windows.Media.SolidColorBrush> 資源 `MyBrush` 用於提供數個屬性 \(Property\) 的值，這些屬性皆以 <xref:System.Windows.Media.Brush> 型別為值。  <xref:System.Windows.Style> 資源 `PageBackground`、`TitleText` 和 `Label` 各以特定的控制項型別為目標。  當使用資源索引鍵參考樣式資源，並用樣式資源設定在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中定義的數個特定控制項項目的 <xref:System.Windows.FrameworkElement.Style%2A> 屬性 \(Property\) 時，該樣式會在目標控制項上設定各種不同的屬性 \(Property\)。  
  
 請注意，`Label` 樣式的 setter 中的其中一個屬性 \(Property\) 也會參考稍早定義的 `MyBrush` 資源。  這是一個常用的技巧，但是要記住，剖析資源以及將資源輸入至資源字典中的順序和它們原來列出的順序一樣。  如果您使用 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)在另一個資源中參考資源，要求資源的順序也會和在字典中找到它們的順序一樣。  請確定您要參考的資源都在要求資源之前就在資源集合中定義完畢。  若要免除嚴格的資源參考建立順序問題，可以改成在執行時期才用 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)參考資源，但是您要知道，這個 DynamicResource 技巧得犧牲效能。  如需詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 [!code-xml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## 請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)