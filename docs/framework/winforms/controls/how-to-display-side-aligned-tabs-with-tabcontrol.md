---
title: 如何：使用 TabControl 顯示對齊側邊的定位點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: e145547ba4c8648a765e9507b7f35e50cb15fd82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532457"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="62c4f-102">如何：使用 TabControl 顯示對齊側邊的定位點</span><span class="sxs-lookup"><span data-stu-id="62c4f-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="62c4f-103"><xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.Alignment%2A> 屬性支援以垂直方式 (沿著控制項的左或右邊緣) 顯示索引標籤，而非水平方式 (橫跨控制項的頂端或底部) 。</span><span class="sxs-lookup"><span data-stu-id="62c4f-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="62c4f-104">根據預設，此垂直顯示會導致不良的使用者經驗，因為當啟用視覺化樣式時，<xref:System.Windows.Forms.TabPage> 物件的 <xref:System.Windows.Forms.TabPage.Text%2A> 屬性並不會在索引標籤中顯示。</span><span class="sxs-lookup"><span data-stu-id="62c4f-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="62c4f-105">也沒有直接控制索引標籤內文字方向的方式。您可以在 <xref:System.Windows.Forms.TabControl> 上面使用主控描繪，來改善這種經驗。</span><span class="sxs-lookup"><span data-stu-id="62c4f-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="62c4f-106">下列程序示範如何使用主控描繪功能來呈現靠右對齊的索引標籤，使索引標籤文字從左向右跑。</span><span class="sxs-lookup"><span data-stu-id="62c4f-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="62c4f-107">若要顯示靠右對齊的索引標籤</span><span class="sxs-lookup"><span data-stu-id="62c4f-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="62c4f-108">加入 <xref:System.Windows.Forms.TabControl> 至您的表單。</span><span class="sxs-lookup"><span data-stu-id="62c4f-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="62c4f-109">將 <xref:System.Windows.Forms.TabControl.Alignment%2A> 屬性設定為 <xref:System.Windows.Forms.TabAlignment.Right>。</span><span class="sxs-lookup"><span data-stu-id="62c4f-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="62c4f-110">設定 <xref:System.Windows.Forms.TabControl.SizeMode%2A> 屬性為 <xref:System.Windows.Forms.TabSizeMode.Fixed>，好讓所有的索引標籤有相同寬度。</span><span class="sxs-lookup"><span data-stu-id="62c4f-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="62c4f-111">設定 <xref:System.Windows.Forms.TabControl.ItemSize%2A> 屬性為索引標籤的慣用固定大小。</span><span class="sxs-lookup"><span data-stu-id="62c4f-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="62c4f-112">請記住，<xref:System.Windows.Forms.TabControl.ItemSize%2A> 屬性的行為如同索引標籤已在頂端，儘管它們是靠右對齊的。</span><span class="sxs-lookup"><span data-stu-id="62c4f-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="62c4f-113">因此，為了讓索引標籤更寬，您必須變更 <xref:System.Drawing.Size.Height%2A> 屬性，而且為了讓它們更高，您必須變更 <xref:System.Drawing.Size.Width%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="62c4f-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="62c4f-114">為了使下列程式碼範例獲得最佳結果，請設定索引標籤的 <xref:System.Drawing.Size.Width%2A> 為 25 ，並設定 <xref:System.Drawing.Size.Height%2A> 為 100。</span><span class="sxs-lookup"><span data-stu-id="62c4f-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="62c4f-115">將 <xref:System.Windows.Forms.TabControl.DrawMode%2A> 屬性設定為 <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>。</span><span class="sxs-lookup"><span data-stu-id="62c4f-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="62c4f-116">定義 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.DrawItem> 事件處理常式，這會從左到右呈現文字。</span><span class="sxs-lookup"><span data-stu-id="62c4f-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="62c4f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62c4f-117">See Also</span></span>  
 [<span data-ttu-id="62c4f-118">TabControl 控制項</span><span class="sxs-lookup"><span data-stu-id="62c4f-118">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
