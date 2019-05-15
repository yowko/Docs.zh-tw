---
title: 作法：使用 BindingSource 反映 Windows Forms 控制項中的資料來源更新
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: 9b3f3c53a74fa00c4e2c674fe6270a22e6e8cef5
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591468"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="2b034-102">HOW TO：使用 BindingSource 反映 Windows Forms 控制項中的資料來源更新</span><span class="sxs-lookup"><span data-stu-id="2b034-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="2b034-103">當您使用資料繫結控制項時，如果資料來源未引發清單變更事件，您有時必須回應資料來源中的變更。</span><span class="sxs-lookup"><span data-stu-id="2b034-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="2b034-104">當您使用 <xref:System.Windows.Forms.BindingSource> 元件將資料來源繫結至 Windows Form 控制項時，可藉由呼叫 <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> 方法來通知控制項資料來源已變更。</span><span class="sxs-lookup"><span data-stu-id="2b034-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b034-105">範例</span><span class="sxs-lookup"><span data-stu-id="2b034-105">Example</span></span>  
 <span data-ttu-id="2b034-106">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> 方法來通知繫結控制項有關資料來源中的更新。</span><span class="sxs-lookup"><span data-stu-id="2b034-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2b034-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2b034-107">Compiling the Code</span></span>  
 <span data-ttu-id="2b034-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="2b034-108">This example requires:</span></span>  
  
- <span data-ttu-id="2b034-109">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="2b034-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b034-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b034-110">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="2b034-111">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="2b034-111">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="2b034-112">如何：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="2b034-112">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
