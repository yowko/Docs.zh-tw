---
title: 如何：對表單提供標準功能表項目
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
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6e2514adc2b2bbd5b2d1ab3371b48d760842140
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="bd92d-102">如何：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="bd92d-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="bd92d-103">您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。</span><span class="sxs-lookup"><span data-stu-id="bd92d-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="bd92d-104">沒有對 Visual Studio 中的這項功能有廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="bd92d-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="bd92d-105">另請參閱[逐步解說：對表單提供標準功能表項目](http://msdn.microsoft.com/library/ms233662\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="bd92d-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](http://msdn.microsoft.com/library/ms233662\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd92d-106">範例</span><span class="sxs-lookup"><span data-stu-id="bd92d-106">Example</span></span>  
 <span data-ttu-id="bd92d-107">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.MenuStrip> 控制項來建立具有標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="bd92d-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="bd92d-108"><xref:System.Windows.Forms.StatusStrip> 控制項中會顯示功能表項目選項。</span><span class="sxs-lookup"><span data-stu-id="bd92d-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd92d-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bd92d-109">Compiling the Code</span></span>  
 <span data-ttu-id="bd92d-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="bd92d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="bd92d-111">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="bd92d-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="bd92d-112">Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="bd92d-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="bd92d-113">您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。</span><span class="sxs-lookup"><span data-stu-id="bd92d-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="bd92d-114">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="bd92d-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd92d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd92d-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="bd92d-116">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="bd92d-116">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
