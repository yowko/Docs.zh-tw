---
title: 作法：將 Windows Forms 控制項繫結至 Factory 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: b64545528746e50d00f88d626a07ac98839e926c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589730"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="c1f5d-102">作法：將 Windows Forms 控制項繫結至 Factory 物件</span><span class="sxs-lookup"><span data-stu-id="c1f5d-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="c1f5d-103">當您在建立與資料互動的控制項時，有時會發現需要將控制項繫結程序至會產生其他物件的物件或方法。</span><span class="sxs-lookup"><span data-stu-id="c1f5d-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="c1f5d-104">這類物件或方法就叫做 Factory。</span><span class="sxs-lookup"><span data-stu-id="c1f5d-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="c1f5d-105">比方說，您的資料來源可能是從方法呼叫傳回的值，而不是記憶體或類型中的物件。</span><span class="sxs-lookup"><span data-stu-id="c1f5d-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="c1f5d-106">只要來源傳回集合，您就可以將控制項繫結至這種資料來源。</span><span class="sxs-lookup"><span data-stu-id="c1f5d-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="c1f5d-107">使用 <xref:System.Windows.Forms.BindingSource> 控制項可讓您輕鬆將控制項繫結至 Factory 物件。</span><span class="sxs-lookup"><span data-stu-id="c1f5d-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f5d-108">範例</span><span class="sxs-lookup"><span data-stu-id="c1f5d-108">Example</span></span>  
 <span data-ttu-id="c1f5d-109">下列範例示範如何使用 <xref:System.Windows.Forms.BindingSource> 控制項，將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至 Factory 方法。</span><span class="sxs-lookup"><span data-stu-id="c1f5d-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="c1f5d-110">Factory 方法名為 `GetOrdersByCustomerId`，它會傳回 Northwind 資料庫中指定客戶的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="c1f5d-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1f5d-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c1f5d-111">Compiling the Code</span></span>  
 <span data-ttu-id="c1f5d-112">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="c1f5d-112">This example requires:</span></span>  
  
- <span data-ttu-id="c1f5d-113">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c1f5d-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f5d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1f5d-114">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="c1f5d-115">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="c1f5d-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="c1f5d-116">如何：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="c1f5d-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
