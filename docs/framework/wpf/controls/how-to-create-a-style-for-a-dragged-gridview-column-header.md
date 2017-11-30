---
title: "如何：為已拖曳的 GridView 資料行行首建立樣式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 503683de875b8853e219139800eef2a5417a1574
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="277a9-102">如何：為已拖曳的 GridView 資料行行首建立樣式</span><span class="sxs-lookup"><span data-stu-id="277a9-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="277a9-103">這個範例示範如何變更外觀拖曳的<xref:System.Windows.Controls.GridViewColumnHeader>當使用者變更資料行的位置。</span><span class="sxs-lookup"><span data-stu-id="277a9-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="277a9-104">範例</span><span class="sxs-lookup"><span data-stu-id="277a9-104">Example</span></span>  
 <span data-ttu-id="277a9-105">將資料行標頭拖曳到另一個位置<xref:System.Windows.Controls.ListView>使用<xref:System.Windows.Controls.GridView>其檢視模式中，資料行移到新位置。</span><span class="sxs-lookup"><span data-stu-id="277a9-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="277a9-106">當您拖曳資料行標頭時，浮動標頭中的複本會顯示除了原始的標頭。</span><span class="sxs-lookup"><span data-stu-id="277a9-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="277a9-107">中的資料行標頭<xref:System.Windows.Controls.GridView>由<xref:System.Windows.Controls.GridViewColumnHeader>物件。</span><span class="sxs-lookup"><span data-stu-id="277a9-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="277a9-108">若要自訂的浮點數和原始標頭的外觀，您可以設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>修改<xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>。</span><span class="sxs-lookup"><span data-stu-id="277a9-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="277a9-109">這些<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>時套用<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>屬性值是`true`和<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性值是<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。</span><span class="sxs-lookup"><span data-stu-id="277a9-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="277a9-110">當使用者按下滑鼠按鈕並按住它時滑鼠停留在<xref:System.Windows.Controls.GridViewColumnHeader>、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>屬性值變更為`true`。</span><span class="sxs-lookup"><span data-stu-id="277a9-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="277a9-111">同樣地，當使用者開始拖曳作業時，才<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性變更為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。</span><span class="sxs-lookup"><span data-stu-id="277a9-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="277a9-112">下列範例示範如何設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>變更<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.Background%2A>原始和浮動標頭時使用者會將資料行拖曳至新位置的色彩。</span><span class="sxs-lookup"><span data-stu-id="277a9-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="277a9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="277a9-113">See Also</span></span>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="277a9-114">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="277a9-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="277a9-115">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="277a9-115">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="277a9-116">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="277a9-116">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
