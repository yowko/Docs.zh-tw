---
title: 如何：處理 Windows Forms 控制項中的使用者輸入事件
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
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7599bcbd93183aa06bb35c30e0265b9b15b966cc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="81774-102">如何：處理 Windows Forms 控制項中的使用者輸入事件</span><span class="sxs-lookup"><span data-stu-id="81774-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="81774-103">此範例示範如何處理 Windows Form 控制項中可能發生的大部分鍵盤、滑鼠、焦點和驗證事件。</span><span class="sxs-lookup"><span data-stu-id="81774-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="81774-104">名為 `TextBoxInput` 的文字方塊中有焦點時，會接收那些事件，而每個事件的相關資訊，會依據事件引發的順序，寫入名為 `TextBoxOutput` 的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="81774-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="81774-105">應用程式中也包含一組核取方塊，可用來篩選所要報告的事件。</span><span class="sxs-lookup"><span data-stu-id="81774-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81774-106">範例</span><span class="sxs-lookup"><span data-stu-id="81774-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="81774-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="81774-107">Compiling the Code</span></span>  
 <span data-ttu-id="81774-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="81774-108">This example requires:</span></span>  
  
-   <span data-ttu-id="81774-109">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="81774-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="81774-110">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="81774-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="81774-111">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="81774-111">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="81774-112">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="81774-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81774-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81774-113">See Also</span></span>  
 [<span data-ttu-id="81774-114">Windows Forms 中的使用者輸入</span><span class="sxs-lookup"><span data-stu-id="81774-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
