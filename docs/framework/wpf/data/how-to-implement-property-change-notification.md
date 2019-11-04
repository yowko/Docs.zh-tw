---
title: 操作說明：實作屬性變更通知
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
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459740"
---
# <a name="how-to-implement-property-change-notification"></a>操作說明：實作屬性變更通知
若要支援 <xref:System.Windows.Data.BindingMode.OneWay> 或 <xref:System.Windows.Data.BindingMode.TwoWay> 系結，讓您的系結目標屬性自動反映系結來源的動態變更（例如，當使用者編輯表單時，自動更新預覽窗格），您的類別必須提供適當的屬性變更通知。 這個範例示範如何建立可執行 <xref:System.ComponentModel.INotifyPropertyChanged>的類別。  
  
## <a name="example"></a>範例  
 若要執行 <xref:System.ComponentModel.INotifyPropertyChanged> 您需要宣告 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件，並建立 `OnPropertyChanged` 方法。 然後，對於您想變更通知的每個屬性，您會在每回更新屬性時呼叫 `OnPropertyChanged`。  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 若要查看如何使用 `Person` 類別來支援 <xref:System.Windows.Data.BindingMode.TwoWay> 系結的範例，請參閱[控制 TextBox 文字更新來源](how-to-control-when-the-textbox-text-updates-the-source.md)的時機。  
  
## <a name="see-also"></a>請參閱

- [繫結來源概觀](binding-sources-overview.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
