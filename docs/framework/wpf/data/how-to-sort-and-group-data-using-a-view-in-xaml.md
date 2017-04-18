---
title: "如何：使用 XAML 排序和分組資料 | Microsoft Docs"
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
  - "資料繫結, 在 XAML 檢視中區分資料群組"
  - "資料繫結, 在 XAML 檢視中排序資料"
  - "在 XAML 檢視中區分資料群組"
  - "在 XAML 檢視中排序資料"
  - "檢視, 分組資料"
  - "檢視, 排序資料"
  - "XAML, 在檢視中區分資料群組"
  - "XAML, 在檢視中排序資料"
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 XAML 排序和分組資料
本範例示範如何在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中建立資料收集的檢視。  在檢視中有對目前項目進行分組、排序、篩選和概念化的功能。  
  
## 範例  
 在下列範例中，名為 *places* 的靜態資源是以 *Place* 物件的集合來定義，每一個 *Place* 物件都是由城市名稱和州名所組成。  前置詞 *src* 對應至用於定義資料來源 *Places* 的命名空間。  前置詞 *scm* 對應至 `"clr-namespace:System.ComponentModel;assembly=WindowsBase"`，而 *dat* 對應至 `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`。  
  
 下列範例建立資料集合的檢視，這個檢視中的資料集合會依城市名稱排序，並依州名分組。  
  
 [!code-xml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 然後這個檢視就可以當做繫結來源，如下列範例所示：  
  
 [!code-xml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 若要繫結至 <xref:System.Windows.Data.XmlDataProvider> 資源中定義的 XML 資料，請在 XML 名稱前面加上 @ 符號。  
  
 [!code-xml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## 請參閱  
 <xref:System.Windows.Data.CollectionViewSource>   
 [取得資料集合的預設檢視](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)