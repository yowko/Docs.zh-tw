---
title: "操作說明：清除繫結"
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
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f8e009d00960f40abcd3c3913a15fa51f1be4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-clear-bindings"></a>操作說明：清除繫結
這個範例顯示如何清除物件的繫結。  
  
## <a name="example"></a>範例  
 若要清除從物件上的個別屬性的繫結，請呼叫<xref:System.Windows.Data.BindingOperations.ClearBinding%2A>如下列範例所示。 下列範例會移除從繫結<xref:System.Windows.Controls.TextBlock.TextProperty>的*mytext*、<xref:System.Windows.Controls.TextBlock>物件。  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 清除繫結會移除繫結，讓相依性屬性的值還原為沒有繫結時應該有的值。 這個值可以是預設值、繼承值或是資料範本繫結的值。  
  
 若要清除的物件上的所有可能屬性繫結，請使用<xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Data.BindingOperations>  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
