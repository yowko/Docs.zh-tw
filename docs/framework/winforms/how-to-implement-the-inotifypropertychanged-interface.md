---
title: 作法：實作 INotifyPropertyChanged 介面
description: 瞭解如何在 Windows Forms 資料系結中使用的商務物件上，執行 INotifyPropertyChanged 介面。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 83d2ef32787d2dbcd877bc77dcede10111098f8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619264"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>作法：實作 INotifyPropertyChanged 介面
下列程式碼範例示範如何執行 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。 在用於 Windows Forms 資料系結的商務物件上，執行此介面。 當執行時，介面會與繫結控制項通訊，而該屬性會在商務物件上進行變更。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [作法：套用 PropertyNameChanged 模式](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows Form 資料繫結](windows-forms-data-binding.md)
- [如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知](./controls/raise-change-notifications--bindingsource.md)
- [Windows Form 資料繫結中的變更告知](change-notification-in-windows-forms-data-binding.md)
