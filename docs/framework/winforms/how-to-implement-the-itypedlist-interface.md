---
title: HOW TO：實作 ITypedList 介面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ITypedList interface
- BindingList(Of T) class
- data binding [Windows Forms], implementing
- IBindingList interface
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
ms.openlocfilehash: df4b009ca225b4bf4290398ccd7dd252c9189915
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709778"
---
# <a name="how-to-implement-the-itypedlist-interface"></a><span data-ttu-id="8b25a-102">HOW TO：實作 ITypedList 介面</span><span class="sxs-lookup"><span data-stu-id="8b25a-102">How to: Implement the ITypedList Interface</span></span>
<span data-ttu-id="8b25a-103">實作<xref:System.ComponentModel.ITypedList>介面，以讓您探索可繫結清單的結構描述。</span><span class="sxs-lookup"><span data-stu-id="8b25a-103">Implement the <xref:System.ComponentModel.ITypedList> interface to enable discovery of the schema for a bindable list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b25a-104">範例</span><span class="sxs-lookup"><span data-stu-id="8b25a-104">Example</span></span>  
 <span data-ttu-id="8b25a-105">下列程式碼範例示範如何實作<xref:System.ComponentModel.ITypedList>介面。</span><span class="sxs-lookup"><span data-stu-id="8b25a-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="8b25a-106">名為泛型型別`SortableBindingList`衍生自<xref:System.ComponentModel.BindingList%601>類別，並且實作<xref:System.ComponentModel.ITypedList>介面。</span><span class="sxs-lookup"><span data-stu-id="8b25a-106">A generic type named `SortableBindingList` derives from the <xref:System.ComponentModel.BindingList%601> class and implements the <xref:System.ComponentModel.ITypedList> interface.</span></span> <span data-ttu-id="8b25a-107">簡單的類別，名為`Customer`提供資料繫結至的標頭<xref:System.Windows.Forms.DataGridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="8b25a-107">A simple class named `Customer` provides data, which is bound to the header of a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8b25a-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8b25a-108">Compiling the Code</span></span>  
 <span data-ttu-id="8b25a-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8b25a-109">This example requires:</span></span>  
  
-   <span data-ttu-id="8b25a-110">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8b25a-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b25a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b25a-111">See also</span></span>
- <xref:System.ComponentModel.ITypedList>
- <xref:System.ComponentModel.BindingList%601>
- <xref:System.ComponentModel.IBindingList>
- [<span data-ttu-id="8b25a-112">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b25a-112">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
