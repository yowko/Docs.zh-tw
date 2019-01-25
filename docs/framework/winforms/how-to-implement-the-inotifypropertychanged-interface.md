---
title: HOW TO：實作 INotifyPropertyChanged 介面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: c92406899cffa56a1001f50f89cb53303df5da39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560070"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>HOW TO：實作 INotifyPropertyChanged 介面
下列程式碼範例示範如何實作<xref:System.ComponentModel.INotifyPropertyChanged>介面。 在 Windows Form 資料繫結中使用的商務物件上實作這個介面。 實作時，介面與繫結控制項的商務物件的屬性變更。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- [如何：套用 PropertyNameChanged 模式](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)
- [Windows Forms 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)
- [如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)
- [Windows Forms 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
