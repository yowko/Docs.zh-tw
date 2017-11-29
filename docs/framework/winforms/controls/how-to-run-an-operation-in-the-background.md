---
title: "如何：在背景執行作業"
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
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c07d2e5dfb89827f00a03d3c361ccc1417cdeeeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="d5081-102">如何：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="d5081-102">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="d5081-103">如果您有要花費較長時間才能完成的作業，但您不想導致使用者介面發生延遲，就可以使用 <xref:System.ComponentModel.BackgroundWorker> 類別在另一個執行緒上執行該作業。</span><span class="sxs-lookup"><span data-stu-id="d5081-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="d5081-104">下列程式碼範例示範如何在背景執行耗時的作業。</span><span class="sxs-lookup"><span data-stu-id="d5081-104">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="d5081-105">表單具有 [開始] 和 [取消] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d5081-105">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="d5081-106">按一下 [開始] 按鈕以執行非同步作業。</span><span class="sxs-lookup"><span data-stu-id="d5081-106">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="d5081-107">按一下 [取消] 按鈕以停止執行中的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="d5081-107">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="d5081-108">每個作業的結果會顯示於 <xref:System.Windows.Forms.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="d5081-108">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="d5081-109">在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中對這項工作有廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="d5081-109">There is extensive support for this task in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="d5081-110">另請參閱[逐步解說：在背景執行作業](http://msdn.microsoft.com/library/ms233672\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="d5081-110">Also see [Walkthrough: Running an Operation in the Background](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5081-111">範例</span><span class="sxs-lookup"><span data-stu-id="d5081-111">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d5081-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d5081-112">Compiling the Code</span></span>  
 <span data-ttu-id="d5081-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d5081-113">This example requires:</span></span>  
  
-   <span data-ttu-id="d5081-114">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="d5081-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d5081-115">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="d5081-115">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d5081-116">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="d5081-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="d5081-117">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="d5081-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5081-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5081-118">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="d5081-119">操作說明：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="d5081-119">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="d5081-120">BackgroundWorker 元件</span><span class="sxs-lookup"><span data-stu-id="d5081-120">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
