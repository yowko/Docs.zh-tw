---
title: HOW TO：實作屬性變更通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: d37d468acc94470be8c2afdc495b40168932ec83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931439"
---
# <a name="how-to-implement-property-change-notification"></a>HOW TO：實作屬性變更通知
若要支援<xref:System.Windows.Data.BindingMode.OneWay>或<xref:System.Windows.Data.BindingMode.TwoWay>繫結而讓您能自動反映繫結來源 （例如，將會自動更新，當使用者編輯表單的 [預覽] 窗格），動態變更的繫結目標屬性類別必須提供適當的屬性變更通知。 此範例示範如何建立可實作類別<xref:System.ComponentModel.INotifyPropertyChanged>。  
  
## <a name="example"></a>範例  
 若要實作<xref:System.ComponentModel.INotifyPropertyChanged>您需要宣告<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件，並建立`OnPropertyChanged`方法。 然後，對於您想變更通知的每個屬性，您會在每回更新屬性時呼叫 `OnPropertyChanged`。  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 若要查看範例如何`Person`類別可以用來支援<xref:System.Windows.Data.BindingMode.TwoWay>繫結，請參閱[控制 TextBox 文字更新來源的時機](how-to-control-when-the-textbox-text-updates-the-source.md)。  
  
## <a name="see-also"></a>另請參閱

- [繫結來源概觀](binding-sources-overview.md)
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
