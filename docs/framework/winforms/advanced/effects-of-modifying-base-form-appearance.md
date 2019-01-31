---
title: 修改基底表單外觀的效果
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: fc0edaa8ca115a09eb6d8382a12d9a7c0c0db7f6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260160"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a><span data-ttu-id="bee4b-102">修改基底表單外觀的效果</span><span class="sxs-lookup"><span data-stu-id="bee4b-102">Effects of Modifying a Base Form's Appearance</span></span>
<span data-ttu-id="bee4b-103">在應用程式開發期間，您通常可能需要變更專案中 (或其他專案中) 的其他表單所繼承之基底表單的外觀。</span><span class="sxs-lookup"><span data-stu-id="bee4b-103">During application development, you may often need to change the appearance of the base form from which other forms in the project (or in other projects) are inheriting.</span></span>  
  
 <span data-ttu-id="bee4b-104">在設計階段，建置包含基底表單的專案時，基底表單外觀的變更 (也就是設定屬性或增減控制項) 會反映在繼承的表單上。</span><span class="sxs-lookup"><span data-stu-id="bee4b-104">At design time, changes to the base form's appearance (be it the setting of properties or the addition and subtraction of controls) are reflected on inherited forms when the project containing the base form is built.</span></span> <span data-ttu-id="bee4b-105">只是儲存基底表單的變更並不足夠。</span><span class="sxs-lookup"><span data-stu-id="bee4b-105">It is not sufficient for you to simply save the changes to the base form.</span></span> <span data-ttu-id="bee4b-106">若要建置專案，請從 [建置] 功能表中選擇 [建置]。</span><span class="sxs-lookup"><span data-stu-id="bee4b-106">To build a project, choose **Build** from the **Build** menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bee4b-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="bee4b-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bee4b-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="bee4b-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bee4b-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="bee4b-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
 <span data-ttu-id="bee4b-110">在執行階段對基底表單所做的修改對於已具現化的繼承表單沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="bee4b-110">Modifications made to the base form at run time have no affect on inherited forms that are already instantiated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee4b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bee4b-111">See also</span></span>
- [<span data-ttu-id="bee4b-112">base</span><span class="sxs-lookup"><span data-stu-id="bee4b-112">base</span></span>](~/docs/csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="bee4b-113">如何：繼承 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bee4b-113">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
- [<span data-ttu-id="bee4b-114">Windows Forms 視覺繼承</span><span class="sxs-lookup"><span data-stu-id="bee4b-114">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
