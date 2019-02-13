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
ms.openlocfilehash: e3ca2ab4be95a77bd2549ae8435d8158434532da
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220240"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="bba68-102">HOW TO：將物件繫結至 Windows Forms DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="bba68-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="bba68-103">下列程式碼範例示範如何將物件的集合繫結至 <xref:System.Windows.Forms.DataGridView> 控制項，以便每個物件顯示成個別的資料列。</span><span class="sxs-lookup"><span data-stu-id="bba68-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="bba68-104">此範例也說明如何在 <xref:System.Windows.Forms.DataGridViewComboBoxColumn> 中顯示具有列舉類型的屬性，以便下拉式方塊的下拉式清單能包含列舉值。</span><span class="sxs-lookup"><span data-stu-id="bba68-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bba68-105">範例</span><span class="sxs-lookup"><span data-stu-id="bba68-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bba68-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bba68-106">Compiling the Code</span></span>  
 <span data-ttu-id="bba68-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="bba68-107">This example requires:</span></span>  
  
-   <span data-ttu-id="bba68-108">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="bba68-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bba68-109">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="bba68-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bba68-110">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="bba68-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba68-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bba68-111">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="bba68-112">在 Windows Forms DataGridView 控制項中顯示資料</span><span class="sxs-lookup"><span data-stu-id="bba68-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bba68-113">如何：存取物件的繫結至 Windows Forms DataGridView 資料列</span><span class="sxs-lookup"><span data-stu-id="bba68-113">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
