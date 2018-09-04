---
title: 如何：對表單提供標準功能表項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: bf43d27ed728d11b5cde5b9250cfc4614077ed94
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512986"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="595d1-102">如何：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="595d1-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="595d1-103">您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。</span><span class="sxs-lookup"><span data-stu-id="595d1-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="595d1-104">沒有這項功能在 Visual Studio 中的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="595d1-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="595d1-105">另請參閱[逐步解說：對表單提供標準功能表項目](walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="595d1-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="595d1-106">範例</span><span class="sxs-lookup"><span data-stu-id="595d1-106">Example</span></span>  
 <span data-ttu-id="595d1-107">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.MenuStrip> 控制項來建立具有標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="595d1-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="595d1-108"><xref:System.Windows.Forms.StatusStrip> 控制項中會顯示功能表項目選項。</span><span class="sxs-lookup"><span data-stu-id="595d1-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="595d1-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="595d1-109">Compiling the Code</span></span>  
 <span data-ttu-id="595d1-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="595d1-110">This example requires:</span></span>  
  
-   <span data-ttu-id="595d1-111">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="595d1-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="595d1-112">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="595d1-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="595d1-113">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="595d1-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="595d1-114">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="595d1-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595d1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="595d1-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="595d1-116">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="595d1-116">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
