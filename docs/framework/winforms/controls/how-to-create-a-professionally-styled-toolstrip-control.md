---
title: 作法：建立專業樣式的 ToolStrip 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 4e4e899d583eb87b3ced7161f1fd274c0bcc591c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586561"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="5e4a8-102">HOW TO：建立專業樣式的 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="5e4a8-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="5e4a8-103">您可以藉由自行撰寫衍生自 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類型的類別，賦與應用程式的 <xref:System.Windows.Forms.ToolStrip> 控制項專業外觀和行為 (外觀及操作)。</span><span class="sxs-lookup"><span data-stu-id="5e4a8-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="5e4a8-104">沒有這項功能在 Visual Studio 中的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="5e4a8-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="5e4a8-105">請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](walkthrough-creating-a-professionally-styled-toolstrip-control.md)。</span><span class="sxs-lookup"><span data-stu-id="5e4a8-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e4a8-106">範例</span><span class="sxs-lookup"><span data-stu-id="5e4a8-106">Example</span></span>  
 <span data-ttu-id="5e4a8-107">下列程式碼範例示範如何使用<xref:System.Windows.Forms.ToolStrip>控制項，以建立複合控制項，以模擬**瀏覽窗格**Microsoft® Outlook® 提供的。</span><span class="sxs-lookup"><span data-stu-id="5e4a8-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e4a8-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5e4a8-108">Compiling the Code</span></span>  
 <span data-ttu-id="5e4a8-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="5e4a8-109">This example requires:</span></span>  
  
- <span data-ttu-id="5e4a8-110">System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="5e4a8-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4a8-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e4a8-111">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="5e4a8-112">ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="5e4a8-112">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="5e4a8-113">如何：對表單提供標準功能表項目</span><span class="sxs-lookup"><span data-stu-id="5e4a8-113">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)
