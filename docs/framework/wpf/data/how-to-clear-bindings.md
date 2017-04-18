---
title: "如何：清除繫結 | Microsoft Docs"
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
  - "繫結, 清除"
  - "清除繫結"
  - "資料繫結, 清除繫結"
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：清除繫結
這個範例顯示如何清除物件的繫結。  
  
## 範例  
 若要清除物件個別屬性的繫結，請呼叫 <xref:System.Windows.Data.BindingOperations.ClearBinding%2A>，如同下列範例所示。  下列範例會從 *mytext* \(一個 <xref:System.Windows.Controls.TextBlock> 物件\) 的 <xref:System.Windows.Controls.TextBlock.TextProperty> 移除繫結。  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 清除繫結會移除繫結，讓[相依性屬性](GTMT)的值還原為沒有繫結時應該有的值。  這個值可以是預設值、繼承值或是資料範本繫結的值。  
  
 若要清除物件上所有可能屬性的繫結，請使用 <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>。  
  
## 請參閱  
 <xref:System.Windows.Data.BindingOperations>   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)