---
title: 如何：建立專業樣式的 ToolStrip 控制項
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
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8b2d67f38f9533e60575b45df011f50e7ec091d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="0789b-102">如何：建立專業樣式的 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="0789b-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="0789b-103">您可以藉由自行撰寫衍生自 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類型的類別，賦與應用程式的 <xref:System.Windows.Forms.ToolStrip> 控制項專業外觀和行為 (外觀及操作)。</span><span class="sxs-lookup"><span data-stu-id="0789b-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="0789b-104">沒有對 Visual Studio 中的這項功能有廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="0789b-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="0789b-105">請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0789b-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0789b-106">範例</span><span class="sxs-lookup"><span data-stu-id="0789b-106">Example</span></span>  
 <span data-ttu-id="0789b-107">下列程式碼範例示範如何使用<xref:System.Windows.Forms.ToolStrip>控制項建立複合控制項，以模擬**瀏覽窗格**Microsoft® Outlook® 提供的。</span><span class="sxs-lookup"><span data-stu-id="0789b-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0789b-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0789b-108">Compiling the Code</span></span>  
 <span data-ttu-id="0789b-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0789b-109">This example requires:</span></span>  
  
-   <span data-ttu-id="0789b-110">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="0789b-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0789b-111">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="0789b-111">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0789b-112">您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。</span><span class="sxs-lookup"><span data-stu-id="0789b-112">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0789b-113">另請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](http://msdn.microsoft.com/library/ms233664\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="0789b-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0789b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0789b-114">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="0789b-115">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="0789b-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="0789b-116">操作說明：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="0789b-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
