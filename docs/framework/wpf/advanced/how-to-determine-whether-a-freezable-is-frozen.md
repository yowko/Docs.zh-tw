---
title: "如何：決定 Freezable 是否凍結 | Microsoft Docs"
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
  - "Freezable 物件, 判斷是否凍結"
  - "IsFrozen 屬性"
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：決定 Freezable 是否凍結
下列範例說明如何判斷 <xref:System.Windows.Freezable> 物件是否凍結。  如果您試著修改凍結的 <xref:System.Windows.Freezable> 物件，它會擲回 <xref:System.InvalidOperationException>。  為避免擲回這個例外狀況，請使用 <xref:System.Windows.Freezable> 物件的 <xref:System.Windows.Freezable.IsFrozen%2A> 屬性，判斷物件是否凍結。  
  
## 範例  
 下列範例會凍結 <xref:System.Windows.Media.SolidColorBrush>，然後使用 <xref:System.Windows.Freezable.IsFrozen%2A> 屬性測試它，以判斷它是否凍結。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 如需 <xref:System.Windows.Freezable> 物件的詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
## 請參閱  
 <xref:System.Windows.Freezable>   
 <xref:System.Windows.Freezable.IsFrozen%2A>   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)