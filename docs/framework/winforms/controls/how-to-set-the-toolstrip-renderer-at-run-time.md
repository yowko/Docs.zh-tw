---
title: 如何：在執行階段設定 ToolStrip 產生器
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
- ToolStripManager class [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 525e2347-0804-49aa-b9a3-9b2cabbf1c35
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f98d4c4b587e30631d53d89484f5de35197fbfc8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-set-the-toolstrip-renderer-at-run-time"></a><span data-ttu-id="11802-102">如何：在執行階段設定 ToolStrip 產生器</span><span class="sxs-lookup"><span data-stu-id="11802-102">How to: Set the ToolStrip Renderer at Run Time</span></span>
<span data-ttu-id="11802-103">您可以藉由建立自訂 `ProfessionalColorTable` 類別，自訂 <xref:System.Windows.Forms.ToolStrip> 控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="11802-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> control by creating a custom `ProfessionalColorTable` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11802-104">範例</span><span class="sxs-lookup"><span data-stu-id="11802-104">Example</span></span>  
 <span data-ttu-id="11802-105">下列程式碼範例示範如何建立自訂 `ProfessionalColorTable` 類別。</span><span class="sxs-lookup"><span data-stu-id="11802-105">The following code example demonstrates how to create a custom `ProfessionalColorTable` class.</span></span> <span data-ttu-id="11802-106">這個類別會定義 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ToolStrip> 控制項的漸層。</span><span class="sxs-lookup"><span data-stu-id="11802-106">This class defines gradients for a <xref:System.Windows.Forms.MenuStrip> and a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
 <span data-ttu-id="11802-107">若要使用此程式碼範例，請編譯並執行應用程式，然後按一下 [變更色彩] 套用在自訂 `ProfessionalColorTable` 類別中定義的漸層。</span><span class="sxs-lookup"><span data-stu-id="11802-107">To use this code example, compile and run the application, and then click **Change Colors** to apply the gradients defined in the custom `ProfessionalColorTable` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="defining-a-custom-professionalcolortable-class"></a><span data-ttu-id="11802-108">定義自訂 ProfessionalColorTable 類別</span><span class="sxs-lookup"><span data-stu-id="11802-108">Defining a Custom ProfessionalColorTable class</span></span>  
 <span data-ttu-id="11802-109">自訂的漸層定義在 `CustomProfessionalColors` 類別中。</span><span class="sxs-lookup"><span data-stu-id="11802-109">The custom gradients are defined in the `CustomProfessionalColors` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#30)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#30)]  
  
## <a name="assigning-a-custom-renderer"></a><span data-ttu-id="11802-110">指派自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="11802-110">Assigning a Custom Renderer</span></span>  
 <span data-ttu-id="11802-111">使用 `CustomProfessionalColors` 類別建立新的 `ToolStripProfessionalRenderer`，並將它指派給 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="11802-111">Create a new `ToolStripProfessionalRenderer` with a `CustomProfessionalColors` class, and assign it to the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#22)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="11802-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="11802-112">Compiling the Code</span></span>  
 <span data-ttu-id="11802-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="11802-113">This example requires:</span></span>  
  
-   <span data-ttu-id="11802-114">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="11802-114">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="11802-115">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="11802-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="11802-116">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="11802-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="11802-117">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="11802-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11802-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11802-118">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.ProfessionalColorTable>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 [<span data-ttu-id="11802-119">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="11802-119">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
