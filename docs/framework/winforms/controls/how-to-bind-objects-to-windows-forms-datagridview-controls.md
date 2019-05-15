---
title: HOW TO：將物件繫結至 Windows Forms DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 8cdfd5d8e5ec3dcd22abb9e4efcec3bb61fee1d9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591314"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="2f8ed-102">HOW TO：將物件繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="2f8ed-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="2f8ed-103">下列程式碼範例示範如何將物件的集合繫結至 <xref:System.Windows.Forms.DataGridView> 控制項，以便每個物件顯示成個別的資料列。</span><span class="sxs-lookup"><span data-stu-id="2f8ed-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="2f8ed-104">此範例也說明如何在 <xref:System.Windows.Forms.DataGridViewComboBoxColumn> 中顯示具有列舉類型的屬性，以便下拉式方塊的下拉式清單能包含列舉值。</span><span class="sxs-lookup"><span data-stu-id="2f8ed-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f8ed-105">範例</span><span class="sxs-lookup"><span data-stu-id="2f8ed-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2f8ed-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="2f8ed-106">Compiling the Code</span></span>  
 <span data-ttu-id="2f8ed-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="2f8ed-107">This example requires:</span></span>  
  
- <span data-ttu-id="2f8ed-108">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="2f8ed-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f8ed-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f8ed-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="2f8ed-110">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="2f8ed-110">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="2f8ed-111">如何：存取物件的繫結至 Windows Forms DataGridView 資料列</span><span class="sxs-lookup"><span data-stu-id="2f8ed-111">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
