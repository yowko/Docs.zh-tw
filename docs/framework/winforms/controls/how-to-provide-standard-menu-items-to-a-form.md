---
title: HOW TO：向表單提供標準的功能表項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
ms.openlocfilehash: 530e4185b065c9483f112146c496860f2c8a52c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662327"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="1e91d-102">HOW TO：向表單提供標準的功能表項目</span><span class="sxs-lookup"><span data-stu-id="1e91d-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="1e91d-103">您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。</span><span class="sxs-lookup"><span data-stu-id="1e91d-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="1e91d-104">沒有這項功能在 Visual Studio 中的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="1e91d-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="1e91d-105">另請參閱[逐步解說：對表單提供標準功能表項目](walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="1e91d-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e91d-106">範例</span><span class="sxs-lookup"><span data-stu-id="1e91d-106">Example</span></span>  
 <span data-ttu-id="1e91d-107">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.MenuStrip> 控制項來建立具有標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="1e91d-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="1e91d-108"><xref:System.Windows.Forms.StatusStrip> 控制項中會顯示功能表項目選項。</span><span class="sxs-lookup"><span data-stu-id="1e91d-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e91d-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1e91d-109">Compiling the Code</span></span>  
 <span data-ttu-id="1e91d-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1e91d-110">This example requires:</span></span>  
  
- <span data-ttu-id="1e91d-111">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1e91d-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1e91d-112">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1e91d-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1e91d-113">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1e91d-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e91d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e91d-114">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="1e91d-115">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="1e91d-115">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
