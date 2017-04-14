---
title: "如何：處理 Loaded 事件 | Microsoft Docs"
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
  - "事件, Loaded"
  - "Loaded 事件"
  - "XAML, Loaded 事件"
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：處理 Loaded 事件
本範例示範如何處理 <xref:System.Windows.FrameworkElement.Loaded?displayProperty=fullName> 事件，以及處理該事件的適當情況。  當頁面載入時，處理常式會建立 <xref:System.Windows.Controls.Button>。  
  
## 範例  
 下列範例使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 以及程式碼後置 \(Code\-Behind\) 的檔案。  
  
 [!code-xml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## 請參閱  
 <xref:System.Windows.FrameworkElement>   
 [物件存留期事件](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)