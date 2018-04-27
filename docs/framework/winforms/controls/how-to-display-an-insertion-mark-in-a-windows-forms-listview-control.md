---
title: 如何：在 Windows Forms ListView 控制項中顯示插入標記
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
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f50aa16424a50d51fa88bb89d393c9da0f5def7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="71193-102">如何：在 Windows Forms ListView 控制項中顯示插入標記</span><span class="sxs-lookup"><span data-stu-id="71193-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="71193-103"><xref:System.Windows.Forms.ListView> 控制項中的插入標記會向使用者顯示將會插入拖曳項目的點。</span><span class="sxs-lookup"><span data-stu-id="71193-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="71193-104">當使用者將項目拖曳至另外兩個項目之間的某個點時，插入標記會顯示該項目的預期新位置。</span><span class="sxs-lookup"><span data-stu-id="71193-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71193-105">當您的應用程式呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法時，只有 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 上會出現插入標記功能。</span><span class="sxs-lookup"><span data-stu-id="71193-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="71193-106">在舊版作業系統上，與插入標記相關的任何程式碼都沒有任何作用，而且不會出現插入標記。</span><span class="sxs-lookup"><span data-stu-id="71193-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="71193-107">如需詳細資訊，請參閱<xref:System.Windows.Forms.ListViewInsertionMark>。</span><span class="sxs-lookup"><span data-stu-id="71193-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="71193-108">下圖顯示插入標記：</span><span class="sxs-lookup"><span data-stu-id="71193-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="71193-109">![ListView 插入標記](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="71193-109">![A ListView Insertion Mark](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="71193-110">下列程式碼範例示範如何使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="71193-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71193-111">範例</span><span class="sxs-lookup"><span data-stu-id="71193-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="71193-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="71193-112">Compiling the Code</span></span>  
 <span data-ttu-id="71193-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="71193-113">This example requires:</span></span>  
  
-   <span data-ttu-id="71193-114">System 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="71193-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="71193-115">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="71193-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="71193-116">您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。</span><span class="sxs-lookup"><span data-stu-id="71193-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="71193-117">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="71193-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71193-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71193-118">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewInsertionMark>  
 [<span data-ttu-id="71193-119">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="71193-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="71193-120">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="71193-120">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="71193-121">Windows XP 功能和 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="71193-121">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="71193-122">逐步解說：在 Windows Forms 中執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="71193-122">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
