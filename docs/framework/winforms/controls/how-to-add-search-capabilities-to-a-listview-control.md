---
title: 如何：將搜尋能力加入至 ListView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: 2049638998f7a8d099e14fab9c95384a49c67833
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528270"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>如何：將搜尋能力加入至 ListView 控制項
有時候當使用大型清單中的項目時，才<xref:System.Windows.Forms.ListView>控制項，您想要提供給使用者的搜尋能力。 <xref:System.Windows.Forms.ListView>控制兩個不同的方式提供這項功能： 文字比對和搜尋的位置。  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>方法可讓您執行的文字搜尋<xref:System.Windows.Forms.ListView>在清單或詳細資料檢視中，指定搜尋字串和選擇性的開始和結束索引。 相反地，<xref:System.Windows.Forms.ListView.FindNearestItem%2A>方法可讓您尋找中的項目<xref:System.Windows.Forms.ListView>在圖示或並排顯示檢視中，提供一組 x 和 y 座標和搜尋方向。  
  
### <a name="to-find-an-item-using-text"></a>若要尋找的項目，使用文字  
  
1.  建立<xref:System.Windows.Forms.ListView>與<xref:System.Windows.Forms.ListView.View%2A>屬性設定為<xref:System.Windows.Forms.View.Details>或<xref:System.Windows.Forms.View.List>，並於其中填入<xref:System.Windows.Forms.ListView>與項目。  
  
2.  呼叫<xref:System.Windows.Forms.ListView.FindItemWithText%2A>方法，傳遞您想要尋找之項目的文字。  
  
3.  下列程式碼範例示範如何建立基本<xref:System.Windows.Forms.ListView>，填入項目，並使用使用者的文字輸入清單中尋找項目。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>若要尋找使用 x 和 y 座標的項目  
  
1.  建立<xref:System.Windows.Forms.ListView>與<xref:System.Windows.Forms.View>屬性設定為<xref:System.Windows.Forms.View.SmallIcon>或<xref:System.Windows.Forms.View.LargeIcon>，並於其中填入<xref:System.Windows.Forms.ListView>與項目。  
  
2.  呼叫<xref:System.Windows.Forms.ListView.FindNearestItem%2A>方法，傳遞所需 x 和 y 座標和您想要搜尋的方向。  
  
3.  下列程式碼範例示範如何建立基本的圖示<xref:System.Windows.Forms.ListView>，填入項目和擷取<xref:System.Windows.Forms.Control.MouseDown>事件，以尋找最新的方向中最接近的項目。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
