---
title: HOW TO：在 Windows Form ListView 控制項中的群組項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
ms.openlocfilehash: 52030b78b95d88432a5cac9b089ab87ca6d4f534
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500703"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>HOW TO：在 Windows Form ListView 控制項中的群組項目
使用群組功能的<xref:System.Windows.Forms.ListView>控制項，您可以在群組中顯示相關的項目集。 這些群組是在螢幕上分隔包含群組標題的水平群組標頭。 您可以使用<xref:System.Windows.Forms.ListView>群組，使導覽更容易的大型清單依字母順序，分組項目，依日期，或任何其他的邏輯群組。 下圖顯示一些分組的項目。  
  
 ![ListView 群組](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
ListView 群組項目  
  
 若要啟用群組，您必須先建立一個或多個群組，在設計工具或以程式設計的方式。 在定義的群組之後，您可以指派<xref:System.Windows.Forms.ListView>給群組的項目。 您也可以移動項目從一個群組到另一個以程式設計的方式。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> 群組是僅適用於[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]當您的應用程式呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法。 在舊版的作業系統，與群組相關的任何程式碼沒有任何作用，並不會出現群組。 如需詳細資訊，請參閱<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>。  
  
### <a name="to-add-groups"></a>若要加入群組  
  
1.  使用 <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> 集合的 <xref:System.Windows.Forms.ListView.Groups%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>若要移除群組  
  
1.  使用<xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>或是<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>方法<xref:System.Windows.Forms.ListView.Groups%2A>集合。  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>方法會移除單一群組;<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>方法從清單中移除所有群組。  
  
    > [!NOTE]
    >  移除群組並不會移除該群組內的項目。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>若要將項目指派給群組，或在群組之間移動項目  
  
1.  設定<xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType>屬性的個別項目。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView 控制項](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Windows XP 功能和 Windows Forms 控制項](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
- [如何：新增和移除項目，使用 Windows Forms ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
