---
title: 如何：實作 IListSource 介面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], implementing
- IListSource interface
ms.assetid: 63ce27aa-2e23-4fbd-8228-0c1726f6c421
ms.openlocfilehash: 3b580208e003a1706cca8e9fdff4ab374b7193ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539412"
---
# <a name="how-to-implement-the-ilistsource-interface"></a><span data-ttu-id="2dd9c-102">如何：實作 IListSource 介面</span><span class="sxs-lookup"><span data-stu-id="2dd9c-102">How to: Implement the IListSource Interface</span></span>
<span data-ttu-id="2dd9c-103">實作<xref:System.ComponentModel.IListSource>介面來建立可繫結的類別未實作<xref:System.Collections.IList>但會提供來自另一個位置的清單。</span><span class="sxs-lookup"><span data-stu-id="2dd9c-103">Implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class that does not implement <xref:System.Collections.IList> but instead provides a list from another location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dd9c-104">範例</span><span class="sxs-lookup"><span data-stu-id="2dd9c-104">Example</span></span>  
 <span data-ttu-id="2dd9c-105">下列程式碼範例示範如何實作<xref:System.ComponentModel.IListSource>介面。</span><span class="sxs-lookup"><span data-stu-id="2dd9c-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.IListSource> interface.</span></span> <span data-ttu-id="2dd9c-106">名為元件`EmployeeListSource`公開<xref:System.Collections.IList>藉由實作資料繫結<xref:System.ComponentModel.IListSource.GetList%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2dd9c-106">A component named `EmployeeListSource` exposes an <xref:System.Collections.IList> for data binding by implementing the <xref:System.ComponentModel.IListSource.GetList%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.IListSource#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/EmployeeListSource.cs#1)]
 [!code-vb[System.ComponentModel.IListSource#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/EmployeeListSource.vb#1)]  
  
 [!code-csharp[System.ComponentModel.IListSource#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Employee.cs#10)]
 [!code-vb[System.ComponentModel.IListSource#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Employee.vb#10)]  
  
 [!code-csharp[System.ComponentModel.IListSource#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/BusinessObjectBase.cs#100)]
 [!code-vb[System.ComponentModel.IListSource#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/BusinessObjectBase.vb#100)]  
  
 [!code-csharp[System.ComponentModel.IListSource#1000](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Form1.cs#1000)]
 [!code-vb[System.ComponentModel.IListSource#1000](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Form1.vb#1000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2dd9c-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2dd9c-107">Compiling the Code</span></span>  
 <span data-ttu-id="2dd9c-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="2dd9c-108">This example requires:</span></span>  
  
-   <span data-ttu-id="2dd9c-109">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="2dd9c-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd9c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dd9c-110">See Also</span></span>  
 <xref:System.ComponentModel.IListSource>  
 <xref:System.ComponentModel.ITypedList>  
 <xref:System.ComponentModel.BindingList%601>  
 <xref:System.ComponentModel.IBindingList>  
 [<span data-ttu-id="2dd9c-111">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2dd9c-111">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
