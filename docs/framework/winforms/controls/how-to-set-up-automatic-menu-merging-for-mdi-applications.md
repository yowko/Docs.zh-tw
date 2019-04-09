---
title: HOW TO：設定 MDI 應用程式的自動功能表合併功能
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: 17edde6e3968823abc915eb5faed6d2751ed9393
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129346"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="51c94-102">HOW TO：設定 MDI 應用程式的自動功能表合併功能</span><span class="sxs-lookup"><span data-stu-id="51c94-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="51c94-103">下列程序提供的基本步驟來設定在多重文件介面 (MDI) 應用程式中使用的自動合併<xref:System.Windows.Forms.MenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="51c94-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="51c94-104">若要設定自動功能表合併功能</span><span class="sxs-lookup"><span data-stu-id="51c94-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="51c94-105">建立 MDI 父表單，藉由設定其<xref:System.Windows.Forms.Form.IsMdiContainer%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="51c94-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="51c94-106">新增<xref:System.Windows.Forms.MenuStrip>到 MDI 父代，設定其<xref:System.Windows.Forms.Form.MainMenuStrip%2A>屬性， <xref:System.Windows.Forms.MenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="51c94-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="51c94-107">建立 MDI 子表單，並設定其<xref:System.Windows.Forms.Form.MdiParent%2A>屬性，以父表單的名稱。</span><span class="sxs-lookup"><span data-stu-id="51c94-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="51c94-108">新增<xref:System.Windows.Forms.MenuStrip>MDI 子表單。</span><span class="sxs-lookup"><span data-stu-id="51c94-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="51c94-109">在 子表單中，設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>的屬性<xref:System.Windows.Forms.MenuStrip>至`false`。</span><span class="sxs-lookup"><span data-stu-id="51c94-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="51c94-110">將功能表項目新增至子表單<xref:System.Windows.Forms.MenuStrip>想要合併至父表單的<xref:System.Windows.Forms.MenuStrip>何時啟動的子表單。</span><span class="sxs-lookup"><span data-stu-id="51c94-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="51c94-111">使用<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A>功能表上的屬性項目在子表單的<xref:System.Windows.Forms.MenuStrip>來控制它們合併至父表單的方式。</span><span class="sxs-lookup"><span data-stu-id="51c94-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c94-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51c94-112">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="51c94-113">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="51c94-113">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
