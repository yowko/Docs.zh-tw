---
title: 作法：使用 BindingSource ResetItem 方法引發變更通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 39beb5c7162fb01a51360330216687c158ff433c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583707"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a><span data-ttu-id="1d2b9-102">HOW TO：使用 BindingSource ResetItem 方法引發變更通知</span><span class="sxs-lookup"><span data-stu-id="1d2b9-102">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>
<span data-ttu-id="1d2b9-103">變更、加入或刪除項目時，控制項的某些資料來源並不會引發變更通知。</span><span class="sxs-lookup"><span data-stu-id="1d2b9-103">Some data sources for your controls do not raise change notifications when items are changed, added, or deleted.</span></span> <span data-ttu-id="1d2b9-104">利用 <xref:System.Windows.Forms.BindingSource> 元件，您可以繫結至這類資料來源，並從您的程式碼引發變更通知。</span><span class="sxs-lookup"><span data-stu-id="1d2b9-104">With the <xref:System.Windows.Forms.BindingSource> component, you can bind to such data sources and raise a change notification from your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d2b9-105">範例</span><span class="sxs-lookup"><span data-stu-id="1d2b9-105">Example</span></span>  
 <span data-ttu-id="1d2b9-106">這個表單示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件將清單繫結至 <xref:System.Windows.Forms.DataGridView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1d2b9-106">This form demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind a list to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1d2b9-107">清單不會引發變更通知，因此當清單中的項目變更時，將不會對 <xref:System.Windows.Forms.BindingSource> 呼叫 <xref:System.Windows.Forms.BindingSource.ResetItem%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="1d2b9-107">The list does not raise change notifications, so the <xref:System.Windows.Forms.BindingSource.ResetItem%2A> method on the <xref:System.Windows.Forms.BindingSource> is called when an item in the list is changed.</span></span> <span data-ttu-id="1d2b9-108">。</span><span class="sxs-lookup"><span data-stu-id="1d2b9-108">.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d2b9-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1d2b9-109">Compiling the Code</span></span>  
 <span data-ttu-id="1d2b9-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1d2b9-110">This example requires:</span></span>  
  
- <span data-ttu-id="1d2b9-111">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1d2b9-111">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2b9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d2b9-112">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1d2b9-113">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="1d2b9-113">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="1d2b9-114">如何：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="1d2b9-114">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
