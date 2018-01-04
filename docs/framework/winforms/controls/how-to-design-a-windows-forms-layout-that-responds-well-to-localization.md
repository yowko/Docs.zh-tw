---
title: "如何：設計可適當回應當地語系化的 Windows Form 配置"
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
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 072d0694b3e92d9bf4bd8d0cf118b2f4af024af6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="6a84a-102">如何：設計可適當回應當地語系化的 Windows Form 配置</span><span class="sxs-lookup"><span data-stu-id="6a84a-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="6a84a-103">建立準備好當地語系化的表單，將會大幅加速開發國際市場。</span><span class="sxs-lookup"><span data-stu-id="6a84a-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="6a84a-104">您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來實作版面配置，當控制項因 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更而調整大小時，它會依正常程序回應。</span><span class="sxs-lookup"><span data-stu-id="6a84a-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a84a-105">範例</span><span class="sxs-lookup"><span data-stu-id="6a84a-105">Example</span></span>  
 <span data-ttu-id="6a84a-106">在您翻譯顯示字串值為其他語言時，此表單會示範如何建立可按比例調整的版面配置。</span><span class="sxs-lookup"><span data-stu-id="6a84a-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="6a84a-107">這個翻譯的過程稱為「當地語系化」(localization)。</span><span class="sxs-lookup"><span data-stu-id="6a84a-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="6a84a-108">如需詳細資訊，請參閱[當地語系化](../../../../docs/standard/globalization-localization/localization.md)。</span><span class="sxs-lookup"><span data-stu-id="6a84a-108">For more information, see [Localization](../../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
 <span data-ttu-id="6a84a-109">在 Visual Studio 中對於本工作有更詳盡的支援。</span><span class="sxs-lookup"><span data-stu-id="6a84a-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="6a84a-110">另請參閱[逐步解說：建立可調整比例以配合當地語系化的配置](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="6a84a-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  <span data-ttu-id="6a84a-111">[操作說明：在 TableLayoutPanel 控制項中對齊和縮放控制項](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-111">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="6a84a-112">[逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-112">[Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="6a84a-113">[如何：擴展 TableLayoutPanel 控制項中的資料列和資料行](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-113">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="6a84a-114">[如何：編輯 TableLayoutPanel 控制項中的資料行和資料列](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-114">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
5.  <span data-ttu-id="6a84a-115">[逐步解說：使用 Windows Forms 控制項中的智慧標籤執行一般工作](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-115">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))</span></span>  
  
6.  <span data-ttu-id="6a84a-116">[逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-116">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
7.  <span data-ttu-id="6a84a-117">[逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-117">[Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))</span></span>  
  
8.  <span data-ttu-id="6a84a-118">[如何‎：使用 AutoSize 和 TableLayoutPanel 控制項支援 Windows Forms 的當地語系化](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-118">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))</span></span>  
  
9. <span data-ttu-id="6a84a-119">[逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="6a84a-119">[Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a84a-120">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6a84a-120">Compiling the Code</span></span>  
 <span data-ttu-id="6a84a-121">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="6a84a-121">This example requires:</span></span>  
  
-   <span data-ttu-id="6a84a-122">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="6a84a-122">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6a84a-123">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="6a84a-123">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6a84a-124">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="6a84a-124">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6a84a-125">另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="6a84a-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a84a-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="6a84a-126">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="6a84a-127">當地語系化</span><span class="sxs-lookup"><span data-stu-id="6a84a-127">Localization</span></span>](../../../../docs/standard/globalization-localization/localization.md)
