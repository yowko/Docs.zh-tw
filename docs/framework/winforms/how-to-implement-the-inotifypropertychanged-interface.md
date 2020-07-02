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
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="a5d56-103">作法：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="a5d56-103">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="a5d56-104">下列程式碼範例示範如何執行 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。</span><span class="sxs-lookup"><span data-stu-id="a5d56-104">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="a5d56-105">在用於 Windows Forms 資料系結的商務物件上，執行此介面。</span><span class="sxs-lookup"><span data-stu-id="a5d56-105">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="a5d56-106">當執行時，介面會與繫結控制項通訊，而該屬性會在商務物件上進行變更。</span><span class="sxs-lookup"><span data-stu-id="a5d56-106">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5d56-107">範例</span><span class="sxs-lookup"><span data-stu-id="a5d56-107">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a5d56-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5d56-108">See also</span></span>

- [<span data-ttu-id="a5d56-109">作法：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="a5d56-109">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="a5d56-110">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="a5d56-110">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="a5d56-111">如何：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更告知</span><span class="sxs-lookup"><span data-stu-id="a5d56-111">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="a5d56-112">Windows Form 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="a5d56-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
