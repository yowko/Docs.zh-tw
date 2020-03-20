---
title: 清單查看控制項中的組專案
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
ms.openlocfilehash: a1754d10de2bbb5895ae861cd17f4af1f18810e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141987"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>如何：在 Windows Form ListView 控制項中群組項目
使用<xref:System.Windows.Forms.ListView>控制項的分組功能，可以分組顯示相關的專案集。 這些組在螢幕上由包含組標題的水準組標題分隔。 您可以使用<xref:System.Windows.Forms.ListView>組通過按字母順序、按日期或通過任何其他邏輯分組對專案進行分組，使導航大型清單變得更加容易。 下圖顯示了一些分組專案。  
  
 ![奇數和偶數清單視圖組的螢幕截圖。](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)  

 要啟用分組，必須首先在設計器中或以程式設計方式創建一個或多個組。 定義組後，可以將專案分配給<xref:System.Windows.Forms.ListView>組。 您還可以以程式設計方式將專案從一個組移動到另一個組。  
  
### <a name="to-add-groups"></a>添加組  
  
1. 使用 <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> 集合的 <xref:System.Windows.Forms.ListView.Groups%2A> 方法。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>刪除組  
  
1. 使用<xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>集合<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>的<xref:System.Windows.Forms.ListView.Groups%2A>或 方法。  
  
     該方法<xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A>刪除單個組;因此，該方法將刪除單個組。該方法<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A>從清單中刪除所有組。  
  
    > [!NOTE]
    > 刪除組不會刪除該組中的專案。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>將專案分配給組或在組之間移動專案  
  
1. 設置<xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType>單個項的屬性。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView 控制項](listview-control-windows-forms.md)
- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
