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
ms.openlocfilehash: a95476ff3d182bf2a56e6527c9ee83c8c56af246
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583636"
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="c059a-102">作法：向表單提供標準的功能表項目</span><span class="sxs-lookup"><span data-stu-id="c059a-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="c059a-103">您可以使用 <xref:System.Windows.Forms.MenuStrip> 控制項來為您的表單提供標準功能表。</span><span class="sxs-lookup"><span data-stu-id="c059a-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="c059a-104">沒有這項功能在 Visual Studio 中的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="c059a-104">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="c059a-105">另請參閱[逐步解說：對表單提供標準功能表項目](walkthrough-providing-standard-menu-items-to-a-form.md)。</span><span class="sxs-lookup"><span data-stu-id="c059a-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c059a-106">範例</span><span class="sxs-lookup"><span data-stu-id="c059a-106">Example</span></span>  
 <span data-ttu-id="c059a-107">下列程式碼範例示範如何使用 <xref:System.Windows.Forms.MenuStrip> 控制項來建立具有標準功能表的表單。</span><span class="sxs-lookup"><span data-stu-id="c059a-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="c059a-108"><xref:System.Windows.Forms.StatusStrip> 控制項中會顯示功能表項目選項。</span><span class="sxs-lookup"><span data-stu-id="c059a-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c059a-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c059a-109">Compiling the Code</span></span>  
 <span data-ttu-id="c059a-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="c059a-110">This example requires:</span></span>  
  
- <span data-ttu-id="c059a-111">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="c059a-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c059a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c059a-112">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="c059a-113">MenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="c059a-113">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
