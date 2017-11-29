---
title: "如何：實作 INotifyPropertyChanged 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54dc436ec40f001ab1bf90acaedf22745d35d1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="57683-102">如何：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="57683-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="57683-103">下列程式碼範例示範如何實作<xref:System.ComponentModel.INotifyPropertyChanged>介面。</span><span class="sxs-lookup"><span data-stu-id="57683-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="57683-104">在 Windows Form 資料繫結中使用的商務物件上實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="57683-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="57683-105">實作之後，介面溝通商務物件上的屬性變更繫結的控制項。</span><span class="sxs-lookup"><span data-stu-id="57683-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57683-106">範例</span><span class="sxs-lookup"><span data-stu-id="57683-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="57683-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57683-107">See Also</span></span>  
 [<span data-ttu-id="57683-108">操作說明：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="57683-108">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [<span data-ttu-id="57683-109">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="57683-109">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="57683-110">操作說明：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知</span><span class="sxs-lookup"><span data-stu-id="57683-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [<span data-ttu-id="57683-111">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="57683-111">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
