---
title: HOW TO：為已拖曳的 GridView 資料行行首建立樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: dd347781451c9e574fed97c1a553c25bda1b8d7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545393"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>HOW TO：為已拖曳的 GridView 資料行行首建立樣式
此範例示範如何變更外觀的拖曳<xref:System.Windows.Controls.GridViewColumnHeader>當使用者變更資料行的位置。  
  
## <a name="example"></a>範例  
 當您拖曳資料行標頭中的另一個位置<xref:System.Windows.Controls.ListView>使用<xref:System.Windows.Controls.GridView>其檢視模式中，資料行移至新的位置。 當您拖曳資料行標頭時，則會在原始標頭除了出現標頭的浮動複本。 中的資料行標頭<xref:System.Windows.Controls.GridView>由<xref:System.Windows.Controls.GridViewColumnHeader>物件。  
  
 若要自訂的浮點數和原始標頭的外觀，您可以設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>來修改<xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>。 這些<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>時套用<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>屬性值是`true`並<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性值是<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。  
  
 當使用者按下滑鼠按鈕並按住它時滑鼠暫停在<xref:System.Windows.Controls.GridViewColumnHeader>，則<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>屬性值變更為`true`。 同樣地，當使用者開始拖曳作業時，才<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性變更為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。  
  
 下列範例示範如何設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>若要變更<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.Background%2A>原始和浮動標頭時的使用者會將資料行拖曳至新位置的色彩。  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [HOW-TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
- [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)
- [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)
