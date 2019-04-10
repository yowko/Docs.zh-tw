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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225595"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="c81a1-102">HOW TO：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="c81a1-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="c81a1-103">下列程式碼範例示範如何實作<xref:System.ComponentModel.INotifyPropertyChanged>介面。</span><span class="sxs-lookup"><span data-stu-id="c81a1-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="c81a1-104">在 Windows Form 資料繫結中使用的商務物件上實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="c81a1-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="c81a1-105">實作時，介面與繫結控制項的商務物件的屬性變更。</span><span class="sxs-lookup"><span data-stu-id="c81a1-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c81a1-106">範例</span><span class="sxs-lookup"><span data-stu-id="c81a1-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c81a1-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c81a1-107">See also</span></span>

- [<span data-ttu-id="c81a1-108">HOW TO：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="c81a1-108">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="c81a1-109">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="c81a1-109">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="c81a1-110">HOW TO：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知</span><span class="sxs-lookup"><span data-stu-id="c81a1-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="c81a1-111">Windows Form 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="c81a1-111">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
