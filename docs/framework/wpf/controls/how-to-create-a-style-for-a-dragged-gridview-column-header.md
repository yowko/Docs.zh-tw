---
title: HOW TO：為拖曳的 GridView 資料行標題建立樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: dbcdd38e0397b8e637aff962420a2959f33203df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090091"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a><span data-ttu-id="8672b-102">HOW TO：為拖曳的 GridView 資料行標題建立樣式</span><span class="sxs-lookup"><span data-stu-id="8672b-102">How to: Create a Style for a Dragged GridView Column Header</span></span>
<span data-ttu-id="8672b-103">此範例示範如何變更外觀的拖曳<xref:System.Windows.Controls.GridViewColumnHeader>當使用者變更資料行的位置。</span><span class="sxs-lookup"><span data-stu-id="8672b-103">This example shows how to change the appearance of a dragged <xref:System.Windows.Controls.GridViewColumnHeader> when the user changes the position of a column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8672b-104">範例</span><span class="sxs-lookup"><span data-stu-id="8672b-104">Example</span></span>  
 <span data-ttu-id="8672b-105">當您拖曳資料行標頭中的另一個位置<xref:System.Windows.Controls.ListView>使用<xref:System.Windows.Controls.GridView>其檢視模式中，資料行移至新的位置。</span><span class="sxs-lookup"><span data-stu-id="8672b-105">When you drag a column header to another location in a <xref:System.Windows.Controls.ListView> that uses <xref:System.Windows.Controls.GridView> for its view mode, the column moves to the new position.</span></span> <span data-ttu-id="8672b-106">當您拖曳資料行標頭時，則會在原始標頭除了出現標頭的浮動複本。</span><span class="sxs-lookup"><span data-stu-id="8672b-106">While you are dragging the column header, a floating copy of the header appears in addition to the original header.</span></span> <span data-ttu-id="8672b-107">中的資料行標頭<xref:System.Windows.Controls.GridView>由<xref:System.Windows.Controls.GridViewColumnHeader>物件。</span><span class="sxs-lookup"><span data-stu-id="8672b-107">A column header in a <xref:System.Windows.Controls.GridView> is represented by a <xref:System.Windows.Controls.GridViewColumnHeader> object.</span></span>  
  
 <span data-ttu-id="8672b-108">若要自訂的浮點數和原始標頭的外觀，您可以設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>來修改<xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>。</span><span class="sxs-lookup"><span data-stu-id="8672b-108">To customize the appearance of both the floating and original headers, you can set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to modify the <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>.</span></span> <span data-ttu-id="8672b-109">這些<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>時套用<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>屬性值是`true`並<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性值是<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。</span><span class="sxs-lookup"><span data-stu-id="8672b-109">These <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> are applied when the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value is `true` and the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property value is <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="8672b-110">當使用者按下滑鼠按鈕並按住它時滑鼠暫停在<xref:System.Windows.Controls.GridViewColumnHeader>，則<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>屬性值變更為`true`。</span><span class="sxs-lookup"><span data-stu-id="8672b-110">When the user presses the mouse button and holds it down while the mouse pauses on the <xref:System.Windows.Controls.GridViewColumnHeader>, the <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> property value changes to `true`.</span></span> <span data-ttu-id="8672b-111">同樣地，當使用者開始拖曳作業時，才<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性變更為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。</span><span class="sxs-lookup"><span data-stu-id="8672b-111">Likewise, when the user begins the drag operation, the <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> property changes to <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.</span></span>  
  
 <span data-ttu-id="8672b-112">下列範例示範如何設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>若要變更<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.Background%2A>原始和浮動標頭時的使用者會將資料行拖曳至新位置的色彩。</span><span class="sxs-lookup"><span data-stu-id="8672b-112">The following example shows how to set <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> to change the <xref:System.Windows.Controls.Control.Foreground%2A> and <xref:System.Windows.Controls.Control.Background%2A> colors of the original and floating headers when the user drags a column to a new position.</span></span>  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a><span data-ttu-id="8672b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8672b-113">See also</span></span>

- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="8672b-114">HOW TO 主題</span><span class="sxs-lookup"><span data-stu-id="8672b-114">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="8672b-115">ListView 概觀</span><span class="sxs-lookup"><span data-stu-id="8672b-115">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="8672b-116">GridView 概觀</span><span class="sxs-lookup"><span data-stu-id="8672b-116">GridView Overview</span></span>](gridview-overview.md)
