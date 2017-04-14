---
title: "如何：從繫結的目標屬性取得繫結物件 | Microsoft Docs"
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
  - "資料繫結, 從繫結的目標屬性取得繫結物件"
  - "屬性, 取得繫結物件"
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：從繫結的目標屬性取得繫結物件
這個範例顯示如何從資料繫結目標屬性取得繫結物件。  
  
## 範例  
 執行下列動作，就可以取得 <xref:System.Windows.Data.Binding> 物件：  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  因為目標物件可能有多個屬性使用資料繫結，所以必須指定所要繫結的[相依性屬性](GTMT)。  
  
 或者，您也可以取得 <xref:System.Windows.Data.BindingExpression>，然後取得 <xref:System.Windows.Data.BindingExpression.ParentBinding%2A> 屬性的值。  
  
 如需完整範例，請參閱[繫結驗證範例](http://go.microsoft.com/fwlink/?LinkID=159972) \(英文\)。  
  
> [!NOTE]
>  如果繫結是 <xref:System.Windows.Data.MultiBinding>，請使用 <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>。  如果是 <xref:System.Windows.Data.PriorityBinding>，請使用 <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>。  如果不確定是使用 <xref:System.Windows.Data.Binding>、<xref:System.Windows.Data.MultiBinding> 還是 <xref:System.Windows.Data.PriorityBinding> 繫結目標屬性，則可以使用 <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>。  
  
## 請參閱  
 [使用程式碼建立繫結](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)