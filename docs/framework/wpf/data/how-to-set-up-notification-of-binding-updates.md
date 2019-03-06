---
title: HOW TO：設定繫結更新的通知
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 0a28e6fc31601e881cf972f586f75ba0b1526b45
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357959"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>HOW TO：設定繫結更新的通知
本範例顯示如何設定在繫結的繫結目標 (目標) 或繫結來源 (來源) 屬性更新時收到通知。  
  
## <a name="example"></a>範例  
 每次繫結來源或目標更新時，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 都會引發資料更新事件。 在內部，此事件是用於通知使用者介面 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 它該更新，因為繫結的資料已經變更。 請注意，這些事件運作，同時也為單向或雙向繫結才能正常運作，需要實作您的資料類別使用<xref:System.ComponentModel.INotifyPropertyChanged>介面。 如需詳細資訊，請參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。  
  
 設定<xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>或是<xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>屬性 （或兩者） 來`true`繫結中。 您提供用來接聽此事件的處理常式必須直接附加至您想收到其變更通知的元素，或者，如果您想知道內容中的任何變更，則附加至整體資料內容。  
  
 這個範例顯示如何設定在目標屬性更新時收到通知。  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 接著，您可以根據 EventHandler\<T> 委派 (在此範例中是 *OnTargetUpdated*) 指派處理常式來處理事件：  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 事件的參數，如型別或特定元素 (若同一處理常式附加至一個或數個元素)，可用來決定已變更之屬性的詳細資訊，如果在單一元素上有數個繫結屬性，這十分有用。  
  
## <a name="see-also"></a>另請參閱
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
