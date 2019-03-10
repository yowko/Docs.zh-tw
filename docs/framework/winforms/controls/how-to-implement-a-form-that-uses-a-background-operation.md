---
title: HOW TO：實作使用背景作業的表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 9fe514cce4d4aec386f9d61cb84f3a39273c35b0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723331"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="8ae97-102">HOW TO：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="8ae97-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="8ae97-103">下列範例程式會建立表單，計算 Fibonacci 數字。</span><span class="sxs-lookup"><span data-stu-id="8ae97-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="8ae97-104">該計算在執行緒上執行，與使用者介面執行緒中的不同，因此使用者介面會繼續執行，在繼續計算時不會造成延遲。</span><span class="sxs-lookup"><span data-stu-id="8ae97-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="8ae97-105">在 Visual Studio 中對於本工作有更詳盡的支援。</span><span class="sxs-lookup"><span data-stu-id="8ae97-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="8ae97-106">另請參閱[逐步解說：實作使用背景作業的表單](walkthrough-implementing-a-form-that-uses-a-background-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="8ae97-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ae97-107">範例</span><span class="sxs-lookup"><span data-stu-id="8ae97-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ae97-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8ae97-108">Compiling the Code</span></span>  
 <span data-ttu-id="8ae97-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8ae97-109">This example requires:</span></span>  
  
-   <span data-ttu-id="8ae97-110">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="8ae97-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8ae97-111">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="8ae97-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8ae97-112">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8ae97-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8ae97-113">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="8ae97-113">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8ae97-114">無論使用何種多執行緒作業，您都可能會面臨嚴重而複雜的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8ae97-114">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="8ae97-115">請在實作使用多執行緒的任何解決方案之前參閱 [Managed 執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="8ae97-115">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae97-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ae97-116">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="8ae97-117">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="8ae97-117">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="8ae97-118">Managed 執行緒處理的最佳實施方針</span><span class="sxs-lookup"><span data-stu-id="8ae97-118">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
