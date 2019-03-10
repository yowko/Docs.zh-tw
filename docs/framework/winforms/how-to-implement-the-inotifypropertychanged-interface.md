---
title: HOW TO：實作 INotifyPropertyChanged 介面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 51c0b1fa535921b7b33a16f55bdc8b76d6125e72
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704085"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>HOW TO：實作 INotifyPropertyChanged 介面
下列程式碼範例示範如何實作<xref:System.ComponentModel.INotifyPropertyChanged>介面。 在 Windows Form 資料繫結中使用的商務物件上實作這個介面。 實作時，介面與繫結控制項的商務物件的屬性變更。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- [如何：套用 PropertyNameChanged 模式](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows Forms 資料繫結](windows-forms-data-binding.md)
- [如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知](./controls/raise-change-notifications--bindingsource.md)
- [Windows Forms 資料繫結中的變更告知](change-notification-in-windows-forms-data-binding.md)
