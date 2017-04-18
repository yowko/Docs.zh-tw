---
title: "如何：讓資料可於 XAML 中繫結 | Microsoft Docs"
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
  - "資料繫結, 讓資料可用於"
  - "資料繫結, 讓資料可用於繫結"
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：讓資料可於 XAML 中繫結
本主題討論依據應用程式的需求，讓資料可於[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中繫結的不同方法。  
  
## 範例  
 如果您有想要從 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 繫結的 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件，讓物件可以繫結的一個方法是將物件定義為資源並指定 `x:Key` 給它。  在下列範例中，您有具有 `PersonName` 字串屬性的 `Person` 物件。  `Person` 物件是在名為 `SDKSample` 的命名空間中定義的。  
  
 [!code-xml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 然後您就可以在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中繫結至這個物件，如同下列範例所示。  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 或者，您也可以使用 <xref:System.Windows.Data.ObjectDataProvider> 類別，如同下列範例。  
  
 [!code-xml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 定義繫結的方法一樣：  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 在這個特定範例中，結果是一樣的：您有具有文字內容 `Joe` 的 <xref:System.Windows.Controls.TextBlock>。  但是，<xref:System.Windows.Data.ObjectDataProvider> 類別提供了直接繫結至方法結果等功能。  如果您需要它提供的功能，可以選擇使用 <xref:System.Windows.Data.ObjectDataProvider> 類別。  
  
 但是，如果您是要繫結至已建立的物件，則需要在程式碼中設定 `DataContext`，如同下列範例。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 若要存取 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料以使用 <xref:System.Windows.Data.XmlDataProvider> 類別繫結，請參閱 [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。  若要存取 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 資料以使用 <xref:System.Windows.Data.ObjectDataProvider> 類別繫結，請參閱 [繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。  
  
 如需各種可以指定要繫結之資料的方法的詳細資訊，請參閱 [指定繫結來源](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)。  如需可以繫結的資料型別，或如何實作自己的 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件以進行繫結的詳細資訊，請參閱[繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)。  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)