---
title: "如何：定義名稱範圍 | Microsoft Docs"
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
  - "動畫, 分鏡腳本, 在程序性程式碼中"
  - "名稱範圍, 定義"
  - "分鏡腳本, 以程序性程式碼建立動畫"
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：定義名稱範圍
若要在程式碼中以 <xref:System.Windows.Media.Animation.Storyboard> 建立動畫，您必須建立 <xref:System.Windows.NameScope>，並將目標物件的名稱註冊至擁有該名稱範圍的項目。  下列範例建立了 `myMainPanel` 的 <xref:System.Windows.NameScope>、  將 `button1` 和 `button2` 兩個按鈕加入面格中，並註冊這兩個按鈕的名稱。  另外還建立了幾個動畫和 <xref:System.Windows.Media.Animation.Storyboard>。  這個腳本的 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法可用來啟動動畫。  
  
 因為 `button1`、`button2` 和 `myMainPanel` 全都共用相同的名稱範圍，所以任何一個都可以和 <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法一起使用，以啟動動畫。  
  
## 範例  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## 請參閱  
 [使用腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)