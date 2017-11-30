---
title: "操作說明：實作屬性變更通知"
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
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6674628acd4ea6b18f98a0ab5e20935220595de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-property-change-notification"></a>操作說明：實作屬性變更通知
若要支援<xref:System.Windows.Data.BindingMode.OneWay>或<xref:System.Windows.Data.BindingMode.TwoWay>繫結至啟用您的繫結目標屬性，以自動反映繫結來源 （例如，讓使用者編輯表單時，自動更新 [預覽] 窗格），動態變更您的類別必須提供適當的屬性已變更通知。 這個範例示範如何建立類別，實作<xref:System.ComponentModel.INotifyPropertyChanged>。  
  
## <a name="example"></a>範例  
 若要實作<xref:System.ComponentModel.INotifyPropertyChanged>您需要宣告<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件，並建立`OnPropertyChanged`方法。 然後，對於您想變更通知的每個屬性，您會在每回更新屬性時呼叫 `OnPropertyChanged`。  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 若要查看如何的範例`Person`類別可以用來支援<xref:System.Windows.Data.BindingMode.TwoWay>繫結，請參閱[控制當文字方塊的文字更新來源](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)。  
  
## <a name="see-also"></a>另請參閱  
 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
