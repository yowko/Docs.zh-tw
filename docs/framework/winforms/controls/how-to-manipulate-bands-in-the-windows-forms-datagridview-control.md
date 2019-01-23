---
title: HOW TO：管理 Windows Forms DataGridView 控制項中的寬線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], manipulating bands
- bands [Windows Forms], manipulating in Windows Forms
- DataGridView control [Windows Forms], manipulating bands
ms.assetid: 1ea3470e-480f-4edc-bcbd-51373eca3856
ms.openlocfilehash: d8ec0c0c0fc1b7e5178d138c51e7a579e65869f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543928"
---
# <a name="how-to-manipulate-bands-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1510c-102">HOW TO：管理 Windows Forms DataGridView 控制項中的寬線</span><span class="sxs-lookup"><span data-stu-id="1510c-102">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1510c-103">下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridViewBand> 類別的屬性來管理 <xref:System.Windows.Forms.DataGridView> 資料列和資料行的各種方式，<xref:System.Windows.Forms.DataGridViewRow> 和 <xref:System.Windows.Forms.DataGridViewColumn> 類別便是衍生自這個類別。</span><span class="sxs-lookup"><span data-stu-id="1510c-103">The following code example shows various ways to manipulate <xref:System.Windows.Forms.DataGridView> rows and columns using properties of the <xref:System.Windows.Forms.DataGridViewBand> class from which the <xref:System.Windows.Forms.DataGridViewRow> and <xref:System.Windows.Forms.DataGridViewColumn> classes derive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1510c-104">範例</span><span class="sxs-lookup"><span data-stu-id="1510c-104">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewBandDemo.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewBandDemo.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewbanddemo.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1510c-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1510c-105">Compiling the Code</span></span>  
 <span data-ttu-id="1510c-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1510c-106">This example requires:</span></span>  
  
-   <span data-ttu-id="1510c-107">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1510c-107">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1510c-108">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1510c-108">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1510c-109">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1510c-109">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1510c-110">另請參閱[How to:編譯並執行完整的 Windows Form 程式碼範例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="1510c-110">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1510c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1510c-111">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="1510c-112">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="1510c-112">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
