---
title: "如何：使用程式碼建立繫結 | Microsoft Docs"
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
  - "資料繫結, 建立"
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 如何：使用程式碼建立繫結
這個範例顯示如何使用程式碼建立和設定 <xref:System.Windows.Data.Binding>。  
  
## 範例  
 <xref:System.Windows.FrameworkElement> 類別和 <xref:System.Windows.FrameworkContentElement> 類別都會公開 `SetBinding` 方法。  如果您要繫結的項目繼承這些類別的任何一個，可以直接呼叫 <xref:System.Windows.FrameworkElement.SetBinding%2A> 方法。  
  
 下例範例會建立名為 `MyData` 的類別，其包含名為 `MyDataProperty` 的屬性。  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 下列範例顯示如何建立繫結物件來設定繫結的來源。  範例會使用 <xref:System.Windows.FrameworkElement.SetBinding%2A>，將 `myText` \(是 <xref:System.Windows.Controls.TextBlock> 控制項\) 的 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性繫結至 `MyDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 如需完整程式碼範例，請參閱[Code\-only Binding Sample](http://msdn.microsoft.com/zh-tw/764aaf0b-2216-4941-9548-9c98da18d1a6)。  
  
 您可以使用 <xref:System.Windows.Data.BindingOperations> 類別的 <xref:System.Windows.Data.BindingOperations.SetBinding%2A> 靜態方法，而不是呼叫 <xref:System.Windows.FrameworkElement.SetBinding%2A>。  下列範例會呼叫 <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=fullName> 而非 <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=fullName>，將 `myText` 繫結至 `myDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)