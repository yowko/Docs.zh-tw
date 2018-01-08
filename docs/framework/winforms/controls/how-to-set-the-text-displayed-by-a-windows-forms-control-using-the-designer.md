---
title: "如何：使用設計工具設定由 Windows Form 控制項所顯示的文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6d49466e5dd25bbe9e97262d68f2c3fb2f8ba1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="305a5-102">如何：使用設計工具設定由 Windows Form 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="305a5-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="305a5-103">Windows Form 控制項通常會顯示控制項的主要功能與相關的文字。</span><span class="sxs-lookup"><span data-stu-id="305a5-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="305a5-104">例如，<xref:System.Windows.Forms.Button>控制項通常會顯示表示按下按鈕時，將會執行什麼動作的標題。</span><span class="sxs-lookup"><span data-stu-id="305a5-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="305a5-105">針對所有控制項，您都可以使用 <xref:System.Windows.Forms.Control.Text%2A> 屬性來設定或傳回該文字。</span><span class="sxs-lookup"><span data-stu-id="305a5-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="305a5-106">您可以使用 <xref:System.Windows.Forms.Control.Font%2A> 屬性來變更字型。</span><span class="sxs-lookup"><span data-stu-id="305a5-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="305a5-107">若要設定文字和字型與設計工具</span><span class="sxs-lookup"><span data-stu-id="305a5-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="305a5-108">在 [屬性] 視窗中，設定<xref:System.Windows.Forms.Control.Text%2A>要適當的字串控制項屬性。</span><span class="sxs-lookup"><span data-stu-id="305a5-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="305a5-109">若要建立加底線的快速鍵，包括連字號 (&) 會成為快顯索引鍵的字母前面。</span><span class="sxs-lookup"><span data-stu-id="305a5-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="305a5-110">在 [屬性] 視窗中，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.Control.Font%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="305a5-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="305a5-111">在標準的字型 對話方塊中，選取您想要的字型、 字型樣式、 大小、 效果 （例如刪除線或底線） 和指令碼。</span><span class="sxs-lookup"><span data-stu-id="305a5-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="305a5-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="305a5-112">See Also</span></span>  
 [<span data-ttu-id="305a5-113">操作說明：設定由 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="305a5-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="305a5-114">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="305a5-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="305a5-115">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="305a5-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
