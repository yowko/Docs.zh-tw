---
title: "如何：使用程式碼建立繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2ad9f855f1051ad6c0afac6bc813eecf87f7d36
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-binding-in-code"></a>如何：使用程式碼建立繫結
此範例示範如何建立及設定<xref:System.Windows.Data.Binding>程式碼中。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.FrameworkElement>類別和<xref:System.Windows.FrameworkContentElement>類別同時公開`SetBinding`方法。 如果您要繫結任一種類別繼承的項目，您可以呼叫<xref:System.Windows.FrameworkElement.SetBinding%2A>直接的方法。  
  
 下列範例會建立名為，類別`MyData`，其中包含一個名為屬性`MyDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 下列範例會示範如何建立繫結物件來設定繫結來源。  此範例會使用<xref:System.Windows.FrameworkElement.SetBinding%2A>繫結<xref:System.Windows.Controls.TextBlock.Text%2A>屬性`myText`，也就是<xref:System.Windows.Controls.TextBlock>控制，請為`MyDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 如需完整的程式碼範例，請參閱[純程式碼的繫結範例](http://msdn.microsoft.com/library/764aaf0b-2216-4941-9548-9c98da18d1a6)。  
  
 而不是呼叫<xref:System.Windows.FrameworkElement.SetBinding%2A>，您可以使用<xref:System.Windows.Data.BindingOperations.SetBinding%2A>靜態方法<xref:System.Windows.Data.BindingOperations>類別。 下列範例會呼叫<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>而不是<xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>繫結`myText`至`myDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
