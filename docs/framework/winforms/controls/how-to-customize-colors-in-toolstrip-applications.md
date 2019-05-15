---
title: 作法：自訂 ToolStrip 應用程式的色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], customizing colors
- colors [Windows Forms], customizing in ToolStrip controls [Windows Forms]
- ToolStrip control [Windows Forms], custom colors
ms.assetid: e2752fe2-1afb-489e-ab96-b7805acd96bc
ms.openlocfilehash: 6719156d0ab6d1e53cd0bd8f16f306577589fb40
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592839"
---
# <a name="how-to-customize-colors-in-toolstrip-applications"></a><span data-ttu-id="3aad8-102">HOW TO：自訂 ToolStrip 應用程式的色彩</span><span class="sxs-lookup"><span data-stu-id="3aad8-102">How to: Customize Colors in ToolStrip Applications</span></span>
<span data-ttu-id="3aad8-103">您可以自訂 <xref:System.Windows.Forms.ToolStrip> 的外觀，藉由使用 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類別來使用自訂的色彩。</span><span class="sxs-lookup"><span data-stu-id="3aad8-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> by using the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class to use customized colors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aad8-104">範例</span><span class="sxs-lookup"><span data-stu-id="3aad8-104">Example</span></span>  
 <span data-ttu-id="3aad8-105">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 在執行階段定義自訂色彩。</span><span class="sxs-lookup"><span data-stu-id="3aad8-105">The following code example demonstrates how to use a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> to define custom colors at run time.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3aad8-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3aad8-106">Compiling the Code</span></span>  
 <span data-ttu-id="3aad8-107">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="3aad8-107">This example requires:</span></span>  
  
- <span data-ttu-id="3aad8-108">System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="3aad8-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aad8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3aad8-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.ProfessionalColorTable>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
