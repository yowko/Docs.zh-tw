---
title: 如何：為已拖曳的 GridView 資料行行首建立樣式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: 2e57b4cb1b8ddb90e8e6e0abc6db3e7f0b864cfa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554569"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>如何：為已拖曳的 GridView 資料行行首建立樣式
這個範例示範如何變更外觀拖曳的<xref:System.Windows.Controls.GridViewColumnHeader>當使用者變更資料行的位置。  
  
## <a name="example"></a>範例  
 將資料行標頭拖曳到另一個位置<xref:System.Windows.Controls.ListView>使用<xref:System.Windows.Controls.GridView>其檢視模式中，資料行移到新位置。 當您拖曳資料行標頭時，浮動標頭中的複本會顯示除了原始的標頭。 中的資料行標頭<xref:System.Windows.Controls.GridView>由<xref:System.Windows.Controls.GridViewColumnHeader>物件。  
  
 若要自訂的浮點數和原始標頭的外觀，您可以設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>修改<xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>。 這些<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>時套用<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>屬性值是`true`和<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性值是<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。  
  
 當使用者按下滑鼠按鈕並按住它時滑鼠停留在<xref:System.Windows.Controls.GridViewColumnHeader>、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>屬性值變更為`true`。 同樣地，當使用者開始拖曳作業時，才<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>屬性變更為<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。  
  
 下列範例示範如何設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>變更<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.Background%2A>原始和浮動標頭時使用者會將資料行拖曳至新位置的色彩。  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView 概觀](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView 概觀](../../../../docs/framework/wpf/controls/gridview-overview.md)
