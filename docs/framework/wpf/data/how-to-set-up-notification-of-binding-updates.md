---
title: "如何：設定繫結更新的通知 | Microsoft Docs"
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
  - "繫結, 更新, 告知"
  - "資料繫結, 繫結更新的告知"
  - "告知, 繫結更新"
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：設定繫結更新的通知
本範例顯示如何設定在繫結的[繫結目標](GTMT) \(目標\) 或[繫結來源](GTMT) \(來源\) 屬性更新時收到通知。  
  
## 範例  
 每次繫結來源或目標更新時，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 都會引發更新事件。  在內部，此事件是用於通知[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 它該更新，因為繫結的資料已經更新。  請注意，為了要讓這些事件運作，以及讓單向或雙向繫結運作正常，您必須用 <xref:System.ComponentModel.INotifyPropertyChanged> 介面實作您的資料類別。  如需詳細資訊，請參閱 [實作屬性變更通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)。  
  
 將繫結的 <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> 或 <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> 屬性 \(或兩者\) 設為 `true`。  您提供用來接聽此事件的處理常式必須直接附加至知道其變更的項目，或者，如果您想知道內容中的任何變更，則附加至整體資料內容。  
  
 這個範例顯示如何設定在目標屬性變更時收到通知。  
  
 [!code-xml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 接著，您可以根據 EventHandler\<T\> 委派 \(在此範例中是 *OnTargetUpdated*\) 指定事件的處理常式。  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 事件的參數，如型別或特定項目 \(若同一處理常式附加至一個或數個項目\)，可用來決定已變更之屬性的詳細資訊，如果在單一項目上有數個繫結屬性，這十分有用。  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)