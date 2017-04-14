---
title: "如何：建立簡單繫結 | Microsoft Docs"
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
  - "資料繫結, 建立"
  - "資料繫結, 建立簡單繫結"
  - "簡單繫結, 建立"
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：建立簡單繫結
這個範例顯示如何建立簡單 <xref:System.Windows.Data.Binding>。  
  
## 範例  
 在這個範例中，您有一個字串屬性命名為 `PersonName` 的 `Person` 物件。  `Person` 物件是在名為 `SDKSample` 的命名空間 \(Namespace\) 中定義的。  
  
 下列範例會具現化 \(Instantiate\) 具有 `Joe` 之 `PersonName` 屬性值的 `Person` 物件。  這是在 `Resources` 區段中完成，而且會指派 `x:Key`。  
  
 [!code-xml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
[!code-xml[SimpleBinding#EndWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#endwindow)]  
  
 若要繫結至 `PersonName` 屬性，則請執行下列動作：  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 因此，<xref:System.Windows.Controls.TextBlock> 會顯示值 "Joe"。  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)