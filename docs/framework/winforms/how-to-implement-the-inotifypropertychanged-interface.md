---
title: HOW TO：實作 INotifyPropertyChanged 介面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: cfdfb22fd854a8f630243e0f612761c71cb778d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802033"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="c1dba-102">HOW TO：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="c1dba-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="c1dba-103">下列程式碼範例示範如何實作<xref:System.ComponentModel.INotifyPropertyChanged>介面。</span><span class="sxs-lookup"><span data-stu-id="c1dba-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="c1dba-104">在 Windows Form 資料繫結中使用的商務物件上實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="c1dba-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="c1dba-105">實作時，介面與繫結控制項的商務物件的屬性變更。</span><span class="sxs-lookup"><span data-stu-id="c1dba-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1dba-106">範例</span><span class="sxs-lookup"><span data-stu-id="c1dba-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c1dba-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1dba-107">See also</span></span>

- [<span data-ttu-id="c1dba-108">如何：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="c1dba-108">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="c1dba-109">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="c1dba-109">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="c1dba-110">如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知</span><span class="sxs-lookup"><span data-stu-id="c1dba-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="c1dba-111">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="c1dba-111">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
