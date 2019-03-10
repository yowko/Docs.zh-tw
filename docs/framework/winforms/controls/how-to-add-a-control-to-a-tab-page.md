---
title: HOW TO：將控制項加入索引標籤頁
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 6eb509fd10a5000a5423d624cec5b6d126990d73
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723938"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="1f15a-102">HOW TO：將控制項加入索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="1f15a-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="1f15a-103">您可以使用 Windows Form<xref:System.Windows.Forms.TabControl>以顯示其他控制項，以組織方式。</span><span class="sxs-lookup"><span data-stu-id="1f15a-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="1f15a-104">下列程序示範如何將按鈕加入到第一個索引標籤。如需將圖示新增至索引標籤頁的標籤部分資訊，請參閱[How to:變更 Windows Form TabControl 的外觀](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="1f15a-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="1f15a-105">若要以程式設計方式加入控制項</span><span class="sxs-lookup"><span data-stu-id="1f15a-105">To add a control programmatically</span></span>  
  
1.  <span data-ttu-id="1f15a-106">使用<xref:System.Windows.Forms.Control.ControlCollection.Add%2A>方法所傳回的集合<xref:System.Windows.Forms.Control.Controls%2A>屬性<xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="1f15a-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](~/samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1f15a-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f15a-107">See also</span></span>
- [<span data-ttu-id="1f15a-108">TabControl 控制項</span><span class="sxs-lookup"><span data-stu-id="1f15a-108">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="1f15a-109">TabControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1f15a-109">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="1f15a-110">如何：變更 Windows Form TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="1f15a-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="1f15a-111">如何：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="1f15a-111">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="1f15a-112">如何：新增和移除使用 Windows Form TabControl 的索引標籤</span><span class="sxs-lookup"><span data-stu-id="1f15a-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
