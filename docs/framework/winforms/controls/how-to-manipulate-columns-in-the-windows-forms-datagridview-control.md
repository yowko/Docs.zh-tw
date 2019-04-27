---
title: HOW TO：管理 Windows Forms DataGridView 控制項中的資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGridView control [Windows Forms], manipulating columns
- columns [Windows Forms], manipulating
- data grids [Windows Forms], manipulating columns
ms.assetid: d8cfe6b3-bbab-4182-bec2-0517d9f1eaf6
ms.openlocfilehash: 95d41093178c56c999ecfe515a380927513e715d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913714"
---
# <a name="how-to-manipulate-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="56193-102">HOW TO：管理 Windows Forms DataGridView 控制項中的資料行</span><span class="sxs-lookup"><span data-stu-id="56193-102">How to: Manipulate Columns in the Windows Forms DataGridView Control</span></span>

<span data-ttu-id="56193-103">下列程式碼範例顯示使用 <xref:System.Windows.Forms.DataGridViewColumn> 類別屬性操作 <xref:System.Windows.Forms.DataGridView> 資料行的各種方式。</span><span class="sxs-lookup"><span data-stu-id="56193-103">The following code example shows the various ways to manipulate <xref:System.Windows.Forms.DataGridView> columns using properties of the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>

## <a name="example"></a><span data-ttu-id="56193-104">範例</span><span class="sxs-lookup"><span data-stu-id="56193-104">Example</span></span>

[!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewColumnDemo.cpp#100)]
[!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewColumnDemo.cs#100)]
[!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewcolumndemo.vb#100)]

## <a name="compiling-the-code"></a><span data-ttu-id="56193-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="56193-105">Compiling the Code</span></span>

<span data-ttu-id="56193-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="56193-106">This example requires:</span></span>

- <span data-ttu-id="56193-107">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="56193-107">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

<span data-ttu-id="56193-108">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="56193-108">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="56193-109">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="56193-109">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>

## <a name="see-also"></a><span data-ttu-id="56193-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56193-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [<span data-ttu-id="56193-111">在 Windows Forms DataGridView 控制項中利用儲存格、資料列和資料行進行程式設計</span><span class="sxs-lookup"><span data-stu-id="56193-111">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
