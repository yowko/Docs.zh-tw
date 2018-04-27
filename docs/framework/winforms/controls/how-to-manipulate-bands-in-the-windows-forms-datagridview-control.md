---
title: 如何：管理 Windows Forms DataGridView 控制項中的寬線
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], manipulating bands
- bands [Windows Forms], manipulating in Windows Forms
- DataGridView control [Windows Forms], manipulating bands
ms.assetid: 1ea3470e-480f-4edc-bcbd-51373eca3856
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 66969071371498767b8693dc42ea4b6b36c73a2b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manipulate-bands-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fa519-102">如何：管理 Windows Forms DataGridView 控制項中的寬線</span><span class="sxs-lookup"><span data-stu-id="fa519-102">How to: Manipulate Bands in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fa519-103">下列程式碼範例示範使用 <xref:System.Windows.Forms.DataGridViewBand> 類別的屬性來管理 <xref:System.Windows.Forms.DataGridView> 資料列和資料行的各種方式，<xref:System.Windows.Forms.DataGridViewRow> 和 <xref:System.Windows.Forms.DataGridViewColumn> 類別便是衍生自這個類別。</span><span class="sxs-lookup"><span data-stu-id="fa519-103">The following code example shows various ways to manipulate <xref:System.Windows.Forms.DataGridView> rows and columns using properties of the <xref:System.Windows.Forms.DataGridViewBand> class from which the <xref:System.Windows.Forms.DataGridViewRow> and <xref:System.Windows.Forms.DataGridViewColumn> classes derive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa519-104">範例</span><span class="sxs-lookup"><span data-stu-id="fa519-104">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewBandDemo.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewBandDemo.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewbanddemo.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa519-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="fa519-105">Compiling the Code</span></span>  
 <span data-ttu-id="fa519-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="fa519-106">This example requires:</span></span>  
  
-   <span data-ttu-id="fa519-107">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="fa519-107">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="fa519-108">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="fa519-108">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="fa519-109">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="fa519-109">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="fa519-110">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="fa519-110">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa519-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa519-111">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewBand>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 [<span data-ttu-id="fa519-112">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="fa519-112">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
