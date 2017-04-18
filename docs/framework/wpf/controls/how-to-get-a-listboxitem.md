---
title: "如何：取得 ListBoxItem | Microsoft Docs"
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
  - "ListBox 控制項, 取得 ListBoxItem"
  - "ListBoxItem"
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：取得 ListBoxItem
如果您需要取得位於 <xref:System.Windows.Controls.ListBox> 中特定索引處的特定 <xref:System.Windows.Controls.ListBoxItem>，可以使用 <xref:System.Windows.Controls.ItemContainerGenerator>。  
  
## 範例  
 下列範例顯示 <xref:System.Windows.Controls.ListBox> 及其項目。  
  
 [!code-xml[ListBoxItems#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 下列範例示範如何在 <xref:System.Windows.Controls.ItemContainerGenerator> 的 <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> 屬性中指定項目的索引，以便擷取該項目。  
  
 [!code-csharp[ListBoxItems#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 擷取清單方塊項目之後，您就可以顯示項目的內容，如下列範例所示。  
  
 [!code-csharp[ListBoxItems#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]