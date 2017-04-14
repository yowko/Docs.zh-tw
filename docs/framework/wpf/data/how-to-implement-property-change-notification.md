---
title: "如何：實作屬性變更通知 | Microsoft Docs"
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
  - "變更告知"
  - "資料繫結, 屬性變更告知"
  - "變更告知"
  - "屬性, 變更告知"
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：實作屬性變更通知
若要支援 <xref:System.Windows.Data.BindingMode> 或 <xref:System.Windows.Data.BindingMode> 繫結而讓[繫結目標](GTMT)屬性能自動反映[繫結來源](GTMT)的動態變更 \(例如，當使用者編輯表單時自動更新預覽窗格\)，您的類別就必須提供適當的屬性變更通知。  本範例顯示如何建立可實作 <xref:System.ComponentModel.INotifyPropertyChanged> 的類別。  
  
## 範例  
 若要實作 <xref:System.ComponentModel.INotifyPropertyChanged>，您必須宣告 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件並建立 `OnPropertyChanged` 方法。  然後，對於您想變更通知的每個屬性，您會在每回更新屬性時呼叫 `OnPropertyChanged`。  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 若要查看 `Person` 類別可如何用於支援 <xref:System.Windows.Data.BindingMode> 繫結的範例，請參閱 [TextBox 文字更新來源時控制](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)。  
  
## 請參閱  
 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)