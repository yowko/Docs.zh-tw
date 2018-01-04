---
title: "如何：使用 Windows Form DataGridView 控制項中的影像資料行"
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
- cpp
helpviewer_keywords:
- image columns
- image columns [Windows Forms], Windows Forms
- DataGridView control [Windows Forms], image columns
ms.assetid: 8a37aa75-3c6e-4893-91d0-7a5f34bfe287
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b10b2a0ec38a84aa281debf9a091689cac83dd8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-work-with-image-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5bfce-102">如何：使用 Windows Form DataGridView 控制項中的影像資料行</span><span class="sxs-lookup"><span data-stu-id="5bfce-102">How to: Work with Image Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5bfce-103">下列程式碼範例示範如何在互動式使用者介面 (UI) 中使用 <xref:System.Windows.Forms.DataGridView> 影像資料行。</span><span class="sxs-lookup"><span data-stu-id="5bfce-103">The following code example shows how to use the <xref:System.Windows.Forms.DataGridView> image columns in an interactive user interface (UI).</span></span> <span data-ttu-id="5bfce-104">此範例也會示範使用 <xref:System.Windows.Forms.DataGridViewImageColumn> 時的影像大小調整和配置的可能性。</span><span class="sxs-lookup"><span data-stu-id="5bfce-104">The example also demonstrates image sizing and layout possibilities with the <xref:System.Windows.Forms.DataGridViewImageColumn>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bfce-105">範例</span><span class="sxs-lookup"><span data-stu-id="5bfce-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ImageColumn_TicTacToe#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ImageColumn_TicTacToe/CPP/tictactoe.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ImageColumn_TicTacToe#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ImageColumn_TicTacToe/CS/tictactoe.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ImageColumn_TicTacToe#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ImageColumn_TicTacToe/VB/tictactoe.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bfce-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5bfce-106">Compiling the Code</span></span>  
 <span data-ttu-id="5bfce-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="5bfce-107">This example requires:</span></span>  
  
-   <span data-ttu-id="5bfce-108">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="5bfce-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5bfce-109">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="5bfce-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5bfce-110">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="5bfce-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="5bfce-111">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="5bfce-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfce-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="5bfce-112">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 [<span data-ttu-id="5bfce-113">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="5bfce-113">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 [<span data-ttu-id="5bfce-114">操作說明：顯示 Windows Form DataGridView 控制項的儲存格影像</span><span class="sxs-lookup"><span data-stu-id="5bfce-114">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
